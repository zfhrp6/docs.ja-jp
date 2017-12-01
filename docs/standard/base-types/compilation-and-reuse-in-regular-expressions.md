---
title: "正規表現におけるコンパイルと再利用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 76acdf2d0d2f7805ec78ea44136bfc63441b9bc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>正規表現におけるコンパイルと再利用
正規表現エンジンが式をどのようにコンパイルするか、および正規表現がどのようにキャッシュされるかを理解することで、正規表現を幅広く使用するアプリケーションのパフォーマンスを最適化できます。 このトピックでは、コンパイルとキャッシュの両方について説明します。  
  
## <a name="compiled-regular-expressions"></a>コンパイルされた正規表現  
 既定では、正規表現エンジンは、内部命令のシーケンス (Microsoft 中間言語 (MSIL) とは異なる高度なコード) に正規表現をコンパイルします。 エンジンは、正規表現を実行するときに内部コードを解釈します。  
  
 場合、<xref:System.Text.RegularExpressions.Regex>にオブジェクトを構築、<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>オプション、高度な正規表現内部の手順ではなく明示的な MSIL コードを正規表現をコンパイルします。 これにより、.NET の Just-In-Time (JIT) コンパイラは、式をネイティブのマシン コードに変換してパフォーマンスを高めることができます。  
  
ただし、生成された MSIL をアンロードすることはできません。 コードをアンロードする唯一の方法は、アプリケーション ドメイン全体をアンロードする (つまり、アプリケーションのすべてのコードをアンロードする) ことです。 実際には、正規表現をコンパイルした後、<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>オプションで、正規表現が作成した場合でも、コンパイル済みの式で使用したリソースを解放しない、<xref:System.Text.RegularExpressions.Regex>ガベージ コレクションにリリースされた自体であるオブジェクト。  
  
 コンパイルすると、さまざまな正規表現の数を制限するように注意する必要があります、<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>多くのリソースを消費しないようにするにはオプションです。 アプリケーションで多数または無制限の数の正規表現を使用しなければならない場合は、各式をコンパイルするのではなく、解釈する必要があります。 ただし、正規表現の数が少ないを繰り返し使用する場合、コンパイルは<xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>パフォーマンスが向上します。 代わりに、プリコンパイル済みの正規表現の使用を開始します。 すべての dll を再利用可能な表現を使用してコンパイルすることができます、<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>メソッドです。 これにより、コンパイルされた正規表現の速度も維持しながら、実行時にコンパイルする必要があります。  
  
## <a name="the-regular-expressions-cache"></a>正規表現のキャッシュ  
 パフォーマンスを高めるために、正規表現エンジンは、コンパイルされた正規表現のアプリケーション全体のキャッシュを保持します。 キャッシュは、静的メソッド呼び出しでのみ使用される正規表現パターンを格納します (インスタンス メソッドに渡される正規表現パターンはキャッシュされません)。これにより、式を使用するたびに高度なバイト コードに再解析する必要がなくなります。  
  
 キャッシュの正規表現の最大数の値によって決まります、 `static` (`Shared` Visual Basic で)<xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>プロパティです。 既定では、正規表現エンジンは最大 15 個のコンパイルされた正規表現をキャッシュします。 コンパイルされた正規表現の数がキャッシュ サイズを超えた場合は、最近の使用頻度が最も低い正規表現が破棄され、新しい正規表現がキャッシュされます。  
  
 アプリケーションでは、次の 2 つの方法のいずれかでプリコンパイル済みの正規表現を利用できます。  
  
-   静的メソッドを使用して、<xref:System.Text.RegularExpressions.Regex>正規表現を定義するオブジェクト。 別の静的メソッド呼び出しで既に定義されている正規表現パターンを使用している場合、正規表現エンジンはこれをキャッシュから取得します。 そうでない場合、エンジンは正規表現をコンパイルしてキャッシュに追加します。  
  
-   既存の再利用して<xref:System.Text.RegularExpressions.Regex>オブジェクトの正規表現パターンが必要な限り、します。  
  
 オブジェクトのインスタンス化と作成と破棄迅速に、さまざまな正規表現のコンパイル時のオーバーヘッドが原因<xref:System.Text.RegularExpressions.Regex>オブジェクトは、非常に高価なプロセスです。 多数の異なる正規表現を使用するアプリケーションでは、静的に呼び出しを使用してパフォーマンスを最適化できます`Regex`メソッドおよび可能性のあるによって、正規表現のキャッシュのサイズを大ききます。  
  
## <a name="see-also"></a>関連項目  
 [.NET の正規表現](../../../docs/standard/base-types/regular-expressions.md)

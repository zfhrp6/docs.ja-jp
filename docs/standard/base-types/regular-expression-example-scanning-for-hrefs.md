---
title: "正規表現の例: HREFS のスキャン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a>正規表現の例: HREFS のスキャン
次の例では、入力文字列を検索して、文字列中のすべての href="…" 値とその場所を表示します。  
  
## <a name="the-regex-object"></a>Regex オブジェクト  
 `DumpHRefs`メソッドは、ユーザー コードから複数回呼び出すことがあります、これを使用して、 `static` (`Shared` Visual Basic で)<xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>メソッドです。 これにより、正規表現をキャッシュする正規表現エンジンを新しいのインスタンス化のオーバーヘッドを回避<xref:System.Text.RegularExpressions.Regex>オブジェクト、メソッドが呼び出されるたびにします。 A<xref:System.Text.RegularExpressions.Match>オブジェクトを文字列に一致するすべての反復処理に使用しています。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 `DumpHRefs` メソッドを呼び出す例を次に示します。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 この正規表現パターン `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` の解釈を次の表に示します。  
  
|パターン|説明|  
|-------------|-----------------|  
|`href`|リテラル文字列 "href" と一致します。 一致では、大文字と小文字を区別しません。|  
|`\s*`|0 個以上の空白文字と一致します。|  
|`=`|等号と一致します。|  
|`\s*`|0 個以上の空白文字と一致します。|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|キャプチャされたグループに、結果を割り当てずに、次のいずれかに一致します。<br /><br /> は、引用符または引用符または後に引用符またはアポストロフィ アポストロフィ以外の任意の文字の 0 個以上の出現が続くアポストロフィです。 このパターンには `1` という名前のグループが含まれています。<br />-1 つ以上の空白以外の文字。 このパターンには `1` という名前のグループが含まれています。|  
|`(?<1>[^"']*)`|引用符またはアポストロフィ以外の任意の文字の 0 回以上の繰り返しを `1` という名前のキャプチャ グループに代入します。|  
|`"(?<1>\S+)`|1 個以上の空白以外の文字を `1` という名前のキャプチャ グループに代入します。|  
  
## <a name="match-result-class"></a>Match 結果クラス  
 検索の結果が格納されている、<xref:System.Text.RegularExpressions.Match>検索で抽出されたすべての部分文字列へのアクセスを提供するクラス。 情報も保存されて検索対象の文字列と正規表現が使用されているため、呼び出すことができます、<xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>から別の検索最後の 1 つの終了位置を実行するメソッド。  
  
## <a name="explicitly-named-captures"></a>明示的に指定したキャプチャ  
 従来の正規表現では、キャプチャするかっこに自動的に連番が割り当てられます。 その結果、2 つの問題が発生します。 1 つ目の問題は、かっこのペアの挿入や削除を行って正規表現が修正されると、新しい番号を反映するために、番号付きのキャプチャを参照するコードをすべて書き直す必要があることです。 2 つ目の問題は、ある文字列の検索用に 2 つの代替表現を指定する際、異なるかっこのペアを使用することが多いため、実際にどちらの代替表現から結果が返されたのかを判断するのが難しい場合があることです。  
  
 これらの問題に対処する、<xref:System.Text.RegularExpressions.Regex>クラスには、構文がサポートしている`(?<name>…)`指定されたスロットに一致するものをキャプチャするため (スロットの名前は、文字列または整数を使用して、整数をより迅速に取り消すことができる)。 これにより、同じ文字列に対する代替表現の一致結果をすべて同じ場所に渡すことができます。 競合が発生する場合は、スロットにキャプチャされた最後の一致文字列が、適切な一致であると見なされます。 (ただし、1 つのスロットで複数の一致文字列の完全なリストを使用することもできます。 参照してください、<xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType>詳細のコレクション)。  
  
## <a name="see-also"></a>関連項目  
 [.NET の正規表現](../../../docs/standard/base-types/regular-expressions.md)

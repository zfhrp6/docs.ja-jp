---
title: "正規表現におけるコンパイルと再利用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 正規表現, コンパイル"
  - ".NET Framework 正規表現, エンジン"
  - "コンパイル, 正規表現"
  - "解析 (正規表現を使用したテキストを), コンパイル"
  - "パターン一致 (正規表現を使用した), コンパイル"
  - "正規表現, コンパイル"
  - "正規表現, エンジン"
  - "検索 (正規表現を使用した), コンパイル"
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 正規表現におけるコンパイルと再利用
正規表現エンジンが表現をどのようにコンパイルするか、および正規表現がどのようにキャッシュされるかを理解すると、正規表現を多く使用するアプリケーションのパフォーマンスを最適化できます。  このトピックでは、コンパイルとキャッシュの両方について説明します。  
  
## コンパイルされた正規表現  
 既定では、正規表現エンジンは正規表現をコンパイルして内部命令のシーケンスを生成します。これらは Microsoft Intermediate Language \(MSIL\) とは別の高水準コードです。  エンジンは正規表現を実行するときに、その内部コードを解釈します。  
  
 <xref:System.Text.RegularExpressions.Regex> オブジェクトを構築するときに <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> オプションを使用すると、正規表現エンジンは、高水準の正規表現内部命令ではなく、明示的な MSIL コードに正規表現をコンパイルします。  これにより、.NET Framework の JIT \(Just\-In\-Time\) コンパイラは、正規表現をネイティブな機械語コードに変換してパフォーマンスの向上を図ることができます。  
  
 ただし、生成された MSIL はアンロードできません。  コードをアンロードする唯一の方法は、アプリケーション ドメイン全体をアンロードする \(つまり、アプリケーションのコードをすべてアンロードする\) ことです。  実際、<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> オプションを使用して正規表現をコンパイルした場合は、その正規表現を作成した <xref:System.Text.RegularExpressions.Regex> オブジェクト自体がガベージ コレクションで解放されたとしても、コンパイル済みの正規表現によって使用されるリソースを .NET Framework が解放することはありません。  
  
 このため、<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> オプションを使用してコンパイルする正規表現の数を制限することで、リソースの消費が過度にならないように注意する必要があります。  大量または無制限の正規表現をアプリケーションで使用する必要がある場合、**Options.Compiled** オプションを使用したコンパイルを行わないようにします。  ただし、少数の正規表現を繰り返して使用する場合は、パフォーマンスを向上させるために、<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> を使用して正規表現をコンパイルする必要があります。  別の方法として、プリコンパイル済みの正規表現を使用することもできます。  <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> メソッドを使用すると、再利用できる DLL にすべての表現をコンパイルできます。  これにより、実行時にコンパイルする必要がなくなり、コンパイルされた正規表現の処理速度も維持されます。  
  
## 正規表現キャッシュ  
 パフォーマンスを向上させるために、正規表現エンジンは、コンパイル済みの正規表現のキャッシュをアプリケーション全体で保持します。  このキャッシュには、静的メソッド呼び出しでのみ使用される正規表現パターンが格納されます \(インスタンス メソッドに渡される正規表現パターンはキャッシュされません\)。これにより、正規表現を使用するたびに解析し直して高水準のバイト コードを生成する必要がなくなります。  
  
 キャッシュされる正規表現の最大数は、`static` \(Visual Basic では `Shared`\) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=fullName> プロパティの値で決まります。  既定では、正規表現エンジンは最大で 15 個のコンパイル済み正規表現をキャッシュします。  コンパイル済み正規表現の数がキャッシュ サイズを超えると、最後に使用されてからの時間が最も長い正規表現が破棄され、新しい正規表現がキャッシュされます。  
  
> [!IMPORTANT]
>  .NET Framework Version 2.0 での正規表現のキャッシュ方法は、.NET Framework Version 1.0 および 1.1 とは大きく異なります。  .NET Framework 1.0 および 1.1 では、静的メソッド呼び出しとインスタンス メソッド呼び出しの両方で使用されるすべての正規表現がキャッシュされます。  このキャッシュは、新しい正規表現を格納するために自動的に拡張されます。  .NET Framework 2.0 では、静的メソッド呼び出しで使用された正規表現のみがキャッシュされます。  既定では最新の 15 個の正規表現だけがキャッシュされますが、キャッシュのサイズは <xref:System.Text.RegularExpressions.Regex.CacheSize%2A> プロパティの値を設定することで調整できます。  
  
 アプリケーションでは、次の 2 つの方法のいずれかにより、プリコンパイル済みの正規表現を利用できます。  
  
-   <xref:System.Text.RegularExpressions.Regex> オブジェクトの静的メソッドを使用して、正規表現を定義します。  別の静的メソッド呼び出しで既に定義されている正規表現パターンを使用する場合、正規表現エンジンはその表現をキャッシュから取得します。  それ以外の場合、エンジンは正規表現をコンパイルしてキャッシュに追加します。  
  
-   正規表現パターンが必要な場合に、既存の <xref:System.Text.RegularExpressions.Regex> オブジェクトを再利用します。  
  
 オブジェクトのインスタンス化と正規表現のコンパイルによって生じるオーバーヘッドのため、多数の <xref:System.Text.RegularExpressions.Regex> オブジェクトを作成してすぐに破棄するのは効率が良くありません。  多数の異なる正規表現を使用するアプリケーションでは、静的な `Regex` メソッドの呼び出しを使用することと、必要に応じて正規表現キャッシュのサイズを大きくすることで、パフォーマンスを最適化できます。  
  
## 参照  
 [.NET Framework の正規表現](../../../docs/standard/base-types/regular-expressions.md)
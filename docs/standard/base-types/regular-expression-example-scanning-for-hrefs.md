---
title: "正規表現の例: HREFS のスキャン | Microsoft Docs"
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
  - "検索 (正規表現を使用した)、例"
  - "解析 (テキストを正規表現で)、例"
  - "正規表現、例"
  - ".NET Framework 正規表現、例"
  - "正規表現 [.NET Framework]、例"
  - "パターン一致 (正規表現を使用した)、例"
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# 正規表現の例: HREFS のスキャン
次の例では、入力文字列を検索して、表示されるすべての href\=」…」 文字列の値と場所。  
  
## Regex オブジェクト  
 `DumpHRefs` メソッドは、ユーザー コードから複数回呼び出される可能性があるため、`static` \(Visual Basic では `Shared`\) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> メソッドを使用します。  これにより、正規表現エンジンが正規表現をキャッシュできるようになり、メソッドを呼び出すたびに新しい <xref:System.Text.RegularExpressions.Regex> オブジェクトをインスタンス化するオーバーヘッドを回避できます。  <xref:System.Text.RegularExpressions.Match> オブジェクトは、文字列内のすべての一致を反復処理するために使用されます。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 `DumpHRefs` メソッドを呼び出す例を次に示します。  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 正規表現パターン `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` の解釈を次の表に示します。  
  
|パターン|説明|  
|----------|--------|  
|`href`|リテラル文字列 "href" と一致します。  一致では、大文字と小文字を区別しません。|  
|`\s*`|0 個以上の空白文字と一致します。|  
|`=`|等号と一致します。|  
|`\s*`|0 個以上の空白文字と一致します。|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|次のいずれかと一致し、結果をキャプチャされたグループに代入しません。<br /><br /> -   引用符または二重引用符またはアポストロフィ以外の任意の文字のゼロ以上の後に続くアポストロフィ引用符またはアポストロフィしています。  このパターンには `1` という名前のグループが含まれています。<br />-   1 つ以上の空白以外の文字。  このパターンには `1` という名前のグループが含まれています。|  
|`(?<1>[^"']*)`|引用符以外の文字または `1`という名前のキャプチャ グループに代入アポストロフィのゼロ以上の繰り返しを検索します。|  
|`"(?<1>\S+)`|空白以外の 1 個以上の文字を、`1` という名前のキャプチャ グループに代入します。|  
  
## Match 結果クラス  
 検索結果は <xref:System.Text.RegularExpressions.Match> クラス内に格納されます。これにより、検索処理によって抽出されたすべての部分文字列にアクセスできます。  このクラスは、検索対象となった文字列や、使用された正規表現も記憶しているため、最後に検索が実行された位置から別の検索を実行するときに、<xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=fullName> メソッドを呼び出すことができます。  
  
## 明示的に指定したキャプチャ  
 従来の正規表現では、キャプチャするためのかっこに自動的に連番が割り当てられます。  その結果、2 つの問題が発生します。  1 つ目の問題は、かっこのペアの挿入や削除により、ある正規表現が修正されると、新しい番号を反映するために、番号付きのキャプチャを参照するコードをすべて書き直す必要があることです。  2 つ目の問題は、ある文字列の検索用に 2 つの代替表現を用意するにあたって、さまざまなかっこを使用することがあるため、実際にどちらの代替表現から結果が返されたのかを判断するのが難しくなる可能性があることです。  
  
 これらの問題に対処するために、<xref:System.Text.RegularExpressions.Regex> クラスは指定されたスロットに一致文字列をキャプチャするための構文 `(?<name>…)` をサポートしています。このスロットには、文字列または整数の名前を付けることができます。整数の名前を付けた方が、よりすばやく再呼び出しできます。  この方法により、同一文字列に対する代替表現に一致した文字列をすべて同じスロットにキャプチャできます。  競合が発生する場合は、スロットに最後にキャプチャされた一致文字列が、正当な一致文字列と見なされます。\(しかし、1 つのスロットに対して複数の一致対象の完全なリストを使用できます。  詳細については、<xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=fullName> コレクションを参照してください。\)  
  
## 参照  
 [.NET Framework の正規表現](../../../docs/standard/base-types/regular-expressions.md)
---
title: "方法 : 文字列から無効な文字を取り除く | Microsoft Docs"
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
  - "正規表現、例"
  - "整形 (入力の)"
  - "ユーザー入力、例"
  - ".NET Framework 正規表現、例"
  - "正規表現 [.NET Framework]、例"
  - "Regex.Replace メソッド"
  - "削除 (無効な文字列を)"
  - "Replace メソッド"
  - "検証 (ユーザー入力の)"
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : 文字列から無効な文字を取り除く
静的な <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> メソッドを使用して、文字列から無効な文字を取り除く例を次に示します。  
  
## 使用例  
 この例で定義した `CleanInput` メソッドを使用すると、ユーザーがテキスト フィールドで入力した文字列の中から、潜在的な危険性がある文字を取り除くことができます。  この場合、`CleanInput` は、ピリオド \(.\)、アット マーク \(@\)、およびハイフン \(\-\) 以外のすべての非英数文字を取り除き、残りの文字列を返します。  ただし、入力文字列に含めてはいけないすべての文字を取り除くように正規表現パターンを変更することができます。  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 正規表現パターン `[^\w\.@-]` は、単語に使用される文字、ピリオド、@ 記号、またはハイフン以外の任意の文字と一致します。  単語に使用される文字は、任意の文字、10 進数字、またはアンダースコアなどのコネクタ区切り記号です。  このパターンに一致する文字は、置換パターンで定義された文字列である <xref:System.String.Empty?displayProperty=fullName> に置き換えられます。  ユーザー入力でその他の文字を許可するには、それらの文字を正規表現パターンの文字クラスに追加します。  たとえば、正規表現パターン `[^\w\.@-\\%]` は、入力文字列でパーセント記号と円記号も許可します。  
  
## 参照  
 [.NET Framework の正規表現](../../../docs/standard/base-types/regular-expressions.md)
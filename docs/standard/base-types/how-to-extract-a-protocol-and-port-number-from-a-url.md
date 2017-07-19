---
title: "方法 : URL からプロトコルとポート番号を抽出する | Microsoft Docs"
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
  - ".NET Framework 正規表現, 例"
  - "解析 (正規表現を使用したテキストを), 例"
  - "パターン一致 (正規表現を使用した), 例"
  - "正規表現 [.NET Framework], 例"
  - "正規表現, 例"
  - "検索 (正規表現を使用した), 例"
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : URL からプロトコルとポート番号を抽出する
URL からプロトコルとポート番号を抽出する例を次に示します。  
  
## 使用例  
 この例では、<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> メソッドを使用して、プロトコルとそれに続くコロンおよびポート番号を返します。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` は、次の表に示すように解釈できます。  
  
|パターン|説明|  
|----------|--------|  
|`^`|文字列の先頭から照合を開始します。|  
|`(?<proto>\w+)`|1 つ以上の単語文字に一致します。  このグループに `proto` という名前を付けます。|  
|`://`|コロンとそれに続く 2 つのスラッシュ記号に一致します。|  
|`[^/]+?`|スラッシュ記号以外の任意の文字の 1 回以上の出現 \(ただし、可能な限り少ない回数\) に一致します。|  
|`(?<port>:\d+)?`|コロンとそれに続く 1 つ以上の 10 進数字の 0 回以上の出現に一致します。  このグループに `port` という名前を付けます。|  
|`/`|スラッシュ記号に一致します。|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> メソッドは、正規表現パターンでキャプチャされた 2 つの名前付きグループを連結する `${proto}${port}` 置換シーケンスを展開します。  これは、<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName> プロパティによって返されたコレクション オブジェクトから取得された文字列を明示的に連結する便利な代替方法です。  
  
 例では、`${proto}` と `${port}` の 2 つの置換がある <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=fullName> メソッドを使用して、キャプチャされたグループを出力文字列に含めています。  次のコードに示すように、一致部分の <xref:System.Text.RegularExpressions.GroupCollection> オブジェクトから、キャプチャされたグループを取得できます。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## 参照  
 [.NET Framework の正規表現](../../../docs/standard/base-types/regular-expressions.md)
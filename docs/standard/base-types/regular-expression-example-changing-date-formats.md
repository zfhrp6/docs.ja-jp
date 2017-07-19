---
title: "正規表現の例: 日付形式の変更 | Microsoft Docs"
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
  - "テキストの解析 (正規表現を使用した)、例"
  - "正規表現、例"
  - ".NET Framework 正規表現、例"
  - "正規表現 [.NET Framework]、例"
  - "パターン マッチング (正規表現を使用した)、例"
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# 正規表現の例: 日付形式の変更
次のコード例はフォーム *dd*\-*mm*\-*yy*の日付でフォーム *mm*\/*dd*\/*yy* の日付を置き換えるに <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> のメソッドを使用します。  
  
## 例  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 次のコードは、アプリケーションの中で `MDYToDMY` メソッドを呼び出す方法を示しています。  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## コメント  
 正規表現パターン `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` の解釈を次の表に示します。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から照合を開始します。|  
|`(?<month>\d{1,2})`|1 桁または 2 桁の 10 進数と一致します。  これが `month` キャプチャ グループです。|  
|`/`|スラッシュ記号に一致します。|  
|`(?<day>\d{1,2})`|1 桁または 2 桁の 10 進数と一致します。  これが `day` キャプチャ グループです。|  
|`/`|スラッシュ記号に一致します。|  
|`(?<year>\d{2,4})`|2 ～ 4 個の 10 進数と一致します。  これが `year` キャプチャ グループです。|  
|`\b`|ワード境界で照合を終了します。|  
  
 パターン `${day}-${month}-${year}` による置換文字列の定義を次の表に示します。  
  
|パターン|説明|  
|----------|--------|  
|`$(day)`|`day` キャプチャ グループによってキャプチャされた文字列を追加します。|  
|`-`|ハイフンを追加します。|  
|`$(month)`|`month` キャプチャ グループによってキャプチャされた文字列を追加します。|  
|`-`|ハイフンを追加します。|  
|`$(year)`|`year` キャプチャ グループによってキャプチャされた文字列を追加します。|  
  
## 参照  
 [.NET Framework の正規表現](../../../docs/standard/base-types/regular-expressions.md)
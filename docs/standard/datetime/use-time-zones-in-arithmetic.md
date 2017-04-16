---
title: "方法 : 日付と時刻の演算でタイム ゾーンを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "算術演算 [.NET Framework], 日付と時刻"
  - "日付 [.NET Framework], 加算と減算"
  - "タイム ゾーン [.NET Framework], 算術演算"
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 日付と時刻の演算でタイム ゾーンを使用する
通常、<xref:System.DateTime> 値または <xref:System.DateTimeOffset> 値を使用して日付と時刻の演算を実行するとき、その結果にはタイム ゾーン調整規則は反映されません。  これは、日時の値のタイム ゾーンを明確に識別できる場合 \(<xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind> に設定されている場合など\) でも同じです。  このトピックでは、特定のタイム ゾーンに属する日時の値の算術演算を実行する方法について説明します。  算術演算の結果には、タイム ゾーンの調整規則が反映されます。  
  
### 日付と時刻の演算に調整規則を適用するには  
  
1.  なんらかの方法を実装して、日時の値と、その値が属するタイム ゾーンを密接に結び付ます。  たとえば、日時の値とそのタイム ゾーンの両方を含む構造体を宣言します。  次の例では、この方法を使用して <xref:System.DateTime> 値とそのタイム ゾーンをリンクします。  
  
     [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
     [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]  
  
2.  <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> メソッドまたは <xref:System.TimeZoneInfo.ConvertTime%2A> メソッドを呼び出して、時刻を世界協定時刻 \(UTC: Coordinated Universal Time\) に変換します。  
  
3.  UTC 時刻で算術演算を実行します。  
  
4.  <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=fullName> メソッドを呼び出して、UTC の時刻から、元の時刻に関連付けられたタイム ゾーンの時刻に変換します。  
  
## 使用例  
 次の例では、中部標準時の 2008 年 3 月 9 日午前 1 時 30 分に、2 時間 30 分を加えます。  夏時間 30 分にタイム ゾーンの移行が 2008 \(3 年 12 月 9 日の午前 2:00 に、後で発生します。  例では、前のセクションに記載されている手順に従って 4 から 2008 年 1 月 3 日 9 時に午前 5:00 と、結果は正しい時刻を報告します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
 [!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]  
  
 <xref:System.DateTime> 値と <xref:System.DateTimeOffset> 値はどちらも、どのタイム ゾーンとも関連付けられていません。  タイム ゾーンの調整規則が自動的に適用されるような方法で日付と時刻の演算を実行するには、日時の値の属するタイム ゾーンがすぐに識別できる状態であることが必要です。  つまり、日時とそのタイム ゾーンを密に結合する必要があります。  そのためには、次に示すようにいくつかの方法があります。  
  
-   アプリケーションで使用されるすべての時刻が、特定のタイム ゾーンに属するものと仮定します。  この方法は、適切な場合もありますが、柔軟性が限られ、移植性が制限される可能性もあります。  
  
-   日時とそのタイム ゾーンを型のフィールドとして組み込むことで、両者を密に結合する型を定義します。  このコード例では、この方法を使用して、日時とタイム ゾーンを 2 つのメンバー フィールドに格納する構造体を定義しています。  
  
 この例は、タイム ゾーンの調整規則が結果に適用されるように <xref:System.DateTime> 値の算術演算を実行する方法を示しています。  ただし、<xref:System.DateTimeOffset> 値も同じように簡単に使用できます。  次の例では、<xref:System.DateTime> 値の代わりに <xref:System.DateTimeOffset> を使用するように、元の例のコードを適合させる方法を示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]  
  
 最初に UTC に変換せず、単純に <xref:System.DateTimeOffset> 値に対してこの加算を実行すると、結果には正しい時刻が反映されますが、その時刻に対して指定されたタイム ゾーンのオフセットは反映されません。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   <xref:System> 名前空間を `using` ステートメントでインポートする \(C\# のコードで必要\)。  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [日付と時刻を使用した算術演算の実行](../../../docs/standard/datetime/performing-arithmetic-operations.md)
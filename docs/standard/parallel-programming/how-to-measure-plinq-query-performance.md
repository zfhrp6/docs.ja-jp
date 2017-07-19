---
title: "How to: Measure PLINQ Query Performance | Microsoft Docs"
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
  - "PLINQ queries, how to measure performance"
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Measure PLINQ Query Performance
この例では、<xref:System.Diagnostics.Stopwatch> クラスを使用して PLINQ クエリの実行に要する時間を測定します。  
  
## 使用例  
 この例では、空の `foreach` ループ \(Visual Basic では `For Each`\) を使用して、クエリの実行に要する時間を測定します。  実際のコードでは、通常、ループにはその他の処理手順が含まれ、クエリの総実行時間に追加されます。  ストップウォッチは、クエリの実行が開始されるループの直前まで開始されません。  さらに詳細な計測が必要な場合は、`ElapsedMilliseconds` の代わりに `ElapsedTicks` プロパティを使用できます。  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 総実行時間は、クエリの実装を試している場合には便利なメトリックですが、常に全体の状況を表すわけではありません。  クエリ スレッドのスレッドどうし、およびその他の実行プロセスとの相互作用をより詳しくわかりやすく表示するには、同時実行ビジュアライザーを使用します。  詳細については、「[同時実行ビジュアライザー](../Topic/Concurrency%20Visualizer.md)」を参照してください。  
  
## 参照  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
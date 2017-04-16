---
title: "How to: Write a Custom PLINQ Aggregate Function | Microsoft Docs"
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
  - "PLINQ queries, how to create aggregate function"
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Write a Custom PLINQ Aggregate Function
この例では、<xref:System.Linq.ParallelEnumerable.Aggregate%2A> メソッドを使用してカスタムの集計関数をソース シーケンスに適用する方法を示します。  
  
> [!WARNING]
>  この例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。  高速化の詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 使用例  
 次の例では、整数のシーケンスの標準偏差を計算します。  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 この例では、PLINQ に固有の Aggregate 標準クエリ演算子のオーバーロードを使用します。  このオーバーロードでは、3 つ目の入力パラメーターとして <xref:System.Func%603?displayProperty=fullName> を使用します。  このデリゲートでは、すべてのスレッドの結果をまとめてから、集計結果での最終的な計算が実行されます。  この例では、すべてのスレッドからの合計が追加されます。  
  
 ラムダ式の本体が単一の式から構成される場合、<xref:System.Func%602?displayProperty=fullName> デリゲートの戻り値は式の値になります。  
  
## 参照  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
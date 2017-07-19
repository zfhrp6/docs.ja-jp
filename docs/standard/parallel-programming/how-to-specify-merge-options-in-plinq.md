---
title: "How to: Specify Merge Options in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to use merge options"
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Specify Merge Options in PLINQ
ここでは、PLINQ クエリで後続のすべての演算子に適用するマージ オプションを指定する例を示します。  マージ オプションは明示的に設定する必要はありませんが、設定するとパフォーマンスが向上する場合があります。  マージ オプションの詳細については、「[Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)」を参照してください。  
  
> [!WARNING]
>  この例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。  高速化の詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 使用例  
 次の例は基本的なシナリオでのマージ オプションで、順序なしのソースを用いてすべての要素に負荷の大きい関数を適用する動作を示しています。  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <xref:System.Linq.ParallelMergeOptions> オプションによって、最初の要素が生成されるまでに余分な待機時間が発生する場合は、<xref:System.Linq.ParallelMergeOptions> オプションを使用すると結果要素を高速かつスムーズに生成できます。  
  
## 参照  
 <xref:System.Linq.ParallelMergeOptions>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
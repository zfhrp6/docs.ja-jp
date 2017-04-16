---
title: "How to: Implement Dynamic Partitions | Microsoft Docs"
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
  - "tasks, how to create a dynamic partitioner"
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# How to: Implement Dynamic Partitions
次の例では、動的パーティション分割を実装し、特定のオーバーロードの <xref:System.Threading.Tasks.Parallel.ForEach%2A> および PLINQ から使用できる、カスタムの <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=fullName> を実装する方法を示します。  
  
## 使用例  
 パーティションで列挙子に対して <xref:System.Collections.IEnumerator.MoveNext%2A> を呼び出すたびに、パーティションにリスト要素が 1 つ提供されます。  PLINQ および <xref:System.Threading.Tasks.Parallel.ForEach%2A> の場合、パーティションは <xref:System.Threading.Tasks.Task> インスタンスです。  複数のスレッドで要求が同時に発生するため、現在のインデックスへのアクセスが同期されます。  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 これは、各チャンクが 1 つの要素で構成されたチャンク パーティション分割の一例です。  一度により多くの要素を提供することで、ロックの競合を減らすことができるため、理論上はパフォーマンスを向上させることができます。  ただし、大きなチャンクでは、すべての処理が完了するまですべてのスレッドをビジー状態に維持するために、ある時点で追加の負荷分散ロジックが必要になる場合があります。  
  
## 参照  
 [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)   
 [How to: Implement a Partitioner for Static Partitioning](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
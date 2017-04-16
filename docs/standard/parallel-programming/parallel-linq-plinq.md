---
title: "Parallel LINQ (PLINQ) | Microsoft Docs"
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
  - "PLINQ, overview"
ms.assetid: 3d4d0cd3-bde4-490b-99e7-f4e41be96455
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Parallel LINQ (PLINQ)
Parallel LINQ \(PLINQ\) は、LINQ to Objects の並列実装です。  PLINQ では LINQ 標準クエリ演算子の完全なセットを T:System.Linq 名前空間の拡張メソッドとして実装します。また、並列操作用の追加の演算子も備えています。  PLINQ では並列プログラミングの機能が強化され、LINQ 構文が簡略化され読みやすくなっています。  タスク並列ライブラリを対象としたコードと同様に、PLINQ クエリでは、ホスト コンピューターの性能に基づいて同時実行の程度が調整されます。  
  
 多くの場合、PLINQ により、ホスト コンピューター上で使用できるコアをより効率的に使用することで、LINQ to Objects クエリの処理速度が大幅に向上します。  このようにパフォーマンスが向上することで、デスクトップ上の演算性能が高まります。  
  
## このセクションの内容  
 [Introduction to PLINQ](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
 [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)  
  
 [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)  
  
 [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)  
  
 [How to: Create and Execute a Simple PLINQ Query](../../../docs/standard/parallel-programming/how-to-create-and-execute-a-simple-plinq-query.md)  
  
 [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
 [How to: Combine Parallel and Sequential LINQ Queries](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md)  
  
 [How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
 [How to: Cancel a PLINQ Query](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md)  
  
 [How to: Write a Custom PLINQ Aggregate Function](../../../docs/standard/parallel-programming/how-to-write-a-custom-plinq-aggregate-function.md)  
  
 [How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md)  
  
 [How to: Specify Merge Options in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 [How to: Iterate File Directories with PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)  
  
 [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)  
  
 [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md)  
  
## 参照  
 <xref:System.Linq.ParallelEnumerable>   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)
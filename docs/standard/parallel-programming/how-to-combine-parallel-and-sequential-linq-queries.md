---
title: "How to: Combine Parallel and Sequential LINQ Queries | Microsoft Docs"
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
  - "parallel queries, combine parallel and sequential"
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Combine Parallel and Sequential LINQ Queries
この例では、<xref:System.Linq.ParallelEnumerable.AsSequential%2A> メソッドを使用して、クエリのすべての後続演算子を順次処理するよう PLINQ に指示する方法を示します。  一般的に、順次処理は並列処理よりも時間がかかりますが、正しい結果を生成するために必要な場合があります。  
  
> [!WARNING]
>  この例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。  高速化の詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 使用例  
 次の例は、<xref:System.Linq.ParallelEnumerable.AsSequential%2A> が必要で、クエリの直前の句で設定された順序を維持するシナリオを示しています。  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## コードのコンパイル  
 このコードをコンパイルして実行するには、コードを [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) プロジェクトに貼り付け、`Main` からメソッドを呼び出す行を追加し、F5 キーを押します。  
  
## 参照  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
---
title: "How to: Cancel a Parallel.For or ForEach Loop | Microsoft Docs"
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
  - "parallel foreach loop, how to cancel"
  - "parallel for loops, how to cancel"
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Cancel a Parallel.For or ForEach Loop
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> メソッドおよび <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> メソッドは、キャンセル トークンを使用したキャンセルをサポートしています。  一般的なキャンセルの詳細については、「[キャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)」を参照してください。  並列ループでは、<xref:System.Threading.CancellationToken> を <xref:System.Threading.Tasks.ParallelOptions> パラメーターのメソッドに指定し、並列呼び出しを try\-catch ブロックで囲みます。  
  
## 使用例  
 次の例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> への呼び出しを取り消す方法を示しています。  同じ方法を <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> の呼び出しにも適用できます。  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 トークンによって、キャンセルが <xref:System.Threading.Tasks.ParallelOptions> インスタンスで指定されたトークンと同じであることが示された場合、並列ループは取り消し時に単一の <xref:System.OperationCanceledException> をスローします。  その他のトークンによってキャンセルが発生した場合、ループは <xref:System.OperationCanceledException> と共に <xref:System.AggregateException> を InnerException としてスローします。  
  
## 参照  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
---
title: "How to: Specify the Execution Mode in PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to use execution mode"
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Specify the Execution Mode in PLINQ
この例では、PLINQ に既定のヒューリスティックをバイパスさせ、クエリの形態に関係なくクエリを並列化する方法を示します。  
  
> [!WARNING]
>  この例は使用法を示すことを目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が遅い場合があります。  高速化の詳細については、「[Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ は、並列化を利用しやすくするために設計されています。  ただし、すべてのクエリが並列実行の利点を活用できるわけではありません。  たとえば、負荷が非常に小さい単一のユーザー デリゲートを含むクエリの場合、順次実行の方が速度が速くなります。  これは、並列化して実行できるようにすることで発生するオーバーヘッドが、並列化で高速にする場合の負荷より大きいためです。  このため、PLINQ はすべてのクエリを自動的に並列化しません。  最初に、クエリの形態とクエリを構成しているさまざまな演算子を調べます。  この分析に基づいて、既定の実行モードの PLINQ によって、クエリの一部またはすべてを順次実行するかどうかが決定されます。  ただし、PLINQ が分析から判断するよりも、ユーザーの方がクエリをより詳しく理解している場合があります。  たとえば、デリゲートの負荷が非常に大きいため、クエリで並列化を使用する方が良いとわかっているとします。  このような場合は、<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> メソッドを使用し、<xref:System.Linq.ParallelExecutionMode> 値を指定することで、クエリを常に並列実行するよう PLINQ に指示できます。  
  
## コードのコンパイル  
 このコードをコピーして [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) に貼り付けて、`Main` からメソッドを呼び出します。  
  
## 参照  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
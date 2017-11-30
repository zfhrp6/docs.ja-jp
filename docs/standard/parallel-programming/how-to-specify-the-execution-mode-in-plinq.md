---
title: "方法: PLINQ の実行モードを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 745ceae9832582c7b66a56075d128f9cf1c8ff69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="36ff8-102">方法: PLINQ の実行モードを指定する</span><span class="sxs-lookup"><span data-stu-id="36ff8-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="36ff8-103">この例では、PLINQ を既定のヒューリスティックをバイパスし、クエリの図形に関係なくクエリを並列化を強制する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="36ff8-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="36ff8-104">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36ff8-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="36ff8-105">高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。</span><span class="sxs-lookup"><span data-stu-id="36ff8-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36ff8-106">例</span><span class="sxs-lookup"><span data-stu-id="36ff8-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="36ff8-107">PLINQ が並列化の機会を利用するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="36ff8-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="36ff8-108">ただし、すべてのクエリは並列実行を享受できます。</span><span class="sxs-lookup"><span data-stu-id="36ff8-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="36ff8-109">たとえば、クエリには、ほとんどの処理を行う単一のユーザー デリゲートが含まれている、クエリは、通常実行順番に高速化します。</span><span class="sxs-lookup"><span data-stu-id="36ff8-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="36ff8-110">これは、並列実行を有効にするのにはオーバーヘッドが取得される速度よりも高価であるためです。</span><span class="sxs-lookup"><span data-stu-id="36ff8-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="36ff8-111">したがって、PLINQ は自動的には並列化しないすべてのクエリ。</span><span class="sxs-lookup"><span data-stu-id="36ff8-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="36ff8-112">まず、クエリおよび構成するさまざまな演算子の図形を調べます。</span><span class="sxs-lookup"><span data-stu-id="36ff8-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="36ff8-113">この分析に基づき、既定の実行モードで PLINQ があります、クエリの一部またはすべてを順番に実行します。</span><span class="sxs-lookup"><span data-stu-id="36ff8-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="36ff8-114">ただし、場合によってはするがわかっている場合より、クエリに関する PLINQ は、分析から判断するよりもします。</span><span class="sxs-lookup"><span data-stu-id="36ff8-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="36ff8-115">たとえば、デリゲートが非常に不経済とするクエリは並列化を確実に利用がわかっている場合があります。</span><span class="sxs-lookup"><span data-stu-id="36ff8-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="36ff8-116">このような場合に使用することができます、<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>メソッドを指定し、<xref:System.Linq.ParallelExecutionMode.ForceParallelism>常に並列としてクエリを実行するために PLINQ に指示する値。</span><span class="sxs-lookup"><span data-stu-id="36ff8-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="36ff8-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="36ff8-117">Compiling the Code</span></span>  
 <span data-ttu-id="36ff8-118">切り取って貼り付けるには、このコード、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)からメソッドを呼び出すと`Main`です。</span><span class="sxs-lookup"><span data-stu-id="36ff8-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ff8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="36ff8-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="36ff8-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="36ff8-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

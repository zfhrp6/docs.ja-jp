---
title: '方法: PLINQ の実行モードを指定する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebea62f33c5df252dd73a0708f31612cd2998728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="a8b95-102">方法: PLINQ の実行モードを指定する</span><span class="sxs-lookup"><span data-stu-id="a8b95-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="a8b95-103">この例では、PLINQ に既定のヒューリスティックをバイパスさせ、クエリのシェイプに関係なくクエリを並列化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8b95-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a8b95-104">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8b95-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="a8b95-105">高速化の詳細については、「[PLINQ での高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8b95-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8b95-106">例</span><span class="sxs-lookup"><span data-stu-id="a8b95-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="a8b95-107">PLINQ は、並列化を利用しやすくするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="a8b95-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="a8b95-108">ただし、すべてのクエリが並列実行の利点を活用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a8b95-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="a8b95-109">たとえば、負荷が非常に小さい単一のユーザー デリゲートを含むクエリの場合、順次実行の方が速度が速くなります。</span><span class="sxs-lookup"><span data-stu-id="a8b95-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="a8b95-110">これは、実行を並列するために必要なオーバーヘッドが、並列化で高速にする場合の負荷より大きいためです。</span><span class="sxs-lookup"><span data-stu-id="a8b95-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="a8b95-111">このため、PLINQ はすべてのクエリを自動的に並列化するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a8b95-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="a8b95-112">最初に、クエリのシェイプとクエリを構成しているさまざまな演算子を調べます。</span><span class="sxs-lookup"><span data-stu-id="a8b95-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="a8b95-113">この分析に基づいて、既定の実行モードの PLINQ によって、クエリの一部またはすべてを順次実行するかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="a8b95-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="a8b95-114">ただし、PLINQ が分析から判断するよりも、ユーザーの方がクエリをより詳しく理解している場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8b95-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="a8b95-115">たとえば、デリゲートの負荷が非常に大きいため、クエリで並列化を使用する方がよいとわかっているとします。</span><span class="sxs-lookup"><span data-stu-id="a8b95-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="a8b95-116">このような場合は、<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> メソッドを使用し、<xref:System.Linq.ParallelExecutionMode.ForceParallelism> 値を指定することで、クエリを常に並列実行するよう PLINQ に指示できます。</span><span class="sxs-lookup"><span data-stu-id="a8b95-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8b95-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a8b95-117">Compiling the Code</span></span>  
 <span data-ttu-id="a8b95-118">このコードをコピーして [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) に貼り付けて、`Main` からメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a8b95-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b95-119">参照</span><span class="sxs-lookup"><span data-stu-id="a8b95-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="a8b95-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a8b95-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

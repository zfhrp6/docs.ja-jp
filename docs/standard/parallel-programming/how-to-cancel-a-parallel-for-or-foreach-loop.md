---
title: "方法: Parallel.For または ForEach ループを取り消す"
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
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="d7936-102">方法: Parallel.For または ForEach ループを取り消す</span><span class="sxs-lookup"><span data-stu-id="d7936-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="d7936-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>と<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>メソッドは、キャンセル トークンを使用して取り消しをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d7936-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="d7936-104">取り消し処理の詳細については一般を参照してください[キャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7936-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="d7936-105">並列ループで指定する、<xref:System.Threading.CancellationToken>内のメソッドに、<xref:System.Threading.Tasks.ParallelOptions>パラメーター try catch ブロックで並列呼び出しを囲みます。</span><span class="sxs-lookup"><span data-stu-id="d7936-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7936-106">例</span><span class="sxs-lookup"><span data-stu-id="d7936-106">Example</span></span>  
 <span data-ttu-id="d7936-107">次の例への呼び出しを取り消す方法を示しています。<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="d7936-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d7936-108">同じアプローチを適用することができます、<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d7936-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="d7936-109">取り消しを通知するトークンが同じ場合はトークンで指定されている、<xref:System.Threading.Tasks.ParallelOptions>インスタンス、並列ループは、1 つをスローし、<xref:System.OperationCanceledException>キャンセルします。</span><span class="sxs-lookup"><span data-stu-id="d7936-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="d7936-110">その他のいくつかのトークンには、キャンセルが発生する場合、ループがスローされます、<xref:System.AggregateException>で、<xref:System.OperationCanceledException>内部例外として。</span><span class="sxs-lookup"><span data-stu-id="d7936-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7936-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7936-111">See Also</span></span>  
 [<span data-ttu-id="d7936-112">データの並列化</span><span class="sxs-lookup"><span data-stu-id="d7936-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="d7936-113">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="d7936-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)

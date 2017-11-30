---
title: "方法: 小さいループ本体を高速化する"
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d38d8beedf342720d4dc68026297edb457f5ed35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="ab9ca-102">方法: 小さいループ本体を高速化する</span><span class="sxs-lookup"><span data-stu-id="ab9ca-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="ab9ca-103">ときに、<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>ループ小さな本文が含まれるため、可能性があります実行と同等の連続したループよりも時間がかかるなど、[の](~/docs/csharp/language-reference/keywords/for.md)(C#) ループと[の](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980)Visual Basic でループします。</span><span class="sxs-lookup"><span data-stu-id="ab9ca-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="ab9ca-104">パフォーマンスの低下は、データのパーティション分割と、各ループのイテレーションでデリゲートを呼び出す負荷によって発生します。</span><span class="sxs-lookup"><span data-stu-id="ab9ca-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="ab9ca-105">このようなシナリオに対処するため、<xref:System.Collections.Concurrent.Partitioner> クラスには <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> メソッドが用意されています。このメソッドにより、デリゲートがイテレーションごとに 1 回ではなく、パーティションごとに 1 回だけ呼び出されるように、デリゲートの本体に順次ループを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab9ca-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="ab9ca-106">詳細については、「[Custom Partitioners for PLINQ and TPL (PLINQ および TPL 用のカスタム パーティショナー)](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab9ca-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab9ca-107">例</span><span class="sxs-lookup"><span data-stu-id="ab9ca-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="ab9ca-108">この例で示す方法は、ループが最小限の作業を実行するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="ab9ca-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="ab9ca-109">作業がより負荷の大きい処理になるにつれ、既定のパーティショナーで <xref:System.Threading.Tasks.Parallel.For%2A> ループまたは <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループを使用すると、同じまたはそれ以上のパフォーマンスが得られることがあります。</span><span class="sxs-lookup"><span data-stu-id="ab9ca-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9ca-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab9ca-110">See Also</span></span>  
 [<span data-ttu-id="ab9ca-111">データの並列化</span><span class="sxs-lookup"><span data-stu-id="ab9ca-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="ab9ca-112">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="ab9ca-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="ab9ca-113">反復子</span><span class="sxs-lookup"><span data-stu-id="ab9ca-113">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="ab9ca-114">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="ab9ca-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)

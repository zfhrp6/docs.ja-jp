---
title: "方法: 動的パーティションを実装する"
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
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="7a727-102">方法: 動的パーティションを実装する</span><span class="sxs-lookup"><span data-stu-id="7a727-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="7a727-103">次の例は、カスタムを実装する方法を示しています。<xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>を動的なパーティション分割を実装し、特定のオーバー ロードから使用できる<xref:System.Threading.Tasks.Parallel.ForEach%2A>と PLINQ の間です。</span><span class="sxs-lookup"><span data-stu-id="7a727-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a727-104">例</span><span class="sxs-lookup"><span data-stu-id="7a727-104">Example</span></span>  
 <span data-ttu-id="7a727-105">パーティションを呼び出すたびに<xref:System.Collections.IEnumerator.MoveNext%2A>列挙子に対して、列挙子は 1 つのリストの要素を持つパーティションを提供します。</span><span class="sxs-lookup"><span data-stu-id="7a727-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="7a727-106">PLINQ の場合と<xref:System.Threading.Tasks.Parallel.ForEach%2A>、パーティションが、<xref:System.Threading.Tasks.Task>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="7a727-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="7a727-107">要求は、複数のスレッドで同時に発生している、ため、現在のインデックスへのアクセスが同期されます。</span><span class="sxs-lookup"><span data-stu-id="7a727-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="7a727-108">これは、パーティション分割、1 つの要素で構成される各チャンクをチャンクの例です。</span><span class="sxs-lookup"><span data-stu-id="7a727-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="7a727-109">を一度に複数の要素を提供するにはロックの競合を減らしでしたして理論的には高速なパフォーマンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="7a727-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="7a727-110">ただし、いくつかの時点では、大きな単位必要があります負荷分散のロジックを追加、すべての作業が完了するまでのすべてのスレッドをビジー状態に保つためにします。</span><span class="sxs-lookup"><span data-stu-id="7a727-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a727-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a727-111">See Also</span></span>  
 [<span data-ttu-id="7a727-112">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="7a727-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="7a727-113">方法: 静的パーティション分割用にパーティショナーを実装する</span><span class="sxs-lookup"><span data-stu-id="7a727-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)

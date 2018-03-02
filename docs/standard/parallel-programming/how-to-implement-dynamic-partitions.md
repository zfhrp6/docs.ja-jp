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
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="94ec5-102">方法: 動的パーティションを実装する</span><span class="sxs-lookup"><span data-stu-id="94ec5-102">How to: Implement Dynamic Partitions</span></span>
<span data-ttu-id="94ec5-103">次の例は、特定のオーバーロード <xref:System.Threading.Tasks.Parallel.ForEach%2A> と PLINQ から動的なパーティション分割を実装するカスタム <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="94ec5-103">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94ec5-104">例</span><span class="sxs-lookup"><span data-stu-id="94ec5-104">Example</span></span>  
 <span data-ttu-id="94ec5-105">列挙子でパーティションが <xref:System.Collections.IEnumerator.MoveNext%2A> を呼び出すたびに、列挙子はパーティションに 1 つのリスト要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="94ec5-105">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="94ec5-106">PLINQ と <xref:System.Threading.Tasks.Parallel.ForEach%2A> では、パーティションは <xref:System.Threading.Tasks.Task> インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="94ec5-106">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="94ec5-107">要求は、複数のスレッドで同時に発生しているため、現在のインデックスへのアクセスは同期されます。</span><span class="sxs-lookup"><span data-stu-id="94ec5-107">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 <span data-ttu-id="94ec5-108">これは、各チャンクが 1 つの要素で構成されるチャンク パーティション分割の例です。</span><span class="sxs-lookup"><span data-stu-id="94ec5-108">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="94ec5-109">一度に複数の要素を提供することにより、ロックの競合を減らし、理論的により高速なパフォーマンスを実現することができます。</span><span class="sxs-lookup"><span data-stu-id="94ec5-109">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="94ec5-110">ただし、チャンクが大きい場合、すべての作業が完了するまで、すべてのスレッドをビジーにするために、ある時点で追加の負荷分散ロジックが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="94ec5-110">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ec5-111">参照</span><span class="sxs-lookup"><span data-stu-id="94ec5-111">See Also</span></span>  
 [<span data-ttu-id="94ec5-112">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="94ec5-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="94ec5-113">方法: 静的パーティション分割用にパーティショナーを実装する</span><span class="sxs-lookup"><span data-stu-id="94ec5-113">How to: Implement a Partitioner for Static Partitioning</span></span>](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)

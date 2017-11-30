---
title: "方法: 静的パーティション分割用にパーティショナーを実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="aff94-102">方法: 静的パーティション分割用にパーティショナーを実装する</span><span class="sxs-lookup"><span data-stu-id="aff94-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="aff94-103">次の例は、plinq が静的パーティション分割を実行する場合は、単純なカスタム パーティショナーを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aff94-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="aff94-104">パーティショナーは動的なパーティションがサポートされていませんはから利用できる<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="aff94-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aff94-105">このパーティショナーは、データ ソースの各要素が大量の処理時間が必要です、既定の範囲パーティショナー経由で速度が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aff94-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aff94-106">例</span><span class="sxs-lookup"><span data-stu-id="aff94-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="aff94-107">この例では、パーティションは処理時間の各要素を直線的に増加するという前提に基づいています。</span><span class="sxs-lookup"><span data-stu-id="aff94-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="aff94-108">この方法で処理時間を予測するが困難な現実世界があります。</span><span class="sxs-lookup"><span data-stu-id="aff94-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="aff94-109">静的パーティショナーで特定のデータ ソースを使用している場合、ソースの数式でパーティション分割を最適化、負荷分散のロジックを追加したり、使用に示すようにパーティション分割手法チャンク[する方法: 動的パーティションを実装します。](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="aff94-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff94-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="aff94-110">See Also</span></span>  
 [<span data-ttu-id="aff94-111">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="aff94-111">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)

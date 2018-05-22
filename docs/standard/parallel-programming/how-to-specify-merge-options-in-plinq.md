---
title: '方法: PLINQ のマージ オプションを指定する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1f30245b398ae894e7226d1e94046fc9111dcf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="92987-102">方法: PLINQ のマージ オプションを指定する</span><span class="sxs-lookup"><span data-stu-id="92987-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="92987-103">この例では、PLINQ クエリの後続のすべての演算子に適用されるマージ オプションを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="92987-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="92987-104">マージ オプションを明示的に設定する必要はありませんが、設定することでパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92987-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="92987-105">マージ オプションの詳細については、「[PLINQ のマージ オプション](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92987-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="92987-106">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92987-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="92987-107">高速化の詳細については、「[PLINQ での高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92987-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92987-108">例</span><span class="sxs-lookup"><span data-stu-id="92987-108">Example</span></span>  
 <span data-ttu-id="92987-109">次の例では、順序付けされていないソースがあり、すべての要素に負荷が大きい関数を適用する基本的なシナリオでのマージ オプションの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="92987-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="92987-110">最初の要素が生成される前に <xref:System.Linq.ParallelMergeOptions.AutoBuffered> オプションで望ましくない待機時間が発生した場合は、結果要素をより速く、よりスムーズに生成するために <xref:System.Linq.ParallelMergeOptions.NotBuffered> オプションを試してください。</span><span class="sxs-lookup"><span data-stu-id="92987-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92987-111">参照</span><span class="sxs-lookup"><span data-stu-id="92987-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="92987-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="92987-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

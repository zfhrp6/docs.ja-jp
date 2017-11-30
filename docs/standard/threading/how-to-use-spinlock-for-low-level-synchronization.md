---
title: "方法: 下位レベルの同期に SpinLock を使用する"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="80163-102">方法: 下位レベルの同期に SpinLock を使用する</span><span class="sxs-lookup"><span data-stu-id="80163-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="80163-103">次の例で使用する方法、<xref:System.Threading.SpinLock>です。</span><span class="sxs-lookup"><span data-stu-id="80163-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80163-104">例</span><span class="sxs-lookup"><span data-stu-id="80163-104">Example</span></span>  
 <span data-ttu-id="80163-105">この例ではクリティカル セクションには最小限の作業は、これはにとって適切な候補を実行、<xref:System.Threading.SpinLock>です。</span><span class="sxs-lookup"><span data-stu-id="80163-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="80163-106">少量の作業を増やすとパフォーマンスが向上、<xref:System.Threading.SpinLock>標準的なロックを比較します。</span><span class="sxs-lookup"><span data-stu-id="80163-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="80163-107">ただし、SpinLock が標準ロックよりも高負荷になるポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="80163-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="80163-108">プロファイリング ツールで同時実行プロファイリング機能を使用して、どのタイプのロックを使用すればプログラムのパフォーマンスが高まるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="80163-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="80163-109">詳細については、「[同時実行ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80163-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="80163-110"><xref:System.Threading.SpinLock>共有リソースのロックが保持されるを行わない場合に便利な場合あります非常に長いです。</span><span class="sxs-lookup"><span data-stu-id="80163-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="80163-111">そのような場合、マルチコア コンピューターでは、ロックが解除されるまで数回のサイクルの間、ブロックされたスレッドをスピンさせると効率が高まることがあります。</span><span class="sxs-lookup"><span data-stu-id="80163-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="80163-112">スピンするとスレッドはブロックされなくなりますが、これは CPU 負荷の高いプロセスです。</span><span class="sxs-lookup"><span data-stu-id="80163-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="80163-113"><xref:System.Threading.SpinLock>論理プロセッサまたはハイパー スレッディングのシステムで優先順位の逆転の枯渇を防ぐために特定の条件下でスピンは停止されます。</span><span class="sxs-lookup"><span data-stu-id="80163-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="80163-114">この例では、<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>クラスは、マルチ スレッド アクセスをユーザーの同期が必要です。</span><span class="sxs-lookup"><span data-stu-id="80163-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="80163-115">アプリケーションで .NET Framework version 4 を対象とする、別のオプションが使用する、<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>ユーザーのすべてのロックは不要です。</span><span class="sxs-lookup"><span data-stu-id="80163-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="80163-116">使用に注意してください`false`(`False` Visual Basic で) への呼び出しで<xref:System.Threading.SpinLock.Exit%2A>です。</span><span class="sxs-lookup"><span data-stu-id="80163-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="80163-117">これにより、最適なパフォーマンスを得られます。</span><span class="sxs-lookup"><span data-stu-id="80163-117">This provides the best performance.</span></span> <span data-ttu-id="80163-118">メモリ フェンスを使用するには、IA64 アーキテクチャで `true` (`True`) を指定します。これにより、書き込みバッファーがフラッシュされるので、ロックを使用して他のスレッドを終了できるようになります。</span><span class="sxs-lookup"><span data-stu-id="80163-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80163-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="80163-119">See Also</span></span>  
 [<span data-ttu-id="80163-120">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="80163-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)

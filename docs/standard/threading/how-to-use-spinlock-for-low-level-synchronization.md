---
title: '方法: 下位レベルの同期に SpinLock を使用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7795b25ca8e9337a53fc67ebc6f56130237d0764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582757"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="6b596-102">方法: 下位レベルの同期に SpinLock を使用する</span><span class="sxs-lookup"><span data-stu-id="6b596-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="6b596-103"><xref:System.Threading.SpinLock> の使用例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6b596-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b596-104">例</span><span class="sxs-lookup"><span data-stu-id="6b596-104">Example</span></span>  
 <span data-ttu-id="6b596-105">この例では、クリティカル セクションが実行する作業量は最小限であるため、<xref:System.Threading.SpinLock> に適しています。</span><span class="sxs-lookup"><span data-stu-id="6b596-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="6b596-106">作業量を少し増やすと、標準ロックと比較して <xref:System.Threading.SpinLock> のパフォーマンスは高まります。</span><span class="sxs-lookup"><span data-stu-id="6b596-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="6b596-107">ただし、SpinLock が標準ロックよりも高負荷になるポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="6b596-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="6b596-108">プロファイリング ツールで同時実行プロファイリング機能を使用して、どのタイプのロックを使用すればプログラムのパフォーマンスが高まるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6b596-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="6b596-109">詳細については、「[同時実行ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b596-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="6b596-110"><xref:System.Threading.SpinLock> は、共有リソースのロックが非常に長い期間使用されない場合に有用なことがあります。</span><span class="sxs-lookup"><span data-stu-id="6b596-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="6b596-111">そのような場合、マルチコア コンピューターでは、ロックが解除されるまで数回のサイクルの間、ブロックされたスレッドをスピンさせると効率が高まることがあります。</span><span class="sxs-lookup"><span data-stu-id="6b596-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="6b596-112">スピンするとスレッドはブロックされなくなりますが、これは CPU 負荷の高いプロセスです。</span><span class="sxs-lookup"><span data-stu-id="6b596-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="6b596-113">ハイパースレッディングを使用するシステムでは、<xref:System.Threading.SpinLock> は特定の状況でスピンを停止して、論理プロセッサの不足や優先順位の逆転が発生するのを回避します。</span><span class="sxs-lookup"><span data-stu-id="6b596-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="6b596-114">この例では、<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> クラスを使用するため、マルチスレッド アクセスにはユーザーによる同期が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6b596-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="6b596-115">.NET Framework Version 4 をターゲットにしているアプリケーションでは、ユーザーのロックが不要な <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b596-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="6b596-116"><xref:System.Threading.SpinLock.Exit%2A> の呼び出しに `false` (Visual Basic では `False`) が使用されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="6b596-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="6b596-117">これにより、最適なパフォーマンスを得られます。</span><span class="sxs-lookup"><span data-stu-id="6b596-117">This provides the best performance.</span></span> <span data-ttu-id="6b596-118">メモリ フェンスを使用するには、IA64 アーキテクチャで `true` (`True`) を指定します。これにより、書き込みバッファーがフラッシュされるので、ロックを使用して他のスレッドを終了できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6b596-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b596-119">参照</span><span class="sxs-lookup"><span data-stu-id="6b596-119">See Also</span></span>  
 [<span data-ttu-id="6b596-120">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="6b596-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)

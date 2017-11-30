---
title: SpinWait
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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a><span data-ttu-id="242ef-102">SpinWait</span><span class="sxs-lookup"><span data-stu-id="242ef-102">SpinWait</span></span>
<span data-ttu-id="242ef-103"><xref:System.Threading.SpinWait?displayProperty=nameWithType>高価なコンテキストの切り替えとカーネル イベントに必要なカーネル遷移を避けるために低レベルのシナリオで使用できる軽量な同期型です。</span><span class="sxs-lookup"><span data-stu-id="242ef-103"><xref:System.Threading.SpinWait?displayProperty=nameWithType> is a lightweight synchronization type that you can use in low-level scenarios to avoid the expensive context switches and kernel transitions that are required for kernel events.</span></span> <span data-ttu-id="242ef-104">マルチコア コンピューターは、長期間保持するリソースが予期されていない場合があります数十または数百サイクル、ユーザー モードで起動し、リソースの取得を再試行を待機中のスレッドの効率。</span><span class="sxs-lookup"><span data-stu-id="242ef-104">On multicore computers, when a resource is not expected to be held for long periods of time, it can be more efficient for a waiting thread to spin in user mode for a few dozen or a few hundred cycles, and then retry to acquire the resource.</span></span> <span data-ttu-id="242ef-105">回転の後に、リソースが利用可能な場合は、数千サイクルを保存しました。</span><span class="sxs-lookup"><span data-stu-id="242ef-105">If the resource is available after spinning, then you have saved several thousand cycles.</span></span> <span data-ttu-id="242ef-106">リソースがまだ使用できない場合は、いくつかのサイクルのみを費やしし、カーネル ベースの待機を入力できます。</span><span class="sxs-lookup"><span data-stu-id="242ef-106">If the resource is still not available, then you have spent only a few cycles and can still enter a kernel-based wait.</span></span> <span data-ttu-id="242ef-107">この待機時間、回転の組み合わせとも呼ば、 *2 フェーズ待機操作*です。</span><span class="sxs-lookup"><span data-stu-id="242ef-107">This spinning-then-waiting combination is sometimes referred to as a *two-phase wait operation*.</span></span>  
  
 <span data-ttu-id="242ef-108"><xref:System.Threading.SpinWait>などのカーネル イベントをラップする .NET Framework の型と組み合わせて使用するように設計された<xref:System.Threading.ManualResetEvent>です。</span><span class="sxs-lookup"><span data-stu-id="242ef-108"><xref:System.Threading.SpinWait> is designed to be used in conjunction with the .NET Framework types that wrap kernel events such as <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="242ef-109"><xref:System.Threading.SpinWait>1 つだけのプログラムの基本的な回転機能を単独でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="242ef-109"><xref:System.Threading.SpinWait> can also be used by itself for basic spinning functionality in just one program.</span></span>  
  
 <span data-ttu-id="242ef-110"><xref:System.Threading.SpinWait>空のループだけがします。</span><span class="sxs-lookup"><span data-stu-id="242ef-110"><xref:System.Threading.SpinWait> is more than just an empty loop.</span></span> <span data-ttu-id="242ef-111">動作を提供する適切なスピン一般的なケースでは、慎重に実装されているし、コンテキスト スイッチが開始場合は、回転する十分な時間 (ほぼカーネル遷移に必要な時間の長さ)。</span><span class="sxs-lookup"><span data-stu-id="242ef-111">It is carefully implemented to provide correct spinning behavior for the general case, and will itself initiate context switches if it spins long enough (roughly the length of time required for a kernel transition).</span></span> <span data-ttu-id="242ef-112">たとえば、コンピューターでは単一コア、<xref:System.Threading.SpinWait>スレッドのタイム スライスの生成スピン ブロックのすべてのスレッドでの進行状況を転送するためにすぐにします。</span><span class="sxs-lookup"><span data-stu-id="242ef-112">For example, on single-core computers, <xref:System.Threading.SpinWait> yields the time slice of the thread immediately because spinning blocks forward progress on all threads.</span></span> <span data-ttu-id="242ef-113"><xref:System.Threading.SpinWait>またを待機中のスレッドが優先順位の高いスレッドや、ガベージ コレクターをブロックするを防ぐために、マルチコア コンピューター上であっても生成します。</span><span class="sxs-lookup"><span data-stu-id="242ef-113"><xref:System.Threading.SpinWait> also yields even on multi-core machines to prevent the waiting thread from blocking higher-priority threads or the garbage collector.</span></span> <span data-ttu-id="242ef-114">そのためを使用している場合、 <xref:System.Threading.SpinWait> 2 フェーズ待機操作では、ことをお勧めする前に、カーネル待機が起動される、<xref:System.Threading.SpinWait>コンテキスト スイッチをそれ自体を開始します。</span><span class="sxs-lookup"><span data-stu-id="242ef-114">Therefore, if you are using a <xref:System.Threading.SpinWait> in a two-phase wait operation, we recommend that you invoke the kernel wait before the <xref:System.Threading.SpinWait> itself initiates a context switch.</span></span> <span data-ttu-id="242ef-115"><xref:System.Threading.SpinWait>提供、<xref:System.Threading.SpinWait.NextSpinWillYield%2A>プロパティで、すべての呼び出しにする前に確認できる<xref:System.Threading.SpinWait.SpinOnce%2A>です。</span><span class="sxs-lookup"><span data-stu-id="242ef-115"><xref:System.Threading.SpinWait> provides the <xref:System.Threading.SpinWait.NextSpinWillYield%2A> property, which you can check before every call to <xref:System.Threading.SpinWait.SpinOnce%2A>.</span></span> <span data-ttu-id="242ef-116">プロパティが返されるときに`true`、独自の待機操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="242ef-116">When the property returns `true`, initiate your own Wait operation.</span></span> <span data-ttu-id="242ef-117">例については、次を参照してください。[する方法: 2 フェーズ待機操作を実装する使用 SpinWait](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="242ef-117">For an example, see [How to: Use SpinWait to Implement a Two-Phase Wait Operation](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).</span></span>  
  
 <span data-ttu-id="242ef-118">有効にできますが、2 フェーズ待機操作を実行していないいくつかの条件が true になるまでだけ回転している場合は、<xref:System.Threading.SpinWait>をそのコンテキストを実行する Windows オペレーティング システムの環境での良き市民ようにを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="242ef-118">If you are not performing a two-phase wait operation but are just spinning until some condition is true, you can enable <xref:System.Threading.SpinWait> to perform its context switches so that it is a good citizen in the Windows operating system environment.</span></span> <span data-ttu-id="242ef-119">基本的な例を次に、<xref:System.Threading.SpinWait>ロック制御不要のスタックにします。</span><span class="sxs-lookup"><span data-stu-id="242ef-119">The following basic example shows a <xref:System.Threading.SpinWait> in a lock-free stack.</span></span> <span data-ttu-id="242ef-120">高パフォーマンス、スレッド セーフであるスタックを必要とする場合は、使用を検討して<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="242ef-120">If you require a high-performance, thread-safe stack, consider using <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a><span data-ttu-id="242ef-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="242ef-121">See Also</span></span>  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [<span data-ttu-id="242ef-122">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="242ef-122">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)

---
title: "スレッドの一時中断と再開"
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
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a><span data-ttu-id="fca13-102">スレッドの一時中断と再開</span><span class="sxs-lookup"><span data-stu-id="fca13-102">Pausing and Resuming Threads</span></span>
<span data-ttu-id="fca13-103">スレッドの活動を同期する最も一般的な方法は、スレッドのブロックと解放を行うか、コード領域またはオブジェクトをロックすることです。</span><span class="sxs-lookup"><span data-stu-id="fca13-103">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="fca13-104">ロックとブロックのしくみの詳細については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fca13-104">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="fca13-105">また、スレッドそのものをスリープ状態にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fca13-105">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="fca13-106">スレッドがブロックされているかまたはスリープ状態の場合は、<xref:System.Threading.ThreadInterruptedException> を使用して待機状態を解除できます。</span><span class="sxs-lookup"><span data-stu-id="fca13-106">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="fca13-107">Thread.Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="fca13-107">The Thread.Sleep Method</span></span>  
 <span data-ttu-id="fca13-108">呼び出す、<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>メソッドが現在のスレッド (ミリ秒) か、メソッドに渡す時間間隔の数をすぐにブロックして、別のスレッドに自らのタイム スライスの残りの部分が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fca13-108">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="fca13-109">時間が経過すると、スリープ状態のスレッドは実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="fca13-109">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="fca13-110">もう一方のスレッドが他方のスレッドに対して <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="fca13-110">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="fca13-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>常に現在のスレッドがスリープ状態の原因となる静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fca13-111"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="fca13-112">呼び出す<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>の値を持つ<xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>スレッドを呼び出す別のスレッドによって中断されるまで、スリープ状態を<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>メソッドへの呼び出しによって停止されるまでまたはスリープ状態のスレッドでその<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fca13-112">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="fca13-113">次の例は、スリープ状態のスレッドを中断する両方の方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fca13-113">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="fca13-114">スレッドの中断</span><span class="sxs-lookup"><span data-stu-id="fca13-114">Interrupting Threads</span></span>  
 <span data-ttu-id="fca13-115">呼び出して待機中のスレッドを中断することができます、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>をスローする、ブロックされたスレッド上のメソッド、 <xref:System.Threading.ThreadInterruptedException>、ブロッキング呼び出しからスレッドを中断します。</span><span class="sxs-lookup"><span data-stu-id="fca13-115">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="fca13-116">スレッドは、<xref:System.Threading.ThreadInterruptedException> をキャッチし、操作を継続するために適切な処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="fca13-116">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="fca13-117">スレッドがこの例外を無視した場合は、ランタイムがこの例外をキャッチし、そのスレッドを停止します。</span><span class="sxs-lookup"><span data-stu-id="fca13-117">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fca13-118"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> が呼び出されたときに対象となるスレッドがブロックされていない場合、スレッドはブロックされるまで中断されません。</span><span class="sxs-lookup"><span data-stu-id="fca13-118">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="fca13-119">スレッドがまったくブロックされない場合は、中断されることなく完了することがあります。</span><span class="sxs-lookup"><span data-stu-id="fca13-119">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="fca13-120">待機がマネージ待機である場合、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> と <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> はどちらもすぐにスレッドを起動します。</span><span class="sxs-lookup"><span data-stu-id="fca13-120">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="fca13-121">待機がアンマネージ待機の場合 (など、プラットフォーム呼び出しに Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx)関数)、どちらも<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>も<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>戻るか、またはマネージ コードを呼び出すまで、スレッドの制御が可能にします。</span><span class="sxs-lookup"><span data-stu-id="fca13-121">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="fca13-122">マネージ コードの動作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fca13-122">In managed code, the behavior is as follows:</span></span>  
  
-   <span data-ttu-id="fca13-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> はスレッドをどのような待機からも起動し、これによって起動先のスレッドで <xref:System.Threading.ThreadInterruptedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fca13-123"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
-   <span data-ttu-id="fca13-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>スレッドによりしている可能性がありますすべての待機をスリープ状態を解除、<xref:System.Threading.ThreadAbortException>スレッドでスローされます。</span><span class="sxs-lookup"><span data-stu-id="fca13-124"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="fca13-125">詳細については、「[スレッドの破棄](../../../docs/standard/threading/destroying-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fca13-125">For details, see [Destroying Threads](../../../docs/standard/threading/destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca13-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="fca13-126">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [<span data-ttu-id="fca13-127">スレッド化</span><span class="sxs-lookup"><span data-stu-id="fca13-127">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="fca13-128">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="fca13-128">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="fca13-129">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="fca13-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)

---
title: "マネージ スレッドの状態"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956472ef0e3b0bab85a4eb0b5585f1a4d1e0a991
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="managed-thread-states"></a><span data-ttu-id="eabfb-102">マネージ スレッドの状態</span><span class="sxs-lookup"><span data-stu-id="eabfb-102">Managed Thread States</span></span>
<span data-ttu-id="eabfb-103">プロパティ <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> には、スレッドの現在の状態を示すビット マスクが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eabfb-103">The property <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> provides a bit mask that indicates the thread's current state.</span></span> <span data-ttu-id="eabfb-104">スレッドは、 <xref:System.Threading.ThreadState> 列挙型に含まれる状態のうち、常に少なくとも 1 つの状態となり、同時に複数の状態になることもあります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-104">A thread is always in at least one of the possible states in the <xref:System.Threading.ThreadState> enumeration, and can be in multiple states at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eabfb-105">スレッドの状態は、いくつかのデバッグ シナリオでのみ必要になります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-105">Thread state is only of interest in a few debugging scenarios.</span></span> <span data-ttu-id="eabfb-106">スレッドの動作を同期化する目的でコード内でスレッドの状態を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="eabfb-106">Your code should never use thread state to synchronize the activities of threads.</span></span>  
  
 <span data-ttu-id="eabfb-107">マネージ スレッドを作成すると、そのスレッドは <xref:System.Threading.ThreadState.Unstarted> 状態になります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-107">When you create a managed thread, it is in the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="eabfb-108">スレッドは、オペレーティング システムによって起動状態にされるまで、 <xref:System.Threading.ThreadState.Unstarted> 状態のままです。</span><span class="sxs-lookup"><span data-stu-id="eabfb-108">The thread remains in the <xref:System.Threading.ThreadState.Unstarted> state until it is moved into the started state by the operating system.</span></span> <span data-ttu-id="eabfb-109"><xref:System.Threading.Thread.Start%2A> を呼び出すと、スレッドを開始できることをオペレーティング システムに通知できますが、スレッドの状態は変化しません。</span><span class="sxs-lookup"><span data-stu-id="eabfb-109">Calling <xref:System.Threading.Thread.Start%2A> lets the operating system know that the thread can be started; it does not change the state of the thread.</span></span>  
  
 <span data-ttu-id="eabfb-110">マネージ環境に入ってくるアンマネージ スレッドは、既に起動状態になっています。</span><span class="sxs-lookup"><span data-stu-id="eabfb-110">Unmanaged threads that enter the managed environment are already in the started state.</span></span> <span data-ttu-id="eabfb-111">スレッドがいったん起動状態になると、さまざまなアクションによってスレッドの状態が変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-111">Once a thread is in the started state, a number of actions can cause it to change states.</span></span> <span data-ttu-id="eabfb-112">状態が変更される原因となるアクションと、対応する新しい状態を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="eabfb-112">The following table lists the actions that cause a change of state, along with the corresponding new state.</span></span>  
  
|<span data-ttu-id="eabfb-113">アクション</span><span class="sxs-lookup"><span data-stu-id="eabfb-113">Action</span></span>|<span data-ttu-id="eabfb-114">変更後の新しい状態</span><span class="sxs-lookup"><span data-stu-id="eabfb-114">Resulting new state</span></span>|  
|------------|-------------------------|  
|<span data-ttu-id="eabfb-115"><xref:System.Threading.Thread> クラスのコンストラクターが呼び出される。</span><span class="sxs-lookup"><span data-stu-id="eabfb-115">The constructor for the <xref:System.Threading.Thread> class is called.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="eabfb-116">別のスレッドが <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-116">Another thread calls <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Unstarted>|  
|<span data-ttu-id="eabfb-117">スレッドが <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> に応答して実行を開始する。</span><span class="sxs-lookup"><span data-stu-id="eabfb-117">The thread responds to <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> and starts running.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="eabfb-118">スレッドが <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-118">The thread calls <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="eabfb-119">スレッドが別のオブジェクトで <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-119">The thread calls <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> on another object.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="eabfb-120">スレッドが別のスレッドで <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-120">The thread calls <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> on another thread.</span></span>|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|<span data-ttu-id="eabfb-121">別のスレッドが <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-121">Another thread calls <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.SuspendRequested>|  
|<span data-ttu-id="eabfb-122">スレッドが <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> 要求に応答する。</span><span class="sxs-lookup"><span data-stu-id="eabfb-122">The thread responds to a <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> request.</span></span>|<xref:System.Threading.ThreadState.Suspended>|  
|<span data-ttu-id="eabfb-123">別のスレッドが <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-123">Another thread calls <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.Running>|  
|<span data-ttu-id="eabfb-124">別のスレッドが <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を呼び出す。</span><span class="sxs-lookup"><span data-stu-id="eabfb-124">Another thread calls <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<xref:System.Threading.ThreadState.AbortRequested>|  
|<span data-ttu-id="eabfb-125">スレッドが <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> に応答する。</span><span class="sxs-lookup"><span data-stu-id="eabfb-125">The thread responds to an <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>|<span data-ttu-id="eabfb-126"><xref:System.Threading.ThreadState.Aborted>の後 <xref:System.Threading.ThreadState.Stopped></span><span class="sxs-lookup"><span data-stu-id="eabfb-126"><xref:System.Threading.ThreadState.Aborted>, then <xref:System.Threading.ThreadState.Stopped></span></span>|  
  
 <span data-ttu-id="eabfb-127"><xref:System.Threading.ThreadState.Running> 状態の値は 0 のため、ビット テストを実行しても、この状態を検出できません。</span><span class="sxs-lookup"><span data-stu-id="eabfb-127">Because the <xref:System.Threading.ThreadState.Running> state has a value of 0, it is not possible to perform a bit test to discover this state.</span></span> <span data-ttu-id="eabfb-128">代わりに、擬似コードによる次のテストを実行できます。</span><span class="sxs-lookup"><span data-stu-id="eabfb-128">Instead, the following test (in pseudo-code) can be used:</span></span>  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 <span data-ttu-id="eabfb-129">スレッドは、どの時点でも複数の状態にあることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-129">Threads are often in more than one state at any given time.</span></span> <span data-ttu-id="eabfb-130">たとえば、<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> 呼び出しでスレッドがブロックされ、別のスレッドが同じスレッドに対して <xref:System.Threading.Thread.Abort%2A> を呼び出した場合、スレッドは同時に <xref:System.Threading.ThreadState.WaitSleepJoin> 状態と <xref:System.Threading.ThreadState.AbortRequested> 状態になります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-130">For example, if a thread is blocked on a <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> call and another thread calls <xref:System.Threading.Thread.Abort%2A> on that same thread, the thread will be in both the <xref:System.Threading.ThreadState.WaitSleepJoin> and the <xref:System.Threading.ThreadState.AbortRequested> states at the same time.</span></span> <span data-ttu-id="eabfb-131">この場合、スレッドは、 <xref:System.Threading.Monitor.Wait%2A> への呼び出しから戻るか中断されるとすぐに、 <xref:System.Threading.ThreadAbortException>を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="eabfb-131">In that case, as soon as the thread returns from the call to <xref:System.Threading.Monitor.Wait%2A> or is interrupted, it will receive the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
 <span data-ttu-id="eabfb-132">スレッドは、 <xref:System.Threading.ThreadState.Unstarted> への呼び出しの結果として <xref:System.Threading.Thread.Start%2A>状態から出ると、 <xref:System.Threading.ThreadState.Unstarted> 状態に戻ることはできません。</span><span class="sxs-lookup"><span data-stu-id="eabfb-132">Once a thread leaves the <xref:System.Threading.ThreadState.Unstarted> state as the result of a call to <xref:System.Threading.Thread.Start%2A>, it can never return to the <xref:System.Threading.ThreadState.Unstarted> state.</span></span> <span data-ttu-id="eabfb-133">また、スレッドは <xref:System.Threading.ThreadState.Stopped> 状態から出ることはできません。</span><span class="sxs-lookup"><span data-stu-id="eabfb-133">A thread can never leave the <xref:System.Threading.ThreadState.Stopped> state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabfb-134">参照</span><span class="sxs-lookup"><span data-stu-id="eabfb-134">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [<span data-ttu-id="eabfb-135">スレッド化</span><span class="sxs-lookup"><span data-stu-id="eabfb-135">Threading</span></span>](../../../docs/standard/threading/index.md)

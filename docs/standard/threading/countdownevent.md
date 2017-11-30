---
title: CountdownEvent
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
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a><span data-ttu-id="8ec83-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="8ec83-102">CountdownEvent</span></span>
<span data-ttu-id="8ec83-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>待機中のスレッドのブロックが解除された後に同期プリミティブの通知回数だけです。</span><span class="sxs-lookup"><span data-stu-id="8ec83-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="8ec83-104"><xref:System.Threading.CountdownEvent>シナリオではそれ以外の場合があるを使用するよう設計されていますが、<xref:System.Threading.ManualResetEvent>または<xref:System.Threading.ManualResetEventSlim>と手動でイベントを通知する前に、変数をデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="8ec83-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="8ec83-105">たとえば、分岐および結合のシナリオでのみ作成できます、 <xref:System.Threading.CountdownEvent> 5 のシグナルのカウントを持つと 5 つの作業項目、スレッドの開始をプールし、作業項目の各呼び出しがある<xref:System.Threading.CountdownEvent.Signal%2A>完了時にします。</span><span class="sxs-lookup"><span data-stu-id="8ec83-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="8ec83-106">各呼び出し<xref:System.Threading.CountdownEvent.Signal%2A>信号カウントを 1 だけデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="8ec83-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="8ec83-107">メイン スレッドへの呼び出しで<xref:System.Threading.CountdownEvent.Wait%2A>シグナル カウントがゼロになるまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="8ec83-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ec83-108">従来の .NET Framework の同期 Api と対話する必要はありませんコード、使用を検討して<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>オブジェクトまたは<xref:System.Threading.Tasks.Parallel.Invoke%2A>分岐と結合の並列処理の表現をさらに簡単なアプローチのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="8ec83-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="8ec83-109"><xref:System.Threading.CountdownEvent>これらの追加機能があります。</span><span class="sxs-lookup"><span data-stu-id="8ec83-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="8ec83-110">キャンセル トークンを使用して、待機操作をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="8ec83-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="8ec83-111">インスタンスが作成された後、その信号カウントをインクリメントできます。</span><span class="sxs-lookup"><span data-stu-id="8ec83-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="8ec83-112">インスタンスが後に再利用できる<xref:System.Threading.CountdownEvent.Wait%2A>呼び出しで返されるが、<xref:System.Threading.CountdownEvent.Reset%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8ec83-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="8ec83-113">インスタンスを公開、<xref:System.Threading.WaitHandle>他の .NET Framework の同期 Api と統合するためなど<xref:System.Threading.WaitHandle.WaitAll%2A>です。</span><span class="sxs-lookup"><span data-stu-id="8ec83-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="8ec83-114">基本的な使用方法</span><span class="sxs-lookup"><span data-stu-id="8ec83-114">Basic Usage</span></span>  
 <span data-ttu-id="8ec83-115">次の例で使用する方法、<xref:System.Threading.CountdownEvent>で<xref:System.Threading.ThreadPool>作業項目です。</span><span class="sxs-lookup"><span data-stu-id="8ec83-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="8ec83-116">キャンセルを CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="8ec83-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="8ec83-117">次の例での待機操作をキャンセルする方法を示しています。<xref:System.Threading.CountdownEvent>キャンセル トークンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="8ec83-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="8ec83-118">基本的なパターンが統一されたキャンセルで導入されたのモデルを採用[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="8ec83-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="8ec83-119">詳細については、次を参照してください。[マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ec83-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="8ec83-120">待ち操作がそのシグナル状態のスレッドをキャンセルしていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8ec83-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="8ec83-121">通常、取り消しは、論理操作に適用され、待機を同期しているすべての作業項目と同様に、イベントで待機していることを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8ec83-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="8ec83-122">この例では、各作業項目は、同じキャンセル トークンのコピーには、キャンセル要求に応答できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8ec83-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec83-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ec83-123">See Also</span></span>  
 [<span data-ttu-id="8ec83-124">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="8ec83-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)

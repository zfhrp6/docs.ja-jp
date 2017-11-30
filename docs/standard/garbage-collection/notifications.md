---
title: "ガベージ コレクションの通知"
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
- cpp
helpviewer_keywords: garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41a2ed9c5d239f1570955e87bb5b749e29830bc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="4df72-102">ガベージ コレクションの通知</span><span class="sxs-lookup"><span data-stu-id="4df72-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="4df72-103">パフォーマンスは、共通言語ランタイムによるフル ガベージ コレクション (つまり、ジェネレーション 2 のコレクション) に悪影響を及ぼす場合があります。</span><span class="sxs-lookup"><span data-stu-id="4df72-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="4df72-104">これが特に大量の要求を処理するサーバーで問題になります。この例では、長時間のガベージ コレクションには、要求のタイムアウトを可能性があります。重要な期間中に発生するを防ぐためには、通知が可能フル ガベージ コレクションが近づいていると、ワークロードを別のサーバー インスタンスにリダイレクトするアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4df72-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="4df72-105">できますも強制的に実行するコレクション、自分で提供する現在のサーバー インスタンスが要求を処理する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4df72-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="4df72-106"><xref:System.GC.RegisterForFullGCNotification%2A>メソッドは、ランタイムは、フル ガベージ コレクションが近づいていることを検出するときに発生の通知を登録します。</span><span class="sxs-lookup"><span data-stu-id="4df72-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="4df72-107">この通知に 2 つの部分があります: フル ガベージ コレクションが近づいているときに、フル ガベージ コレクションが完了するとします。</span><span class="sxs-lookup"><span data-stu-id="4df72-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4df72-108">唯一のブロッキング ガベージ コレクションは、通知を発生させます。</span><span class="sxs-lookup"><span data-stu-id="4df72-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="4df72-109">ときに、 [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)構成要素が有効になっている、バック グラウンド ガベージ コレクションでは、通知は発生しません。</span><span class="sxs-lookup"><span data-stu-id="4df72-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="4df72-110">調べるには、通知が発生したときに、使用、<xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4df72-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="4df72-111">通常、これらのメソッドを使用して、`while`を継続的に取得するループ、<xref:System.GCNotificationStatus>通知の状態を列挙します。</span><span class="sxs-lookup"><span data-stu-id="4df72-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="4df72-112">その値が場合<xref:System.GCNotificationStatus.Succeeded>次を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4df72-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="4df72-113">取得された通知に応答、<xref:System.GC.WaitForFullGCApproach%2A>メソッド、ワークロードをリダイレクトしたり、場合によって引き起こされるコレクション自分でします。</span><span class="sxs-lookup"><span data-stu-id="4df72-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="4df72-114">取得された通知に応答、<xref:System.GC.WaitForFullGCComplete%2A>方法、もう一度要求を処理に使用できる現在のサーバー インスタンスをすることができます。</span><span class="sxs-lookup"><span data-stu-id="4df72-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="4df72-115">情報を収集することもできます。</span><span class="sxs-lookup"><span data-stu-id="4df72-115">You can also gather information.</span></span> <span data-ttu-id="4df72-116">たとえば、使用することができます、<xref:System.GC.CollectionCount%2A>メソッドのコレクションの数を記録します。</span><span class="sxs-lookup"><span data-stu-id="4df72-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="4df72-117"><xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドは連携して動作するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="4df72-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="4df72-118">せず、他のいずれかを使用すると、不確定な結果が生成することができます。</span><span class="sxs-lookup"><span data-stu-id="4df72-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="4df72-119">フル ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="4df72-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="4df72-120">ランタイムでは、次のシナリオのいずれかに当てはまる場合にフル ガベージ コレクションが発生します。</span><span class="sxs-lookup"><span data-stu-id="4df72-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="4df72-121">十分なメモリが次のジェネレーション 2 のコレクションが発生する第 2 世代に昇格されました。</span><span class="sxs-lookup"><span data-stu-id="4df72-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="4df72-122">十分なメモリが、次のジェネレーション 2 のコレクションが発生する大きなオブジェクト ヒープに昇格されました。</span><span class="sxs-lookup"><span data-stu-id="4df72-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="4df72-123">ジェネレーション 1 のガベージ コレクションは、その他の要因により第 2 世代のコレクションにエスカレートされます。</span><span class="sxs-lookup"><span data-stu-id="4df72-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="4df72-124">指定したしきい値、<xref:System.GC.RegisterForFullGCNotification%2A>メソッドが最初の 2 つのシナリオに適用します。</span><span class="sxs-lookup"><span data-stu-id="4df72-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="4df72-125">ただし、最初のシナリオでしていない常に、通知を受け取る 2 つの理由を指定するしきい値の値に比例した時に。</span><span class="sxs-lookup"><span data-stu-id="4df72-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="4df72-126">ランタイムは、パフォーマンス上の理由により) 各小さなオブジェクトの割り当てをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="4df72-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="4df72-127">のみジェネレーション 1 のガベージ コレクションのプロモート メモリ ジェネレーション 2 にします。</span><span class="sxs-lookup"><span data-stu-id="4df72-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="4df72-128">3 番目のシナリオは、通知を受信するときの不確実性にも作用します。</span><span class="sxs-lookup"><span data-stu-id="4df72-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="4df72-129">これではありませんが、保証は、この期間中に、要求をリダイレクトするか、ガベージ コレクション自分で、都合の良いときに、不適切なフル ガベージ コレクションの影響を軽減するために便利な方法である証明は。</span><span class="sxs-lookup"><span data-stu-id="4df72-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="4df72-130">通知のしきい値のパラメーター</span><span class="sxs-lookup"><span data-stu-id="4df72-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="4df72-131"><xref:System.GC.RegisterForFullGCNotification%2A>メソッドが 2 つのパラメーターの第 2 世代のオブジェクトと、大きなオブジェクト ヒープのしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4df72-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="4df72-132">これらの値を満たしたときに、ガベージ コレクションの通知が発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4df72-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="4df72-133">次の表では、これらのパラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4df72-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="4df72-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4df72-134">Parameter</span></span>|<span data-ttu-id="4df72-135">説明</span><span class="sxs-lookup"><span data-stu-id="4df72-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="4df72-136">通知を発行するタイミングを指定する、1 ~ 99 の数値は、ジェネレーション 2 に昇格されたオブジェクトに基づいています。</span><span class="sxs-lookup"><span data-stu-id="4df72-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="4df72-137">通知を発行するタイミングを指定する、1 ~ 99 の数値は、大きなオブジェクト ヒープに割り当てられているオブジェクトに基づいています。</span><span class="sxs-lookup"><span data-stu-id="4df72-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="4df72-138">大きすぎる値を指定する場合は、確率が高い、通知を受け取りますが、実行時にコレクションが発生する前に待機する長期間がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4df72-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="4df72-139">強制的に実行するコレクション自分で、ランタイムでガベージ コレクションが解放は複数のオブジェクトを回収することがあります。</span><span class="sxs-lookup"><span data-stu-id="4df72-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="4df72-140">小さすぎる値を指定するに通知するための十分な時間をかけてする前に、ランタイムは、コレクションをおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="4df72-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df72-141">例</span><span class="sxs-lookup"><span data-stu-id="4df72-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4df72-142">説明</span><span class="sxs-lookup"><span data-stu-id="4df72-142">Description</span></span>  
 <span data-ttu-id="4df72-143">次の例では、サーバーのグループは受信 Web 要求をサービスします。</span><span class="sxs-lookup"><span data-stu-id="4df72-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="4df72-144">バイト配列を追加する要求の処理のワークロードをシミュレートする、<xref:System.Collections.Generic.List%601>コレクション。</span><span class="sxs-lookup"><span data-stu-id="4df72-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="4df72-145">各サーバーのガベージ コレクションの通知を登録およびでスレッドを開始し、`WaitForFullGCProc`を継続的に監視するユーザーのメソッド、<xref:System.GCNotificationStatus>によって返される列挙型、<xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4df72-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="4df72-146"><xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドは、通知が発生したときに、それぞれのイベント処理ユーザー メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4df72-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="4df72-147">このメソッドは、`RedirectRequests`サーバーへの要求をユーザーのメソッドは、要求キュー サーバの送信を中断するように指示します。</span><span class="sxs-lookup"><span data-stu-id="4df72-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="4df72-148">これは、クラス レベルの変数を設定してシミュレート`bAllocate`に`false`オブジェクトが割り当てられるようにします。</span><span class="sxs-lookup"><span data-stu-id="4df72-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="4df72-149">次に、`FinishExistingRequests`ユーザー メソッドが呼び出され、保留中のサーバー要求の処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="4df72-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="4df72-150">これは、シミュレートをオフにして、<xref:System.Collections.Generic.List%601>コレクション。</span><span class="sxs-lookup"><span data-stu-id="4df72-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="4df72-151">最後に、ワークロードが薄いあるため、ガベージ コレクションが誘発されます。</span><span class="sxs-lookup"><span data-stu-id="4df72-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="4df72-152">このメソッドは、ユーザー`AcceptRequests`サーバーは、フル ガベージ コレクションを受けやすくなりますが不要になったために、要求の受け入れを再開します。</span><span class="sxs-lookup"><span data-stu-id="4df72-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="4df72-153">設定してこの操作をシミュレートした、`bAllocate`変数を`true`に追加されているオブジェクトを再開できるように、<xref:System.Collections.Generic.List%601>コレクション。</span><span class="sxs-lookup"><span data-stu-id="4df72-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="4df72-154">次のコードが含まれています、`Main`例のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="4df72-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="4df72-155">次のコードが含まれています、`WaitForFullGCProc`ガベージ コレクションの通知をチェックするループの中に継続的なを含む、ユーザー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4df72-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="4df72-156">次のコードが含まれています、`OnFullGCApproachNotify`メソッドから呼び出されると、</span><span class="sxs-lookup"><span data-stu-id="4df72-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="4df72-157">`WaitForFullGCProc` メソッド</span><span class="sxs-lookup"><span data-stu-id="4df72-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="4df72-158">次のコードが含まれています、`OnFullGCApproachComplete`メソッドから呼び出されると、</span><span class="sxs-lookup"><span data-stu-id="4df72-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="4df72-159">`WaitForFullGCProc` メソッド</span><span class="sxs-lookup"><span data-stu-id="4df72-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="4df72-160">次のコードにはから呼び出されるユーザー メソッドが含まれています、`OnFullGCApproachNotify`と`OnFullGCCompleteNotify`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4df72-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="4df72-161">ユーザー メソッドは、要求をリダイレクト、既存の要求を完了し、フル ガベージ コレクションが発生した後に要求を再開します。</span><span class="sxs-lookup"><span data-stu-id="4df72-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="4df72-162">完全なコード例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4df72-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4df72-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="4df72-163">See Also</span></span>  
 [<span data-ttu-id="4df72-164">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="4df72-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)

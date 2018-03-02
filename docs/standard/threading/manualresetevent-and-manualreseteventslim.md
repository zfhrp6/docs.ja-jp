---
title: "ManualResetEvent と ManualResetEventSlim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b90a84cf87c6c64d48d89840e2213d83b2e39d44
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="83072-102">ManualResetEvent と ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="83072-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="83072-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> クラスはローカル待機ハンドル イベントを表します。これは、シグナル状態になった後、手動でリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83072-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="83072-104">このクラスは、その基底クラス <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> の特殊なケースを表します。</span><span class="sxs-lookup"><span data-stu-id="83072-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83072-105">手動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念に関する文書を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83072-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="83072-106"><xref:System.Threading.ManualResetEvent> オブジェクトは、<xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> メソッドが呼び出されるまでシグナル状態のままです。</span><span class="sxs-lookup"><span data-stu-id="83072-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="83072-107">待機スレッド、つまりイベントがシグナル状態になるまで待機するスレッドは、そのオブジェクトがシグナル状態である間にいくつでも解放できます。</span><span class="sxs-lookup"><span data-stu-id="83072-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="83072-108"><xref:System.Threading.ManualResetEvent> は、`bManualReset` 引数に対して `true` を指定する、Win32 `CreateEvent` 呼び出しに対応します。</span><span class="sxs-lookup"><span data-stu-id="83072-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="83072-109">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、待機時間が非常に短いと予測される場合とイベントがプロセスの境界を越えない場合に、<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> クラスを使用してパフォーマンスを高めることができます。</span><span class="sxs-lookup"><span data-stu-id="83072-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="83072-110"><xref:System.Threading.ManualResetEventSlim> は、イベントがシグナル状態になるまで待機している間、ビジー スピンを短時間使用します。</span><span class="sxs-lookup"><span data-stu-id="83072-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="83072-111">待機時間が短い場合、待機ハンドルを使用して待機するより、スピンを使用するほうが負荷が大幅に低くなります。</span><span class="sxs-lookup"><span data-stu-id="83072-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="83072-112">ただし、特定の期間内にイベントがシグナル状態にならない場合、<xref:System.Threading.ManualResetEventSlim> は通常のイベント ハンドル待機を使用します。</span><span class="sxs-lookup"><span data-stu-id="83072-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83072-113">参照</span><span class="sxs-lookup"><span data-stu-id="83072-113">See Also</span></span>  
 [<span data-ttu-id="83072-114">スレッド化</span><span class="sxs-lookup"><span data-stu-id="83072-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="83072-115">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="83072-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="83072-116">待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="83072-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="83072-117">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="83072-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="83072-118">SpinWait</span><span class="sxs-lookup"><span data-stu-id="83072-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="83072-119">Semaphore と SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="83072-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)

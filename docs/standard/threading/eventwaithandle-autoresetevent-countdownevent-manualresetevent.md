---
title: "EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="3f31b-102">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="3f31b-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="3f31b-103">イベント待機ハンドルを使用して、スレッドでお互いにシグナル通知し、それぞれのシグナルを待機することで、スレッドの動作を同期できます。</span><span class="sxs-lookup"><span data-stu-id="3f31b-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="3f31b-104">これらの同期イベントは Win32 待機ハンドルに基づいており、通知を受けると自動的にリセットされるものと、手動でリセットされるものの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="3f31b-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="3f31b-105">イベント待機ハンドルは、同じ同期シナリオの多くに便利な<xref:System.Threading.Monitor>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3f31b-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="3f31b-106">イベント待機ハンドルがより使いやすく、多くの場合、<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>と<xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>メソッド、および、シグナリングより詳細に制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f31b-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="3f31b-107">名前付きのイベント待機ハンドルを使用して、アプリケーション ドメイン間やプロセス間で動作を同期させるためにも使用できます。これに対し、モニターはアプリケーション ドメインに対してローカルです。</span><span class="sxs-lookup"><span data-stu-id="3f31b-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f31b-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3f31b-108">In This Section</span></span>  
 [<span data-ttu-id="3f31b-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="3f31b-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="3f31b-110"><xref:System.Threading.EventWaitHandle>クラスは、自動のいずれかを表すことができるか、手動リセット イベントと、ローカル イベントまたはシステム イベントの名前します。</span><span class="sxs-lookup"><span data-stu-id="3f31b-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="3f31b-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="3f31b-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="3f31b-112"><xref:System.Threading.AutoResetEvent>クラスから派生<xref:System.Threading.EventWaitHandle>ローカル イベントに自動的にリセットを表すとします。</span><span class="sxs-lookup"><span data-stu-id="3f31b-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="3f31b-113">ManualResetEvent と ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="3f31b-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="3f31b-114"><xref:System.Threading.ManualResetEvent>クラスから派生<xref:System.Threading.EventWaitHandle>手動でリセットする必要があるローカル イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="3f31b-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="3f31b-115"><xref:System.Threading.ManualResetEventSlim>クラスは軽量で高速のバージョンで、同一プロセス内のイベントに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3f31b-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="3f31b-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="3f31b-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="3f31b-117"><xref:System.Threading.CountdownEvent>クラスには、待機ハンドルを使用しているコードの分岐および結合の並列処理のパターンを実装する簡単な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="3f31b-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3f31b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f31b-118">Related Sections</span></span>  
 [<span data-ttu-id="3f31b-119">待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="3f31b-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="3f31b-120"><xref:System.Threading.WaitHandle>クラスは、基本クラスの<xref:System.Threading.EventWaitHandle>、 <xref:System.Threading.Semaphore>、および<xref:System.Threading.Mutex>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3f31b-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="3f31b-121">などの静的メソッドがある<xref:System.Threading.WaitHandle.SignalAndWait%2A>と<xref:System.Threading.WaitHandle.WaitAll%2A>待機ハンドルのすべての型を使用する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3f31b-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f31b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f31b-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="3f31b-123">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="3f31b-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="3f31b-124">マネージ スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="3f31b-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)

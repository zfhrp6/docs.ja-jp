---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="fa0a6-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="fa0a6-102">AutoResetEvent</span></span>
<span data-ttu-id="fa0a6-103"><xref:System.Threading.AutoResetEvent>クラスはシグナルを受け取ると、1 つの待機中のスレッドを解放した後に自動的にリセットするローカルの待機ハンドルのイベントを表します。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="fa0a6-104">このクラスは、その基本クラスの特殊なケースを表します<xref:System.Threading.EventWaitHandle>です。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="fa0a6-105">自動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念に関する文書を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="fa0a6-106"><xref:System.Threading.AutoResetEvent>オブジェクトが自動的にリセットを非シグナル、システムによって 1 つの待機中のスレッドが解放された後です。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="fa0a6-107">待機しているスレッドがない場合でも、イベント オブジェクトの状態はシグナルのままです。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="fa0a6-108"><xref:System.Threading.AutoResetEvent>Win32 に対応する`CreateEvent`を呼び出すと、指定する`false`の`bManualReset`引数。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="fa0a6-109">使用する例については<xref:System.Threading.AutoResetEvent>を参照してください[モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)です。</span><span class="sxs-lookup"><span data-stu-id="fa0a6-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa0a6-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa0a6-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="fa0a6-111">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="fa0a6-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="fa0a6-112">スレッド化</span><span class="sxs-lookup"><span data-stu-id="fa0a6-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="fa0a6-113">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="fa0a6-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="fa0a6-114">待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="fa0a6-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)

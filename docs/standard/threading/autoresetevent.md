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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 71933d0be804fdf68b0dc602902343f2d88b8c82
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="b9a7d-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="b9a7d-102">AutoResetEvent</span></span>
<span data-ttu-id="b9a7d-103"><xref:System.Threading.AutoResetEvent> クラスは、単一の待機スレッドを解放した後、シグナル状態になると自動的にリセットするローカル待機ハンドル イベントを表します。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="b9a7d-104">このクラスは、その基底クラス <xref:System.Threading.EventWaitHandle> の特殊なケースを表します。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="b9a7d-105">自動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念に関する文書を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="b9a7d-106"><xref:System.Threading.AutoResetEvent> オブジェクトは、単一の待機スレッドが解放された後、システムによって自動的に非シグナルにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="b9a7d-107">待機しているスレッドがない場合でも、イベント オブジェクトの状態はシグナルのままです。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="b9a7d-108"><xref:System.Threading.AutoResetEvent> は、`bManualReset` 引数に対して `false` を指定する、Win32 `CreateEvent` 呼び出しに対応します。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="b9a7d-109"><xref:System.Threading.AutoResetEvent> の使用例については、「[Monitor クラス](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9a7d-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a7d-110">参照</span><span class="sxs-lookup"><span data-stu-id="b9a7d-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="b9a7d-111">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="b9a7d-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="b9a7d-112">スレッド化</span><span class="sxs-lookup"><span data-stu-id="b9a7d-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="b9a7d-113">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="b9a7d-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="b9a7d-114">待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="b9a7d-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)

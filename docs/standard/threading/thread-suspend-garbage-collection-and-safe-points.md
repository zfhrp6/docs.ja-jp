---
title: "Thread.Suspend、ガベージ コレクション、およびセーフ ポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdd56763712dee9c6fa1f292eb3bbb2f0ccbf505
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="b6ffb-102">Thread.Suspend、ガベージ コレクション、およびセーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="b6ffb-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="b6ffb-103">スレッドで <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> を呼び出すと、システムはスレッドの中断が要求されたことを示し、スレッドを実際に中断する前にセーフ ポイントに到達するまでスレッドを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="b6ffb-104">スレッドのセーフ ポイントは、ガベージ コレクションを実行できる実行ポイントです。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="b6ffb-105">セーフ ポイントに到達すると、ランタイムにより、中断されたスレッドがマネージ コードで続行されないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="b6ffb-106">マネージ コードの外部で実行中のスレッドは、通常、ガベージ コレクションでは安全であり、その実行はマネージ コードの実行再開が試行されるまで続行します。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6ffb-107">ガベージ コレクションを実行するために、ランタイムはコレクションを実行中のスレッドを除くすべてのスレッドを中断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="b6ffb-108">各スレッドを中断するには、セーフ ポイントに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6ffb-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ffb-109">参照</span><span class="sxs-lookup"><span data-stu-id="b6ffb-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="b6ffb-110">スレッド化</span><span class="sxs-lookup"><span data-stu-id="b6ffb-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="b6ffb-111">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="b6ffb-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)

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
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="51840-102">Thread.Suspend、ガベージ コレクション、およびセーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="51840-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="51840-103">呼び出すと<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>システム ノートのスレッドの中断が要求されているし、により、実際には、スレッドを中断する前に、安全なポイントに達するまで実行するスレッドのスレッドでします。</span><span class="sxs-lookup"><span data-stu-id="51840-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="51840-104">スレッド セーフである点で、ガベージ コレクションを実行できる実行ポイントです。</span><span class="sxs-lookup"><span data-stu-id="51840-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="51840-105">セーフ ポイントに達すると、ランタイムはように中断されたスレッドは注意が必要、さらに進行状況のマネージ コードに保証されます。</span><span class="sxs-lookup"><span data-stu-id="51840-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="51840-106">マネージ コードの外部で実行中のスレッドがガベージ コレクションでは常に、その実行をマネージ コードの実行を再開しようとするまで続行します。</span><span class="sxs-lookup"><span data-stu-id="51840-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51840-107">ガベージ コレクションを実行するために、ランタイムは、コレクションの実行スレッドを除くすべてのスレッドを中断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51840-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="51840-108">各スレッドは、中断する前に、セーフ ポイントに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51840-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51840-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="51840-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="51840-110">スレッド化</span><span class="sxs-lookup"><span data-stu-id="51840-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="51840-111">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="51840-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)

---
title: "競合 ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d739eaf73ff8336e74130d7176697229fdffd12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="contention-etw-events"></a><span data-ttu-id="69247-102">競合 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="69247-102">Contention ETW Events</span></span>
<span data-ttu-id="69247-103">競合イベントは、ランタイムによって使用される <xref:System.Threading.Monitor?displayProperty=nameWithType> ロックまたはネイティブ ロックの競合が発生するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="69247-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="69247-104">競合は、あるスレッドが、別のスレッドが保持しているロックを待機しているときに発生します。</span><span class="sxs-lookup"><span data-stu-id="69247-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="69247-105">競合イベントが発生するキーワードとイベントのレベルを次の表に示します </span><span class="sxs-lookup"><span data-stu-id="69247-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="69247-106">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="69247-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="69247-107">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="69247-107">Keyword for raising the event</span></span>|<span data-ttu-id="69247-108">レベル</span><span class="sxs-lookup"><span data-stu-id="69247-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="69247-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="69247-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="69247-110">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="69247-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="69247-111">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="69247-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="69247-112">イベント</span><span class="sxs-lookup"><span data-stu-id="69247-112">Event</span></span>|<span data-ttu-id="69247-113">イベント ID</span><span class="sxs-lookup"><span data-stu-id="69247-113">Event ID</span></span>|<span data-ttu-id="69247-114">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="69247-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="69247-115">81</span><span class="sxs-lookup"><span data-stu-id="69247-115">81</span></span>|<span data-ttu-id="69247-116">競合が開始されたとき。</span><span class="sxs-lookup"><span data-stu-id="69247-116">Contention starts.</span></span> <span data-ttu-id="69247-117">このイベントには、スレッドがロックの取得を待機する前のスピン時間は含まれません。このイベントが発生するのは、スレッドがロックの取得を待機するときだけです。</span><span class="sxs-lookup"><span data-stu-id="69247-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="69247-118">81</span><span class="sxs-lookup"><span data-stu-id="69247-118">81</span></span>|<span data-ttu-id="69247-119">競合が終了したとき。</span><span class="sxs-lookup"><span data-stu-id="69247-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="69247-120">次の表にイベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="69247-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="69247-121">フィールド名</span><span class="sxs-lookup"><span data-stu-id="69247-121">Field name</span></span>|<span data-ttu-id="69247-122">データ型</span><span class="sxs-lookup"><span data-stu-id="69247-122">Data type</span></span>|<span data-ttu-id="69247-123">説明</span><span class="sxs-lookup"><span data-stu-id="69247-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="69247-124">フラグ</span><span class="sxs-lookup"><span data-stu-id="69247-124">Flags</span></span>|<span data-ttu-id="69247-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="69247-125">win:UInt8</span></span>|<span data-ttu-id="69247-126">マネージの場合は 0、ネイティブの場合は 1 です。</span><span class="sxs-lookup"><span data-stu-id="69247-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="69247-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="69247-127">ClrInstanceID</span></span>|<span data-ttu-id="69247-128">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="69247-128">win:UInt16</span></span>|<span data-ttu-id="69247-129">CLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="69247-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69247-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="69247-130">See Also</span></span>  
 [<span data-ttu-id="69247-131">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="69247-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)

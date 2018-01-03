---
title: "スタック ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1107c6608fe5136eb6159b1d4f0a438e95c4dabb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="4d488-102">スタック ETW イベント</span><span class="sxs-lookup"><span data-stu-id="4d488-102">Stack ETW Event</span></span>
<span data-ttu-id="4d488-103">イベントの発生後にスタック トレースを生成するには、スタック イベントを他のイベントと併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d488-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="4d488-104">ランタイム プロバイダーが有効になると、ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="4d488-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="4d488-105">これは頻度が非常に高いイベントです。別のランタイム イベントが発生するたびに発生するためです。</span><span class="sxs-lookup"><span data-stu-id="4d488-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="4d488-106">そのような理由から、このイベントの使用には注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="4d488-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="4d488-107">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4d488-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="4d488-108">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="4d488-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4d488-109">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="4d488-109">Keyword for raising the event</span></span>|<span data-ttu-id="4d488-110">レベル</span><span class="sxs-lookup"><span data-stu-id="4d488-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4d488-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="4d488-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="4d488-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="4d488-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="4d488-113">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4d488-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4d488-114">イベント</span><span class="sxs-lookup"><span data-stu-id="4d488-114">Event</span></span>|<span data-ttu-id="4d488-115">イベント ID</span><span class="sxs-lookup"><span data-stu-id="4d488-115">Event ID</span></span>|<span data-ttu-id="4d488-116">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="4d488-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="4d488-117">82</span><span class="sxs-lookup"><span data-stu-id="4d488-117">82</span></span>|<span data-ttu-id="4d488-118">他のイベントを併用し、イベント後にスタック トレースを生成します。</span><span class="sxs-lookup"><span data-stu-id="4d488-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="4d488-119">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="4d488-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4d488-120">フィールド名</span><span class="sxs-lookup"><span data-stu-id="4d488-120">Field name</span></span>|<span data-ttu-id="4d488-121">データ型</span><span class="sxs-lookup"><span data-stu-id="4d488-121">Data Type</span></span>|<span data-ttu-id="4d488-122">説明</span><span class="sxs-lookup"><span data-stu-id="4d488-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4d488-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4d488-123">ClrInstanceID</span></span>|<span data-ttu-id="4d488-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="4d488-124">win:Uint16</span></span>|<span data-ttu-id="4d488-125">一意のランタイム識別子。</span><span class="sxs-lookup"><span data-stu-id="4d488-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="4d488-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="4d488-126">Reserved1</span></span>|<span data-ttu-id="4d488-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="4d488-127">win:UInt8</span></span>|<span data-ttu-id="4d488-128">予約済み。</span><span class="sxs-lookup"><span data-stu-id="4d488-128">Reserved.</span></span>|  
|<span data-ttu-id="4d488-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="4d488-129">Reserved2</span></span>|<span data-ttu-id="4d488-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="4d488-130">win:UInt8</span></span>|<span data-ttu-id="4d488-131">予約済み。</span><span class="sxs-lookup"><span data-stu-id="4d488-131">Reserved.</span></span>|  
|<span data-ttu-id="4d488-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="4d488-132">FrameCount</span></span>|<span data-ttu-id="4d488-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4d488-133">win:UInt32</span></span>|<span data-ttu-id="4d488-134">スタック トレースのフレーム数。</span><span class="sxs-lookup"><span data-stu-id="4d488-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="4d488-135">Stack</span><span class="sxs-lookup"><span data-stu-id="4d488-135">Stack</span></span>|<span data-ttu-id="4d488-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="4d488-136">win:Pointer</span></span>|<span data-ttu-id="4d488-137">命令ポインターの列。</span><span class="sxs-lookup"><span data-stu-id="4d488-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d488-138">参照</span><span class="sxs-lookup"><span data-stu-id="4d488-138">See Also</span></span>  
 [<span data-ttu-id="4d488-139">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="4d488-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)

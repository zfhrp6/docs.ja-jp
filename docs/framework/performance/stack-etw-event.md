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
ms.openlocfilehash: 55219fe755f49b6edbd3b53cc686bf4f9087aa08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="f3688-102">スタック ETW イベント</span><span class="sxs-lookup"><span data-stu-id="f3688-102">Stack ETW Event</span></span>
<span data-ttu-id="f3688-103">イベントの発生後にスタック トレースを生成するには、スタック イベントを他のイベントと併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3688-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="f3688-104">ランタイム プロバイダーが有効になると、ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f3688-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="f3688-105">これは頻度が非常に高いイベントです。別のランタイム イベントが発生するたびに発生するためです。</span><span class="sxs-lookup"><span data-stu-id="f3688-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="f3688-106">そのような理由から、このイベントの使用には注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="f3688-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="f3688-107">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f3688-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="f3688-108">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f3688-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f3688-109">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="f3688-109">Keyword for raising the event</span></span>|<span data-ttu-id="f3688-110">レベル</span><span class="sxs-lookup"><span data-stu-id="f3688-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f3688-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="f3688-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="f3688-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="f3688-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="f3688-113">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f3688-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f3688-114">イベント</span><span class="sxs-lookup"><span data-stu-id="f3688-114">Event</span></span>|<span data-ttu-id="f3688-115">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f3688-115">Event ID</span></span>|<span data-ttu-id="f3688-116">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="f3688-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="f3688-117">82</span><span class="sxs-lookup"><span data-stu-id="f3688-117">82</span></span>|<span data-ttu-id="f3688-118">他のイベントを併用し、イベント後にスタック トレースを生成します。</span><span class="sxs-lookup"><span data-stu-id="f3688-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="f3688-119">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="f3688-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f3688-120">フィールド名</span><span class="sxs-lookup"><span data-stu-id="f3688-120">Field name</span></span>|<span data-ttu-id="f3688-121">データ型</span><span class="sxs-lookup"><span data-stu-id="f3688-121">Data Type</span></span>|<span data-ttu-id="f3688-122">説明</span><span class="sxs-lookup"><span data-stu-id="f3688-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f3688-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3688-123">ClrInstanceID</span></span>|<span data-ttu-id="f3688-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="f3688-124">win:Uint16</span></span>|<span data-ttu-id="f3688-125">一意のランタイム識別子。</span><span class="sxs-lookup"><span data-stu-id="f3688-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="f3688-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="f3688-126">Reserved1</span></span>|<span data-ttu-id="f3688-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="f3688-127">win:UInt8</span></span>|<span data-ttu-id="f3688-128">予約済み。</span><span class="sxs-lookup"><span data-stu-id="f3688-128">Reserved.</span></span>|  
|<span data-ttu-id="f3688-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="f3688-129">Reserved2</span></span>|<span data-ttu-id="f3688-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="f3688-130">win:UInt8</span></span>|<span data-ttu-id="f3688-131">予約済み。</span><span class="sxs-lookup"><span data-stu-id="f3688-131">Reserved.</span></span>|  
|<span data-ttu-id="f3688-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="f3688-132">FrameCount</span></span>|<span data-ttu-id="f3688-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f3688-133">win:UInt32</span></span>|<span data-ttu-id="f3688-134">スタック トレースのフレーム数。</span><span class="sxs-lookup"><span data-stu-id="f3688-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="f3688-135">Stack</span><span class="sxs-lookup"><span data-stu-id="f3688-135">Stack</span></span>|<span data-ttu-id="f3688-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="f3688-136">win:Pointer</span></span>|<span data-ttu-id="f3688-137">命令ポインターの列。</span><span class="sxs-lookup"><span data-stu-id="f3688-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3688-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3688-138">See Also</span></span>  
 [<span data-ttu-id="f3688-139">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="f3688-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)

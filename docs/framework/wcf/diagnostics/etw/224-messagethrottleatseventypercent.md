---
title: 224 - MessageThrottleAtSeventyPercent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0dd985e3986548938f06e86c1f49d23c43307d17
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="30b56-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="30b56-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="30b56-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="30b56-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30b56-104">ID</span><span class="sxs-lookup"><span data-stu-id="30b56-104">ID</span></span>|<span data-ttu-id="30b56-105">224</span><span class="sxs-lookup"><span data-stu-id="30b56-105">224</span></span>|  
|<span data-ttu-id="30b56-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="30b56-106">Keywords</span></span>|<span data-ttu-id="30b56-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30b56-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="30b56-108">レベル</span><span class="sxs-lookup"><span data-stu-id="30b56-108">Level</span></span>|<span data-ttu-id="30b56-109">警告</span><span class="sxs-lookup"><span data-stu-id="30b56-109">Warning</span></span>|  
|<span data-ttu-id="30b56-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="30b56-110">Channel</span></span>|<span data-ttu-id="30b56-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="30b56-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30b56-112">説明</span><span class="sxs-lookup"><span data-stu-id="30b56-112">Description</span></span>  
 <span data-ttu-id="30b56-113">`MessageThrottleExceeded` イベントは、主要なサービス スロットルの 1 つを超過したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="30b56-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="30b56-114">アクティビティの急増が緩やかになり、スロットルの現在の値が現在の制限の 70% である場合は、このイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="30b56-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="30b56-115">このイベントは、アクティビティが緩やかになったときに一度だけ生成されます。</span><span class="sxs-lookup"><span data-stu-id="30b56-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="30b56-116">現在の値が 70% の基準付近を上下している (70、69、70、71、70、69 など) 場合は、最初に 70% に達したときにイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="30b56-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="30b56-117">このイベントが生成された後にスロットル制限を超えた場合は、`MessageThrottleExceeded` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="30b56-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30b56-118">メッセージ</span><span class="sxs-lookup"><span data-stu-id="30b56-118">Message</span></span>  
 <span data-ttu-id="30b56-119">スロットル '%1' の '%2' の制限は 70%% です。</span><span class="sxs-lookup"><span data-stu-id="30b56-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="30b56-120">詳細</span><span class="sxs-lookup"><span data-stu-id="30b56-120">Details</span></span>  
  
|<span data-ttu-id="30b56-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="30b56-121">Data Item Name</span></span>|<span data-ttu-id="30b56-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="30b56-122">Data Item Type</span></span>|<span data-ttu-id="30b56-123">説明</span><span class="sxs-lookup"><span data-stu-id="30b56-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30b56-124">Throttle Name</span><span class="sxs-lookup"><span data-stu-id="30b56-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="30b56-125">超過したスロットルの名前。</span><span class="sxs-lookup"><span data-stu-id="30b56-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="30b56-126">`MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="30b56-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="30b56-127">Limit</span><span class="sxs-lookup"><span data-stu-id="30b56-127">Limit</span></span>|`xs:long`|<span data-ttu-id="30b56-128">現在構成されている、スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="30b56-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="30b56-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="30b56-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="30b56-130">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="30b56-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="30b56-131">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="30b56-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="30b56-132">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="30b56-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="30b56-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="30b56-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="30b56-134">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="30b56-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

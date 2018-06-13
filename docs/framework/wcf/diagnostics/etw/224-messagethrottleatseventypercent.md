---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460396"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="9d302-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="9d302-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="9d302-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9d302-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d302-104">ID</span><span class="sxs-lookup"><span data-stu-id="9d302-104">ID</span></span>|<span data-ttu-id="9d302-105">224</span><span class="sxs-lookup"><span data-stu-id="9d302-105">224</span></span>|  
|<span data-ttu-id="9d302-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="9d302-106">Keywords</span></span>|<span data-ttu-id="9d302-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9d302-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9d302-108">レベル</span><span class="sxs-lookup"><span data-stu-id="9d302-108">Level</span></span>|<span data-ttu-id="9d302-109">警告</span><span class="sxs-lookup"><span data-stu-id="9d302-109">Warning</span></span>|  
|<span data-ttu-id="9d302-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9d302-110">Channel</span></span>|<span data-ttu-id="9d302-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9d302-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d302-112">説明</span><span class="sxs-lookup"><span data-stu-id="9d302-112">Description</span></span>  
 <span data-ttu-id="9d302-113">`MessageThrottleExceeded` イベントは、主要なサービス スロットルの 1 つを超過したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d302-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="9d302-114">アクティビティの急増が緩やかになり、スロットルの現在の値が現在の制限の 70% である場合は、このイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d302-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="9d302-115">このイベントは、アクティビティが緩やかになったときに一度だけ生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d302-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="9d302-116">現在の値が 70% の基準付近を上下している (70、69、70、71、70、69 など) 場合は、最初に 70% に達したときにイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d302-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="9d302-117">このイベントが生成された後にスロットル制限を超えた場合は、`MessageThrottleExceeded` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d302-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d302-118">メッセージ</span><span class="sxs-lookup"><span data-stu-id="9d302-118">Message</span></span>  
 <span data-ttu-id="9d302-119">スロットル '%1' の '%2' の制限は 70%% です。</span><span class="sxs-lookup"><span data-stu-id="9d302-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d302-120">説明</span><span class="sxs-lookup"><span data-stu-id="9d302-120">Details</span></span>  
  
|<span data-ttu-id="9d302-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9d302-121">Data Item Name</span></span>|<span data-ttu-id="9d302-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9d302-122">Data Item Type</span></span>|<span data-ttu-id="9d302-123">説明</span><span class="sxs-lookup"><span data-stu-id="9d302-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d302-124">Throttle Name</span><span class="sxs-lookup"><span data-stu-id="9d302-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="9d302-125">超過したスロットルの名前。</span><span class="sxs-lookup"><span data-stu-id="9d302-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="9d302-126">`MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="9d302-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="9d302-127">Limit</span><span class="sxs-lookup"><span data-stu-id="9d302-127">Limit</span></span>|`xs:long`|<span data-ttu-id="9d302-128">現在構成されている、スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="9d302-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="9d302-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="9d302-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="9d302-130">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="9d302-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9d302-131">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="9d302-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9d302-132">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="9d302-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9d302-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9d302-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9d302-134">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9d302-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

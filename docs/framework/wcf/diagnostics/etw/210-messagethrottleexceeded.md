---
title: 210 - MessageThrottleExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 299cc11dc4f6794b65761ad7da71bcf062c318db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="5af32-102">210 - MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="5af32-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="5af32-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5af32-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5af32-104">ID</span><span class="sxs-lookup"><span data-stu-id="5af32-104">ID</span></span>|<span data-ttu-id="5af32-105">210</span><span class="sxs-lookup"><span data-stu-id="5af32-105">210</span></span>|  
|<span data-ttu-id="5af32-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="5af32-106">Keywords</span></span>|<span data-ttu-id="5af32-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5af32-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5af32-108">レベル</span><span class="sxs-lookup"><span data-stu-id="5af32-108">Level</span></span>|<span data-ttu-id="5af32-109">警告</span><span class="sxs-lookup"><span data-stu-id="5af32-109">Warning</span></span>|  
|<span data-ttu-id="5af32-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5af32-110">Channel</span></span>|<span data-ttu-id="5af32-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5af32-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5af32-112">説明</span><span class="sxs-lookup"><span data-stu-id="5af32-112">Description</span></span>  
 <span data-ttu-id="5af32-113">このイベントは、3 つの主要なサービス スロットルの 1 つを超過したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="5af32-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="5af32-114">このイベントが生成されるのは、最初にスロットル制限を超過したときのみです。</span><span class="sxs-lookup"><span data-stu-id="5af32-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="5af32-115">たとえば、同時呼び出しのスロットル制限が 10 の場合は、11 番目の同時呼び出しが `MessageThrottleExceeded` イベントになります。</span><span class="sxs-lookup"><span data-stu-id="5af32-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="5af32-116">12 番目の呼び出しが別のイベントになることはありません。</span><span class="sxs-lookup"><span data-stu-id="5af32-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="5af32-117">また、イベント ストリームが煩雑になるのを避けるため、制限値の前後のアクティビティの結果が別のイベントになることはありません。</span><span class="sxs-lookup"><span data-stu-id="5af32-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="5af32-118">この例では、2 つの呼び出しが完了した場合、9 つの同時呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="5af32-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="5af32-119">続いて 2 つの呼び出しが行われた場合は、現在の値が再び 11 になります。</span><span class="sxs-lookup"><span data-stu-id="5af32-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="5af32-120">これは、別のイベントにはなりません。</span><span class="sxs-lookup"><span data-stu-id="5af32-120">This does not result in another event.</span></span> <span data-ttu-id="5af32-121">現在の値がスロットル制限の 70% になると、アクティビティの遅れを示す別のイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5af32-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="5af32-122">以降のアクティビティが制限を超えた場合は、別の `MessageThrottleExceeded` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5af32-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="5af32-123">この例では、同時呼び出しの数が 7 になり、再び 11 に達すると、別の `MessageThrottleExceeded` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5af32-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5af32-124">メッセージ</span><span class="sxs-lookup"><span data-stu-id="5af32-124">Message</span></span>  
 <span data-ttu-id="5af32-125">スロットル '%1' の '%2' の制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="5af32-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5af32-126">説明</span><span class="sxs-lookup"><span data-stu-id="5af32-126">Details</span></span>  
  
|<span data-ttu-id="5af32-127">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5af32-127">Data Item Name</span></span>|<span data-ttu-id="5af32-128">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5af32-128">Data Item Type</span></span>|<span data-ttu-id="5af32-129">説明</span><span class="sxs-lookup"><span data-stu-id="5af32-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5af32-130">Throttle Name</span><span class="sxs-lookup"><span data-stu-id="5af32-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="5af32-131">超過したスロットルの名前。</span><span class="sxs-lookup"><span data-stu-id="5af32-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="5af32-132">`MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="5af32-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="5af32-133">Limit</span><span class="sxs-lookup"><span data-stu-id="5af32-133">Limit</span></span>|`xs:long`|<span data-ttu-id="5af32-134">現在構成されている、スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="5af32-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="5af32-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="5af32-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="5af32-136">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="5af32-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5af32-137">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="5af32-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5af32-138">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="5af32-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5af32-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5af32-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5af32-140">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5af32-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

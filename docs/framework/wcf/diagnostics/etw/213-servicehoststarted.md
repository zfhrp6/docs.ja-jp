---
title: 213 - ServiceHostStarted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a83cb1cfb87b562add1a791de5a651b563d63d4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="782b2-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="782b2-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="782b2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="782b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="782b2-104">ID</span><span class="sxs-lookup"><span data-stu-id="782b2-104">ID</span></span>|<span data-ttu-id="782b2-105">213</span><span class="sxs-lookup"><span data-stu-id="782b2-105">213</span></span>|  
|<span data-ttu-id="782b2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="782b2-106">Keywords</span></span>|<span data-ttu-id="782b2-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceHost</span><span class="sxs-lookup"><span data-stu-id="782b2-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="782b2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="782b2-108">Level</span></span>|<span data-ttu-id="782b2-109">LogAlways (常にログ)</span><span class="sxs-lookup"><span data-stu-id="782b2-109">LogAlways</span></span>|  
|<span data-ttu-id="782b2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="782b2-110">Channel</span></span>|<span data-ttu-id="782b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="782b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="782b2-112">説明</span><span class="sxs-lookup"><span data-stu-id="782b2-112">Description</span></span>  
 <span data-ttu-id="782b2-113">このイベントは、Web でホストされているサービス ホストが起動されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="782b2-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="782b2-114">通常、サービスがメッセージによってアクティブにされた時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="782b2-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="782b2-115">また、サービスが自動的に開始するように構成されている場合も発生します。</span><span class="sxs-lookup"><span data-stu-id="782b2-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="782b2-116">メッセージ</span><span class="sxs-lookup"><span data-stu-id="782b2-116">Message</span></span>  
 <span data-ttu-id="782b2-117">ServiceHost は '%1' で開始されています。</span><span class="sxs-lookup"><span data-stu-id="782b2-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="782b2-118">説明</span><span class="sxs-lookup"><span data-stu-id="782b2-118">Details</span></span>  
  
|<span data-ttu-id="782b2-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="782b2-119">Data Item Name</span></span>|<span data-ttu-id="782b2-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="782b2-120">Data Item Type</span></span>|<span data-ttu-id="782b2-121">説明</span><span class="sxs-lookup"><span data-stu-id="782b2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="782b2-122">Service Type Name</span><span class="sxs-lookup"><span data-stu-id="782b2-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="782b2-123">サービス実装の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="782b2-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="782b2-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="782b2-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="782b2-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="782b2-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="782b2-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="782b2-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="782b2-127">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="782b2-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="782b2-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="782b2-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="782b2-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="782b2-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

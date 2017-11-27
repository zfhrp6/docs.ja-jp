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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61d79adce71be9ef93e9232e01a8cba5f5319f79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="ee6a4-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="ee6a4-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="ee6a4-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ee6a4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee6a4-104">ID</span><span class="sxs-lookup"><span data-stu-id="ee6a4-104">ID</span></span>|<span data-ttu-id="ee6a4-105">213</span><span class="sxs-lookup"><span data-stu-id="ee6a4-105">213</span></span>|  
|<span data-ttu-id="ee6a4-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ee6a4-106">Keywords</span></span>|<span data-ttu-id="ee6a4-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceHost</span><span class="sxs-lookup"><span data-stu-id="ee6a4-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="ee6a4-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ee6a4-108">Level</span></span>|<span data-ttu-id="ee6a4-109">LogAlways (常にログ)</span><span class="sxs-lookup"><span data-stu-id="ee6a4-109">LogAlways</span></span>|  
|<span data-ttu-id="ee6a4-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ee6a4-110">Channel</span></span>|<span data-ttu-id="ee6a4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ee6a4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ee6a4-112">説明</span><span class="sxs-lookup"><span data-stu-id="ee6a4-112">Description</span></span>  
 <span data-ttu-id="ee6a4-113">このイベントは、Web でホストされているサービス ホストが起動されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="ee6a4-114">通常、サービスがメッセージによってアクティブにされた時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="ee6a4-115">また、サービスが自動的に開始するように構成されている場合も発生します。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ee6a4-116">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ee6a4-116">Message</span></span>  
 <span data-ttu-id="ee6a4-117">ServiceHost は '%1' で開始されています。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ee6a4-118">詳細</span><span class="sxs-lookup"><span data-stu-id="ee6a4-118">Details</span></span>  
  
|<span data-ttu-id="ee6a4-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ee6a4-119">Data Item Name</span></span>|<span data-ttu-id="ee6a4-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ee6a4-120">Data Item Type</span></span>|<span data-ttu-id="ee6a4-121">説明</span><span class="sxs-lookup"><span data-stu-id="ee6a4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ee6a4-122">Service Type Name</span><span class="sxs-lookup"><span data-stu-id="ee6a4-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="ee6a4-123">サービス実装の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="ee6a4-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="ee6a4-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="ee6a4-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ee6a4-126">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ee6a4-127">例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ee6a4-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ee6a4-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ee6a4-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ee6a4-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

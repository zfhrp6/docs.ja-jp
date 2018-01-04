---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba48f19de1be3cfd2461e159b91fa365e24ee750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="959ee-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="959ee-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="959ee-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="959ee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="959ee-104">ID</span><span class="sxs-lookup"><span data-stu-id="959ee-104">ID</span></span>|<span data-ttu-id="959ee-105">57398</span><span class="sxs-lookup"><span data-stu-id="959ee-105">57398</span></span>|  
|<span data-ttu-id="959ee-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="959ee-106">Keywords</span></span>|<span data-ttu-id="959ee-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="959ee-107">WFServices</span></span>|  
|<span data-ttu-id="959ee-108">レベル</span><span class="sxs-lookup"><span data-stu-id="959ee-108">Level</span></span>|<span data-ttu-id="959ee-109">警告</span><span class="sxs-lookup"><span data-stu-id="959ee-109">Warning</span></span>|  
|<span data-ttu-id="959ee-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="959ee-110">Channel</span></span>|<span data-ttu-id="959ee-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="959ee-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="959ee-112">説明</span><span class="sxs-lookup"><span data-stu-id="959ee-112">Description</span></span>  
 <span data-ttu-id="959ee-113">システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="959ee-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="959ee-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="959ee-114">Message</span></span>  
 <span data-ttu-id="959ee-115">システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="959ee-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="959ee-116">このスロットルの制限は %1 に設定されました。</span><span class="sxs-lookup"><span data-stu-id="959ee-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="959ee-117">スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="959ee-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="959ee-118">詳細</span><span class="sxs-lookup"><span data-stu-id="959ee-118">Details</span></span>  
  
|<span data-ttu-id="959ee-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="959ee-119">Data Item Name</span></span>|<span data-ttu-id="959ee-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="959ee-120">Data Item Type</span></span>|<span data-ttu-id="959ee-121">説明</span><span class="sxs-lookup"><span data-stu-id="959ee-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="959ee-122">名前</span><span class="sxs-lookup"><span data-stu-id="959ee-122">Name</span></span>|<span data-ttu-id="959ee-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="959ee-123">xs:string</span></span>|<span data-ttu-id="959ee-124">項目の名前。</span><span class="sxs-lookup"><span data-stu-id="959ee-124">The name of the item.</span></span>|  
|<span data-ttu-id="959ee-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="959ee-125">AppDomain</span></span>|<span data-ttu-id="959ee-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="959ee-126">xs:string</span></span>|<span data-ttu-id="959ee-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="959ee-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

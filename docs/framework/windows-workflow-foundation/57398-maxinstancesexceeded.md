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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="95acc-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="95acc-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="95acc-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="95acc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95acc-104">ID</span><span class="sxs-lookup"><span data-stu-id="95acc-104">ID</span></span>|<span data-ttu-id="95acc-105">57398</span><span class="sxs-lookup"><span data-stu-id="95acc-105">57398</span></span>|  
|<span data-ttu-id="95acc-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="95acc-106">Keywords</span></span>|<span data-ttu-id="95acc-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="95acc-107">WFServices</span></span>|  
|<span data-ttu-id="95acc-108">レベル</span><span class="sxs-lookup"><span data-stu-id="95acc-108">Level</span></span>|<span data-ttu-id="95acc-109">警告</span><span class="sxs-lookup"><span data-stu-id="95acc-109">Warning</span></span>|  
|<span data-ttu-id="95acc-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="95acc-110">Channel</span></span>|<span data-ttu-id="95acc-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="95acc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="95acc-112">説明</span><span class="sxs-lookup"><span data-stu-id="95acc-112">Description</span></span>  
 <span data-ttu-id="95acc-113">システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="95acc-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="95acc-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="95acc-114">Message</span></span>  
 <span data-ttu-id="95acc-115">システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="95acc-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="95acc-116">このスロットルの制限は %1 に設定されました。</span><span class="sxs-lookup"><span data-stu-id="95acc-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="95acc-117">スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95acc-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="95acc-118">詳細</span><span class="sxs-lookup"><span data-stu-id="95acc-118">Details</span></span>  
  
|<span data-ttu-id="95acc-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="95acc-119">Data Item Name</span></span>|<span data-ttu-id="95acc-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="95acc-120">Data Item Type</span></span>|<span data-ttu-id="95acc-121">説明</span><span class="sxs-lookup"><span data-stu-id="95acc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="95acc-122">名前</span><span class="sxs-lookup"><span data-stu-id="95acc-122">Name</span></span>|<span data-ttu-id="95acc-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="95acc-123">xs:string</span></span>|<span data-ttu-id="95acc-124">項目の名前。</span><span class="sxs-lookup"><span data-stu-id="95acc-124">The name of the item.</span></span>|  
|<span data-ttu-id="95acc-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="95acc-125">AppDomain</span></span>|<span data-ttu-id="95acc-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="95acc-126">xs:string</span></span>|<span data-ttu-id="95acc-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="95acc-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

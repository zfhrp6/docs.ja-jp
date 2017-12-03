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
ms.openlocfilehash: 803616fdd287491afa27d3ac23dfce99c5db08ca
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="ece45-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="ece45-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="ece45-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ece45-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ece45-104">ID</span><span class="sxs-lookup"><span data-stu-id="ece45-104">ID</span></span>|<span data-ttu-id="ece45-105">57398</span><span class="sxs-lookup"><span data-stu-id="ece45-105">57398</span></span>|  
|<span data-ttu-id="ece45-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ece45-106">Keywords</span></span>|<span data-ttu-id="ece45-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ece45-107">WFServices</span></span>|  
|<span data-ttu-id="ece45-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ece45-108">Level</span></span>|<span data-ttu-id="ece45-109">警告</span><span class="sxs-lookup"><span data-stu-id="ece45-109">Warning</span></span>|  
|<span data-ttu-id="ece45-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ece45-110">Channel</span></span>|<span data-ttu-id="ece45-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ece45-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ece45-112">説明</span><span class="sxs-lookup"><span data-stu-id="ece45-112">Description</span></span>  
 <span data-ttu-id="ece45-113">システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ece45-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ece45-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ece45-114">Message</span></span>  
 <span data-ttu-id="ece45-115">システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="ece45-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="ece45-116">このスロットルの制限は %1 に設定されました。</span><span class="sxs-lookup"><span data-stu-id="ece45-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="ece45-117">スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ece45-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ece45-118">詳細</span><span class="sxs-lookup"><span data-stu-id="ece45-118">Details</span></span>  
  
|<span data-ttu-id="ece45-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ece45-119">Data Item Name</span></span>|<span data-ttu-id="ece45-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ece45-120">Data Item Type</span></span>|<span data-ttu-id="ece45-121">説明</span><span class="sxs-lookup"><span data-stu-id="ece45-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ece45-122">名前</span><span class="sxs-lookup"><span data-stu-id="ece45-122">Name</span></span>|<span data-ttu-id="ece45-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="ece45-123">xs:string</span></span>|<span data-ttu-id="ece45-124">項目の名前。</span><span class="sxs-lookup"><span data-stu-id="ece45-124">The name of the item.</span></span>|  
|<span data-ttu-id="ece45-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ece45-125">AppDomain</span></span>|<span data-ttu-id="ece45-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="ece45-126">xs:string</span></span>|<span data-ttu-id="ece45-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ece45-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe006534e0199888668145be9da3f964055cc464
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="2b17b-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="2b17b-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2b17b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2b17b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b17b-104">ID</span><span class="sxs-lookup"><span data-stu-id="2b17b-104">ID</span></span>|<span data-ttu-id="2b17b-105">1011</span><span class="sxs-lookup"><span data-stu-id="2b17b-105">1011</span></span>|  
|<span data-ttu-id="2b17b-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2b17b-106">Keywords</span></span>|<span data-ttu-id="2b17b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2b17b-107">WFRuntime</span></span>|  
|<span data-ttu-id="2b17b-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2b17b-108">Level</span></span>|<span data-ttu-id="2b17b-109">詳細</span><span class="sxs-lookup"><span data-stu-id="2b17b-109">Verbose</span></span>|  
|<span data-ttu-id="2b17b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2b17b-110">Channel</span></span>|<span data-ttu-id="2b17b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2b17b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b17b-112">説明</span><span class="sxs-lookup"><span data-stu-id="2b17b-112">Description</span></span>  
 <span data-ttu-id="2b17b-113">ExecuteActivityWorkItem がスケジュールされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="2b17b-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b17b-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2b17b-114">Message</span></span>  
 <span data-ttu-id="2b17b-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="2b17b-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b17b-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2b17b-116">Details</span></span>  
  
|<span data-ttu-id="2b17b-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2b17b-117">Data Item Name</span></span>|<span data-ttu-id="2b17b-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2b17b-118">Data Item Type</span></span>|<span data-ttu-id="2b17b-119">説明</span><span class="sxs-lookup"><span data-stu-id="2b17b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b17b-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2b17b-120">Activity</span></span>|<span data-ttu-id="2b17b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b17b-121">xs:string</span></span>|<span data-ttu-id="2b17b-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="2b17b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2b17b-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2b17b-123">DisplayName</span></span>|<span data-ttu-id="2b17b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b17b-124">xs:string</span></span>|<span data-ttu-id="2b17b-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2b17b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2b17b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2b17b-126">InstanceId</span></span>|<span data-ttu-id="2b17b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b17b-127">xs:string</span></span>|<span data-ttu-id="2b17b-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="2b17b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2b17b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b17b-129">AppDomain</span></span>|<span data-ttu-id="2b17b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b17b-130">xs:string</span></span>|<span data-ttu-id="2b17b-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2b17b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

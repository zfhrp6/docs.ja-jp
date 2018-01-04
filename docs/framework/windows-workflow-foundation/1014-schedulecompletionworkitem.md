---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a80406ce56000703555f7834714222e03d2b65f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="3d971-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="3d971-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3d971-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3d971-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d971-104">ID</span><span class="sxs-lookup"><span data-stu-id="3d971-104">ID</span></span>|<span data-ttu-id="3d971-105">1014</span><span class="sxs-lookup"><span data-stu-id="3d971-105">1014</span></span>|  
|<span data-ttu-id="3d971-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="3d971-106">Keywords</span></span>|<span data-ttu-id="3d971-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3d971-107">WFRuntime</span></span>|  
|<span data-ttu-id="3d971-108">レベル</span><span class="sxs-lookup"><span data-stu-id="3d971-108">Level</span></span>|<span data-ttu-id="3d971-109">詳細</span><span class="sxs-lookup"><span data-stu-id="3d971-109">Verbose</span></span>|  
|<span data-ttu-id="3d971-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="3d971-110">Channel</span></span>|<span data-ttu-id="3d971-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3d971-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d971-112">説明</span><span class="sxs-lookup"><span data-stu-id="3d971-112">Description</span></span>  
 <span data-ttu-id="3d971-113">CompletionWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d971-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d971-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="3d971-114">Message</span></span>  
 <span data-ttu-id="3d971-115">親 Activity '%1'、DisplayName に対して CompletionWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="3d971-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="3d971-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3d971-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d971-117">詳細</span><span class="sxs-lookup"><span data-stu-id="3d971-117">Details</span></span>  
  
|<span data-ttu-id="3d971-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3d971-118">Data Item Name</span></span>|<span data-ttu-id="3d971-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3d971-119">Data Item Type</span></span>|<span data-ttu-id="3d971-120">説明</span><span class="sxs-lookup"><span data-stu-id="3d971-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d971-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="3d971-121">ParentActivity</span></span>|<span data-ttu-id="3d971-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-122">xs:string</span></span>|<span data-ttu-id="3d971-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="3d971-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="3d971-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="3d971-124">ParentDisplayName</span></span>|<span data-ttu-id="3d971-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-125">xs:string</span></span>|<span data-ttu-id="3d971-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3d971-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="3d971-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="3d971-127">ParentInstanceId</span></span>|<span data-ttu-id="3d971-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-128">xs:string</span></span>|<span data-ttu-id="3d971-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="3d971-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="3d971-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="3d971-130">CompletedActivity</span></span>|<span data-ttu-id="3d971-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-131">xs:string</span></span>|<span data-ttu-id="3d971-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="3d971-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="3d971-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3d971-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="3d971-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-134">xs:string</span></span>|<span data-ttu-id="3d971-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3d971-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="3d971-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3d971-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="3d971-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-137">xs:string</span></span>|<span data-ttu-id="3d971-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="3d971-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="3d971-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d971-139">AppDomain</span></span>|<span data-ttu-id="3d971-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d971-140">xs:string</span></span>|<span data-ttu-id="3d971-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3d971-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

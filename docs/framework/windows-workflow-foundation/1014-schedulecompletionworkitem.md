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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="7043c-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="7043c-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7043c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7043c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7043c-104">ID</span><span class="sxs-lookup"><span data-stu-id="7043c-104">ID</span></span>|<span data-ttu-id="7043c-105">1014</span><span class="sxs-lookup"><span data-stu-id="7043c-105">1014</span></span>|  
|<span data-ttu-id="7043c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7043c-106">Keywords</span></span>|<span data-ttu-id="7043c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7043c-107">WFRuntime</span></span>|  
|<span data-ttu-id="7043c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7043c-108">Level</span></span>|<span data-ttu-id="7043c-109">詳細</span><span class="sxs-lookup"><span data-stu-id="7043c-109">Verbose</span></span>|  
|<span data-ttu-id="7043c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7043c-110">Channel</span></span>|<span data-ttu-id="7043c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7043c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7043c-112">説明</span><span class="sxs-lookup"><span data-stu-id="7043c-112">Description</span></span>  
 <span data-ttu-id="7043c-113">CompletionWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="7043c-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7043c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7043c-114">Message</span></span>  
 <span data-ttu-id="7043c-115">親 Activity '%1'、DisplayName に対して CompletionWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="7043c-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="7043c-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="7043c-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7043c-117">詳細</span><span class="sxs-lookup"><span data-stu-id="7043c-117">Details</span></span>  
  
|<span data-ttu-id="7043c-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7043c-118">Data Item Name</span></span>|<span data-ttu-id="7043c-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7043c-119">Data Item Type</span></span>|<span data-ttu-id="7043c-120">説明</span><span class="sxs-lookup"><span data-stu-id="7043c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7043c-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="7043c-121">ParentActivity</span></span>|<span data-ttu-id="7043c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-122">xs:string</span></span>|<span data-ttu-id="7043c-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="7043c-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="7043c-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="7043c-124">ParentDisplayName</span></span>|<span data-ttu-id="7043c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-125">xs:string</span></span>|<span data-ttu-id="7043c-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="7043c-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="7043c-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="7043c-127">ParentInstanceId</span></span>|<span data-ttu-id="7043c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-128">xs:string</span></span>|<span data-ttu-id="7043c-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="7043c-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="7043c-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="7043c-130">CompletedActivity</span></span>|<span data-ttu-id="7043c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-131">xs:string</span></span>|<span data-ttu-id="7043c-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="7043c-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="7043c-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="7043c-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="7043c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-134">xs:string</span></span>|<span data-ttu-id="7043c-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="7043c-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="7043c-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="7043c-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="7043c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-137">xs:string</span></span>|<span data-ttu-id="7043c-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="7043c-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="7043c-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7043c-139">AppDomain</span></span>|<span data-ttu-id="7043c-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="7043c-140">xs:string</span></span>|<span data-ttu-id="7043c-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7043c-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

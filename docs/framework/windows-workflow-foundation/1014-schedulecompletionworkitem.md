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
ms.openlocfilehash: 3d483a681cae6328dd6111b320a12b5a064d3ff5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="89431-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="89431-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="89431-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="89431-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89431-104">ID</span><span class="sxs-lookup"><span data-stu-id="89431-104">ID</span></span>|<span data-ttu-id="89431-105">1014</span><span class="sxs-lookup"><span data-stu-id="89431-105">1014</span></span>|  
|<span data-ttu-id="89431-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="89431-106">Keywords</span></span>|<span data-ttu-id="89431-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="89431-107">WFRuntime</span></span>|  
|<span data-ttu-id="89431-108">レベル</span><span class="sxs-lookup"><span data-stu-id="89431-108">Level</span></span>|<span data-ttu-id="89431-109">詳細</span><span class="sxs-lookup"><span data-stu-id="89431-109">Verbose</span></span>|  
|<span data-ttu-id="89431-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="89431-110">Channel</span></span>|<span data-ttu-id="89431-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="89431-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="89431-112">説明</span><span class="sxs-lookup"><span data-stu-id="89431-112">Description</span></span>  
 <span data-ttu-id="89431-113">CompletionWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="89431-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="89431-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="89431-114">Message</span></span>  
 <span data-ttu-id="89431-115">親 Activity '%1'、DisplayName に対して CompletionWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="89431-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="89431-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="89431-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="89431-117">詳細</span><span class="sxs-lookup"><span data-stu-id="89431-117">Details</span></span>  
  
|<span data-ttu-id="89431-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="89431-118">Data Item Name</span></span>|<span data-ttu-id="89431-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="89431-119">Data Item Type</span></span>|<span data-ttu-id="89431-120">説明</span><span class="sxs-lookup"><span data-stu-id="89431-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="89431-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="89431-121">ParentActivity</span></span>|<span data-ttu-id="89431-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-122">xs:string</span></span>|<span data-ttu-id="89431-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="89431-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="89431-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="89431-124">ParentDisplayName</span></span>|<span data-ttu-id="89431-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-125">xs:string</span></span>|<span data-ttu-id="89431-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="89431-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="89431-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="89431-127">ParentInstanceId</span></span>|<span data-ttu-id="89431-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-128">xs:string</span></span>|<span data-ttu-id="89431-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="89431-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="89431-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="89431-130">CompletedActivity</span></span>|<span data-ttu-id="89431-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-131">xs:string</span></span>|<span data-ttu-id="89431-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="89431-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="89431-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="89431-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="89431-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-134">xs:string</span></span>|<span data-ttu-id="89431-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="89431-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="89431-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="89431-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="89431-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-137">xs:string</span></span>|<span data-ttu-id="89431-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="89431-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="89431-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="89431-139">AppDomain</span></span>|<span data-ttu-id="89431-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="89431-140">xs:string</span></span>|<span data-ttu-id="89431-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="89431-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="bec40-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="bec40-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="bec40-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bec40-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bec40-104">ID</span><span class="sxs-lookup"><span data-stu-id="bec40-104">ID</span></span>|<span data-ttu-id="bec40-105">1014</span><span class="sxs-lookup"><span data-stu-id="bec40-105">1014</span></span>|  
|<span data-ttu-id="bec40-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bec40-106">Keywords</span></span>|<span data-ttu-id="bec40-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bec40-107">WFRuntime</span></span>|  
|<span data-ttu-id="bec40-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bec40-108">Level</span></span>|<span data-ttu-id="bec40-109">詳細</span><span class="sxs-lookup"><span data-stu-id="bec40-109">Verbose</span></span>|  
|<span data-ttu-id="bec40-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bec40-110">Channel</span></span>|<span data-ttu-id="bec40-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bec40-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bec40-112">説明</span><span class="sxs-lookup"><span data-stu-id="bec40-112">Description</span></span>  
 <span data-ttu-id="bec40-113">CompletionWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="bec40-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bec40-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bec40-114">Message</span></span>  
 <span data-ttu-id="bec40-115">親 Activity '%1'、DisplayName に対して CompletionWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="bec40-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="bec40-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="bec40-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bec40-117">詳細</span><span class="sxs-lookup"><span data-stu-id="bec40-117">Details</span></span>  
  
|<span data-ttu-id="bec40-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bec40-118">Data Item Name</span></span>|<span data-ttu-id="bec40-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bec40-119">Data Item Type</span></span>|<span data-ttu-id="bec40-120">説明</span><span class="sxs-lookup"><span data-stu-id="bec40-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bec40-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="bec40-121">ParentActivity</span></span>|<span data-ttu-id="bec40-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-122">xs:string</span></span>|<span data-ttu-id="bec40-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bec40-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="bec40-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="bec40-124">ParentDisplayName</span></span>|<span data-ttu-id="bec40-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-125">xs:string</span></span>|<span data-ttu-id="bec40-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bec40-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="bec40-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="bec40-127">ParentInstanceId</span></span>|<span data-ttu-id="bec40-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-128">xs:string</span></span>|<span data-ttu-id="bec40-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bec40-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="bec40-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="bec40-130">CompletedActivity</span></span>|<span data-ttu-id="bec40-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-131">xs:string</span></span>|<span data-ttu-id="bec40-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bec40-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="bec40-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="bec40-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="bec40-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-134">xs:string</span></span>|<span data-ttu-id="bec40-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bec40-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="bec40-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="bec40-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="bec40-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-137">xs:string</span></span>|<span data-ttu-id="bec40-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bec40-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="bec40-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bec40-139">AppDomain</span></span>|<span data-ttu-id="bec40-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="bec40-140">xs:string</span></span>|<span data-ttu-id="bec40-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bec40-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

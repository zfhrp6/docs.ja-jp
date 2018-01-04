---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="86d43-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="86d43-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="86d43-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="86d43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86d43-104">ID</span><span class="sxs-lookup"><span data-stu-id="86d43-104">ID</span></span>|<span data-ttu-id="86d43-105">1016</span><span class="sxs-lookup"><span data-stu-id="86d43-105">1016</span></span>|  
|<span data-ttu-id="86d43-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="86d43-106">Keywords</span></span>|<span data-ttu-id="86d43-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="86d43-107">WFRuntime</span></span>|  
|<span data-ttu-id="86d43-108">レベル</span><span class="sxs-lookup"><span data-stu-id="86d43-108">Level</span></span>|<span data-ttu-id="86d43-109">詳細</span><span class="sxs-lookup"><span data-stu-id="86d43-109">Verbose</span></span>|  
|<span data-ttu-id="86d43-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="86d43-110">Channel</span></span>|<span data-ttu-id="86d43-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="86d43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86d43-112">説明</span><span class="sxs-lookup"><span data-stu-id="86d43-112">Description</span></span>  
 <span data-ttu-id="86d43-113">CompletionWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="86d43-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86d43-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="86d43-114">Message</span></span>  
 <span data-ttu-id="86d43-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="86d43-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="86d43-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="86d43-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86d43-117">詳細</span><span class="sxs-lookup"><span data-stu-id="86d43-117">Details</span></span>  
  
|<span data-ttu-id="86d43-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="86d43-118">Data Item Name</span></span>|<span data-ttu-id="86d43-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="86d43-119">Data Item Type</span></span>|<span data-ttu-id="86d43-120">説明</span><span class="sxs-lookup"><span data-stu-id="86d43-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86d43-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="86d43-121">ParentActivity</span></span>|<span data-ttu-id="86d43-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-122">xs:string</span></span>|<span data-ttu-id="86d43-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="86d43-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="86d43-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="86d43-124">ParentDisplayName</span></span>|<span data-ttu-id="86d43-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-125">xs:string</span></span>|<span data-ttu-id="86d43-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="86d43-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="86d43-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="86d43-127">ParentInstanceId</span></span>|<span data-ttu-id="86d43-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-128">xs:string</span></span>|<span data-ttu-id="86d43-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="86d43-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="86d43-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="86d43-130">CompletedActivity</span></span>|<span data-ttu-id="86d43-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-131">xs:string</span></span>|<span data-ttu-id="86d43-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="86d43-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="86d43-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="86d43-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="86d43-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-134">xs:string</span></span>|<span data-ttu-id="86d43-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="86d43-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="86d43-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="86d43-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="86d43-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-137">xs:string</span></span>|<span data-ttu-id="86d43-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="86d43-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="86d43-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86d43-139">AppDomain</span></span>|<span data-ttu-id="86d43-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="86d43-140">xs:string</span></span>|<span data-ttu-id="86d43-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="86d43-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

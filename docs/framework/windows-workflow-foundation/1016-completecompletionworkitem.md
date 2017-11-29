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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a7c6b6060e8dd3256d23db7350299d2670f6caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="4fbed-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="4fbed-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4fbed-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4fbed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4fbed-104">ID</span><span class="sxs-lookup"><span data-stu-id="4fbed-104">ID</span></span>|<span data-ttu-id="4fbed-105">1016</span><span class="sxs-lookup"><span data-stu-id="4fbed-105">1016</span></span>|  
|<span data-ttu-id="4fbed-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="4fbed-106">Keywords</span></span>|<span data-ttu-id="4fbed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4fbed-107">WFRuntime</span></span>|  
|<span data-ttu-id="4fbed-108">レベル</span><span class="sxs-lookup"><span data-stu-id="4fbed-108">Level</span></span>|<span data-ttu-id="4fbed-109">詳細</span><span class="sxs-lookup"><span data-stu-id="4fbed-109">Verbose</span></span>|  
|<span data-ttu-id="4fbed-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4fbed-110">Channel</span></span>|<span data-ttu-id="4fbed-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4fbed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4fbed-112">説明</span><span class="sxs-lookup"><span data-stu-id="4fbed-112">Description</span></span>  
 <span data-ttu-id="4fbed-113">CompletionWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="4fbed-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4fbed-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="4fbed-114">Message</span></span>  
 <span data-ttu-id="4fbed-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="4fbed-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="4fbed-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="4fbed-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4fbed-117">詳細</span><span class="sxs-lookup"><span data-stu-id="4fbed-117">Details</span></span>  
  
|<span data-ttu-id="4fbed-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4fbed-118">Data Item Name</span></span>|<span data-ttu-id="4fbed-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4fbed-119">Data Item Type</span></span>|<span data-ttu-id="4fbed-120">説明</span><span class="sxs-lookup"><span data-stu-id="4fbed-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4fbed-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="4fbed-121">ParentActivity</span></span>|<span data-ttu-id="4fbed-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-122">xs:string</span></span>|<span data-ttu-id="4fbed-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="4fbed-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="4fbed-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="4fbed-124">ParentDisplayName</span></span>|<span data-ttu-id="4fbed-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-125">xs:string</span></span>|<span data-ttu-id="4fbed-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4fbed-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="4fbed-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="4fbed-127">ParentInstanceId</span></span>|<span data-ttu-id="4fbed-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-128">xs:string</span></span>|<span data-ttu-id="4fbed-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="4fbed-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="4fbed-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="4fbed-130">CompletedActivity</span></span>|<span data-ttu-id="4fbed-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-131">xs:string</span></span>|<span data-ttu-id="4fbed-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="4fbed-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="4fbed-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="4fbed-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="4fbed-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-134">xs:string</span></span>|<span data-ttu-id="4fbed-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4fbed-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="4fbed-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="4fbed-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="4fbed-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-137">xs:string</span></span>|<span data-ttu-id="4fbed-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="4fbed-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="4fbed-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4fbed-139">AppDomain</span></span>|<span data-ttu-id="4fbed-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="4fbed-140">xs:string</span></span>|<span data-ttu-id="4fbed-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4fbed-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

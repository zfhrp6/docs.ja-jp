---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9463fbf2e7f2ac3424488dc3fca322a91d11126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="bb86a-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="bb86a-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="bb86a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bb86a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb86a-104">ID</span><span class="sxs-lookup"><span data-stu-id="bb86a-104">ID</span></span>|<span data-ttu-id="bb86a-105">1009</span><span class="sxs-lookup"><span data-stu-id="bb86a-105">1009</span></span>|  
|<span data-ttu-id="bb86a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bb86a-106">Keywords</span></span>|<span data-ttu-id="bb86a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bb86a-107">WFRuntime</span></span>|  
|<span data-ttu-id="bb86a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bb86a-108">Level</span></span>|<span data-ttu-id="bb86a-109">情報</span><span class="sxs-lookup"><span data-stu-id="bb86a-109">Information</span></span>|  
|<span data-ttu-id="bb86a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bb86a-110">Channel</span></span>|<span data-ttu-id="bb86a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bb86a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bb86a-112">説明</span><span class="sxs-lookup"><span data-stu-id="bb86a-112">Description</span></span>  
 <span data-ttu-id="bb86a-113">アクティビティの実行がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="bb86a-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bb86a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bb86a-114">Message</span></span>  
 <span data-ttu-id="bb86a-115">Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="bb86a-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bb86a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bb86a-116">Details</span></span>  
  
|<span data-ttu-id="bb86a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bb86a-117">Data Item Name</span></span>|<span data-ttu-id="bb86a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bb86a-118">Data Item Type</span></span>|<span data-ttu-id="bb86a-119">説明</span><span class="sxs-lookup"><span data-stu-id="bb86a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bb86a-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="bb86a-120">ParentActivity</span></span>|<span data-ttu-id="bb86a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-121">xs:string</span></span>|<span data-ttu-id="bb86a-122">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bb86a-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="bb86a-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="bb86a-123">ParentDisplayName</span></span>|<span data-ttu-id="bb86a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-124">xs:string</span></span>|<span data-ttu-id="bb86a-125">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bb86a-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="bb86a-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="bb86a-126">ParentInstanceId</span></span>|<span data-ttu-id="bb86a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-127">xs:string</span></span>|<span data-ttu-id="bb86a-128">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bb86a-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="bb86a-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="bb86a-129">ChildActivity</span></span>|<span data-ttu-id="bb86a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-130">xs:string</span></span>|<span data-ttu-id="bb86a-131">スケジュール済みの子アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bb86a-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="bb86a-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="bb86a-132">ChildDisplayName</span></span>|<span data-ttu-id="bb86a-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-133">xs:string</span></span>|<span data-ttu-id="bb86a-134">スケジュール済みの子アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bb86a-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="bb86a-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="bb86a-135">ChildInstanceId</span></span>|<span data-ttu-id="bb86a-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-136">xs:string</span></span>|<span data-ttu-id="bb86a-137">スケジュール済み子アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bb86a-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="bb86a-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bb86a-138">AppDomain</span></span>|<span data-ttu-id="bb86a-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb86a-139">xs:string</span></span>|<span data-ttu-id="bb86a-140">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bb86a-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

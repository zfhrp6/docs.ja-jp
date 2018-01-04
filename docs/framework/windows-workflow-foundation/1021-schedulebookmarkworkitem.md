---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61c67792f807907f58480f3bfa3d192b811766b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="a92ec-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="a92ec-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a92ec-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a92ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a92ec-104">ID</span><span class="sxs-lookup"><span data-stu-id="a92ec-104">ID</span></span>|<span data-ttu-id="a92ec-105">1021</span><span class="sxs-lookup"><span data-stu-id="a92ec-105">1021</span></span>|  
|<span data-ttu-id="a92ec-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a92ec-106">Keywords</span></span>|<span data-ttu-id="a92ec-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a92ec-107">WFRuntime</span></span>|  
|<span data-ttu-id="a92ec-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a92ec-108">Level</span></span>|<span data-ttu-id="a92ec-109">詳細</span><span class="sxs-lookup"><span data-stu-id="a92ec-109">Verbose</span></span>|  
|<span data-ttu-id="a92ec-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a92ec-110">Channel</span></span>|<span data-ttu-id="a92ec-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a92ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a92ec-112">説明</span><span class="sxs-lookup"><span data-stu-id="a92ec-112">Description</span></span>  
 <span data-ttu-id="a92ec-113">BookmarkWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a92ec-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a92ec-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a92ec-114">Message</span></span>  
 <span data-ttu-id="a92ec-115">Activity '%1'、DisplayName に対して BookmarkWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="a92ec-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="a92ec-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="a92ec-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a92ec-117">詳細</span><span class="sxs-lookup"><span data-stu-id="a92ec-117">Details</span></span>  
  
|<span data-ttu-id="a92ec-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a92ec-118">Data Item Name</span></span>|<span data-ttu-id="a92ec-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a92ec-119">Data Item Type</span></span>|<span data-ttu-id="a92ec-120">説明</span><span class="sxs-lookup"><span data-stu-id="a92ec-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a92ec-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a92ec-121">Activity</span></span>|<span data-ttu-id="a92ec-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a92ec-122">xs:string</span></span>|<span data-ttu-id="a92ec-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="a92ec-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="a92ec-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a92ec-124">DisplayName</span></span>|<span data-ttu-id="a92ec-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a92ec-125">xs:string</span></span>|<span data-ttu-id="a92ec-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a92ec-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="a92ec-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a92ec-127">InstanceId</span></span>|<span data-ttu-id="a92ec-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a92ec-128">xs:string</span></span>|<span data-ttu-id="a92ec-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a92ec-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a92ec-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="a92ec-130">BookmarkName</span></span>|<span data-ttu-id="a92ec-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a92ec-131">xs:string</span></span>|<span data-ttu-id="a92ec-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="a92ec-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="a92ec-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="a92ec-133">BookmarkScope</span></span>|<span data-ttu-id="a92ec-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="a92ec-134">xs:string</span></span>|<span data-ttu-id="a92ec-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="a92ec-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="a92ec-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a92ec-136">AppDomain</span></span>|<span data-ttu-id="a92ec-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="a92ec-137">xs:string</span></span>|<span data-ttu-id="a92ec-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a92ec-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

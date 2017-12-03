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
ms.openlocfilehash: 781f4b6d064ac90f762e10e03783422c64a1bf05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="6a6dd-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="6a6dd-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6a6dd-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6a6dd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a6dd-104">ID</span><span class="sxs-lookup"><span data-stu-id="6a6dd-104">ID</span></span>|<span data-ttu-id="6a6dd-105">1021</span><span class="sxs-lookup"><span data-stu-id="6a6dd-105">1021</span></span>|  
|<span data-ttu-id="6a6dd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6a6dd-106">Keywords</span></span>|<span data-ttu-id="6a6dd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6a6dd-107">WFRuntime</span></span>|  
|<span data-ttu-id="6a6dd-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6a6dd-108">Level</span></span>|<span data-ttu-id="6a6dd-109">詳細</span><span class="sxs-lookup"><span data-stu-id="6a6dd-109">Verbose</span></span>|  
|<span data-ttu-id="6a6dd-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6a6dd-110">Channel</span></span>|<span data-ttu-id="6a6dd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6a6dd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6a6dd-112">説明</span><span class="sxs-lookup"><span data-stu-id="6a6dd-112">Description</span></span>  
 <span data-ttu-id="6a6dd-113">BookmarkWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6a6dd-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6a6dd-114">Message</span></span>  
 <span data-ttu-id="6a6dd-115">Activity '%1'、DisplayName に対して BookmarkWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="6a6dd-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6a6dd-117">詳細</span><span class="sxs-lookup"><span data-stu-id="6a6dd-117">Details</span></span>  
  
|<span data-ttu-id="6a6dd-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6a6dd-118">Data Item Name</span></span>|<span data-ttu-id="6a6dd-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6a6dd-119">Data Item Type</span></span>|<span data-ttu-id="6a6dd-120">説明</span><span class="sxs-lookup"><span data-stu-id="6a6dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6a6dd-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="6a6dd-121">Activity</span></span>|<span data-ttu-id="6a6dd-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6dd-122">xs:string</span></span>|<span data-ttu-id="6a6dd-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="6a6dd-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6a6dd-124">DisplayName</span></span>|<span data-ttu-id="6a6dd-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6dd-125">xs:string</span></span>|<span data-ttu-id="6a6dd-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="6a6dd-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6a6dd-127">InstanceId</span></span>|<span data-ttu-id="6a6dd-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6dd-128">xs:string</span></span>|<span data-ttu-id="6a6dd-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6a6dd-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="6a6dd-130">BookmarkName</span></span>|<span data-ttu-id="6a6dd-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6dd-131">xs:string</span></span>|<span data-ttu-id="6a6dd-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="6a6dd-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="6a6dd-133">BookmarkScope</span></span>|<span data-ttu-id="6a6dd-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6dd-134">xs:string</span></span>|<span data-ttu-id="6a6dd-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="6a6dd-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6a6dd-136">AppDomain</span></span>|<span data-ttu-id="6a6dd-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6dd-137">xs:string</span></span>|<span data-ttu-id="6a6dd-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6a6dd-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

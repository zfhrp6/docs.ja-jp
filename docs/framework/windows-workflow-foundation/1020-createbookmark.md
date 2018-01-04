---
title: 1020 - CreateBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c47a5464222d12c1dba717e24606e5614e392f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1020---createbookmark"></a><span data-ttu-id="6a6db-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="6a6db-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="6a6db-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6a6db-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a6db-104">ID</span><span class="sxs-lookup"><span data-stu-id="6a6db-104">ID</span></span>|<span data-ttu-id="6a6db-105">1020</span><span class="sxs-lookup"><span data-stu-id="6a6db-105">1020</span></span>|  
|<span data-ttu-id="6a6db-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6a6db-106">Keywords</span></span>|<span data-ttu-id="6a6db-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6a6db-107">WFRuntime</span></span>|  
|<span data-ttu-id="6a6db-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6a6db-108">Level</span></span>|<span data-ttu-id="6a6db-109">詳細</span><span class="sxs-lookup"><span data-stu-id="6a6db-109">Verbose</span></span>|  
|<span data-ttu-id="6a6db-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6a6db-110">Channel</span></span>|<span data-ttu-id="6a6db-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6a6db-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6a6db-112">説明</span><span class="sxs-lookup"><span data-stu-id="6a6db-112">Description</span></span>  
 <span data-ttu-id="6a6db-113">あるアクティビティ用のブックマークが作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="6a6db-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6a6db-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6a6db-114">Message</span></span>  
 <span data-ttu-id="6a6db-115">Activity '%1'、DisplayName のブックマークが作成されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="6a6db-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="6a6db-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="6a6db-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6a6db-117">詳細</span><span class="sxs-lookup"><span data-stu-id="6a6db-117">Details</span></span>  
  
|<span data-ttu-id="6a6db-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6a6db-118">Data Item Name</span></span>|<span data-ttu-id="6a6db-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6a6db-119">Data Item Type</span></span>|<span data-ttu-id="6a6db-120">説明</span><span class="sxs-lookup"><span data-stu-id="6a6db-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6a6db-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="6a6db-121">Activity</span></span>|<span data-ttu-id="6a6db-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6db-122">xs:string</span></span>|<span data-ttu-id="6a6db-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="6a6db-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="6a6db-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6a6db-124">DisplayName</span></span>|<span data-ttu-id="6a6db-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6db-125">xs:string</span></span>|<span data-ttu-id="6a6db-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="6a6db-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="6a6db-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6a6db-127">InstanceId</span></span>|<span data-ttu-id="6a6db-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6db-128">xs:string</span></span>|<span data-ttu-id="6a6db-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="6a6db-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6a6db-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="6a6db-130">BookmarkName</span></span>|<span data-ttu-id="6a6db-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6db-131">xs:string</span></span>|<span data-ttu-id="6a6db-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="6a6db-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="6a6db-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="6a6db-133">BookmarkScope</span></span>|<span data-ttu-id="6a6db-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6db-134">xs:string</span></span>|<span data-ttu-id="6a6db-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="6a6db-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="6a6db-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6a6db-136">AppDomain</span></span>|<span data-ttu-id="6a6db-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="6a6db-137">xs:string</span></span>|<span data-ttu-id="6a6db-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6a6db-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

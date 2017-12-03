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
ms.openlocfilehash: 1a0837caa668d6395bf1551c319781934bcfecc1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1020---createbookmark"></a><span data-ttu-id="5ad67-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="5ad67-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="5ad67-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5ad67-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ad67-104">ID</span><span class="sxs-lookup"><span data-stu-id="5ad67-104">ID</span></span>|<span data-ttu-id="5ad67-105">1020</span><span class="sxs-lookup"><span data-stu-id="5ad67-105">1020</span></span>|  
|<span data-ttu-id="5ad67-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="5ad67-106">Keywords</span></span>|<span data-ttu-id="5ad67-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5ad67-107">WFRuntime</span></span>|  
|<span data-ttu-id="5ad67-108">レベル</span><span class="sxs-lookup"><span data-stu-id="5ad67-108">Level</span></span>|<span data-ttu-id="5ad67-109">詳細</span><span class="sxs-lookup"><span data-stu-id="5ad67-109">Verbose</span></span>|  
|<span data-ttu-id="5ad67-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5ad67-110">Channel</span></span>|<span data-ttu-id="5ad67-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5ad67-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5ad67-112">説明</span><span class="sxs-lookup"><span data-stu-id="5ad67-112">Description</span></span>  
 <span data-ttu-id="5ad67-113">あるアクティビティ用のブックマークが作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="5ad67-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5ad67-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="5ad67-114">Message</span></span>  
 <span data-ttu-id="5ad67-115">Activity '%1'、DisplayName のブックマークが作成されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="5ad67-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5ad67-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="5ad67-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5ad67-117">詳細</span><span class="sxs-lookup"><span data-stu-id="5ad67-117">Details</span></span>  
  
|<span data-ttu-id="5ad67-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5ad67-118">Data Item Name</span></span>|<span data-ttu-id="5ad67-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5ad67-119">Data Item Type</span></span>|<span data-ttu-id="5ad67-120">説明</span><span class="sxs-lookup"><span data-stu-id="5ad67-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5ad67-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="5ad67-121">Activity</span></span>|<span data-ttu-id="5ad67-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ad67-122">xs:string</span></span>|<span data-ttu-id="5ad67-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="5ad67-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="5ad67-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5ad67-124">DisplayName</span></span>|<span data-ttu-id="5ad67-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ad67-125">xs:string</span></span>|<span data-ttu-id="5ad67-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="5ad67-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="5ad67-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5ad67-127">InstanceId</span></span>|<span data-ttu-id="5ad67-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ad67-128">xs:string</span></span>|<span data-ttu-id="5ad67-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="5ad67-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5ad67-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="5ad67-130">BookmarkName</span></span>|<span data-ttu-id="5ad67-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ad67-131">xs:string</span></span>|<span data-ttu-id="5ad67-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="5ad67-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="5ad67-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="5ad67-133">BookmarkScope</span></span>|<span data-ttu-id="5ad67-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ad67-134">xs:string</span></span>|<span data-ttu-id="5ad67-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="5ad67-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="5ad67-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5ad67-136">AppDomain</span></span>|<span data-ttu-id="5ad67-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="5ad67-137">xs:string</span></span>|<span data-ttu-id="5ad67-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5ad67-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

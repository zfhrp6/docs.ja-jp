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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d0584c6eeaf0e08e92ad94e01e1fca765616440f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1020---createbookmark"></a><span data-ttu-id="ea374-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="ea374-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="ea374-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ea374-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea374-104">ID</span><span class="sxs-lookup"><span data-stu-id="ea374-104">ID</span></span>|<span data-ttu-id="ea374-105">1020</span><span class="sxs-lookup"><span data-stu-id="ea374-105">1020</span></span>|  
|<span data-ttu-id="ea374-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ea374-106">Keywords</span></span>|<span data-ttu-id="ea374-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ea374-107">WFRuntime</span></span>|  
|<span data-ttu-id="ea374-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ea374-108">Level</span></span>|<span data-ttu-id="ea374-109">詳細</span><span class="sxs-lookup"><span data-stu-id="ea374-109">Verbose</span></span>|  
|<span data-ttu-id="ea374-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ea374-110">Channel</span></span>|<span data-ttu-id="ea374-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ea374-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ea374-112">説明</span><span class="sxs-lookup"><span data-stu-id="ea374-112">Description</span></span>  
 <span data-ttu-id="ea374-113">あるアクティビティ用のブックマークが作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ea374-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ea374-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ea374-114">Message</span></span>  
 <span data-ttu-id="ea374-115">Activity '%1'、DisplayName のブックマークが作成されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="ea374-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ea374-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="ea374-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ea374-117">詳細</span><span class="sxs-lookup"><span data-stu-id="ea374-117">Details</span></span>  
  
|<span data-ttu-id="ea374-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ea374-118">Data Item Name</span></span>|<span data-ttu-id="ea374-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ea374-119">Data Item Type</span></span>|<span data-ttu-id="ea374-120">説明</span><span class="sxs-lookup"><span data-stu-id="ea374-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ea374-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="ea374-121">Activity</span></span>|<span data-ttu-id="ea374-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ea374-122">xs:string</span></span>|<span data-ttu-id="ea374-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="ea374-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="ea374-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ea374-124">DisplayName</span></span>|<span data-ttu-id="ea374-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ea374-125">xs:string</span></span>|<span data-ttu-id="ea374-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="ea374-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="ea374-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ea374-127">InstanceId</span></span>|<span data-ttu-id="ea374-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="ea374-128">xs:string</span></span>|<span data-ttu-id="ea374-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="ea374-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ea374-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="ea374-130">BookmarkName</span></span>|<span data-ttu-id="ea374-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="ea374-131">xs:string</span></span>|<span data-ttu-id="ea374-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="ea374-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="ea374-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="ea374-133">BookmarkScope</span></span>|<span data-ttu-id="ea374-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="ea374-134">xs:string</span></span>|<span data-ttu-id="ea374-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="ea374-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="ea374-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ea374-136">AppDomain</span></span>|<span data-ttu-id="ea374-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="ea374-137">xs:string</span></span>|<span data-ttu-id="ea374-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ea374-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

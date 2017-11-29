---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aaabbdca455d31d22b232ae2b08edef0687ac30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="2b09e-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="2b09e-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2b09e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2b09e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b09e-104">ID</span><span class="sxs-lookup"><span data-stu-id="2b09e-104">ID</span></span>|<span data-ttu-id="2b09e-105">1022</span><span class="sxs-lookup"><span data-stu-id="2b09e-105">1022</span></span>|  
|<span data-ttu-id="2b09e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2b09e-106">Keywords</span></span>|<span data-ttu-id="2b09e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2b09e-107">WFRuntime</span></span>|  
|<span data-ttu-id="2b09e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2b09e-108">Level</span></span>|<span data-ttu-id="2b09e-109">詳細</span><span class="sxs-lookup"><span data-stu-id="2b09e-109">Verbose</span></span>|  
|<span data-ttu-id="2b09e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2b09e-110">Channel</span></span>|<span data-ttu-id="2b09e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2b09e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b09e-112">説明</span><span class="sxs-lookup"><span data-stu-id="2b09e-112">Description</span></span>  
 <span data-ttu-id="2b09e-113">BookmarkWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="2b09e-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b09e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2b09e-114">Message</span></span>  
 <span data-ttu-id="2b09e-115">Activity '%1'、DisplayName BookmarkWorkItem の実行を開始: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="2b09e-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="2b09e-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="2b09e-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b09e-117">詳細</span><span class="sxs-lookup"><span data-stu-id="2b09e-117">Details</span></span>  
  
|<span data-ttu-id="2b09e-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2b09e-118">Data Item Name</span></span>|<span data-ttu-id="2b09e-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2b09e-119">Data Item Type</span></span>|<span data-ttu-id="2b09e-120">説明</span><span class="sxs-lookup"><span data-stu-id="2b09e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b09e-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="2b09e-121">Activity</span></span>|<span data-ttu-id="2b09e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b09e-122">xs:string</span></span>|<span data-ttu-id="2b09e-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="2b09e-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="2b09e-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2b09e-124">DisplayName</span></span>|<span data-ttu-id="2b09e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b09e-125">xs:string</span></span>|<span data-ttu-id="2b09e-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2b09e-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="2b09e-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2b09e-127">InstanceId</span></span>|<span data-ttu-id="2b09e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b09e-128">xs:string</span></span>|<span data-ttu-id="2b09e-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="2b09e-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2b09e-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="2b09e-130">BookmarkName</span></span>|<span data-ttu-id="2b09e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b09e-131">xs:string</span></span>|<span data-ttu-id="2b09e-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="2b09e-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="2b09e-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="2b09e-133">BookmarkScope</span></span>|<span data-ttu-id="2b09e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b09e-134">xs:string</span></span>|<span data-ttu-id="2b09e-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="2b09e-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="2b09e-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b09e-136">AppDomain</span></span>|<span data-ttu-id="2b09e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="2b09e-137">xs:string</span></span>|<span data-ttu-id="2b09e-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2b09e-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

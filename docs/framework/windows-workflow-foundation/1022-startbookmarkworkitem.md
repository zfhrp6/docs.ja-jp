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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7df39bd0f6d6d4d309cf5c599ecd3795eb92067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="fafc5-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="fafc5-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="fafc5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fafc5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fafc5-104">ID</span><span class="sxs-lookup"><span data-stu-id="fafc5-104">ID</span></span>|<span data-ttu-id="fafc5-105">1022</span><span class="sxs-lookup"><span data-stu-id="fafc5-105">1022</span></span>|  
|<span data-ttu-id="fafc5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fafc5-106">Keywords</span></span>|<span data-ttu-id="fafc5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fafc5-107">WFRuntime</span></span>|  
|<span data-ttu-id="fafc5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fafc5-108">Level</span></span>|<span data-ttu-id="fafc5-109">詳細</span><span class="sxs-lookup"><span data-stu-id="fafc5-109">Verbose</span></span>|  
|<span data-ttu-id="fafc5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fafc5-110">Channel</span></span>|<span data-ttu-id="fafc5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fafc5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fafc5-112">説明</span><span class="sxs-lookup"><span data-stu-id="fafc5-112">Description</span></span>  
 <span data-ttu-id="fafc5-113">BookmarkWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="fafc5-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fafc5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fafc5-114">Message</span></span>  
 <span data-ttu-id="fafc5-115">Activity '%1'、DisplayName BookmarkWorkItem の実行を開始: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="fafc5-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="fafc5-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="fafc5-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fafc5-117">詳細</span><span class="sxs-lookup"><span data-stu-id="fafc5-117">Details</span></span>  
  
|<span data-ttu-id="fafc5-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fafc5-118">Data Item Name</span></span>|<span data-ttu-id="fafc5-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fafc5-119">Data Item Type</span></span>|<span data-ttu-id="fafc5-120">説明</span><span class="sxs-lookup"><span data-stu-id="fafc5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fafc5-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="fafc5-121">Activity</span></span>|<span data-ttu-id="fafc5-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="fafc5-122">xs:string</span></span>|<span data-ttu-id="fafc5-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="fafc5-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="fafc5-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fafc5-124">DisplayName</span></span>|<span data-ttu-id="fafc5-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="fafc5-125">xs:string</span></span>|<span data-ttu-id="fafc5-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="fafc5-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="fafc5-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="fafc5-127">InstanceId</span></span>|<span data-ttu-id="fafc5-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="fafc5-128">xs:string</span></span>|<span data-ttu-id="fafc5-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="fafc5-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="fafc5-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="fafc5-130">BookmarkName</span></span>|<span data-ttu-id="fafc5-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="fafc5-131">xs:string</span></span>|<span data-ttu-id="fafc5-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="fafc5-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="fafc5-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="fafc5-133">BookmarkScope</span></span>|<span data-ttu-id="fafc5-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="fafc5-134">xs:string</span></span>|<span data-ttu-id="fafc5-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="fafc5-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="fafc5-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fafc5-136">AppDomain</span></span>|<span data-ttu-id="fafc5-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="fafc5-137">xs:string</span></span>|<span data-ttu-id="fafc5-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fafc5-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

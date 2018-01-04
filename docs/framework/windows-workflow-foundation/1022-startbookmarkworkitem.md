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
ms.workload: dotnet
ms.openlocfilehash: cdb6af10c45e7a93e9a68e6150e5d239002cce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="28073-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="28073-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="28073-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="28073-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28073-104">ID</span><span class="sxs-lookup"><span data-stu-id="28073-104">ID</span></span>|<span data-ttu-id="28073-105">1022</span><span class="sxs-lookup"><span data-stu-id="28073-105">1022</span></span>|  
|<span data-ttu-id="28073-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="28073-106">Keywords</span></span>|<span data-ttu-id="28073-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="28073-107">WFRuntime</span></span>|  
|<span data-ttu-id="28073-108">レベル</span><span class="sxs-lookup"><span data-stu-id="28073-108">Level</span></span>|<span data-ttu-id="28073-109">詳細</span><span class="sxs-lookup"><span data-stu-id="28073-109">Verbose</span></span>|  
|<span data-ttu-id="28073-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="28073-110">Channel</span></span>|<span data-ttu-id="28073-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="28073-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="28073-112">説明</span><span class="sxs-lookup"><span data-stu-id="28073-112">Description</span></span>  
 <span data-ttu-id="28073-113">BookmarkWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="28073-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="28073-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="28073-114">Message</span></span>  
 <span data-ttu-id="28073-115">Activity '%1'、DisplayName BookmarkWorkItem の実行を開始: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="28073-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="28073-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="28073-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="28073-117">詳細</span><span class="sxs-lookup"><span data-stu-id="28073-117">Details</span></span>  
  
|<span data-ttu-id="28073-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="28073-118">Data Item Name</span></span>|<span data-ttu-id="28073-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="28073-119">Data Item Type</span></span>|<span data-ttu-id="28073-120">説明</span><span class="sxs-lookup"><span data-stu-id="28073-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="28073-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="28073-121">Activity</span></span>|<span data-ttu-id="28073-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="28073-122">xs:string</span></span>|<span data-ttu-id="28073-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="28073-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="28073-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="28073-124">DisplayName</span></span>|<span data-ttu-id="28073-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="28073-125">xs:string</span></span>|<span data-ttu-id="28073-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="28073-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="28073-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="28073-127">InstanceId</span></span>|<span data-ttu-id="28073-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="28073-128">xs:string</span></span>|<span data-ttu-id="28073-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="28073-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="28073-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="28073-130">BookmarkName</span></span>|<span data-ttu-id="28073-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="28073-131">xs:string</span></span>|<span data-ttu-id="28073-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="28073-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="28073-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="28073-133">BookmarkScope</span></span>|<span data-ttu-id="28073-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="28073-134">xs:string</span></span>|<span data-ttu-id="28073-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="28073-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="28073-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="28073-136">AppDomain</span></span>|<span data-ttu-id="28073-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="28073-137">xs:string</span></span>|<span data-ttu-id="28073-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="28073-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

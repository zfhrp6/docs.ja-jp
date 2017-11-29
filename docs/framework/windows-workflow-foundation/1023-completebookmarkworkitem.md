---
title: 1023 - CompleteBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5db5b106a6bc92c288aefe309d33625f57b0ddad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="1c2cc-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="1c2cc-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1c2cc-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1c2cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c2cc-104">ID</span><span class="sxs-lookup"><span data-stu-id="1c2cc-104">ID</span></span>|<span data-ttu-id="1c2cc-105">1023</span><span class="sxs-lookup"><span data-stu-id="1c2cc-105">1023</span></span>|  
|<span data-ttu-id="1c2cc-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1c2cc-106">Keywords</span></span>|<span data-ttu-id="1c2cc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1c2cc-107">WFRuntime</span></span>|  
|<span data-ttu-id="1c2cc-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1c2cc-108">Level</span></span>|<span data-ttu-id="1c2cc-109">詳細</span><span class="sxs-lookup"><span data-stu-id="1c2cc-109">Verbose</span></span>|  
|<span data-ttu-id="1c2cc-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1c2cc-110">Channel</span></span>|<span data-ttu-id="1c2cc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1c2cc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c2cc-112">説明</span><span class="sxs-lookup"><span data-stu-id="1c2cc-112">Description</span></span>  
 <span data-ttu-id="1c2cc-113">BookmarkWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c2cc-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1c2cc-114">Message</span></span>  
 <span data-ttu-id="1c2cc-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の BookmarkWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1c2cc-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c2cc-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1c2cc-117">Details</span></span>  
  
|<span data-ttu-id="1c2cc-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1c2cc-118">Data Item Name</span></span>|<span data-ttu-id="1c2cc-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1c2cc-119">Data Item Type</span></span>|<span data-ttu-id="1c2cc-120">説明</span><span class="sxs-lookup"><span data-stu-id="1c2cc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c2cc-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="1c2cc-121">Activity</span></span>|<span data-ttu-id="1c2cc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c2cc-122">xs:string</span></span>|<span data-ttu-id="1c2cc-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="1c2cc-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1c2cc-124">DisplayName</span></span>|<span data-ttu-id="1c2cc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c2cc-125">xs:string</span></span>|<span data-ttu-id="1c2cc-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="1c2cc-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1c2cc-127">InstanceId</span></span>|<span data-ttu-id="1c2cc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c2cc-128">xs:string</span></span>|<span data-ttu-id="1c2cc-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1c2cc-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="1c2cc-130">BookmarkName</span></span>|<span data-ttu-id="1c2cc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c2cc-131">xs:string</span></span>|<span data-ttu-id="1c2cc-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="1c2cc-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="1c2cc-133">BookmarkScope</span></span>|<span data-ttu-id="1c2cc-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c2cc-134">xs:string</span></span>|<span data-ttu-id="1c2cc-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="1c2cc-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c2cc-136">AppDomain</span></span>|<span data-ttu-id="1c2cc-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c2cc-137">xs:string</span></span>|<span data-ttu-id="1c2cc-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1c2cc-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

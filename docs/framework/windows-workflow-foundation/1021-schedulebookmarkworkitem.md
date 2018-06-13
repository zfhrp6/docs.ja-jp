---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509757"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="5388f-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="5388f-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5388f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5388f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5388f-104">ID</span><span class="sxs-lookup"><span data-stu-id="5388f-104">ID</span></span>|<span data-ttu-id="5388f-105">1021</span><span class="sxs-lookup"><span data-stu-id="5388f-105">1021</span></span>|  
|<span data-ttu-id="5388f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="5388f-106">Keywords</span></span>|<span data-ttu-id="5388f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5388f-107">WFRuntime</span></span>|  
|<span data-ttu-id="5388f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="5388f-108">Level</span></span>|<span data-ttu-id="5388f-109">詳細</span><span class="sxs-lookup"><span data-stu-id="5388f-109">Verbose</span></span>|  
|<span data-ttu-id="5388f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5388f-110">Channel</span></span>|<span data-ttu-id="5388f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5388f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5388f-112">説明</span><span class="sxs-lookup"><span data-stu-id="5388f-112">Description</span></span>  
 <span data-ttu-id="5388f-113">BookmarkWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5388f-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5388f-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="5388f-114">Message</span></span>  
 <span data-ttu-id="5388f-115">Activity '%1'、DisplayName に対して BookmarkWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="5388f-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5388f-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="5388f-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5388f-117">詳細</span><span class="sxs-lookup"><span data-stu-id="5388f-117">Details</span></span>  
  
|<span data-ttu-id="5388f-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5388f-118">Data Item Name</span></span>|<span data-ttu-id="5388f-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5388f-119">Data Item Type</span></span>|<span data-ttu-id="5388f-120">説明</span><span class="sxs-lookup"><span data-stu-id="5388f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5388f-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="5388f-121">Activity</span></span>|<span data-ttu-id="5388f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="5388f-122">xs:string</span></span>|<span data-ttu-id="5388f-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="5388f-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="5388f-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="5388f-124">DisplayName</span></span>|<span data-ttu-id="5388f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="5388f-125">xs:string</span></span>|<span data-ttu-id="5388f-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="5388f-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="5388f-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5388f-127">InstanceId</span></span>|<span data-ttu-id="5388f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="5388f-128">xs:string</span></span>|<span data-ttu-id="5388f-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="5388f-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5388f-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="5388f-130">BookmarkName</span></span>|<span data-ttu-id="5388f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="5388f-131">xs:string</span></span>|<span data-ttu-id="5388f-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="5388f-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="5388f-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="5388f-133">BookmarkScope</span></span>|<span data-ttu-id="5388f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="5388f-134">xs:string</span></span>|<span data-ttu-id="5388f-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="5388f-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="5388f-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5388f-136">AppDomain</span></span>|<span data-ttu-id="5388f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="5388f-137">xs:string</span></span>|<span data-ttu-id="5388f-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5388f-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a0d8cc3d17ecd13d9312b42554ef5347cccf213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="c39fd-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="c39fd-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="c39fd-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c39fd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c39fd-104">ID</span><span class="sxs-lookup"><span data-stu-id="c39fd-104">ID</span></span>|<span data-ttu-id="c39fd-105">1009</span><span class="sxs-lookup"><span data-stu-id="c39fd-105">1009</span></span>|  
|<span data-ttu-id="c39fd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c39fd-106">Keywords</span></span>|<span data-ttu-id="c39fd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c39fd-107">WFRuntime</span></span>|  
|<span data-ttu-id="c39fd-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c39fd-108">Level</span></span>|<span data-ttu-id="c39fd-109">情報</span><span class="sxs-lookup"><span data-stu-id="c39fd-109">Information</span></span>|  
|<span data-ttu-id="c39fd-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c39fd-110">Channel</span></span>|<span data-ttu-id="c39fd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c39fd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c39fd-112">説明</span><span class="sxs-lookup"><span data-stu-id="c39fd-112">Description</span></span>  
 <span data-ttu-id="c39fd-113">アクティビティの実行がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c39fd-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c39fd-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c39fd-114">Message</span></span>  
 <span data-ttu-id="c39fd-115">Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="c39fd-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c39fd-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c39fd-116">Details</span></span>  
  
|<span data-ttu-id="c39fd-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c39fd-117">Data Item Name</span></span>|<span data-ttu-id="c39fd-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c39fd-118">Data Item Type</span></span>|<span data-ttu-id="c39fd-119">説明</span><span class="sxs-lookup"><span data-stu-id="c39fd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c39fd-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="c39fd-120">ParentActivity</span></span>|<span data-ttu-id="c39fd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-121">xs:string</span></span>|<span data-ttu-id="c39fd-122">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c39fd-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c39fd-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c39fd-123">ParentDisplayName</span></span>|<span data-ttu-id="c39fd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-124">xs:string</span></span>|<span data-ttu-id="c39fd-125">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c39fd-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c39fd-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c39fd-126">ParentInstanceId</span></span>|<span data-ttu-id="c39fd-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-127">xs:string</span></span>|<span data-ttu-id="c39fd-128">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c39fd-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c39fd-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="c39fd-129">ChildActivity</span></span>|<span data-ttu-id="c39fd-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-130">xs:string</span></span>|<span data-ttu-id="c39fd-131">スケジュール済みの子アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c39fd-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c39fd-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="c39fd-132">ChildDisplayName</span></span>|<span data-ttu-id="c39fd-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-133">xs:string</span></span>|<span data-ttu-id="c39fd-134">スケジュール済みの子アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c39fd-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c39fd-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="c39fd-135">ChildInstanceId</span></span>|<span data-ttu-id="c39fd-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-136">xs:string</span></span>|<span data-ttu-id="c39fd-137">スケジュール済み子アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c39fd-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c39fd-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c39fd-138">AppDomain</span></span>|<span data-ttu-id="c39fd-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="c39fd-139">xs:string</span></span>|<span data-ttu-id="c39fd-140">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c39fd-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec89acb9d83a28ac280db7c3d536bfe63669fa97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="e1554-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="e1554-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e1554-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e1554-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1554-104">ID</span><span class="sxs-lookup"><span data-stu-id="e1554-104">ID</span></span>|<span data-ttu-id="e1554-105">1011</span><span class="sxs-lookup"><span data-stu-id="e1554-105">1011</span></span>|  
|<span data-ttu-id="e1554-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e1554-106">Keywords</span></span>|<span data-ttu-id="e1554-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e1554-107">WFRuntime</span></span>|  
|<span data-ttu-id="e1554-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e1554-108">Level</span></span>|<span data-ttu-id="e1554-109">詳細</span><span class="sxs-lookup"><span data-stu-id="e1554-109">Verbose</span></span>|  
|<span data-ttu-id="e1554-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e1554-110">Channel</span></span>|<span data-ttu-id="e1554-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e1554-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1554-112">説明</span><span class="sxs-lookup"><span data-stu-id="e1554-112">Description</span></span>  
 <span data-ttu-id="e1554-113">ExecuteActivityWorkItem がスケジュールされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="e1554-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1554-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e1554-114">Message</span></span>  
 <span data-ttu-id="e1554-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="e1554-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1554-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e1554-116">Details</span></span>  
  
|<span data-ttu-id="e1554-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e1554-117">Data Item Name</span></span>|<span data-ttu-id="e1554-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e1554-118">Data Item Type</span></span>|<span data-ttu-id="e1554-119">説明</span><span class="sxs-lookup"><span data-stu-id="e1554-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1554-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e1554-120">Activity</span></span>|<span data-ttu-id="e1554-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1554-121">xs:string</span></span>|<span data-ttu-id="e1554-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="e1554-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e1554-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e1554-123">DisplayName</span></span>|<span data-ttu-id="e1554-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1554-124">xs:string</span></span>|<span data-ttu-id="e1554-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="e1554-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e1554-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e1554-126">InstanceId</span></span>|<span data-ttu-id="e1554-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1554-127">xs:string</span></span>|<span data-ttu-id="e1554-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="e1554-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e1554-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1554-129">AppDomain</span></span>|<span data-ttu-id="e1554-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1554-130">xs:string</span></span>|<span data-ttu-id="e1554-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e1554-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

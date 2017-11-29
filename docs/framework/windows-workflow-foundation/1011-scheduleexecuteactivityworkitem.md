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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 498752bfc896891a43a6a2e7a8245c508795c1ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="bc7ba-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="bc7ba-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="bc7ba-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc7ba-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc7ba-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc7ba-104">ID</span></span>|<span data-ttu-id="bc7ba-105">1011</span><span class="sxs-lookup"><span data-stu-id="bc7ba-105">1011</span></span>|  
|<span data-ttu-id="bc7ba-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bc7ba-106">Keywords</span></span>|<span data-ttu-id="bc7ba-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bc7ba-107">WFRuntime</span></span>|  
|<span data-ttu-id="bc7ba-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bc7ba-108">Level</span></span>|<span data-ttu-id="bc7ba-109">詳細</span><span class="sxs-lookup"><span data-stu-id="bc7ba-109">Verbose</span></span>|  
|<span data-ttu-id="bc7ba-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bc7ba-110">Channel</span></span>|<span data-ttu-id="bc7ba-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bc7ba-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc7ba-112">説明</span><span class="sxs-lookup"><span data-stu-id="bc7ba-112">Description</span></span>  
 <span data-ttu-id="bc7ba-113">ExecuteActivityWorkItem がスケジュールされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="bc7ba-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc7ba-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bc7ba-114">Message</span></span>  
 <span data-ttu-id="bc7ba-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="bc7ba-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc7ba-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bc7ba-116">Details</span></span>  
  
|<span data-ttu-id="bc7ba-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bc7ba-117">Data Item Name</span></span>|<span data-ttu-id="bc7ba-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bc7ba-118">Data Item Type</span></span>|<span data-ttu-id="bc7ba-119">説明</span><span class="sxs-lookup"><span data-stu-id="bc7ba-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc7ba-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="bc7ba-120">Activity</span></span>|<span data-ttu-id="bc7ba-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc7ba-121">xs:string</span></span>|<span data-ttu-id="bc7ba-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bc7ba-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bc7ba-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bc7ba-123">DisplayName</span></span>|<span data-ttu-id="bc7ba-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc7ba-124">xs:string</span></span>|<span data-ttu-id="bc7ba-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bc7ba-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bc7ba-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bc7ba-126">InstanceId</span></span>|<span data-ttu-id="bc7ba-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc7ba-127">xs:string</span></span>|<span data-ttu-id="bc7ba-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bc7ba-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bc7ba-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bc7ba-129">AppDomain</span></span>|<span data-ttu-id="bc7ba-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc7ba-130">xs:string</span></span>|<span data-ttu-id="bc7ba-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bc7ba-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2a150b9e9c78a9ce1f5e20b962a58ef2d5dde9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="eef83-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="eef83-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="eef83-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="eef83-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eef83-104">ID</span><span class="sxs-lookup"><span data-stu-id="eef83-104">ID</span></span>|<span data-ttu-id="eef83-105">1032</span><span class="sxs-lookup"><span data-stu-id="eef83-105">1032</span></span>|  
|<span data-ttu-id="eef83-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="eef83-106">Keywords</span></span>|<span data-ttu-id="eef83-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="eef83-107">WFRuntime</span></span>|  
|<span data-ttu-id="eef83-108">レベル</span><span class="sxs-lookup"><span data-stu-id="eef83-108">Level</span></span>|<span data-ttu-id="eef83-109">詳細</span><span class="sxs-lookup"><span data-stu-id="eef83-109">Verbose</span></span>|  
|<span data-ttu-id="eef83-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="eef83-110">Channel</span></span>|<span data-ttu-id="eef83-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="eef83-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eef83-112">説明</span><span class="sxs-lookup"><span data-stu-id="eef83-112">Description</span></span>  
 <span data-ttu-id="eef83-113">RuntimeWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="eef83-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eef83-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="eef83-114">Message</span></span>  
 <span data-ttu-id="eef83-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対してランタイム作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="eef83-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eef83-116">詳細</span><span class="sxs-lookup"><span data-stu-id="eef83-116">Details</span></span>  
  
|<span data-ttu-id="eef83-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="eef83-117">Data Item Name</span></span>|<span data-ttu-id="eef83-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="eef83-118">Data Item Type</span></span>|<span data-ttu-id="eef83-119">説明</span><span class="sxs-lookup"><span data-stu-id="eef83-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eef83-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="eef83-120">Activity</span></span>|<span data-ttu-id="eef83-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="eef83-121">xs:string</span></span>|<span data-ttu-id="eef83-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="eef83-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="eef83-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="eef83-123">DisplayName</span></span>|<span data-ttu-id="eef83-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="eef83-124">xs:string</span></span>|<span data-ttu-id="eef83-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="eef83-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="eef83-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="eef83-126">InstanceId</span></span>|<span data-ttu-id="eef83-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="eef83-127">xs:string</span></span>|<span data-ttu-id="eef83-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="eef83-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="eef83-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eef83-129">AppDomain</span></span>|<span data-ttu-id="eef83-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="eef83-130">xs:string</span></span>|<span data-ttu-id="eef83-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="eef83-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

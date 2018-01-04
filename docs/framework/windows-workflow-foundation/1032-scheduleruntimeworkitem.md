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
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="cbfd2-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="cbfd2-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="cbfd2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cbfd2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cbfd2-104">ID</span><span class="sxs-lookup"><span data-stu-id="cbfd2-104">ID</span></span>|<span data-ttu-id="cbfd2-105">1032</span><span class="sxs-lookup"><span data-stu-id="cbfd2-105">1032</span></span>|  
|<span data-ttu-id="cbfd2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="cbfd2-106">Keywords</span></span>|<span data-ttu-id="cbfd2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cbfd2-107">WFRuntime</span></span>|  
|<span data-ttu-id="cbfd2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="cbfd2-108">Level</span></span>|<span data-ttu-id="cbfd2-109">詳細</span><span class="sxs-lookup"><span data-stu-id="cbfd2-109">Verbose</span></span>|  
|<span data-ttu-id="cbfd2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="cbfd2-110">Channel</span></span>|<span data-ttu-id="cbfd2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cbfd2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cbfd2-112">説明</span><span class="sxs-lookup"><span data-stu-id="cbfd2-112">Description</span></span>  
 <span data-ttu-id="cbfd2-113">RuntimeWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="cbfd2-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cbfd2-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="cbfd2-114">Message</span></span>  
 <span data-ttu-id="cbfd2-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対してランタイム作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="cbfd2-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cbfd2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="cbfd2-116">Details</span></span>  
  
|<span data-ttu-id="cbfd2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cbfd2-117">Data Item Name</span></span>|<span data-ttu-id="cbfd2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cbfd2-118">Data Item Type</span></span>|<span data-ttu-id="cbfd2-119">説明</span><span class="sxs-lookup"><span data-stu-id="cbfd2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cbfd2-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="cbfd2-120">Activity</span></span>|<span data-ttu-id="cbfd2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbfd2-121">xs:string</span></span>|<span data-ttu-id="cbfd2-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="cbfd2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="cbfd2-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="cbfd2-123">DisplayName</span></span>|<span data-ttu-id="cbfd2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbfd2-124">xs:string</span></span>|<span data-ttu-id="cbfd2-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="cbfd2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="cbfd2-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="cbfd2-126">InstanceId</span></span>|<span data-ttu-id="cbfd2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbfd2-127">xs:string</span></span>|<span data-ttu-id="cbfd2-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="cbfd2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="cbfd2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cbfd2-129">AppDomain</span></span>|<span data-ttu-id="cbfd2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbfd2-130">xs:string</span></span>|<span data-ttu-id="cbfd2-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cbfd2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

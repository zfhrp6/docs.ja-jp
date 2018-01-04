---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b524f083c49f517c21c77da4f1d1488625a575b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="e3f43-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="e3f43-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e3f43-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e3f43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3f43-104">ID</span><span class="sxs-lookup"><span data-stu-id="e3f43-104">ID</span></span>|<span data-ttu-id="e3f43-105">1017</span><span class="sxs-lookup"><span data-stu-id="e3f43-105">1017</span></span>|  
|<span data-ttu-id="e3f43-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e3f43-106">Keywords</span></span>|<span data-ttu-id="e3f43-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e3f43-107">WFRuntime</span></span>|  
|<span data-ttu-id="e3f43-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e3f43-108">Level</span></span>|<span data-ttu-id="e3f43-109">詳細</span><span class="sxs-lookup"><span data-stu-id="e3f43-109">Verbose</span></span>|  
|<span data-ttu-id="e3f43-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e3f43-110">Channel</span></span>|<span data-ttu-id="e3f43-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e3f43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e3f43-112">説明</span><span class="sxs-lookup"><span data-stu-id="e3f43-112">Description</span></span>  
 <span data-ttu-id="e3f43-113">CancelActivityWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e3f43-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e3f43-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e3f43-114">Message</span></span>  
 <span data-ttu-id="e3f43-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="e3f43-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e3f43-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e3f43-116">Details</span></span>  
  
|<span data-ttu-id="e3f43-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e3f43-117">Data Item Name</span></span>|<span data-ttu-id="e3f43-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e3f43-118">Data Item Type</span></span>|<span data-ttu-id="e3f43-119">説明</span><span class="sxs-lookup"><span data-stu-id="e3f43-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e3f43-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="e3f43-120">Activity</span></span>|<span data-ttu-id="e3f43-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e3f43-121">xs:string</span></span>|<span data-ttu-id="e3f43-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="e3f43-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e3f43-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e3f43-123">DisplayName</span></span>|<span data-ttu-id="e3f43-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e3f43-124">xs:string</span></span>|<span data-ttu-id="e3f43-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="e3f43-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e3f43-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e3f43-126">InstanceId</span></span>|<span data-ttu-id="e3f43-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e3f43-127">xs:string</span></span>|<span data-ttu-id="e3f43-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="e3f43-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e3f43-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e3f43-129">AppDomain</span></span>|<span data-ttu-id="e3f43-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e3f43-130">xs:string</span></span>|<span data-ttu-id="e3f43-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e3f43-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

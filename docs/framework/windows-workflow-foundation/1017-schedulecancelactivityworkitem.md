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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d348ec18b4d5eff7156d1e9809eb793ac1681d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="1c37a-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="1c37a-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1c37a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1c37a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c37a-104">ID</span><span class="sxs-lookup"><span data-stu-id="1c37a-104">ID</span></span>|<span data-ttu-id="1c37a-105">1017</span><span class="sxs-lookup"><span data-stu-id="1c37a-105">1017</span></span>|  
|<span data-ttu-id="1c37a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1c37a-106">Keywords</span></span>|<span data-ttu-id="1c37a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1c37a-107">WFRuntime</span></span>|  
|<span data-ttu-id="1c37a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1c37a-108">Level</span></span>|<span data-ttu-id="1c37a-109">詳細</span><span class="sxs-lookup"><span data-stu-id="1c37a-109">Verbose</span></span>|  
|<span data-ttu-id="1c37a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1c37a-110">Channel</span></span>|<span data-ttu-id="1c37a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1c37a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c37a-112">説明</span><span class="sxs-lookup"><span data-stu-id="1c37a-112">Description</span></span>  
 <span data-ttu-id="1c37a-113">CancelActivityWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1c37a-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c37a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1c37a-114">Message</span></span>  
 <span data-ttu-id="1c37a-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="1c37a-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c37a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="1c37a-116">Details</span></span>  
  
|<span data-ttu-id="1c37a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1c37a-117">Data Item Name</span></span>|<span data-ttu-id="1c37a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1c37a-118">Data Item Type</span></span>|<span data-ttu-id="1c37a-119">説明</span><span class="sxs-lookup"><span data-stu-id="1c37a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c37a-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="1c37a-120">Activity</span></span>|<span data-ttu-id="1c37a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c37a-121">xs:string</span></span>|<span data-ttu-id="1c37a-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="1c37a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1c37a-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1c37a-123">DisplayName</span></span>|<span data-ttu-id="1c37a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c37a-124">xs:string</span></span>|<span data-ttu-id="1c37a-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="1c37a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1c37a-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1c37a-126">InstanceId</span></span>|<span data-ttu-id="1c37a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c37a-127">xs:string</span></span>|<span data-ttu-id="1c37a-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1c37a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1c37a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c37a-129">AppDomain</span></span>|<span data-ttu-id="1c37a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c37a-130">xs:string</span></span>|<span data-ttu-id="1c37a-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1c37a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

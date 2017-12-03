---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cf96d665bcd5ff703f54d2f15d1912ad0b9573c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="571e7-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="571e7-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="571e7-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="571e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="571e7-104">ID</span><span class="sxs-lookup"><span data-stu-id="571e7-104">ID</span></span>|<span data-ttu-id="571e7-105">1019</span><span class="sxs-lookup"><span data-stu-id="571e7-105">1019</span></span>|  
|<span data-ttu-id="571e7-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="571e7-106">Keywords</span></span>|<span data-ttu-id="571e7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="571e7-107">WFRuntime</span></span>|  
|<span data-ttu-id="571e7-108">レベル</span><span class="sxs-lookup"><span data-stu-id="571e7-108">Level</span></span>|<span data-ttu-id="571e7-109">詳細</span><span class="sxs-lookup"><span data-stu-id="571e7-109">Verbose</span></span>|  
|<span data-ttu-id="571e7-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="571e7-110">Channel</span></span>|<span data-ttu-id="571e7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="571e7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="571e7-112">説明</span><span class="sxs-lookup"><span data-stu-id="571e7-112">Description</span></span>  
 <span data-ttu-id="571e7-113">CancelActivityWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="571e7-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="571e7-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="571e7-114">Message</span></span>  
 <span data-ttu-id="571e7-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="571e7-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="571e7-116">詳細</span><span class="sxs-lookup"><span data-stu-id="571e7-116">Details</span></span>  
  
|<span data-ttu-id="571e7-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="571e7-117">Data Item Name</span></span>|<span data-ttu-id="571e7-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="571e7-118">Data Item Type</span></span>|<span data-ttu-id="571e7-119">説明</span><span class="sxs-lookup"><span data-stu-id="571e7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="571e7-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="571e7-120">Activity</span></span>|<span data-ttu-id="571e7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="571e7-121">xs:string</span></span>|<span data-ttu-id="571e7-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="571e7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="571e7-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="571e7-123">DisplayName</span></span>|<span data-ttu-id="571e7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="571e7-124">xs:string</span></span>|<span data-ttu-id="571e7-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="571e7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="571e7-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="571e7-126">InstanceId</span></span>|<span data-ttu-id="571e7-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="571e7-127">xs:string</span></span>|<span data-ttu-id="571e7-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="571e7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="571e7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="571e7-129">AppDomain</span></span>|<span data-ttu-id="571e7-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="571e7-130">xs:string</span></span>|<span data-ttu-id="571e7-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="571e7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

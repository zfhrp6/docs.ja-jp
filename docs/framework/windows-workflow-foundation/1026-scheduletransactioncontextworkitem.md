---
title: 1026 - ScheduleTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5fb800718c1fd231d0cd02bf015333a44fa794f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="45b94-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="45b94-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="45b94-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="45b94-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45b94-104">ID</span><span class="sxs-lookup"><span data-stu-id="45b94-104">ID</span></span>|<span data-ttu-id="45b94-105">1026</span><span class="sxs-lookup"><span data-stu-id="45b94-105">1026</span></span>|  
|<span data-ttu-id="45b94-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="45b94-106">Keywords</span></span>|<span data-ttu-id="45b94-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="45b94-107">WFRuntime</span></span>|  
|<span data-ttu-id="45b94-108">レベル</span><span class="sxs-lookup"><span data-stu-id="45b94-108">Level</span></span>|<span data-ttu-id="45b94-109">詳細</span><span class="sxs-lookup"><span data-stu-id="45b94-109">Verbose</span></span>|  
|<span data-ttu-id="45b94-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="45b94-110">Channel</span></span>|<span data-ttu-id="45b94-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="45b94-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="45b94-112">説明</span><span class="sxs-lookup"><span data-stu-id="45b94-112">Description</span></span>  
 <span data-ttu-id="45b94-113">TransactionContextWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="45b94-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="45b94-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="45b94-114">Message</span></span>  
 <span data-ttu-id="45b94-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="45b94-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="45b94-116">詳細</span><span class="sxs-lookup"><span data-stu-id="45b94-116">Details</span></span>  
  
|<span data-ttu-id="45b94-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="45b94-117">Data Item Name</span></span>|<span data-ttu-id="45b94-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="45b94-118">Data Item Type</span></span>|<span data-ttu-id="45b94-119">説明</span><span class="sxs-lookup"><span data-stu-id="45b94-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="45b94-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="45b94-120">Activity</span></span>|<span data-ttu-id="45b94-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="45b94-121">xs:string</span></span>|<span data-ttu-id="45b94-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="45b94-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="45b94-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="45b94-123">DisplayName</span></span>|<span data-ttu-id="45b94-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="45b94-124">xs:string</span></span>|<span data-ttu-id="45b94-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="45b94-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="45b94-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="45b94-126">InstanceId</span></span>|<span data-ttu-id="45b94-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="45b94-127">xs:string</span></span>|<span data-ttu-id="45b94-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="45b94-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="45b94-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="45b94-129">AppDomain</span></span>|<span data-ttu-id="45b94-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="45b94-130">xs:string</span></span>|<span data-ttu-id="45b94-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="45b94-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d881f1be4e809cf45f100b966d6013ae8fa88f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="db086-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="db086-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="db086-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="db086-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db086-104">ID</span><span class="sxs-lookup"><span data-stu-id="db086-104">ID</span></span>|<span data-ttu-id="db086-105">1026</span><span class="sxs-lookup"><span data-stu-id="db086-105">1026</span></span>|  
|<span data-ttu-id="db086-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="db086-106">Keywords</span></span>|<span data-ttu-id="db086-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="db086-107">WFRuntime</span></span>|  
|<span data-ttu-id="db086-108">レベル</span><span class="sxs-lookup"><span data-stu-id="db086-108">Level</span></span>|<span data-ttu-id="db086-109">詳細</span><span class="sxs-lookup"><span data-stu-id="db086-109">Verbose</span></span>|  
|<span data-ttu-id="db086-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="db086-110">Channel</span></span>|<span data-ttu-id="db086-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="db086-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db086-112">説明</span><span class="sxs-lookup"><span data-stu-id="db086-112">Description</span></span>  
 <span data-ttu-id="db086-113">TransactionContextWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="db086-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db086-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="db086-114">Message</span></span>  
 <span data-ttu-id="db086-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="db086-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db086-116">詳細</span><span class="sxs-lookup"><span data-stu-id="db086-116">Details</span></span>  
  
|<span data-ttu-id="db086-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="db086-117">Data Item Name</span></span>|<span data-ttu-id="db086-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="db086-118">Data Item Type</span></span>|<span data-ttu-id="db086-119">説明</span><span class="sxs-lookup"><span data-stu-id="db086-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db086-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="db086-120">Activity</span></span>|<span data-ttu-id="db086-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="db086-121">xs:string</span></span>|<span data-ttu-id="db086-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="db086-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="db086-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="db086-123">DisplayName</span></span>|<span data-ttu-id="db086-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="db086-124">xs:string</span></span>|<span data-ttu-id="db086-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="db086-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="db086-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="db086-126">InstanceId</span></span>|<span data-ttu-id="db086-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="db086-127">xs:string</span></span>|<span data-ttu-id="db086-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="db086-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="db086-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db086-129">AppDomain</span></span>|<span data-ttu-id="db086-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="db086-130">xs:string</span></span>|<span data-ttu-id="db086-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="db086-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

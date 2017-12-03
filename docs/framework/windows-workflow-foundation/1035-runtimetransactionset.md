---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fcd6662c0f8899b6830dc8e06cee4f56b5ff906
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="29c02-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="29c02-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="29c02-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="29c02-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29c02-104">ID</span><span class="sxs-lookup"><span data-stu-id="29c02-104">ID</span></span>|<span data-ttu-id="29c02-105">1035</span><span class="sxs-lookup"><span data-stu-id="29c02-105">1035</span></span>|  
|<span data-ttu-id="29c02-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="29c02-106">Keywords</span></span>|<span data-ttu-id="29c02-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="29c02-107">WFRuntime</span></span>|  
|<span data-ttu-id="29c02-108">レベル</span><span class="sxs-lookup"><span data-stu-id="29c02-108">Level</span></span>|<span data-ttu-id="29c02-109">詳細</span><span class="sxs-lookup"><span data-stu-id="29c02-109">Verbose</span></span>|  
|<span data-ttu-id="29c02-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="29c02-110">Channel</span></span>|<span data-ttu-id="29c02-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="29c02-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="29c02-112">説明</span><span class="sxs-lookup"><span data-stu-id="29c02-112">Description</span></span>  
 <span data-ttu-id="29c02-113">アクティビティがランタイムのトランザクションを設定したことを示します。</span><span class="sxs-lookup"><span data-stu-id="29c02-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="29c02-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="29c02-114">Message</span></span>  
 <span data-ttu-id="29c02-115">Activity '%1'、DisplayName によってランタイム トランザクションが設定されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="29c02-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="29c02-116">実行の分離 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' です。</span><span class="sxs-lookup"><span data-stu-id="29c02-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="29c02-117">詳細</span><span class="sxs-lookup"><span data-stu-id="29c02-117">Details</span></span>  
  
|<span data-ttu-id="29c02-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="29c02-118">Data Item Name</span></span>|<span data-ttu-id="29c02-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="29c02-119">Data Item Type</span></span>|<span data-ttu-id="29c02-120">説明</span><span class="sxs-lookup"><span data-stu-id="29c02-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="29c02-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="29c02-121">Activity</span></span>|<span data-ttu-id="29c02-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-122">xs:string</span></span>|<span data-ttu-id="29c02-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="29c02-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="29c02-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="29c02-124">DisplayName</span></span>|<span data-ttu-id="29c02-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-125">xs:string</span></span>|<span data-ttu-id="29c02-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="29c02-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="29c02-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="29c02-127">InstanceId</span></span>|<span data-ttu-id="29c02-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-128">xs:string</span></span>|<span data-ttu-id="29c02-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="29c02-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="29c02-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="29c02-130">IsolatedActivity</span></span>|<span data-ttu-id="29c02-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-131">xs:string</span></span>|<span data-ttu-id="29c02-132">トランザクションが分離されるアクティビティの型の名前。</span><span class="sxs-lookup"><span data-stu-id="29c02-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="29c02-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="29c02-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="29c02-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-134">xs:string</span></span>|<span data-ttu-id="29c02-135">トランザクションが分離されるアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="29c02-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="29c02-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="29c02-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="29c02-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-137">xs:string</span></span>|<span data-ttu-id="29c02-138">トランザクションが分離されるアクティビティのインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="29c02-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="29c02-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="29c02-139">AppDomain</span></span>|<span data-ttu-id="29c02-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="29c02-140">xs:string</span></span>|<span data-ttu-id="29c02-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="29c02-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

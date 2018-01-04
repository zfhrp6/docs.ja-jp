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
ms.workload: dotnet
ms.openlocfilehash: a64a8a4ab6212a5e83b59fd7523df9cd875e7b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="4532b-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="4532b-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="4532b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4532b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4532b-104">ID</span><span class="sxs-lookup"><span data-stu-id="4532b-104">ID</span></span>|<span data-ttu-id="4532b-105">1035</span><span class="sxs-lookup"><span data-stu-id="4532b-105">1035</span></span>|  
|<span data-ttu-id="4532b-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="4532b-106">Keywords</span></span>|<span data-ttu-id="4532b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4532b-107">WFRuntime</span></span>|  
|<span data-ttu-id="4532b-108">レベル</span><span class="sxs-lookup"><span data-stu-id="4532b-108">Level</span></span>|<span data-ttu-id="4532b-109">詳細</span><span class="sxs-lookup"><span data-stu-id="4532b-109">Verbose</span></span>|  
|<span data-ttu-id="4532b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4532b-110">Channel</span></span>|<span data-ttu-id="4532b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4532b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4532b-112">説明</span><span class="sxs-lookup"><span data-stu-id="4532b-112">Description</span></span>  
 <span data-ttu-id="4532b-113">アクティビティがランタイムのトランザクションを設定したことを示します。</span><span class="sxs-lookup"><span data-stu-id="4532b-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4532b-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="4532b-114">Message</span></span>  
 <span data-ttu-id="4532b-115">Activity '%1'、DisplayName によってランタイム トランザクションが設定されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="4532b-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="4532b-116">実行の分離 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' です。</span><span class="sxs-lookup"><span data-stu-id="4532b-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4532b-117">説明</span><span class="sxs-lookup"><span data-stu-id="4532b-117">Details</span></span>  
  
|<span data-ttu-id="4532b-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4532b-118">Data Item Name</span></span>|<span data-ttu-id="4532b-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4532b-119">Data Item Type</span></span>|<span data-ttu-id="4532b-120">説明</span><span class="sxs-lookup"><span data-stu-id="4532b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4532b-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="4532b-121">Activity</span></span>|<span data-ttu-id="4532b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-122">xs:string</span></span>|<span data-ttu-id="4532b-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="4532b-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="4532b-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4532b-124">DisplayName</span></span>|<span data-ttu-id="4532b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-125">xs:string</span></span>|<span data-ttu-id="4532b-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4532b-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="4532b-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4532b-127">InstanceId</span></span>|<span data-ttu-id="4532b-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-128">xs:string</span></span>|<span data-ttu-id="4532b-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="4532b-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4532b-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="4532b-130">IsolatedActivity</span></span>|<span data-ttu-id="4532b-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-131">xs:string</span></span>|<span data-ttu-id="4532b-132">トランザクションが分離されるアクティビティの型の名前。</span><span class="sxs-lookup"><span data-stu-id="4532b-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="4532b-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="4532b-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="4532b-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-134">xs:string</span></span>|<span data-ttu-id="4532b-135">トランザクションが分離されるアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4532b-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="4532b-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="4532b-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="4532b-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-137">xs:string</span></span>|<span data-ttu-id="4532b-138">トランザクションが分離されるアクティビティのインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="4532b-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="4532b-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4532b-139">AppDomain</span></span>|<span data-ttu-id="4532b-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="4532b-140">xs:string</span></span>|<span data-ttu-id="4532b-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4532b-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

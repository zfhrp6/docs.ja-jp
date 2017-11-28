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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="34744-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="34744-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="34744-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34744-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34744-104">ID</span><span class="sxs-lookup"><span data-stu-id="34744-104">ID</span></span>|<span data-ttu-id="34744-105">1035</span><span class="sxs-lookup"><span data-stu-id="34744-105">1035</span></span>|  
|<span data-ttu-id="34744-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="34744-106">Keywords</span></span>|<span data-ttu-id="34744-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="34744-107">WFRuntime</span></span>|  
|<span data-ttu-id="34744-108">レベル</span><span class="sxs-lookup"><span data-stu-id="34744-108">Level</span></span>|<span data-ttu-id="34744-109">詳細</span><span class="sxs-lookup"><span data-stu-id="34744-109">Verbose</span></span>|  
|<span data-ttu-id="34744-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="34744-110">Channel</span></span>|<span data-ttu-id="34744-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="34744-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="34744-112">説明</span><span class="sxs-lookup"><span data-stu-id="34744-112">Description</span></span>  
 <span data-ttu-id="34744-113">アクティビティがランタイムのトランザクションを設定したことを示します。</span><span class="sxs-lookup"><span data-stu-id="34744-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="34744-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="34744-114">Message</span></span>  
 <span data-ttu-id="34744-115">Activity '%1'、DisplayName によってランタイム トランザクションが設定されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="34744-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="34744-116">実行の分離 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' です。</span><span class="sxs-lookup"><span data-stu-id="34744-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="34744-117">詳細</span><span class="sxs-lookup"><span data-stu-id="34744-117">Details</span></span>  
  
|<span data-ttu-id="34744-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="34744-118">Data Item Name</span></span>|<span data-ttu-id="34744-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="34744-119">Data Item Type</span></span>|<span data-ttu-id="34744-120">説明</span><span class="sxs-lookup"><span data-stu-id="34744-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="34744-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="34744-121">Activity</span></span>|<span data-ttu-id="34744-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-122">xs:string</span></span>|<span data-ttu-id="34744-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="34744-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="34744-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="34744-124">DisplayName</span></span>|<span data-ttu-id="34744-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-125">xs:string</span></span>|<span data-ttu-id="34744-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="34744-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="34744-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="34744-127">InstanceId</span></span>|<span data-ttu-id="34744-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-128">xs:string</span></span>|<span data-ttu-id="34744-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="34744-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="34744-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="34744-130">IsolatedActivity</span></span>|<span data-ttu-id="34744-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-131">xs:string</span></span>|<span data-ttu-id="34744-132">トランザクションが分離されるアクティビティの型の名前。</span><span class="sxs-lookup"><span data-stu-id="34744-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="34744-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="34744-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="34744-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-134">xs:string</span></span>|<span data-ttu-id="34744-135">トランザクションが分離されるアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="34744-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="34744-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="34744-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="34744-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-137">xs:string</span></span>|<span data-ttu-id="34744-138">トランザクションが分離されるアクティビティのインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="34744-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="34744-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="34744-139">AppDomain</span></span>|<span data-ttu-id="34744-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="34744-140">xs:string</span></span>|<span data-ttu-id="34744-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="34744-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="31774-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="31774-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="31774-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="31774-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31774-104">ID</span><span class="sxs-lookup"><span data-stu-id="31774-104">ID</span></span>|<span data-ttu-id="31774-105">1015</span><span class="sxs-lookup"><span data-stu-id="31774-105">1015</span></span>|  
|<span data-ttu-id="31774-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="31774-106">Keywords</span></span>|<span data-ttu-id="31774-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31774-107">WFRuntime</span></span>|  
|<span data-ttu-id="31774-108">レベル</span><span class="sxs-lookup"><span data-stu-id="31774-108">Level</span></span>|<span data-ttu-id="31774-109">詳細</span><span class="sxs-lookup"><span data-stu-id="31774-109">Verbose</span></span>|  
|<span data-ttu-id="31774-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="31774-110">Channel</span></span>|<span data-ttu-id="31774-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="31774-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31774-112">説明</span><span class="sxs-lookup"><span data-stu-id="31774-112">Description</span></span>  
 <span data-ttu-id="31774-113">CompletionWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="31774-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31774-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="31774-114">Message</span></span>  
 <span data-ttu-id="31774-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="31774-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="31774-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="31774-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31774-117">詳細</span><span class="sxs-lookup"><span data-stu-id="31774-117">Details</span></span>  
  
|<span data-ttu-id="31774-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="31774-118">Data Item Name</span></span>|<span data-ttu-id="31774-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="31774-119">Data Item Type</span></span>|<span data-ttu-id="31774-120">説明</span><span class="sxs-lookup"><span data-stu-id="31774-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31774-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="31774-121">ParentActivity</span></span>|<span data-ttu-id="31774-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-122">xs:string</span></span>|<span data-ttu-id="31774-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="31774-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="31774-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="31774-124">ParentDisplayName</span></span>|<span data-ttu-id="31774-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-125">xs:string</span></span>|<span data-ttu-id="31774-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="31774-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="31774-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="31774-127">ParentInstanceId</span></span>|<span data-ttu-id="31774-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-128">xs:string</span></span>|<span data-ttu-id="31774-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="31774-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="31774-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="31774-130">CompletedActivity</span></span>|<span data-ttu-id="31774-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-131">xs:string</span></span>|<span data-ttu-id="31774-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="31774-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="31774-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="31774-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="31774-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-134">xs:string</span></span>|<span data-ttu-id="31774-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="31774-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="31774-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="31774-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="31774-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-137">xs:string</span></span>|<span data-ttu-id="31774-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="31774-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="31774-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31774-139">AppDomain</span></span>|<span data-ttu-id="31774-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="31774-140">xs:string</span></span>|<span data-ttu-id="31774-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="31774-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

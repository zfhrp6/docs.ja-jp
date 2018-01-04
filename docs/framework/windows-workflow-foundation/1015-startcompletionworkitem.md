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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="49039-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="49039-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="49039-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="49039-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49039-104">ID</span><span class="sxs-lookup"><span data-stu-id="49039-104">ID</span></span>|<span data-ttu-id="49039-105">1015</span><span class="sxs-lookup"><span data-stu-id="49039-105">1015</span></span>|  
|<span data-ttu-id="49039-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="49039-106">Keywords</span></span>|<span data-ttu-id="49039-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="49039-107">WFRuntime</span></span>|  
|<span data-ttu-id="49039-108">レベル</span><span class="sxs-lookup"><span data-stu-id="49039-108">Level</span></span>|<span data-ttu-id="49039-109">詳細</span><span class="sxs-lookup"><span data-stu-id="49039-109">Verbose</span></span>|  
|<span data-ttu-id="49039-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="49039-110">Channel</span></span>|<span data-ttu-id="49039-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="49039-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49039-112">説明</span><span class="sxs-lookup"><span data-stu-id="49039-112">Description</span></span>  
 <span data-ttu-id="49039-113">CompletionWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="49039-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49039-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="49039-114">Message</span></span>  
 <span data-ttu-id="49039-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="49039-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="49039-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="49039-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49039-117">詳細</span><span class="sxs-lookup"><span data-stu-id="49039-117">Details</span></span>  
  
|<span data-ttu-id="49039-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="49039-118">Data Item Name</span></span>|<span data-ttu-id="49039-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="49039-119">Data Item Type</span></span>|<span data-ttu-id="49039-120">説明</span><span class="sxs-lookup"><span data-stu-id="49039-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49039-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="49039-121">ParentActivity</span></span>|<span data-ttu-id="49039-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-122">xs:string</span></span>|<span data-ttu-id="49039-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="49039-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="49039-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="49039-124">ParentDisplayName</span></span>|<span data-ttu-id="49039-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-125">xs:string</span></span>|<span data-ttu-id="49039-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="49039-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="49039-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="49039-127">ParentInstanceId</span></span>|<span data-ttu-id="49039-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-128">xs:string</span></span>|<span data-ttu-id="49039-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="49039-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="49039-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="49039-130">CompletedActivity</span></span>|<span data-ttu-id="49039-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-131">xs:string</span></span>|<span data-ttu-id="49039-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="49039-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="49039-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="49039-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="49039-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-134">xs:string</span></span>|<span data-ttu-id="49039-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="49039-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="49039-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="49039-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="49039-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-137">xs:string</span></span>|<span data-ttu-id="49039-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="49039-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="49039-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="49039-139">AppDomain</span></span>|<span data-ttu-id="49039-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="49039-140">xs:string</span></span>|<span data-ttu-id="49039-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="49039-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

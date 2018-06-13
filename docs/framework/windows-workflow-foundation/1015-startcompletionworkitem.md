---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509635"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="76f2b-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="76f2b-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="76f2b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="76f2b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76f2b-104">ID</span><span class="sxs-lookup"><span data-stu-id="76f2b-104">ID</span></span>|<span data-ttu-id="76f2b-105">1015</span><span class="sxs-lookup"><span data-stu-id="76f2b-105">1015</span></span>|  
|<span data-ttu-id="76f2b-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="76f2b-106">Keywords</span></span>|<span data-ttu-id="76f2b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="76f2b-107">WFRuntime</span></span>|  
|<span data-ttu-id="76f2b-108">レベル</span><span class="sxs-lookup"><span data-stu-id="76f2b-108">Level</span></span>|<span data-ttu-id="76f2b-109">詳細</span><span class="sxs-lookup"><span data-stu-id="76f2b-109">Verbose</span></span>|  
|<span data-ttu-id="76f2b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="76f2b-110">Channel</span></span>|<span data-ttu-id="76f2b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="76f2b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="76f2b-112">説明</span><span class="sxs-lookup"><span data-stu-id="76f2b-112">Description</span></span>  
 <span data-ttu-id="76f2b-113">CompletionWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="76f2b-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="76f2b-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="76f2b-114">Message</span></span>  
 <span data-ttu-id="76f2b-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="76f2b-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="76f2b-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="76f2b-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="76f2b-117">詳細</span><span class="sxs-lookup"><span data-stu-id="76f2b-117">Details</span></span>  
  
|<span data-ttu-id="76f2b-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="76f2b-118">Data Item Name</span></span>|<span data-ttu-id="76f2b-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="76f2b-119">Data Item Type</span></span>|<span data-ttu-id="76f2b-120">説明</span><span class="sxs-lookup"><span data-stu-id="76f2b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="76f2b-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="76f2b-121">ParentActivity</span></span>|<span data-ttu-id="76f2b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-122">xs:string</span></span>|<span data-ttu-id="76f2b-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="76f2b-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="76f2b-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="76f2b-124">ParentDisplayName</span></span>|<span data-ttu-id="76f2b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-125">xs:string</span></span>|<span data-ttu-id="76f2b-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="76f2b-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="76f2b-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="76f2b-127">ParentInstanceId</span></span>|<span data-ttu-id="76f2b-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-128">xs:string</span></span>|<span data-ttu-id="76f2b-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="76f2b-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="76f2b-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="76f2b-130">CompletedActivity</span></span>|<span data-ttu-id="76f2b-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-131">xs:string</span></span>|<span data-ttu-id="76f2b-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="76f2b-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="76f2b-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="76f2b-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="76f2b-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-134">xs:string</span></span>|<span data-ttu-id="76f2b-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="76f2b-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="76f2b-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="76f2b-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="76f2b-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-137">xs:string</span></span>|<span data-ttu-id="76f2b-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="76f2b-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="76f2b-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="76f2b-139">AppDomain</span></span>|<span data-ttu-id="76f2b-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="76f2b-140">xs:string</span></span>|<span data-ttu-id="76f2b-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="76f2b-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

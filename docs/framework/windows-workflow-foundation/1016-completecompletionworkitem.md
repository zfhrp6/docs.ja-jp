---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510297"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="1d2f6-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="1d2f6-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1d2f6-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1d2f6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d2f6-104">ID</span><span class="sxs-lookup"><span data-stu-id="1d2f6-104">ID</span></span>|<span data-ttu-id="1d2f6-105">1016</span><span class="sxs-lookup"><span data-stu-id="1d2f6-105">1016</span></span>|  
|<span data-ttu-id="1d2f6-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1d2f6-106">Keywords</span></span>|<span data-ttu-id="1d2f6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1d2f6-107">WFRuntime</span></span>|  
|<span data-ttu-id="1d2f6-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1d2f6-108">Level</span></span>|<span data-ttu-id="1d2f6-109">詳細</span><span class="sxs-lookup"><span data-stu-id="1d2f6-109">Verbose</span></span>|  
|<span data-ttu-id="1d2f6-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1d2f6-110">Channel</span></span>|<span data-ttu-id="1d2f6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1d2f6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1d2f6-112">説明</span><span class="sxs-lookup"><span data-stu-id="1d2f6-112">Description</span></span>  
 <span data-ttu-id="1d2f6-113">CompletionWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1d2f6-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1d2f6-114">Message</span></span>  
 <span data-ttu-id="1d2f6-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1d2f6-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1d2f6-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1d2f6-117">Details</span></span>  
  
|<span data-ttu-id="1d2f6-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1d2f6-118">Data Item Name</span></span>|<span data-ttu-id="1d2f6-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1d2f6-119">Data Item Type</span></span>|<span data-ttu-id="1d2f6-120">説明</span><span class="sxs-lookup"><span data-stu-id="1d2f6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1d2f6-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="1d2f6-121">ParentActivity</span></span>|<span data-ttu-id="1d2f6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-122">xs:string</span></span>|<span data-ttu-id="1d2f6-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1d2f6-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="1d2f6-124">ParentDisplayName</span></span>|<span data-ttu-id="1d2f6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-125">xs:string</span></span>|<span data-ttu-id="1d2f6-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1d2f6-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1d2f6-127">ParentInstanceId</span></span>|<span data-ttu-id="1d2f6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-128">xs:string</span></span>|<span data-ttu-id="1d2f6-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1d2f6-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="1d2f6-130">CompletedActivity</span></span>|<span data-ttu-id="1d2f6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-131">xs:string</span></span>|<span data-ttu-id="1d2f6-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="1d2f6-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1d2f6-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="1d2f6-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-134">xs:string</span></span>|<span data-ttu-id="1d2f6-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="1d2f6-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1d2f6-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="1d2f6-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-137">xs:string</span></span>|<span data-ttu-id="1d2f6-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="1d2f6-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1d2f6-139">AppDomain</span></span>|<span data-ttu-id="1d2f6-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="1d2f6-140">xs:string</span></span>|<span data-ttu-id="1d2f6-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1d2f6-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

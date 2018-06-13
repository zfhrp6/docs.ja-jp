---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509973"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="b7f46-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="b7f46-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="b7f46-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b7f46-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7f46-104">ID</span><span class="sxs-lookup"><span data-stu-id="b7f46-104">ID</span></span>|<span data-ttu-id="b7f46-105">1009</span><span class="sxs-lookup"><span data-stu-id="b7f46-105">1009</span></span>|  
|<span data-ttu-id="b7f46-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b7f46-106">Keywords</span></span>|<span data-ttu-id="b7f46-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b7f46-107">WFRuntime</span></span>|  
|<span data-ttu-id="b7f46-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b7f46-108">Level</span></span>|<span data-ttu-id="b7f46-109">情報</span><span class="sxs-lookup"><span data-stu-id="b7f46-109">Information</span></span>|  
|<span data-ttu-id="b7f46-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b7f46-110">Channel</span></span>|<span data-ttu-id="b7f46-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b7f46-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7f46-112">説明</span><span class="sxs-lookup"><span data-stu-id="b7f46-112">Description</span></span>  
 <span data-ttu-id="b7f46-113">アクティビティの実行がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="b7f46-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7f46-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b7f46-114">Message</span></span>  
 <span data-ttu-id="b7f46-115">Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="b7f46-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7f46-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b7f46-116">Details</span></span>  
  
|<span data-ttu-id="b7f46-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b7f46-117">Data Item Name</span></span>|<span data-ttu-id="b7f46-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b7f46-118">Data Item Type</span></span>|<span data-ttu-id="b7f46-119">説明</span><span class="sxs-lookup"><span data-stu-id="b7f46-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7f46-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="b7f46-120">ParentActivity</span></span>|<span data-ttu-id="b7f46-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-121">xs:string</span></span>|<span data-ttu-id="b7f46-122">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="b7f46-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="b7f46-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7f46-123">ParentDisplayName</span></span>|<span data-ttu-id="b7f46-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-124">xs:string</span></span>|<span data-ttu-id="b7f46-125">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="b7f46-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="b7f46-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7f46-126">ParentInstanceId</span></span>|<span data-ttu-id="b7f46-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-127">xs:string</span></span>|<span data-ttu-id="b7f46-128">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="b7f46-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="b7f46-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="b7f46-129">ChildActivity</span></span>|<span data-ttu-id="b7f46-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-130">xs:string</span></span>|<span data-ttu-id="b7f46-131">スケジュール済みの子アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="b7f46-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="b7f46-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7f46-132">ChildDisplayName</span></span>|<span data-ttu-id="b7f46-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-133">xs:string</span></span>|<span data-ttu-id="b7f46-134">スケジュール済みの子アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="b7f46-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="b7f46-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7f46-135">ChildInstanceId</span></span>|<span data-ttu-id="b7f46-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-136">xs:string</span></span>|<span data-ttu-id="b7f46-137">スケジュール済み子アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="b7f46-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="b7f46-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b7f46-138">AppDomain</span></span>|<span data-ttu-id="b7f46-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="b7f46-139">xs:string</span></span>|<span data-ttu-id="b7f46-140">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b7f46-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

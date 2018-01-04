---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfa9553c25f607ec25fd968c2e8c6db061fb49dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="9a8b1-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="9a8b1-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9a8b1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9a8b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a8b1-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a8b1-104">ID</span></span>|<span data-ttu-id="9a8b1-105">1029</span><span class="sxs-lookup"><span data-stu-id="9a8b1-105">1029</span></span>|  
|<span data-ttu-id="9a8b1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="9a8b1-106">Keywords</span></span>|<span data-ttu-id="9a8b1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9a8b1-107">WFRuntime</span></span>|  
|<span data-ttu-id="9a8b1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="9a8b1-108">Level</span></span>|<span data-ttu-id="9a8b1-109">詳細</span><span class="sxs-lookup"><span data-stu-id="9a8b1-109">Verbose</span></span>|  
|<span data-ttu-id="9a8b1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9a8b1-110">Channel</span></span>|<span data-ttu-id="9a8b1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9a8b1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a8b1-112">説明</span><span class="sxs-lookup"><span data-stu-id="9a8b1-112">Description</span></span>  
 <span data-ttu-id="9a8b1-113">FaultWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a8b1-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="9a8b1-114">Message</span></span>  
 <span data-ttu-id="9a8b1-115">Activity '%1'、DisplayName に対して FaultWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="9a8b1-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a8b1-117">詳細</span><span class="sxs-lookup"><span data-stu-id="9a8b1-117">Details</span></span>  
  
|<span data-ttu-id="9a8b1-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9a8b1-118">Data Item Name</span></span>|<span data-ttu-id="9a8b1-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9a8b1-119">Data Item Type</span></span>|<span data-ttu-id="9a8b1-120">説明</span><span class="sxs-lookup"><span data-stu-id="9a8b1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a8b1-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="9a8b1-121">FaultActivity</span></span>|<span data-ttu-id="9a8b1-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-122">xs:string</span></span>|<span data-ttu-id="9a8b1-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="9a8b1-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9a8b1-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="9a8b1-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-125">xs:string</span></span>|<span data-ttu-id="9a8b1-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="9a8b1-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9a8b1-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="9a8b1-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-128">xs:string</span></span>|<span data-ttu-id="9a8b1-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="9a8b1-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="9a8b1-130">ExceptionActivity</span></span>|<span data-ttu-id="9a8b1-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-131">xs:string</span></span>|<span data-ttu-id="9a8b1-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9a8b1-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9a8b1-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="9a8b1-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-134">xs:string</span></span>|<span data-ttu-id="9a8b1-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9a8b1-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="9a8b1-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="9a8b1-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-137">xs:string</span></span>|<span data-ttu-id="9a8b1-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="9a8b1-139">例外</span><span class="sxs-lookup"><span data-stu-id="9a8b1-139">Exception</span></span>|<span data-ttu-id="9a8b1-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-140">xs:string</span></span>|<span data-ttu-id="9a8b1-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="9a8b1-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="9a8b1-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a8b1-142">AppDomain</span></span>|<span data-ttu-id="9a8b1-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a8b1-143">xs:string</span></span>|<span data-ttu-id="9a8b1-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9a8b1-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ba1ae69caff2e08da58e824d35341d3781ea8ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="06d0e-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="06d0e-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="06d0e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="06d0e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06d0e-104">ID</span><span class="sxs-lookup"><span data-stu-id="06d0e-104">ID</span></span>|<span data-ttu-id="06d0e-105">1029</span><span class="sxs-lookup"><span data-stu-id="06d0e-105">1029</span></span>|  
|<span data-ttu-id="06d0e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="06d0e-106">Keywords</span></span>|<span data-ttu-id="06d0e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="06d0e-107">WFRuntime</span></span>|  
|<span data-ttu-id="06d0e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="06d0e-108">Level</span></span>|<span data-ttu-id="06d0e-109">詳細</span><span class="sxs-lookup"><span data-stu-id="06d0e-109">Verbose</span></span>|  
|<span data-ttu-id="06d0e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="06d0e-110">Channel</span></span>|<span data-ttu-id="06d0e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="06d0e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="06d0e-112">説明</span><span class="sxs-lookup"><span data-stu-id="06d0e-112">Description</span></span>  
 <span data-ttu-id="06d0e-113">FaultWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="06d0e-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="06d0e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="06d0e-114">Message</span></span>  
 <span data-ttu-id="06d0e-115">Activity '%1'、DisplayName に対して FaultWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="06d0e-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="06d0e-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="06d0e-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="06d0e-117">詳細</span><span class="sxs-lookup"><span data-stu-id="06d0e-117">Details</span></span>  
  
|<span data-ttu-id="06d0e-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="06d0e-118">Data Item Name</span></span>|<span data-ttu-id="06d0e-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="06d0e-119">Data Item Type</span></span>|<span data-ttu-id="06d0e-120">説明</span><span class="sxs-lookup"><span data-stu-id="06d0e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="06d0e-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="06d0e-121">FaultActivity</span></span>|<span data-ttu-id="06d0e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-122">xs:string</span></span>|<span data-ttu-id="06d0e-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="06d0e-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="06d0e-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="06d0e-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="06d0e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-125">xs:string</span></span>|<span data-ttu-id="06d0e-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="06d0e-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="06d0e-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="06d0e-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="06d0e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-128">xs:string</span></span>|<span data-ttu-id="06d0e-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="06d0e-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="06d0e-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="06d0e-130">ExceptionActivity</span></span>|<span data-ttu-id="06d0e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-131">xs:string</span></span>|<span data-ttu-id="06d0e-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="06d0e-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="06d0e-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="06d0e-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="06d0e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-134">xs:string</span></span>|<span data-ttu-id="06d0e-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="06d0e-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="06d0e-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="06d0e-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="06d0e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-137">xs:string</span></span>|<span data-ttu-id="06d0e-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="06d0e-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="06d0e-139">例外</span><span class="sxs-lookup"><span data-stu-id="06d0e-139">Exception</span></span>|<span data-ttu-id="06d0e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-140">xs:string</span></span>|<span data-ttu-id="06d0e-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="06d0e-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="06d0e-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="06d0e-142">AppDomain</span></span>|<span data-ttu-id="06d0e-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="06d0e-143">xs:string</span></span>|<span data-ttu-id="06d0e-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="06d0e-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

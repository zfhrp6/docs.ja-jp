---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="11b1c-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="11b1c-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="11b1c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="11b1c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11b1c-104">ID</span><span class="sxs-lookup"><span data-stu-id="11b1c-104">ID</span></span>|<span data-ttu-id="11b1c-105">1029</span><span class="sxs-lookup"><span data-stu-id="11b1c-105">1029</span></span>|  
|<span data-ttu-id="11b1c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="11b1c-106">Keywords</span></span>|<span data-ttu-id="11b1c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="11b1c-107">WFRuntime</span></span>|  
|<span data-ttu-id="11b1c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="11b1c-108">Level</span></span>|<span data-ttu-id="11b1c-109">詳細</span><span class="sxs-lookup"><span data-stu-id="11b1c-109">Verbose</span></span>|  
|<span data-ttu-id="11b1c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="11b1c-110">Channel</span></span>|<span data-ttu-id="11b1c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="11b1c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="11b1c-112">説明</span><span class="sxs-lookup"><span data-stu-id="11b1c-112">Description</span></span>  
 <span data-ttu-id="11b1c-113">FaultWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="11b1c-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="11b1c-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="11b1c-114">Message</span></span>  
 <span data-ttu-id="11b1c-115">Activity '%1'、DisplayName に対して FaultWorkItem がスケジュールされました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="11b1c-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="11b1c-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="11b1c-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="11b1c-117">詳細</span><span class="sxs-lookup"><span data-stu-id="11b1c-117">Details</span></span>  
  
|<span data-ttu-id="11b1c-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="11b1c-118">Data Item Name</span></span>|<span data-ttu-id="11b1c-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="11b1c-119">Data Item Type</span></span>|<span data-ttu-id="11b1c-120">説明</span><span class="sxs-lookup"><span data-stu-id="11b1c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="11b1c-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="11b1c-121">FaultActivity</span></span>|<span data-ttu-id="11b1c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-122">xs:string</span></span>|<span data-ttu-id="11b1c-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="11b1c-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="11b1c-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="11b1c-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="11b1c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-125">xs:string</span></span>|<span data-ttu-id="11b1c-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="11b1c-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="11b1c-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="11b1c-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="11b1c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-128">xs:string</span></span>|<span data-ttu-id="11b1c-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="11b1c-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="11b1c-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="11b1c-130">ExceptionActivity</span></span>|<span data-ttu-id="11b1c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-131">xs:string</span></span>|<span data-ttu-id="11b1c-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="11b1c-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="11b1c-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="11b1c-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="11b1c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-134">xs:string</span></span>|<span data-ttu-id="11b1c-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="11b1c-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="11b1c-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="11b1c-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="11b1c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-137">xs:string</span></span>|<span data-ttu-id="11b1c-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="11b1c-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="11b1c-139">例外</span><span class="sxs-lookup"><span data-stu-id="11b1c-139">Exception</span></span>|<span data-ttu-id="11b1c-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-140">xs:string</span></span>|<span data-ttu-id="11b1c-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="11b1c-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="11b1c-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="11b1c-142">AppDomain</span></span>|<span data-ttu-id="11b1c-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="11b1c-143">xs:string</span></span>|<span data-ttu-id="11b1c-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="11b1c-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

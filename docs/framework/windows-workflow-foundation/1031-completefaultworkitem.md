---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="74711-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="74711-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="74711-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="74711-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74711-104">ID</span><span class="sxs-lookup"><span data-stu-id="74711-104">ID</span></span>|<span data-ttu-id="74711-105">1031</span><span class="sxs-lookup"><span data-stu-id="74711-105">1031</span></span>|  
|<span data-ttu-id="74711-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="74711-106">Keywords</span></span>|<span data-ttu-id="74711-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="74711-107">WFRuntime</span></span>|  
|<span data-ttu-id="74711-108">レベル</span><span class="sxs-lookup"><span data-stu-id="74711-108">Level</span></span>|<span data-ttu-id="74711-109">詳細</span><span class="sxs-lookup"><span data-stu-id="74711-109">Verbose</span></span>|  
|<span data-ttu-id="74711-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="74711-110">Channel</span></span>|<span data-ttu-id="74711-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="74711-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="74711-112">説明</span><span class="sxs-lookup"><span data-stu-id="74711-112">Description</span></span>  
 <span data-ttu-id="74711-113">FaultWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="74711-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="74711-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="74711-114">Message</span></span>  
 <span data-ttu-id="74711-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の FaultWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="74711-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="74711-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="74711-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="74711-117">詳細</span><span class="sxs-lookup"><span data-stu-id="74711-117">Details</span></span>  
  
|<span data-ttu-id="74711-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="74711-118">Data Item Name</span></span>|<span data-ttu-id="74711-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="74711-119">Data Item Type</span></span>|<span data-ttu-id="74711-120">説明</span><span class="sxs-lookup"><span data-stu-id="74711-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="74711-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="74711-121">FaultActivity</span></span>|<span data-ttu-id="74711-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-122">xs:string</span></span>|<span data-ttu-id="74711-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="74711-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="74711-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="74711-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="74711-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-125">xs:string</span></span>|<span data-ttu-id="74711-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="74711-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="74711-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="74711-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="74711-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-128">xs:string</span></span>|<span data-ttu-id="74711-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="74711-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="74711-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="74711-130">ExceptionActivity</span></span>|<span data-ttu-id="74711-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-131">xs:string</span></span>|<span data-ttu-id="74711-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="74711-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="74711-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="74711-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="74711-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-134">xs:string</span></span>|<span data-ttu-id="74711-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="74711-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="74711-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="74711-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="74711-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-137">xs:string</span></span>|<span data-ttu-id="74711-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="74711-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="74711-139">例外</span><span class="sxs-lookup"><span data-stu-id="74711-139">Exception</span></span>|<span data-ttu-id="74711-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-140">xs:string</span></span>|<span data-ttu-id="74711-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="74711-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="74711-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="74711-142">AppDomain</span></span>|<span data-ttu-id="74711-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="74711-143">xs:string</span></span>|<span data-ttu-id="74711-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="74711-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

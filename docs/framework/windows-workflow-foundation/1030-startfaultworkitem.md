---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 436a0323fcf4498a1d707f7af9bd8204885fd645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="ee9ce-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="ee9ce-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ee9ce-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ee9ce-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee9ce-104">ID</span><span class="sxs-lookup"><span data-stu-id="ee9ce-104">ID</span></span>|<span data-ttu-id="ee9ce-105">1030</span><span class="sxs-lookup"><span data-stu-id="ee9ce-105">1030</span></span>|  
|<span data-ttu-id="ee9ce-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="ee9ce-106">Keywords</span></span>|<span data-ttu-id="ee9ce-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ee9ce-107">WFRuntime</span></span>|  
|<span data-ttu-id="ee9ce-108">レベル</span><span class="sxs-lookup"><span data-stu-id="ee9ce-108">Level</span></span>|<span data-ttu-id="ee9ce-109">詳細</span><span class="sxs-lookup"><span data-stu-id="ee9ce-109">Verbose</span></span>|  
|<span data-ttu-id="ee9ce-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ee9ce-110">Channel</span></span>|<span data-ttu-id="ee9ce-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ee9ce-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ee9ce-112">説明</span><span class="sxs-lookup"><span data-stu-id="ee9ce-112">Description</span></span>  
 <span data-ttu-id="ee9ce-113">FaultWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ee9ce-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="ee9ce-114">Message</span></span>  
 <span data-ttu-id="ee9ce-115">Activity '%1'、DisplayName FaultWorkItem の実行を開始: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ee9ce-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ee9ce-117">詳細</span><span class="sxs-lookup"><span data-stu-id="ee9ce-117">Details</span></span>  
  
|<span data-ttu-id="ee9ce-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ee9ce-118">Data Item Name</span></span>|<span data-ttu-id="ee9ce-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ee9ce-119">Data Item Type</span></span>|<span data-ttu-id="ee9ce-120">説明</span><span class="sxs-lookup"><span data-stu-id="ee9ce-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ee9ce-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="ee9ce-121">FaultActivity</span></span>|<span data-ttu-id="ee9ce-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-122">xs:string</span></span>|<span data-ttu-id="ee9ce-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="ee9ce-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ee9ce-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="ee9ce-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-125">xs:string</span></span>|<span data-ttu-id="ee9ce-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="ee9ce-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ee9ce-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="ee9ce-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-128">xs:string</span></span>|<span data-ttu-id="ee9ce-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="ee9ce-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="ee9ce-130">ExceptionActivity</span></span>|<span data-ttu-id="ee9ce-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-131">xs:string</span></span>|<span data-ttu-id="ee9ce-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ee9ce-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ee9ce-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="ee9ce-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-134">xs:string</span></span>|<span data-ttu-id="ee9ce-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ee9ce-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ee9ce-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="ee9ce-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-137">xs:string</span></span>|<span data-ttu-id="ee9ce-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ee9ce-139">例外</span><span class="sxs-lookup"><span data-stu-id="ee9ce-139">Exception</span></span>|<span data-ttu-id="ee9ce-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-140">xs:string</span></span>|<span data-ttu-id="ee9ce-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="ee9ce-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="ee9ce-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ee9ce-142">AppDomain</span></span>|<span data-ttu-id="ee9ce-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="ee9ce-143">xs:string</span></span>|<span data-ttu-id="ee9ce-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ee9ce-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

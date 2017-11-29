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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b25dbd5ced96b8e9ca3ef51e4de841a6238d2cbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="01d1a-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="01d1a-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="01d1a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="01d1a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01d1a-104">ID</span><span class="sxs-lookup"><span data-stu-id="01d1a-104">ID</span></span>|<span data-ttu-id="01d1a-105">1030</span><span class="sxs-lookup"><span data-stu-id="01d1a-105">1030</span></span>|  
|<span data-ttu-id="01d1a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="01d1a-106">Keywords</span></span>|<span data-ttu-id="01d1a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="01d1a-107">WFRuntime</span></span>|  
|<span data-ttu-id="01d1a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="01d1a-108">Level</span></span>|<span data-ttu-id="01d1a-109">詳細</span><span class="sxs-lookup"><span data-stu-id="01d1a-109">Verbose</span></span>|  
|<span data-ttu-id="01d1a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="01d1a-110">Channel</span></span>|<span data-ttu-id="01d1a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="01d1a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01d1a-112">説明</span><span class="sxs-lookup"><span data-stu-id="01d1a-112">Description</span></span>  
 <span data-ttu-id="01d1a-113">FaultWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="01d1a-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01d1a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="01d1a-114">Message</span></span>  
 <span data-ttu-id="01d1a-115">Activity '%1'、DisplayName FaultWorkItem の実行を開始: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="01d1a-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="01d1a-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="01d1a-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01d1a-117">詳細</span><span class="sxs-lookup"><span data-stu-id="01d1a-117">Details</span></span>  
  
|<span data-ttu-id="01d1a-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="01d1a-118">Data Item Name</span></span>|<span data-ttu-id="01d1a-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="01d1a-119">Data Item Type</span></span>|<span data-ttu-id="01d1a-120">説明</span><span class="sxs-lookup"><span data-stu-id="01d1a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01d1a-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="01d1a-121">FaultActivity</span></span>|<span data-ttu-id="01d1a-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-122">xs:string</span></span>|<span data-ttu-id="01d1a-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="01d1a-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="01d1a-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="01d1a-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="01d1a-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-125">xs:string</span></span>|<span data-ttu-id="01d1a-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="01d1a-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="01d1a-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="01d1a-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="01d1a-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-128">xs:string</span></span>|<span data-ttu-id="01d1a-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="01d1a-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="01d1a-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="01d1a-130">ExceptionActivity</span></span>|<span data-ttu-id="01d1a-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-131">xs:string</span></span>|<span data-ttu-id="01d1a-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="01d1a-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="01d1a-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="01d1a-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="01d1a-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-134">xs:string</span></span>|<span data-ttu-id="01d1a-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="01d1a-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="01d1a-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="01d1a-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="01d1a-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-137">xs:string</span></span>|<span data-ttu-id="01d1a-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="01d1a-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="01d1a-139">例外</span><span class="sxs-lookup"><span data-stu-id="01d1a-139">Exception</span></span>|<span data-ttu-id="01d1a-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-140">xs:string</span></span>|<span data-ttu-id="01d1a-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="01d1a-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="01d1a-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01d1a-142">AppDomain</span></span>|<span data-ttu-id="01d1a-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="01d1a-143">xs:string</span></span>|<span data-ttu-id="01d1a-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="01d1a-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

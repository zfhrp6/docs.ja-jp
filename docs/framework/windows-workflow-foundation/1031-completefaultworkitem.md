---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509744"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="2db7f-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="2db7f-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2db7f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2db7f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2db7f-104">ID</span><span class="sxs-lookup"><span data-stu-id="2db7f-104">ID</span></span>|<span data-ttu-id="2db7f-105">1031</span><span class="sxs-lookup"><span data-stu-id="2db7f-105">1031</span></span>|  
|<span data-ttu-id="2db7f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2db7f-106">Keywords</span></span>|<span data-ttu-id="2db7f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2db7f-107">WFRuntime</span></span>|  
|<span data-ttu-id="2db7f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2db7f-108">Level</span></span>|<span data-ttu-id="2db7f-109">詳細</span><span class="sxs-lookup"><span data-stu-id="2db7f-109">Verbose</span></span>|  
|<span data-ttu-id="2db7f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2db7f-110">Channel</span></span>|<span data-ttu-id="2db7f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2db7f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2db7f-112">説明</span><span class="sxs-lookup"><span data-stu-id="2db7f-112">Description</span></span>  
 <span data-ttu-id="2db7f-113">FaultWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="2db7f-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2db7f-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2db7f-114">Message</span></span>  
 <span data-ttu-id="2db7f-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の FaultWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="2db7f-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="2db7f-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="2db7f-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2db7f-117">詳細</span><span class="sxs-lookup"><span data-stu-id="2db7f-117">Details</span></span>  
  
|<span data-ttu-id="2db7f-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2db7f-118">Data Item Name</span></span>|<span data-ttu-id="2db7f-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2db7f-119">Data Item Type</span></span>|<span data-ttu-id="2db7f-120">説明</span><span class="sxs-lookup"><span data-stu-id="2db7f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2db7f-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="2db7f-121">FaultActivity</span></span>|<span data-ttu-id="2db7f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-122">xs:string</span></span>|<span data-ttu-id="2db7f-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="2db7f-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="2db7f-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2db7f-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="2db7f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-125">xs:string</span></span>|<span data-ttu-id="2db7f-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2db7f-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="2db7f-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2db7f-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="2db7f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-128">xs:string</span></span>|<span data-ttu-id="2db7f-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="2db7f-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="2db7f-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="2db7f-130">ExceptionActivity</span></span>|<span data-ttu-id="2db7f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-131">xs:string</span></span>|<span data-ttu-id="2db7f-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="2db7f-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2db7f-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2db7f-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="2db7f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-134">xs:string</span></span>|<span data-ttu-id="2db7f-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2db7f-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2db7f-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2db7f-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="2db7f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-137">xs:string</span></span>|<span data-ttu-id="2db7f-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="2db7f-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2db7f-139">例外</span><span class="sxs-lookup"><span data-stu-id="2db7f-139">Exception</span></span>|<span data-ttu-id="2db7f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-140">xs:string</span></span>|<span data-ttu-id="2db7f-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="2db7f-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="2db7f-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2db7f-142">AppDomain</span></span>|<span data-ttu-id="2db7f-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="2db7f-143">xs:string</span></span>|<span data-ttu-id="2db7f-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2db7f-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

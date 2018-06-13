---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509681"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="adf57-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="adf57-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="adf57-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="adf57-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="adf57-104">ID</span><span class="sxs-lookup"><span data-stu-id="adf57-104">ID</span></span>|<span data-ttu-id="adf57-105">1030</span><span class="sxs-lookup"><span data-stu-id="adf57-105">1030</span></span>|  
|<span data-ttu-id="adf57-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="adf57-106">Keywords</span></span>|<span data-ttu-id="adf57-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="adf57-107">WFRuntime</span></span>|  
|<span data-ttu-id="adf57-108">レベル</span><span class="sxs-lookup"><span data-stu-id="adf57-108">Level</span></span>|<span data-ttu-id="adf57-109">詳細</span><span class="sxs-lookup"><span data-stu-id="adf57-109">Verbose</span></span>|  
|<span data-ttu-id="adf57-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="adf57-110">Channel</span></span>|<span data-ttu-id="adf57-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="adf57-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="adf57-112">説明</span><span class="sxs-lookup"><span data-stu-id="adf57-112">Description</span></span>  
 <span data-ttu-id="adf57-113">FaultWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="adf57-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="adf57-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="adf57-114">Message</span></span>  
 <span data-ttu-id="adf57-115">Activity '%1'、DisplayName FaultWorkItem の実行を開始: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="adf57-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="adf57-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="adf57-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="adf57-117">詳細</span><span class="sxs-lookup"><span data-stu-id="adf57-117">Details</span></span>  
  
|<span data-ttu-id="adf57-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="adf57-118">Data Item Name</span></span>|<span data-ttu-id="adf57-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="adf57-119">Data Item Type</span></span>|<span data-ttu-id="adf57-120">説明</span><span class="sxs-lookup"><span data-stu-id="adf57-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="adf57-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="adf57-121">FaultActivity</span></span>|<span data-ttu-id="adf57-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-122">xs:string</span></span>|<span data-ttu-id="adf57-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="adf57-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="adf57-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="adf57-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="adf57-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-125">xs:string</span></span>|<span data-ttu-id="adf57-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="adf57-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="adf57-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="adf57-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="adf57-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-128">xs:string</span></span>|<span data-ttu-id="adf57-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="adf57-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="adf57-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="adf57-130">ExceptionActivity</span></span>|<span data-ttu-id="adf57-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-131">xs:string</span></span>|<span data-ttu-id="adf57-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="adf57-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="adf57-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="adf57-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="adf57-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-134">xs:string</span></span>|<span data-ttu-id="adf57-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="adf57-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="adf57-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="adf57-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="adf57-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-137">xs:string</span></span>|<span data-ttu-id="adf57-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="adf57-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="adf57-139">例外</span><span class="sxs-lookup"><span data-stu-id="adf57-139">Exception</span></span>|<span data-ttu-id="adf57-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-140">xs:string</span></span>|<span data-ttu-id="adf57-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="adf57-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="adf57-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="adf57-142">AppDomain</span></span>|<span data-ttu-id="adf57-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="adf57-143">xs:string</span></span>|<span data-ttu-id="adf57-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="adf57-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

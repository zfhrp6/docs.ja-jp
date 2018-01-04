---
title: 119 - WorkflowInstanceUpdatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cb60a0f7905f49e4bfa4c1c50de686dd74ff114
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="119---workflowinstanceupdatedrecord"></a><span data-ttu-id="45288-102">119 - WorkflowInstanceUpdatedRecord</span><span class="sxs-lookup"><span data-stu-id="45288-102">119 - WorkflowInstanceUpdatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="45288-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="45288-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45288-104">ID</span><span class="sxs-lookup"><span data-stu-id="45288-104">ID</span></span>|<span data-ttu-id="45288-105">119</span><span class="sxs-lookup"><span data-stu-id="45288-105">119</span></span>|  
|<span data-ttu-id="45288-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="45288-106">Keywords</span></span>|<span data-ttu-id="45288-107">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="45288-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="45288-108">レベル</span><span class="sxs-lookup"><span data-stu-id="45288-108">Level</span></span>|<span data-ttu-id="45288-109">情報</span><span class="sxs-lookup"><span data-stu-id="45288-109">Information</span></span>|  
|<span data-ttu-id="45288-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="45288-110">Channel</span></span>|<span data-ttu-id="45288-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="45288-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="45288-112">説明</span><span class="sxs-lookup"><span data-stu-id="45288-112">Description</span></span>  
 <span data-ttu-id="45288-113">このイベントは、ワークフロー インスタンスが更新されたときに、ETW 追跡参加要素によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="45288-113">This event is emitted by the ETW tracking participant when a workflow instance is updated.</span></span>  
  
## <a name="message"></a><span data-ttu-id="45288-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="45288-114">Message</span></span>  
 <span data-ttu-id="45288-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、OriginalDefinitionIdentity = %6、UpdatedDefinitionIdentity = %7、Annotations = %8、ProfileName = %9</span><span class="sxs-lookup"><span data-stu-id="45288-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9</span></span>  
  
## <a name="details"></a><span data-ttu-id="45288-116">詳細</span><span class="sxs-lookup"><span data-stu-id="45288-116">Details</span></span>  
  
|<span data-ttu-id="45288-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="45288-117">Data Item Name</span></span>|<span data-ttu-id="45288-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="45288-118">Data Item Type</span></span>|<span data-ttu-id="45288-119">説明</span><span class="sxs-lookup"><span data-stu-id="45288-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="45288-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="45288-120">InstanceId</span></span>|<span data-ttu-id="45288-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="45288-121">xs:GUID</span></span>|<span data-ttu-id="45288-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="45288-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="45288-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="45288-123">RecordNumber</span></span>|<span data-ttu-id="45288-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="45288-124">xs:long</span></span>|<span data-ttu-id="45288-125">生成されたレコードのシーケンス番号</span><span class="sxs-lookup"><span data-stu-id="45288-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="45288-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="45288-126">EventTime</span></span>|<span data-ttu-id="45288-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="45288-127">xs:dateTime</span></span>|<span data-ttu-id="45288-128">イベントの生成時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="45288-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="45288-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="45288-129">ActivityDefinitionId</span></span>|<span data-ttu-id="45288-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-130">xs:string</span></span>|<span data-ttu-id="45288-131">ワークフローのルート アクティビティの名前</span><span class="sxs-lookup"><span data-stu-id="45288-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="45288-132">状態</span><span class="sxs-lookup"><span data-stu-id="45288-132">State</span></span>|<span data-ttu-id="45288-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-133">xs:string</span></span>|<span data-ttu-id="45288-134">ワークフローの現在の状態。</span><span class="sxs-lookup"><span data-stu-id="45288-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="45288-135">OriginalDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="45288-135">OriginalDefinitionIdentity</span></span>|<span data-ttu-id="45288-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-136">xs:string</span></span>|<span data-ttu-id="45288-137">元のワークフロー定義 ID</span><span class="sxs-lookup"><span data-stu-id="45288-137">The original workflow definition id</span></span>|  
|<span data-ttu-id="45288-138">UpdatedDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="45288-138">UpdatedDefinitionIdentity</span></span>|<span data-ttu-id="45288-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-139">xs:string</span></span>|<span data-ttu-id="45288-140">更新されたワークフロー定義 ID</span><span class="sxs-lookup"><span data-stu-id="45288-140">The updated workflow definition id</span></span>|  
|<span data-ttu-id="45288-141">コメント</span><span class="sxs-lookup"><span data-stu-id="45288-141">Annotations</span></span>|<span data-ttu-id="45288-142">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-142">xs:string</span></span>|<span data-ttu-id="45288-143">このイベントに追加された注釈。</span><span class="sxs-lookup"><span data-stu-id="45288-143">The annotations that were added to this event.</span></span> <span data-ttu-id="45288-144">形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。</span><span class="sxs-lookup"><span data-stu-id="45288-144">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="45288-145">注釈が指定されていない場合、文字列が含まれる\<項目/>。</span><span class="sxs-lookup"><span data-stu-id="45288-145">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="45288-146">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。</span><span class="sxs-lookup"><span data-stu-id="45288-146">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="45288-147">イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。</span><span class="sxs-lookup"><span data-stu-id="45288-147">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="45288-148">ProfileName</span><span class="sxs-lookup"><span data-stu-id="45288-148">ProfileName</span></span>|<span data-ttu-id="45288-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-149">xs:string</span></span>|<span data-ttu-id="45288-150">このイベントを生成した追跡プロファイルの名前</span><span class="sxs-lookup"><span data-stu-id="45288-150">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="45288-151">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="45288-151">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="45288-152">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-152">xs:string</span></span>|<span data-ttu-id="45288-153">ワークフロー定義 ID</span><span class="sxs-lookup"><span data-stu-id="45288-153">The workflow definition id</span></span>|  
|<span data-ttu-id="45288-154">AppDomain</span><span class="sxs-lookup"><span data-stu-id="45288-154">AppDomain</span></span>|<span data-ttu-id="45288-155">xs:string</span><span class="sxs-lookup"><span data-stu-id="45288-155">xs:string</span></span>|<span data-ttu-id="45288-156">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="45288-156">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

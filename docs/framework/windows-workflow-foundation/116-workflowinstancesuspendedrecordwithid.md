---
title: 116 - WorkflowInstanceSuspendedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38232c03-6139-4494-a020-79bc83eb9dce
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59b77e2fac36dea3afce77a74e0ccacb432a2ada
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="116---workflowinstancesuspendedrecordwithid"></a><span data-ttu-id="b357f-102">116 - WorkflowInstanceSuspendedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="b357f-102">116 - WorkflowInstanceSuspendedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="b357f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b357f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b357f-104">ID</span><span class="sxs-lookup"><span data-stu-id="b357f-104">ID</span></span>|<span data-ttu-id="b357f-105">116</span><span class="sxs-lookup"><span data-stu-id="b357f-105">116</span></span>|  
|<span data-ttu-id="b357f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b357f-106">Keywords</span></span>|<span data-ttu-id="b357f-107">HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="b357f-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="b357f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b357f-108">Level</span></span>|<span data-ttu-id="b357f-109">情報</span><span class="sxs-lookup"><span data-stu-id="b357f-109">Information</span></span>|  
|<span data-ttu-id="b357f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b357f-110">Channel</span></span>|<span data-ttu-id="b357f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b357f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b357f-112">説明</span><span class="sxs-lookup"><span data-stu-id="b357f-112">Description</span></span>  
 <span data-ttu-id="b357f-113">このイベントは、ワークフロー インスタンスが WorkflowInstanceSuspended Record を生成したときに、ETW 追跡参加要素によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="b357f-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceSuspended Record.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b357f-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b357f-114">Message</span></span>  
 <span data-ttu-id="b357f-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="b357f-115">TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="b357f-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b357f-116">Details</span></span>  
  
|<span data-ttu-id="b357f-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b357f-117">Data Item Name</span></span>|<span data-ttu-id="b357f-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b357f-118">Data Item Type</span></span>|<span data-ttu-id="b357f-119">説明</span><span class="sxs-lookup"><span data-stu-id="b357f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b357f-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b357f-120">InstanceId</span></span>|<span data-ttu-id="b357f-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="b357f-121">xs:GUID</span></span>|<span data-ttu-id="b357f-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="b357f-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b357f-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="b357f-123">RecordNumber</span></span>|<span data-ttu-id="b357f-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="b357f-124">xs:long</span></span>|<span data-ttu-id="b357f-125">生成されたレコードのシーケンス番号</span><span class="sxs-lookup"><span data-stu-id="b357f-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="b357f-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="b357f-126">EventTime</span></span>|<span data-ttu-id="b357f-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="b357f-127">xs:dateTime</span></span>|<span data-ttu-id="b357f-128">イベントの生成時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="b357f-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="b357f-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b357f-129">ActivityDefinitionId</span></span>|<span data-ttu-id="b357f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b357f-130">xs:string</span></span>|<span data-ttu-id="b357f-131">ワークフローのルート アクティビティの名前</span><span class="sxs-lookup"><span data-stu-id="b357f-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="b357f-132">状態</span><span class="sxs-lookup"><span data-stu-id="b357f-132">State</span></span>|<span data-ttu-id="b357f-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="b357f-133">xs:string</span></span>|<span data-ttu-id="b357f-134">ワークフローの現在の状態。</span><span class="sxs-lookup"><span data-stu-id="b357f-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="b357f-135">コメント</span><span class="sxs-lookup"><span data-stu-id="b357f-135">Annotations</span></span>|<span data-ttu-id="b357f-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="b357f-136">xs:string</span></span>|<span data-ttu-id="b357f-137">このイベントに追加された注釈。</span><span class="sxs-lookup"><span data-stu-id="b357f-137">The annotations that were added to this event.</span></span> <span data-ttu-id="b357f-138">形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。</span><span class="sxs-lookup"><span data-stu-id="b357f-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="b357f-139">注釈が指定されていない場合、文字列が含まれる\<項目/>。</span><span class="sxs-lookup"><span data-stu-id="b357f-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="b357f-140">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。</span><span class="sxs-lookup"><span data-stu-id="b357f-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="b357f-141">イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。</span><span class="sxs-lookup"><span data-stu-id="b357f-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="b357f-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="b357f-142">ProfileName</span></span>|<span data-ttu-id="b357f-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="b357f-143">xs:string</span></span>|<span data-ttu-id="b357f-144">このイベントを生成した追跡プロファイルの名前</span><span class="sxs-lookup"><span data-stu-id="b357f-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="b357f-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="b357f-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="b357f-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="b357f-146">xs:string</span></span>|<span data-ttu-id="b357f-147">ワークフロー定義 ID</span><span class="sxs-lookup"><span data-stu-id="b357f-147">The workflow definition id</span></span>|  
|<span data-ttu-id="b357f-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b357f-148">AppDomain</span></span>|<span data-ttu-id="b357f-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="b357f-149">xs:string</span></span>|<span data-ttu-id="b357f-150">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b357f-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

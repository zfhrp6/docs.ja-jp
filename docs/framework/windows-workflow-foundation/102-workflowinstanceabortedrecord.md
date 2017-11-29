---
title: 102 - WorkflowInstanceAbortedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f238ff792d2b39bb522822d78012a79747f9196c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="102---workflowinstanceabortedrecord"></a><span data-ttu-id="872f2-102">102 - WorkflowInstanceAbortedRecord</span><span class="sxs-lookup"><span data-stu-id="872f2-102">102 - WorkflowInstanceAbortedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="872f2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="872f2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="872f2-104">ID</span><span class="sxs-lookup"><span data-stu-id="872f2-104">Id</span></span>|<span data-ttu-id="872f2-105">102</span><span class="sxs-lookup"><span data-stu-id="872f2-105">102</span></span>|  
|<span data-ttu-id="872f2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="872f2-106">Keywords</span></span>|<span data-ttu-id="872f2-107">EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="872f2-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="872f2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="872f2-108">Level</span></span>|<span data-ttu-id="872f2-109">警告</span><span class="sxs-lookup"><span data-stu-id="872f2-109">Warning</span></span>|  
|<span data-ttu-id="872f2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="872f2-110">Channel</span></span>|<span data-ttu-id="872f2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="872f2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="872f2-112">説明</span><span class="sxs-lookup"><span data-stu-id="872f2-112">Description</span></span>  
 <span data-ttu-id="872f2-113">このイベントは、ワークフロー インスタンスが WorkflowInstanceAbortedRecord を生成したときに、ETW 追跡参加要素によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="872f2-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="872f2-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="872f2-114">Message</span></span>  
 <span data-ttu-id="872f2-115">TrackRecord = WorkflowInstanceAbortedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="872f2-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="872f2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="872f2-116">Details</span></span>  
  
|<span data-ttu-id="872f2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="872f2-117">Data Item Name</span></span>|<span data-ttu-id="872f2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="872f2-118">Data Item Type</span></span>|<span data-ttu-id="872f2-119">説明</span><span class="sxs-lookup"><span data-stu-id="872f2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="872f2-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="872f2-120">InstanceId</span></span>|<span data-ttu-id="872f2-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="872f2-121">xs:GUID</span></span>|<span data-ttu-id="872f2-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="872f2-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="872f2-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="872f2-123">RecordNumber</span></span>|<span data-ttu-id="872f2-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="872f2-124">xs:long</span></span>|<span data-ttu-id="872f2-125">生成されたレコードのシーケンス番号</span><span class="sxs-lookup"><span data-stu-id="872f2-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="872f2-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="872f2-126">EventTime</span></span>|<span data-ttu-id="872f2-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="872f2-127">xs:dateTime</span></span>|<span data-ttu-id="872f2-128">イベントの生成時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="872f2-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="872f2-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="872f2-129">ActivityDefinitionId</span></span>|<span data-ttu-id="872f2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="872f2-130">xs:string</span></span>|<span data-ttu-id="872f2-131">ワークフローのルート アクティビティの名前</span><span class="sxs-lookup"><span data-stu-id="872f2-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="872f2-132">理由</span><span class="sxs-lookup"><span data-stu-id="872f2-132">Reason</span></span>|<span data-ttu-id="872f2-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="872f2-133">xs:string</span></span>|<span data-ttu-id="872f2-134">ワークフローが中止された理由</span><span class="sxs-lookup"><span data-stu-id="872f2-134">The reason the workflow was aborted</span></span>|  
|<span data-ttu-id="872f2-135">コメント</span><span class="sxs-lookup"><span data-stu-id="872f2-135">Annotations</span></span>|<span data-ttu-id="872f2-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="872f2-136">xs:string</span></span>|<span data-ttu-id="872f2-137">このイベントに追加された注釈。</span><span class="sxs-lookup"><span data-stu-id="872f2-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="872f2-138">形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。</span><span class="sxs-lookup"><span data-stu-id="872f2-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="872f2-139">注釈が指定されていない場合、文字列が含まれる\<項目/>。</span><span class="sxs-lookup"><span data-stu-id="872f2-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="872f2-140">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。</span><span class="sxs-lookup"><span data-stu-id="872f2-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="872f2-141">イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。</span><span class="sxs-lookup"><span data-stu-id="872f2-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="872f2-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="872f2-142">ProfileName</span></span>|<span data-ttu-id="872f2-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="872f2-143">xs:string</span></span>|<span data-ttu-id="872f2-144">このイベントを生成した追跡プロファイルの名前</span><span class="sxs-lookup"><span data-stu-id="872f2-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="872f2-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="872f2-145">HostReference</span></span>|<span data-ttu-id="872f2-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="872f2-146">xs:string</span></span>|<span data-ttu-id="872f2-147">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="872f2-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="872f2-148">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="872f2-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="872f2-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="872f2-149">AppDomain</span></span>|<span data-ttu-id="872f2-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="872f2-150">xs:string</span></span>|<span data-ttu-id="872f2-151">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="872f2-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

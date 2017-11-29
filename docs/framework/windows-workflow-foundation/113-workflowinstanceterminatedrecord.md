---
title: 113 - WorkflowInstanceTerminatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f53204ee-4ea2-45e1-8859-e86d07305efd
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e8b6f6c08b8bb3da49dc0e97cb271257ad9ee48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="113---workflowinstanceterminatedrecord"></a><span data-ttu-id="86fb5-102">113 - WorkflowInstanceTerminatedRecord</span><span class="sxs-lookup"><span data-stu-id="86fb5-102">113 - WorkflowInstanceTerminatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="86fb5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="86fb5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86fb5-104">ID</span><span class="sxs-lookup"><span data-stu-id="86fb5-104">Id</span></span>|<span data-ttu-id="86fb5-105">113</span><span class="sxs-lookup"><span data-stu-id="86fb5-105">113</span></span>|  
|<span data-ttu-id="86fb5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="86fb5-106">Keywords</span></span>|<span data-ttu-id="86fb5-107">EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking</span><span class="sxs-lookup"><span data-stu-id="86fb5-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="86fb5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="86fb5-108">Level</span></span>|<span data-ttu-id="86fb5-109">Error</span><span class="sxs-lookup"><span data-stu-id="86fb5-109">Error</span></span>|  
|<span data-ttu-id="86fb5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="86fb5-110">Channel</span></span>|<span data-ttu-id="86fb5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="86fb5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86fb5-112">説明</span><span class="sxs-lookup"><span data-stu-id="86fb5-112">Description</span></span>  
 <span data-ttu-id="86fb5-113">このイベントは、ワークフロー インスタンスが WorkflowInstanceTerminatedRecord を生成したときに、ETW 追跡参加要素によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="86fb5-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86fb5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="86fb5-114">Message</span></span>  
 <span data-ttu-id="86fb5-115">TrackRecord = WorkflowInstanceTerminatedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="86fb5-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="86fb5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="86fb5-116">Details</span></span>  
  
|<span data-ttu-id="86fb5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="86fb5-117">Data Item Name</span></span>|<span data-ttu-id="86fb5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="86fb5-118">Data Item Type</span></span>|<span data-ttu-id="86fb5-119">説明</span><span class="sxs-lookup"><span data-stu-id="86fb5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86fb5-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="86fb5-120">InstanceId</span></span>|<span data-ttu-id="86fb5-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="86fb5-121">xs:GUID</span></span>|<span data-ttu-id="86fb5-122">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="86fb5-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="86fb5-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="86fb5-123">RecordNumber</span></span>|<span data-ttu-id="86fb5-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="86fb5-124">xs:long</span></span>|<span data-ttu-id="86fb5-125">生成されたレコードのシーケンス番号</span><span class="sxs-lookup"><span data-stu-id="86fb5-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="86fb5-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="86fb5-126">EventTime</span></span>|<span data-ttu-id="86fb5-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="86fb5-127">xs:dateTime</span></span>|<span data-ttu-id="86fb5-128">イベントの生成時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="86fb5-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="86fb5-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="86fb5-129">ActivityDefinitionId</span></span>|<span data-ttu-id="86fb5-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="86fb5-130">xs:string</span></span>|<span data-ttu-id="86fb5-131">ワークフローのルート アクティビティの名前</span><span class="sxs-lookup"><span data-stu-id="86fb5-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="86fb5-132">理由</span><span class="sxs-lookup"><span data-stu-id="86fb5-132">Reason</span></span>|<span data-ttu-id="86fb5-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="86fb5-133">xs:string</span></span>|<span data-ttu-id="86fb5-134">ワークフローの終了の理由</span><span class="sxs-lookup"><span data-stu-id="86fb5-134">The reason the workflow was terminated</span></span>|  
|<span data-ttu-id="86fb5-135">コメント</span><span class="sxs-lookup"><span data-stu-id="86fb5-135">Annotations</span></span>|<span data-ttu-id="86fb5-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="86fb5-136">xs:string</span></span>|<span data-ttu-id="86fb5-137">このイベントに追加された注釈。</span><span class="sxs-lookup"><span data-stu-id="86fb5-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="86fb5-138">形式で xml 要素に値が格納されている\<項目 >\<項目名 ="annotationName"type="System.String"> annotationValue\<項目/>\</items >。</span><span class="sxs-lookup"><span data-stu-id="86fb5-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="86fb5-139">注釈が指定されていない場合、文字列が含まれる\<項目/>。</span><span class="sxs-lookup"><span data-stu-id="86fb5-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="86fb5-140">ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。</span><span class="sxs-lookup"><span data-stu-id="86fb5-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="86fb5-141">イベントのサイズが ETW の制限を超えるかどうかは、注釈を削除しを持つ注釈の値を置き換えることによって、イベントが切り捨てられ\<項目 >.\</items >。</span><span class="sxs-lookup"><span data-stu-id="86fb5-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="86fb5-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="86fb5-142">ProfileName</span></span>|<span data-ttu-id="86fb5-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="86fb5-143">xs:string</span></span>|<span data-ttu-id="86fb5-144">このイベントを生成した追跡プロファイルの名前</span><span class="sxs-lookup"><span data-stu-id="86fb5-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="86fb5-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="86fb5-145">HostReference</span></span>|<span data-ttu-id="86fb5-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="86fb5-146">xs:string</span></span>|<span data-ttu-id="86fb5-147">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="86fb5-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="86fb5-148">その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="86fb5-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="86fb5-149">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86fb5-149">AppDomain</span></span>|<span data-ttu-id="86fb5-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="86fb5-150">xs:string</span></span>|<span data-ttu-id="86fb5-151">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="86fb5-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

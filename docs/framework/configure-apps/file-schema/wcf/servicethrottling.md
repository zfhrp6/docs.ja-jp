---
title: '&lt;serviceThrottling&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ba0f3a442e3598322f223be63b64a811c8f785a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicethrottlinggt"></a><span data-ttu-id="37170-102">&lt;serviceThrottling&gt;</span><span class="sxs-lookup"><span data-stu-id="37170-102">&lt;serviceThrottling&gt;</span></span>
<span data-ttu-id="37170-103">WCF (Windows Communication Foundation) サービスの調整機構を指定します。</span><span class="sxs-lookup"><span data-stu-id="37170-103">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="37170-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="37170-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="37170-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="37170-105">\<behaviors></span></span>  
<span data-ttu-id="37170-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="37170-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="37170-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="37170-107">\<behavior></span></span>  
<span data-ttu-id="37170-108">\<serviceThrottling ></span><span class="sxs-lookup"><span data-stu-id="37170-108">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37170-109">構文</span><span class="sxs-lookup"><span data-stu-id="37170-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"  
    maxConcurrentInstances="Integer"  
    maxConcurrentSessions="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37170-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="37170-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37170-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="37170-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37170-112">属性</span><span class="sxs-lookup"><span data-stu-id="37170-112">Attributes</span></span>  
  
|<span data-ttu-id="37170-113">属性</span><span class="sxs-lookup"><span data-stu-id="37170-113">Attribute</span></span>|<span data-ttu-id="37170-114">説明</span><span class="sxs-lookup"><span data-stu-id="37170-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37170-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="37170-115">maxConcurrentCalls</span></span>|<span data-ttu-id="37170-116"><xref:System.ServiceModel.ServiceHost> で同時に処理できるメッセージ数を制限する正の整数。</span><span class="sxs-lookup"><span data-stu-id="37170-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="37170-117">制限を超えた呼び出しはキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="37170-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="37170-118">この値を 0 に設定することは、Int32.MaxValue に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="37170-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="37170-119">既定値は 16 x プロセッサ数です。</span><span class="sxs-lookup"><span data-stu-id="37170-119">The default is 16 * processor count.</span></span>|  
|<span data-ttu-id="37170-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="37170-120">maxConcurrentInstances</span></span>|<span data-ttu-id="37170-121"><xref:System.ServiceModel.InstanceContext> で同時に実行できる <xref:System.ServiceModel.ServiceHost> オブジェクト数を制限する正の整数。</span><span class="sxs-lookup"><span data-stu-id="37170-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="37170-122">追加インスタンスの作成要求は、キューに置かれ、制限下のスロットが利用できるようになったときに完了されます。</span><span class="sxs-lookup"><span data-stu-id="37170-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="37170-123">既定値は maxConcurrentSessions と MaxConcurrentCalls の合計です。</span><span class="sxs-lookup"><span data-stu-id="37170-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="37170-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="37170-124">maxConcurrentSessions</span></span>|<span data-ttu-id="37170-125"><xref:System.ServiceModel.ServiceHost> オブジェクトが受け入れることのできるセッション数を制限する正の整数。</span><span class="sxs-lookup"><span data-stu-id="37170-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="37170-126">サービスは制限を超える接続を受け入れますが、制限内のチャネルだけがアクティブです (メッセージがチャネルから読み取られます)。</span><span class="sxs-lookup"><span data-stu-id="37170-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="37170-127">この値を 0 に設定することは、Int32.MaxValue に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="37170-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="37170-128">既定値は 100 x プロセッサ数です。</span><span class="sxs-lookup"><span data-stu-id="37170-128">The default is 100 * processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37170-129">子要素</span><span class="sxs-lookup"><span data-stu-id="37170-129">Child Elements</span></span>  
 <span data-ttu-id="37170-130">なし。</span><span class="sxs-lookup"><span data-stu-id="37170-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37170-131">親要素</span><span class="sxs-lookup"><span data-stu-id="37170-131">Parent Elements</span></span>  
  
|<span data-ttu-id="37170-132">要素</span><span class="sxs-lookup"><span data-stu-id="37170-132">Element</span></span>|<span data-ttu-id="37170-133">説明</span><span class="sxs-lookup"><span data-stu-id="37170-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37170-134">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="37170-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="37170-135">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="37170-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37170-136">コメント</span><span class="sxs-lookup"><span data-stu-id="37170-136">Remarks</span></span>  
 <span data-ttu-id="37170-137">調整コントロールは、同時呼び出し、同時インスタンス、または同時セッションの数を制限して、リソースの過剰消費を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="37170-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="37170-138">属性の値に到達するたびにトレースが出力されます。</span><span class="sxs-lookup"><span data-stu-id="37170-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="37170-139">最初のトレースは警告として出力されます。</span><span class="sxs-lookup"><span data-stu-id="37170-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37170-140">例</span><span class="sxs-lookup"><span data-stu-id="37170-140">Example</span></span>  
 <span data-ttu-id="37170-141">次の構成例では、サービスで同時呼び出しの最大数を 2 に、同時インスタンスの最大数を 10 に制限することを指定しています。</span><span class="sxs-lookup"><span data-stu-id="37170-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="37170-142">この例を実行する詳細な例についてを参照してください。[スロットル](../../../../../docs/framework/wcf/samples/throttling.md)です。</span><span class="sxs-lookup"><span data-stu-id="37170-142">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37170-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="37170-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [<span data-ttu-id="37170-144">WCF サービスのパフォーマンスを制御する ServiceThrottlingBehavior の使用</span><span class="sxs-lookup"><span data-stu-id="37170-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)

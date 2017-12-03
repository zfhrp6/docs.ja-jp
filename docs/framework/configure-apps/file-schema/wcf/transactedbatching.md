---
title: '&lt;transactedBatching&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d89b6f63f71d0ce5c3f757af7a1af347d875f333
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="7f303-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="7f303-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="7f303-103">受信操作でトランザクション バッチがサポートされるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f303-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="7f303-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7f303-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f303-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="7f303-105">\<behaviors></span></span>  
<span data-ttu-id="7f303-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f303-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7f303-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7f303-107">\<behavior></span></span>  
<span data-ttu-id="7f303-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="7f303-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f303-109">構文</span><span class="sxs-lookup"><span data-stu-id="7f303-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f303-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7f303-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f303-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f303-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f303-112">属性</span><span class="sxs-lookup"><span data-stu-id="7f303-112">Attributes</span></span>  
  
|<span data-ttu-id="7f303-113">属性</span><span class="sxs-lookup"><span data-stu-id="7f303-113">Attribute</span></span>|<span data-ttu-id="7f303-114">説明</span><span class="sxs-lookup"><span data-stu-id="7f303-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="7f303-115">1 回のトランザクションでまとめてバッチ処理できる受信操作の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="7f303-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="7f303-116">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="7f303-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f303-117">子要素</span><span class="sxs-lookup"><span data-stu-id="7f303-117">Child Elements</span></span>  
 <span data-ttu-id="7f303-118">なし。</span><span class="sxs-lookup"><span data-stu-id="7f303-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f303-119">親要素</span><span class="sxs-lookup"><span data-stu-id="7f303-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f303-120">要素</span><span class="sxs-lookup"><span data-stu-id="7f303-120">Element</span></span>|<span data-ttu-id="7f303-121">説明</span><span class="sxs-lookup"><span data-stu-id="7f303-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f303-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7f303-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7f303-123">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f303-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f303-124">コメント</span><span class="sxs-lookup"><span data-stu-id="7f303-124">Remarks</span></span>  
 <span data-ttu-id="7f303-125">トランザクション バッチで構成されるトランスポートは、複数の受信操作を 1 つのトランザクションにバッチ処理しようとします。</span><span class="sxs-lookup"><span data-stu-id="7f303-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="7f303-126">これを実行することにより、受信操作のたびに行うトランザクションの作成とそのコミットの比較的高いコストを回避できます。</span><span class="sxs-lookup"><span data-stu-id="7f303-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f303-127">例</span><span class="sxs-lookup"><span data-stu-id="7f303-127">Example</span></span>  
 <span data-ttu-id="7f303-128">構成ファイル内でサービスにトランザクション バッチ動作を追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7f303-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
        </baseAddresses>  
      </host>  
  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />  
  
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="endpointBehavior">  
        <transactedBatching maxBatchSize="10" />  
      </behavior>  
    </endpointBehaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f303-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f303-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>

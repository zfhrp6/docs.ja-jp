---
title: '&lt;transactedBatching&gt;'
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: f0cf0b78ddcbd3214e30a36ce7641d115275a265
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749713"
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="6ab70-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="6ab70-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="6ab70-103">受信操作でトランザクション バッチがサポートされるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ab70-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="6ab70-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6ab70-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6ab70-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="6ab70-105">\<behaviors></span></span>  
<span data-ttu-id="6ab70-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6ab70-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6ab70-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6ab70-107">\<behavior></span></span>  
<span data-ttu-id="6ab70-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="6ab70-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab70-109">構文</span><span class="sxs-lookup"><span data-stu-id="6ab70-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ab70-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6ab70-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6ab70-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ab70-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ab70-112">属性</span><span class="sxs-lookup"><span data-stu-id="6ab70-112">Attributes</span></span>  
  
|<span data-ttu-id="6ab70-113">属性</span><span class="sxs-lookup"><span data-stu-id="6ab70-113">Attribute</span></span>|<span data-ttu-id="6ab70-114">説明</span><span class="sxs-lookup"><span data-stu-id="6ab70-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="6ab70-115">1 回のトランザクションでまとめてバッチ処理できる受信操作の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="6ab70-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="6ab70-116">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="6ab70-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ab70-117">子要素</span><span class="sxs-lookup"><span data-stu-id="6ab70-117">Child Elements</span></span>  
 <span data-ttu-id="6ab70-118">なし。</span><span class="sxs-lookup"><span data-stu-id="6ab70-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ab70-119">親要素</span><span class="sxs-lookup"><span data-stu-id="6ab70-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6ab70-120">要素</span><span class="sxs-lookup"><span data-stu-id="6ab70-120">Element</span></span>|<span data-ttu-id="6ab70-121">説明</span><span class="sxs-lookup"><span data-stu-id="6ab70-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ab70-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6ab70-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="6ab70-123">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ab70-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ab70-124">コメント</span><span class="sxs-lookup"><span data-stu-id="6ab70-124">Remarks</span></span>  
 <span data-ttu-id="6ab70-125">トランザクション バッチで構成されるトランスポートは、複数の受信操作を 1 つのトランザクションにバッチ処理しようとします。</span><span class="sxs-lookup"><span data-stu-id="6ab70-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="6ab70-126">これを実行することにより、受信操作のたびに行うトランザクションの作成とそのコミットの比較的高いコストを回避できます。</span><span class="sxs-lookup"><span data-stu-id="6ab70-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ab70-127">例</span><span class="sxs-lookup"><span data-stu-id="6ab70-127">Example</span></span>  
 <span data-ttu-id="6ab70-128">構成ファイル内でサービスにトランザクション バッチ動作を追加する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="6ab70-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ab70-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ab70-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>

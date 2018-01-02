---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a997ddffa2267cdeb9e54bb98d4122db254104d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="d9f32-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="d9f32-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="d9f32-103">エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。</span><span class="sxs-lookup"><span data-stu-id="d9f32-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="d9f32-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d9f32-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9f32-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="d9f32-105">\<behaviors></span></span>  
<span data-ttu-id="d9f32-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d9f32-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d9f32-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="d9f32-107">\<behavior></span></span>  
<span data-ttu-id="d9f32-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d9f32-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f32-109">構文</span><span class="sxs-lookup"><span data-stu-id="d9f32-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9f32-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d9f32-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d9f32-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9f32-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9f32-112">属性</span><span class="sxs-lookup"><span data-stu-id="d9f32-112">Attributes</span></span>  
  
|<span data-ttu-id="d9f32-113">属性</span><span class="sxs-lookup"><span data-stu-id="d9f32-113">Attribute</span></span>|<span data-ttu-id="d9f32-114">説明</span><span class="sxs-lookup"><span data-stu-id="d9f32-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9f32-115">enabled</span><span class="sxs-lookup"><span data-stu-id="d9f32-115">enabled</span></span>|<span data-ttu-id="d9f32-116">探索可能性をこのエンドポイントで有効にするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="d9f32-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="d9f32-117">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="d9f32-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9f32-118">子要素</span><span class="sxs-lookup"><span data-stu-id="d9f32-118">Child Elements</span></span>  
  
|<span data-ttu-id="d9f32-119">要素</span><span class="sxs-lookup"><span data-stu-id="d9f32-119">Element</span></span>|<span data-ttu-id="d9f32-120">説明</span><span class="sxs-lookup"><span data-stu-id="d9f32-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9f32-121">\<スコープ ></span><span class="sxs-lookup"><span data-stu-id="d9f32-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="d9f32-122">エンドポイントのスコープ URI のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d9f32-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="d9f32-123">複数の URI を 1 つのエンドポイントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d9f32-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="d9f32-124">[\<拡張機能 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [の\<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="d9f32-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="d9f32-125">エンドポイントで発行されるカスタム メタデータを指定できる、XML 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d9f32-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="d9f32-126">\<種類 ></span><span class="sxs-lookup"><span data-stu-id="d9f32-126">\<types></span></span>|<span data-ttu-id="d9f32-127">検索するインターフェイスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="d9f32-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9f32-128">親要素</span><span class="sxs-lookup"><span data-stu-id="d9f32-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d9f32-129">要素</span><span class="sxs-lookup"><span data-stu-id="d9f32-129">Element</span></span>|<span data-ttu-id="d9f32-130">説明</span><span class="sxs-lookup"><span data-stu-id="d9f32-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9f32-131">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="d9f32-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d9f32-132">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="d9f32-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="d9f32-133">コメント</span><span class="sxs-lookup"><span data-stu-id="d9f32-133">Remarks</span></span>  
 <span data-ttu-id="d9f32-134">エンドポイントの動作構成に追加し、`enabled` 属性を `true` に設定すると、この構成要素の探索可能性が有効になります。</span><span class="sxs-lookup"><span data-stu-id="d9f32-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="d9f32-135">さらに、使用することができます、 [\<スコープ >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)子要素のカスタム スコープ Uri、クエリ中にサービス エンドポイントのフィルター処理に使用できるを指定するだけでなく[\<拡張子 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md)子要素のカスタム メタデータ (EPR、ContractTypeName、必要のある、スコープおよび ListenURI) は、標準の探索可能メタデータと共に発行する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="d9f32-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="d9f32-136">この構成要素が依存、 [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)探索可能性のサービス レベルの制御を提供する要素。</span><span class="sxs-lookup"><span data-stu-id="d9f32-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="d9f32-137">場合、この要素の設定は無視されます、つまり[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)は構成に存在しません。</span><span class="sxs-lookup"><span data-stu-id="d9f32-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9f32-138">例</span><span class="sxs-lookup"><span data-stu-id="d9f32-138">Example</span></span>  
 <span data-ttu-id="d9f32-139">次の構成例では、フィルターのスコープと、エンドポイントで発行される拡張メタデータを指定しています。</span><span class="sxs-lookup"><span data-stu-id="d9f32-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9f32-140">参照</span><span class="sxs-lookup"><span data-stu-id="d9f32-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

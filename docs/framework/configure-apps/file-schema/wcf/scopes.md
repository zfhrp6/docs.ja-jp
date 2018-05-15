---
title: '&lt;スコープ&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7e2dda0d0def4d1f90bf1b4dbf54f18983355222
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltscopesgt"></a><span data-ttu-id="1f042-102">&lt;スコープ&gt;</span><span class="sxs-lookup"><span data-stu-id="1f042-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="1f042-103">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を指定する構成要素のコレクションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="1f042-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="1f042-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1f042-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1f042-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="1f042-105">\<behaviors></span></span>  
<span data-ttu-id="1f042-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1f042-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1f042-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1f042-107">\<behavior></span></span>  
<span data-ttu-id="1f042-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="1f042-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="1f042-109">\<スコープ ></span><span class="sxs-lookup"><span data-stu-id="1f042-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f042-110">構文</span><span class="sxs-lookup"><span data-stu-id="1f042-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f042-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1f042-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1f042-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f042-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f042-113">属性</span><span class="sxs-lookup"><span data-stu-id="1f042-113">Attributes</span></span>  
 <span data-ttu-id="1f042-114">なし。</span><span class="sxs-lookup"><span data-stu-id="1f042-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f042-115">子要素</span><span class="sxs-lookup"><span data-stu-id="1f042-115">Child Elements</span></span>  
  
|<span data-ttu-id="1f042-116">属性</span><span class="sxs-lookup"><span data-stu-id="1f042-116">Attribute</span></span>|<span data-ttu-id="1f042-117">説明</span><span class="sxs-lookup"><span data-stu-id="1f042-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="1f042-118">\<add></span><span class="sxs-lookup"><span data-stu-id="1f042-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="1f042-119">サービス検索の一致条件に使用できるエンドポイントのスコープ情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="1f042-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f042-120">親要素</span><span class="sxs-lookup"><span data-stu-id="1f042-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1f042-121">要素</span><span class="sxs-lookup"><span data-stu-id="1f042-121">Element</span></span>|<span data-ttu-id="1f042-122">説明</span><span class="sxs-lookup"><span data-stu-id="1f042-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f042-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="1f042-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="1f042-124">エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。</span><span class="sxs-lookup"><span data-stu-id="1f042-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f042-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f042-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

---
title: "&lt;スコープ&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f198811483edb8a7be882588c38b1f3942f8bb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="54357-102">&lt;スコープ&gt;</span><span class="sxs-lookup"><span data-stu-id="54357-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="54357-103">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を指定する構成要素のコレクションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="54357-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="54357-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="54357-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="54357-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="54357-105">\<behaviors></span></span>  
<span data-ttu-id="54357-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="54357-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="54357-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="54357-107">\<behavior></span></span>  
<span data-ttu-id="54357-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="54357-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="54357-109">\<スコープ ></span><span class="sxs-lookup"><span data-stu-id="54357-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54357-110">構文</span><span class="sxs-lookup"><span data-stu-id="54357-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54357-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="54357-111">Attributes and Elements</span></span>  
 <span data-ttu-id="54357-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="54357-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54357-113">属性</span><span class="sxs-lookup"><span data-stu-id="54357-113">Attributes</span></span>  
 <span data-ttu-id="54357-114">なし。</span><span class="sxs-lookup"><span data-stu-id="54357-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54357-115">子要素</span><span class="sxs-lookup"><span data-stu-id="54357-115">Child Elements</span></span>  
  
|<span data-ttu-id="54357-116">属性</span><span class="sxs-lookup"><span data-stu-id="54357-116">Attribute</span></span>|<span data-ttu-id="54357-117">説明</span><span class="sxs-lookup"><span data-stu-id="54357-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="54357-118">\<add></span><span class="sxs-lookup"><span data-stu-id="54357-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="54357-119">サービス検索の一致条件に使用できるエンドポイントのスコープ情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="54357-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54357-120">親要素</span><span class="sxs-lookup"><span data-stu-id="54357-120">Parent Elements</span></span>  
  
|<span data-ttu-id="54357-121">要素</span><span class="sxs-lookup"><span data-stu-id="54357-121">Element</span></span>|<span data-ttu-id="54357-122">説明</span><span class="sxs-lookup"><span data-stu-id="54357-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54357-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="54357-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="54357-124">エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。</span><span class="sxs-lookup"><span data-stu-id="54357-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54357-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="54357-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

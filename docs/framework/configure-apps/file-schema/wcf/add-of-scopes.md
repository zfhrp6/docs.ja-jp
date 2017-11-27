---
title: "&lt;scopes&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c720d99a5abee00eeb52f91586503e0a8a89027b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="7ed9c-102">&lt;scopes&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="7ed9c-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="7ed9c-103">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を追加します。</span><span class="sxs-lookup"><span data-stu-id="7ed9c-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="7ed9c-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ed9c-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-105">\<behaviors></span></span>  
<span data-ttu-id="7ed9c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7ed9c-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-107">\<behavior></span></span>  
<span data-ttu-id="7ed9c-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="7ed9c-109">\<スコープ ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-109">\<scopes></span></span>  
<span data-ttu-id="7ed9c-110">\<add></span><span class="sxs-lookup"><span data-stu-id="7ed9c-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed9c-111">構文</span><span class="sxs-lookup"><span data-stu-id="7ed9c-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ed9c-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7ed9c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7ed9c-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ed9c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ed9c-114">属性</span><span class="sxs-lookup"><span data-stu-id="7ed9c-114">Attributes</span></span>  
  
|<span data-ttu-id="7ed9c-115">属性</span><span class="sxs-lookup"><span data-stu-id="7ed9c-115">Attribute</span></span>|<span data-ttu-id="7ed9c-116">説明</span><span class="sxs-lookup"><span data-stu-id="7ed9c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ed9c-117">スコープ</span><span class="sxs-lookup"><span data-stu-id="7ed9c-117">scope</span></span>|<span data-ttu-id="7ed9c-118">サービス検索の一致条件に使用できるエンドポイントのスコープ情報を格納する URI。</span><span class="sxs-lookup"><span data-stu-id="7ed9c-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ed9c-119">子要素</span><span class="sxs-lookup"><span data-stu-id="7ed9c-119">Child Elements</span></span>  
 <span data-ttu-id="7ed9c-120">なし。</span><span class="sxs-lookup"><span data-stu-id="7ed9c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ed9c-121">親要素</span><span class="sxs-lookup"><span data-stu-id="7ed9c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7ed9c-122">要素</span><span class="sxs-lookup"><span data-stu-id="7ed9c-122">Element</span></span>|<span data-ttu-id="7ed9c-123">説明</span><span class="sxs-lookup"><span data-stu-id="7ed9c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ed9c-124">\<スコープ ></span><span class="sxs-lookup"><span data-stu-id="7ed9c-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="7ed9c-125">クエリの実行中に、サービス エンドポイントのフィルター処理に使用できるカスタム スコープ URI を指定する構成要素のコレクションを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="7ed9c-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ed9c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ed9c-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

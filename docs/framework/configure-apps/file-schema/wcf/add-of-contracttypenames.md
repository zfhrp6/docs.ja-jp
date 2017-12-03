---
title: "&lt;contractTypeNames&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d7cfcb8217bbf157af4ba2893773b180f0a9f28
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltcontracttypenamesgt"></a><span data-ttu-id="0dfbd-102">&lt;contractTypeNames&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="0dfbd-102">&lt;add&gt; of &lt;contractTypeNames&gt;</span></span>
<span data-ttu-id="0dfbd-103">検索対象サービスのコントラクト名と、サービスを検索するときに一般的に使用される条件を指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-103">A configuration element that specifies the contract name of the services being searched for, and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="0dfbd-104">複数のコントラクト名が指定されると、すべてのコントラクトに一致するサービス エンドポイントのみが適用されます。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-104">If more than one contract name is specified, only service endpoints matching ALL contracts will reply.</span></span> <span data-ttu-id="0dfbd-105">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] では、1 つのエンドポイントでサポートされるのは 1 つのコントラクトだけであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-105">Note that in [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], an endpoint can only support one contract.</span></span>  
  
 <span data-ttu-id="0dfbd-106">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0dfbd-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="0dfbd-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="0dfbd-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dfbd-108">構文</span><span class="sxs-lookup"><span data-stu-id="0dfbd-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <dynamicEndpoint>           <standardEndpoint>             <discoveryClientSettings discoveryEndpoint="String" >               <findCriteria duration="TimeSpan"                  maxResults="Integer"                   scopeMatchBy="Uri" >                  <contractTypeNames>                     <add name="String" namespace="String" />                  <contractTypeNames>                  <extensions />                  <scopes>                    <add scope="URI"/>                  </scopes>               </findCriteria>             </discoveryClientSettings>          <standardEndpoint>       </dynamicEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dfbd-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0dfbd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0dfbd-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dfbd-111">属性</span><span class="sxs-lookup"><span data-stu-id="0dfbd-111">Attributes</span></span>  
  
|<span data-ttu-id="0dfbd-112">属性</span><span class="sxs-lookup"><span data-stu-id="0dfbd-112">Attribute</span></span>|<span data-ttu-id="0dfbd-113">説明</span><span class="sxs-lookup"><span data-stu-id="0dfbd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0dfbd-114">name</span><span class="sxs-lookup"><span data-stu-id="0dfbd-114">name</span></span>|<span data-ttu-id="0dfbd-115">コントラクト型の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-115">A string that specifies the name of the contract type.</span></span>|  
|<span data-ttu-id="0dfbd-116">namespace</span><span class="sxs-lookup"><span data-stu-id="0dfbd-116">namespace</span></span>|<span data-ttu-id="0dfbd-117">コントラクト型の名前空間を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-117">A string that specifies the namespace of the contract type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dfbd-118">子要素</span><span class="sxs-lookup"><span data-stu-id="0dfbd-118">Child Elements</span></span>  
 <span data-ttu-id="0dfbd-119">なし</span><span class="sxs-lookup"><span data-stu-id="0dfbd-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dfbd-120">親要素</span><span class="sxs-lookup"><span data-stu-id="0dfbd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0dfbd-121">要素</span><span class="sxs-lookup"><span data-stu-id="0dfbd-121">Element</span></span>|<span data-ttu-id="0dfbd-122">説明</span><span class="sxs-lookup"><span data-stu-id="0dfbd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dfbd-123">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="0dfbd-123">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="0dfbd-124">コントラクトの型名のコレクション。</span><span class="sxs-lookup"><span data-stu-id="0dfbd-124">A collection of contract type names.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dfbd-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dfbd-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>

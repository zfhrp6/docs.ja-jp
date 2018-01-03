---
title: '&lt;findCriteria&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f804cdb57355b62db25a559dc3c5db7d4d69369e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="98db7-102">&lt;findCriteria&gt;</span><span class="sxs-lookup"><span data-stu-id="98db7-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="98db7-103">探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。</span><span class="sxs-lookup"><span data-stu-id="98db7-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="98db7-104">条件は、(探しているサービスの種類を指定する) 検索条件にグループ化できるし、検索終了条件 (期間、検索する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="98db7-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="98db7-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="98db7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="98db7-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="98db7-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98db7-107">構文</span><span class="sxs-lookup"><span data-stu-id="98db7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98db7-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="98db7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="98db7-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="98db7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98db7-110">属性</span><span class="sxs-lookup"><span data-stu-id="98db7-110">Attributes</span></span>  
  
|<span data-ttu-id="98db7-111">属性</span><span class="sxs-lookup"><span data-stu-id="98db7-111">Attribute</span></span>|<span data-ttu-id="98db7-112">説明</span><span class="sxs-lookup"><span data-stu-id="98db7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98db7-113">duration</span><span class="sxs-lookup"><span data-stu-id="98db7-113">duration</span></span>|<span data-ttu-id="98db7-114">ネットワーク上でサービスからの応答を待機する最長時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="98db7-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="98db7-115">既定の時間は 20 秒です。</span><span class="sxs-lookup"><span data-stu-id="98db7-115">The default duration is 20 seconds..</span></span>|  
|<span data-ttu-id="98db7-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="98db7-116">maxResults</span></span>|<span data-ttu-id="98db7-117">ネットワークまたはインターネット上で待機する、サービスから応答の最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="98db7-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="98db7-118">`duration` 属性に指定した時間が経過する前に応答の最大数に達した場合、検索操作は終了します。</span><span class="sxs-lookup"><span data-stu-id="98db7-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="98db7-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="98db7-119">scopeMatchBy</span></span>|<span data-ttu-id="98db7-120">Probe メッセージのスコープをエンドポイントのスコープと一致させるときに使用する、一致のアルゴリズムを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="98db7-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="98db7-121">サポートされているスコープ一致規則は 5 つあります。</span><span class="sxs-lookup"><span data-stu-id="98db7-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="98db7-122">スコープ一致規則を指定しなかった場合は、`ScopeMatchByPrefix` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="98db7-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="98db7-123">詳細については、「<xref:System.ServiceModel.Discovery.FindCriteria>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98db7-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98db7-124">子要素</span><span class="sxs-lookup"><span data-stu-id="98db7-124">Child Elements</span></span>  
  
|<span data-ttu-id="98db7-125">要素</span><span class="sxs-lookup"><span data-stu-id="98db7-125">Element</span></span>|<span data-ttu-id="98db7-126">説明</span><span class="sxs-lookup"><span data-stu-id="98db7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98db7-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="98db7-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="98db7-128">ワークフロー サービス コントラクト型の名前を格納する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="98db7-128">A collection of configuration elements that contain the names of workflow service contract types..</span></span>|  
|<span data-ttu-id="98db7-129">\<拡張機能 > の\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="98db7-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="98db7-130">拡張を提供する XML 要素オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="98db7-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="98db7-131">\<スコープ ></span><span class="sxs-lookup"><span data-stu-id="98db7-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="98db7-132">特定のサービスを特定する検索操作の実行中に使用される絶対 URI を格納するオブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="98db7-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="98db7-133">特定のサービスが見つかった場合、サービス URI とスコープ URI が一致します。複雑な一致を処理するスコープ規則が使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="98db7-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98db7-134">親要素</span><span class="sxs-lookup"><span data-stu-id="98db7-134">Parent Elements</span></span>  
  
|<span data-ttu-id="98db7-135">要素</span><span class="sxs-lookup"><span data-stu-id="98db7-135">Element</span></span>|<span data-ttu-id="98db7-136">説明</span><span class="sxs-lookup"><span data-stu-id="98db7-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98db7-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="98db7-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="98db7-138">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="98db7-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98db7-139">参照</span><span class="sxs-lookup"><span data-stu-id="98db7-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>

---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: e9723aed1aa8fbcbf5c4e84080c0ba991ea3fd60
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="def3f-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="def3f-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="def3f-103">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="def3f-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="def3f-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="def3f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="def3f-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="def3f-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def3f-106">構文</span><span class="sxs-lookup"><span data-stu-id="def3f-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" 
                        maxResults="Integer" 
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="def3f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="def3f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="def3f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="def3f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="def3f-109">属性</span><span class="sxs-lookup"><span data-stu-id="def3f-109">Attributes</span></span>  
  
|<span data-ttu-id="def3f-110">属性</span><span class="sxs-lookup"><span data-stu-id="def3f-110">Attribute</span></span>|<span data-ttu-id="def3f-111">説明</span><span class="sxs-lookup"><span data-stu-id="def3f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="def3f-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="def3f-112">discoveryEndpoint</span></span>|<span data-ttu-id="def3f-113">クライアント アプリケーションが実行時に探索可能なサービスを自動的に検索し、そのアドレスを見つけることができる探索エンドポイントの名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="def3f-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="def3f-114">子要素</span><span class="sxs-lookup"><span data-stu-id="def3f-114">Child Elements</span></span>  
  
|<span data-ttu-id="def3f-115">要素</span><span class="sxs-lookup"><span data-stu-id="def3f-115">Element</span></span>|<span data-ttu-id="def3f-116">説明</span><span class="sxs-lookup"><span data-stu-id="def3f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="def3f-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="def3f-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="def3f-118">探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。</span><span class="sxs-lookup"><span data-stu-id="def3f-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="def3f-119">条件は、(探しているサービスの種類を指定する) 検索条件にグループ化できるし、検索終了条件 (期間、検索する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="def3f-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="def3f-120">親要素</span><span class="sxs-lookup"><span data-stu-id="def3f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="def3f-121">要素</span><span class="sxs-lookup"><span data-stu-id="def3f-121">Element</span></span>|<span data-ttu-id="def3f-122">説明</span><span class="sxs-lookup"><span data-stu-id="def3f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="def3f-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="def3f-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="def3f-124">アプリケーションが実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="def3f-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="def3f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="def3f-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>

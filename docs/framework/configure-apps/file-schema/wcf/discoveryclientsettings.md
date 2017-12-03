---
title: '&lt;discoveryClientSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d5e7106de716e4f25e649dbbca716ef66dfa496
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="dc3aa-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="dc3aa-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="dc3aa-103">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="dc3aa-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="dc3aa-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dc3aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc3aa-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="dc3aa-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3aa-106">構文</span><span class="sxs-lookup"><span data-stu-id="dc3aa-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc3aa-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dc3aa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dc3aa-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc3aa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc3aa-109">属性</span><span class="sxs-lookup"><span data-stu-id="dc3aa-109">Attributes</span></span>  
  
|<span data-ttu-id="dc3aa-110">属性</span><span class="sxs-lookup"><span data-stu-id="dc3aa-110">Attribute</span></span>|<span data-ttu-id="dc3aa-111">説明</span><span class="sxs-lookup"><span data-stu-id="dc3aa-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc3aa-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="dc3aa-112">discoveryEndpoint</span></span>|<span data-ttu-id="dc3aa-113">クライアント アプリケーションが実行時に探索可能なサービスを自動的に検索し、そのアドレスを見つけることができる探索エンドポイントの名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="dc3aa-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc3aa-114">子要素</span><span class="sxs-lookup"><span data-stu-id="dc3aa-114">Child Elements</span></span>  
  
|<span data-ttu-id="dc3aa-115">要素</span><span class="sxs-lookup"><span data-stu-id="dc3aa-115">Element</span></span>|<span data-ttu-id="dc3aa-116">説明</span><span class="sxs-lookup"><span data-stu-id="dc3aa-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc3aa-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="dc3aa-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="dc3aa-118">探索サービスの検索にクライアント アプリケーションによって使用される基準を提供する構成要素。</span><span class="sxs-lookup"><span data-stu-id="dc3aa-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="dc3aa-119">条件は、(探しているサービスの種類を指定する) 検索条件にグループ化できるし、検索終了条件 (期間、検索する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="dc3aa-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc3aa-120">親要素</span><span class="sxs-lookup"><span data-stu-id="dc3aa-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dc3aa-121">要素</span><span class="sxs-lookup"><span data-stu-id="dc3aa-121">Element</span></span>|<span data-ttu-id="dc3aa-122">説明</span><span class="sxs-lookup"><span data-stu-id="dc3aa-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc3aa-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="dc3aa-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="dc3aa-124">アプリケーションが実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="dc3aa-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc3aa-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc3aa-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>

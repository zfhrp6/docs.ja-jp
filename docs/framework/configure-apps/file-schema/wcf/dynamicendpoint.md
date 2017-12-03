---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e780e1975aecc80ea458ec6a86fca61e4ad22448
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="d9c23-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="d9c23-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="d9c23-103">この構成要素は、アプリケーションが、実行時に動的にエンドポイント アドレスを検索するクライアント プログラムとして機能するための情報を格納する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="d9c23-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="d9c23-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d9c23-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d9c23-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d9c23-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c23-106">構文</span><span class="sxs-lookup"><span data-stu-id="d9c23-106">Syntax</span></span>  
  
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
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9c23-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d9c23-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d9c23-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9c23-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9c23-109">属性</span><span class="sxs-lookup"><span data-stu-id="d9c23-109">Attributes</span></span>  
 <span data-ttu-id="d9c23-110">なし。</span><span class="sxs-lookup"><span data-stu-id="d9c23-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9c23-111">子要素</span><span class="sxs-lookup"><span data-stu-id="d9c23-111">Child Elements</span></span>  
  
|<span data-ttu-id="d9c23-112">要素</span><span class="sxs-lookup"><span data-stu-id="d9c23-112">Element</span></span>|<span data-ttu-id="d9c23-113">説明</span><span class="sxs-lookup"><span data-stu-id="d9c23-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9c23-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="d9c23-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="d9c23-115">サービス探索プロセスにクライアントとして参加するためにアプリケーションが必要とする設定を格納します。</span><span class="sxs-lookup"><span data-stu-id="d9c23-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9c23-116">親要素</span><span class="sxs-lookup"><span data-stu-id="d9c23-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d9c23-117">要素</span><span class="sxs-lookup"><span data-stu-id="d9c23-117">Element</span></span>|<span data-ttu-id="d9c23-118">説明</span><span class="sxs-lookup"><span data-stu-id="d9c23-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9c23-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d9c23-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d9c23-120">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="d9c23-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9c23-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9c23-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>

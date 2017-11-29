---
title: "&lt;issuerChannelBehaviors&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 051525738f0138955358587a8fd25272dfdb9d28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="40641-102">&lt;issuerChannelBehaviors&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="40641-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="40641-103">指定されたセキュリティ トークン サービスと通信するときに使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアント エンドポイントの動作 (構成で定義されている) のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="40641-103">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="40641-104">未定義の動作は、いずれかを含めることはできません[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。</span><span class="sxs-lookup"><span data-stu-id="40641-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="40641-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="40641-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="40641-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="40641-106">\<behaviors></span></span>  
<span data-ttu-id="40641-107">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="40641-107">endpointBehaviors section</span></span>  
<span data-ttu-id="40641-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="40641-108">\<behavior></span></span>  
<span data-ttu-id="40641-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="40641-109">\<clientCredentials></span></span>  
<span data-ttu-id="40641-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="40641-110">\<issuedToken></span></span>  
<span data-ttu-id="40641-111">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="40641-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40641-112">構文</span><span class="sxs-lookup"><span data-stu-id="40641-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>  
      <add behaviorConfiguraton="string"  
                issuerAddress="string" />  
</issuerChannelBehaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40641-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="40641-113">Attributes and Elements</span></span>  
 <span data-ttu-id="40641-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="40641-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40641-115">属性</span><span class="sxs-lookup"><span data-stu-id="40641-115">Attributes</span></span>  
 <span data-ttu-id="40641-116">なし。</span><span class="sxs-lookup"><span data-stu-id="40641-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40641-117">子要素</span><span class="sxs-lookup"><span data-stu-id="40641-117">Child Elements</span></span>  
  
|<span data-ttu-id="40641-118">要素</span><span class="sxs-lookup"><span data-stu-id="40641-118">Element</span></span>|<span data-ttu-id="40641-119">説明</span><span class="sxs-lookup"><span data-stu-id="40641-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40641-120">\<add></span><span class="sxs-lookup"><span data-stu-id="40641-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="40641-121">コレクションに動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="40641-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40641-122">親要素</span><span class="sxs-lookup"><span data-stu-id="40641-122">Parent Elements</span></span>  
  
|<span data-ttu-id="40641-123">要素</span><span class="sxs-lookup"><span data-stu-id="40641-123">Element</span></span>|<span data-ttu-id="40641-124">説明</span><span class="sxs-lookup"><span data-stu-id="40641-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40641-125">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="40641-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="40641-126">サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="40641-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40641-127">コメント</span><span class="sxs-lookup"><span data-stu-id="40641-127">Remarks</span></span>  
 <span data-ttu-id="40641-128">この要素を使用するのは、なんらかの動作 (`<clientCredentials>` 要素を含む動作以外) を使用してサービスと通信する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="40641-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="40641-129">たとえば場合、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)動作要素を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="40641-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40641-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="40641-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="40641-131">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="40641-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="40641-132">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="40641-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="40641-133">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="40641-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="40641-134">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="40641-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="40641-135">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="40641-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="40641-136">方法: フェデレーション クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="40641-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="40641-137">方法: ローカル発行者を構成します。</span><span class="sxs-lookup"><span data-stu-id="40641-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="40641-138">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="40641-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

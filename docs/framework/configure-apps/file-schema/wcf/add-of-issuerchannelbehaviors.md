---
title: '&lt;issuerChannelBehaviors&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752456"
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="81a28-102">&lt;issuerChannelBehaviors&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="81a28-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="81a28-103">STS と通信するときに使用されるエンドポイントの動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="81a28-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81a28-104">すべてのエンドポイント動作が含まれている場合、 [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="81a28-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="81a28-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="81a28-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="81a28-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="81a28-106">\<behaviors></span></span>  
<span data-ttu-id="81a28-107">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="81a28-107">endpointBehaviors section</span></span>  
<span data-ttu-id="81a28-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="81a28-108">\<behavior></span></span>  
<span data-ttu-id="81a28-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="81a28-109">\<clientCredentials></span></span>  
<span data-ttu-id="81a28-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="81a28-110">\<issuedToken></span></span>  
<span data-ttu-id="81a28-111">\<issuerChannelBehaviors > 要素</span><span class="sxs-lookup"><span data-stu-id="81a28-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="81a28-112">\<add></span><span class="sxs-lookup"><span data-stu-id="81a28-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a28-113">構文</span><span class="sxs-lookup"><span data-stu-id="81a28-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81a28-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="81a28-114">Attributes and Elements</span></span>  
 <span data-ttu-id="81a28-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="81a28-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81a28-116">属性</span><span class="sxs-lookup"><span data-stu-id="81a28-116">Attributes</span></span>  
  
|<span data-ttu-id="81a28-117">属性</span><span class="sxs-lookup"><span data-stu-id="81a28-117">Attribute</span></span>|<span data-ttu-id="81a28-118">説明</span><span class="sxs-lookup"><span data-stu-id="81a28-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81a28-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="81a28-119">issuerAddress</span></span>|<span data-ttu-id="81a28-120">通信するためのセキュリティ トークン発行者の URI。</span><span class="sxs-lookup"><span data-stu-id="81a28-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="81a28-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="81a28-121">behaviorConfiguration</span></span>|<span data-ttu-id="81a28-122">同じ構成ファイルに定義されたエンドポイントの動作の名前。</span><span class="sxs-lookup"><span data-stu-id="81a28-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81a28-123">子要素</span><span class="sxs-lookup"><span data-stu-id="81a28-123">Child Elements</span></span>  
 <span data-ttu-id="81a28-124">なし。</span><span class="sxs-lookup"><span data-stu-id="81a28-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81a28-125">親要素</span><span class="sxs-lookup"><span data-stu-id="81a28-125">Parent Elements</span></span>  
  
|<span data-ttu-id="81a28-126">要素</span><span class="sxs-lookup"><span data-stu-id="81a28-126">Element</span></span>|<span data-ttu-id="81a28-127">説明</span><span class="sxs-lookup"><span data-stu-id="81a28-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81a28-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81a28-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="81a28-129">指定されたセキュリティ トークン サービスと通信するときに使用される Windows Communication Foundation (WCF) クライアント エンドポイントの動作のコレクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="81a28-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81a28-130">コメント</span><span class="sxs-lookup"><span data-stu-id="81a28-130">Remarks</span></span>  
 <span data-ttu-id="81a28-131">`issuerAddress` には、クライアントの通信相手となるセキュリティ トークン サービスの URI が含まれます。</span><span class="sxs-lookup"><span data-stu-id="81a28-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="81a28-132">`behaviorConfiguration` アプリケーションがセキュリティ トークン サービスから発行済みトークンを取得する Windows Communication Foundation (WCF) によって作成されたチャネルで使用するエンドポイントの動作を指します。</span><span class="sxs-lookup"><span data-stu-id="81a28-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a28-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="81a28-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="81a28-134">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="81a28-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="81a28-135">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="81a28-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="81a28-136">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="81a28-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="81a28-137">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="81a28-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="81a28-138">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="81a28-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="81a28-139">方法 : フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="81a28-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="81a28-140">方法 : ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="81a28-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="81a28-141">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="81a28-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="81a28-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="81a28-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)

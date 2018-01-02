---
title: "&lt;issuerChannelBehaviors&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf66b3d3b531ae41329aade6a416c330957d83c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="3cdba-102">&lt;issuerChannelBehaviors&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="3cdba-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="3cdba-103">STS と通信するときに使用されるエンドポイントの動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="3cdba-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cdba-104">すべてのエンドポイント動作が含まれている場合、 [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3cdba-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="3cdba-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3cdba-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3cdba-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="3cdba-106">\<behaviors></span></span>  
<span data-ttu-id="3cdba-107">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="3cdba-107">endpointBehaviors section</span></span>  
<span data-ttu-id="3cdba-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="3cdba-108">\<behavior></span></span>  
<span data-ttu-id="3cdba-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="3cdba-109">\<clientCredentials></span></span>  
<span data-ttu-id="3cdba-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="3cdba-110">\<issuedToken></span></span>  
<span data-ttu-id="3cdba-111">\<issuerChannelBehaviors > 要素</span><span class="sxs-lookup"><span data-stu-id="3cdba-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="3cdba-112">\<add></span><span class="sxs-lookup"><span data-stu-id="3cdba-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cdba-113">構文</span><span class="sxs-lookup"><span data-stu-id="3cdba-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cdba-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3cdba-114">Attributes and Elements</span></span>  
 <span data-ttu-id="3cdba-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3cdba-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cdba-116">属性</span><span class="sxs-lookup"><span data-stu-id="3cdba-116">Attributes</span></span>  
  
|<span data-ttu-id="3cdba-117">属性</span><span class="sxs-lookup"><span data-stu-id="3cdba-117">Attribute</span></span>|<span data-ttu-id="3cdba-118">説明</span><span class="sxs-lookup"><span data-stu-id="3cdba-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3cdba-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="3cdba-119">issuerAddress</span></span>|<span data-ttu-id="3cdba-120">通信するためのセキュリティ トークン発行者の URI。</span><span class="sxs-lookup"><span data-stu-id="3cdba-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="3cdba-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3cdba-121">behaviorConfiguration</span></span>|<span data-ttu-id="3cdba-122">同じ構成ファイルに定義されたエンドポイントの動作の名前。</span><span class="sxs-lookup"><span data-stu-id="3cdba-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cdba-123">子要素</span><span class="sxs-lookup"><span data-stu-id="3cdba-123">Child Elements</span></span>  
 <span data-ttu-id="3cdba-124">なし。</span><span class="sxs-lookup"><span data-stu-id="3cdba-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cdba-125">親要素</span><span class="sxs-lookup"><span data-stu-id="3cdba-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3cdba-126">要素</span><span class="sxs-lookup"><span data-stu-id="3cdba-126">Element</span></span>|<span data-ttu-id="3cdba-127">説明</span><span class="sxs-lookup"><span data-stu-id="3cdba-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cdba-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3cdba-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="3cdba-129">指定されたセキュリティ トークン サービスと通信するときに使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアント エンドポイントの動作のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cdba-129">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cdba-130">コメント</span><span class="sxs-lookup"><span data-stu-id="3cdba-130">Remarks</span></span>  
 <span data-ttu-id="3cdba-131">`issuerAddress` には、クライアントの通信相手となるセキュリティ トークン サービスの URI が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3cdba-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="3cdba-132">`behaviorConfiguration` は、アプリケーションが使用するエンドポイント動作を表します。アプリケーションは、セキュリティ トークン サービスから発行されたトークンを取得するために、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] によって作成されたチャネルでこの動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cdba-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cdba-133">参照</span><span class="sxs-lookup"><span data-stu-id="3cdba-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="3cdba-134">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="3cdba-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="3cdba-135">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="3cdba-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="3cdba-136">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="3cdba-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="3cdba-137">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3cdba-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3cdba-138">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3cdba-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="3cdba-139">方法 : フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="3cdba-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="3cdba-140">方法 : ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="3cdba-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="3cdba-141">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="3cdba-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="3cdba-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3cdba-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)

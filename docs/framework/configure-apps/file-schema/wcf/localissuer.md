---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="1f4c2-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="1f4c2-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="1f4c2-103">セキュリティ トークンの取得に使用される、ローカル発行者のアドレスとバインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="1f4c2-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1f4c2-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-105">\<behaviors></span></span>  
<span data-ttu-id="1f4c2-106">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="1f4c2-106">endpointBehaviors section</span></span>  
<span data-ttu-id="1f4c2-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-107">\<behavior></span></span>  
<span data-ttu-id="1f4c2-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-108">\<clientCredentials></span></span>  
<span data-ttu-id="1f4c2-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-109">\<issuedToken></span></span>  
<span data-ttu-id="1f4c2-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4c2-111">構文</span><span class="sxs-lookup"><span data-stu-id="1f4c2-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f4c2-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1f4c2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1f4c2-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f4c2-114">属性</span><span class="sxs-lookup"><span data-stu-id="1f4c2-114">Attributes</span></span>  
  
|<span data-ttu-id="1f4c2-115">属性</span><span class="sxs-lookup"><span data-stu-id="1f4c2-115">Attribute</span></span>|<span data-ttu-id="1f4c2-116">説明</span><span class="sxs-lookup"><span data-stu-id="1f4c2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f4c2-117">address</span><span class="sxs-lookup"><span data-stu-id="1f4c2-117">address</span></span>|<span data-ttu-id="1f4c2-118">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-118">Required string.</span></span> <span data-ttu-id="1f4c2-119">ローカル発行者の URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="1f4c2-120">バインド</span><span class="sxs-lookup"><span data-stu-id="1f4c2-120">binding</span></span>|<span data-ttu-id="1f4c2-121">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-121">Optional string.</span></span> <span data-ttu-id="1f4c2-122">システム指定のバインディングの 1 つ。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-122">One of the system-provided bindings.</span></span> <span data-ttu-id="1f4c2-123">一覧については、次を参照してください。[システム指定のバインディング](../../../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="1f4c2-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="1f4c2-124">bindingConfiguration</span></span>|<span data-ttu-id="1f4c2-125">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-125">Optional string.</span></span> <span data-ttu-id="1f4c2-126">構成ファイル内に存在するバインド構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f4c2-127">子要素</span><span class="sxs-lookup"><span data-stu-id="1f4c2-127">Child Elements</span></span>  
  
|<span data-ttu-id="1f4c2-128">要素</span><span class="sxs-lookup"><span data-stu-id="1f4c2-128">Element</span></span>|<span data-ttu-id="1f4c2-129">説明</span><span class="sxs-lookup"><span data-stu-id="1f4c2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f4c2-130">\<id ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="1f4c2-131">ローカル発行者の ID 情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="1f4c2-132">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="1f4c2-133">ローカル発行者を正しくアドレス指定するために必要なアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="1f4c2-134">`add` キーワードを使用して、このコレクションにヘッダーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f4c2-135">親要素</span><span class="sxs-lookup"><span data-stu-id="1f4c2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1f4c2-136">要素</span><span class="sxs-lookup"><span data-stu-id="1f4c2-136">Element</span></span>|<span data-ttu-id="1f4c2-137">説明</span><span class="sxs-lookup"><span data-stu-id="1f4c2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f4c2-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="1f4c2-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="1f4c2-139">サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f4c2-140">コメント</span><span class="sxs-lookup"><span data-stu-id="1f4c2-140">Remarks</span></span>  
 <span data-ttu-id="1f4c2-141">発行されたトークンをセキュリティ トークン サービス (STS) から取得する場合は、クライアント アプリケーションに、STS との通信に使用するアドレスとバインディングが構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="1f4c2-142"><xref:System.ServiceModel.WSFederationHttpBinding> にセキュリティ トークン サービスの URL が設定されていない場合、またはフェデレーション バインディングの発行者アドレスが http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous か `null` である場合、クライアントの [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] チャネルは、`address` と `binding` で指定された値を使用して STS と通信し、発行されたトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="1f4c2-143">ローカル発行者を構成する方法については、次を参照してください。[する方法: ローカル発行者を構成する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f4c2-144">例</span><span class="sxs-lookup"><span data-stu-id="1f4c2-144">Example</span></span>  
 <span data-ttu-id="1f4c2-145">次の例は、`address` 要素の `binding`、`bindingConfiguration`、および `localIssuer` 属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f4c2-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f4c2-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="1f4c2-147">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="1f4c2-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1f4c2-148">方法: ローカル発行者を構成します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="1f4c2-149">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="1f4c2-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1f4c2-150">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="1f4c2-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1f4c2-151">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="1f4c2-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1f4c2-152">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="1f4c2-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1f4c2-153">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="1f4c2-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="1f4c2-154">方法: フェデレーション クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1f4c2-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="1f4c2-155">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="1f4c2-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

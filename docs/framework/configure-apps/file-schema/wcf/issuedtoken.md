---
title: '&lt;issuedToken&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c4090dacdbb55f66bf7c27bdd02adf371049f7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="1c133-102">&lt;issuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="1c133-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="1c133-103">サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c133-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="1c133-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1c133-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c133-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="1c133-105">\<behaviors></span></span>  
<span data-ttu-id="1c133-106">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="1c133-106">endpointBehaviors section</span></span>  
<span data-ttu-id="1c133-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1c133-107">\<behavior></span></span>  
<span data-ttu-id="1c133-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1c133-108">\<clientCredentials></span></span>  
<span data-ttu-id="1c133-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="1c133-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c133-110">構文</span><span class="sxs-lookup"><span data-stu-id="1c133-110">Syntax</span></span>  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c133-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1c133-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1c133-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c133-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c133-113">属性</span><span class="sxs-lookup"><span data-stu-id="1c133-113">Attributes</span></span>  
  
|<span data-ttu-id="1c133-114">属性</span><span class="sxs-lookup"><span data-stu-id="1c133-114">Attribute</span></span>|<span data-ttu-id="1c133-115">説明</span><span class="sxs-lookup"><span data-stu-id="1c133-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="1c133-116">トークンがキャッシュされるかどうかを指定する省略可能なブール属性。</span><span class="sxs-lookup"><span data-stu-id="1c133-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="1c133-117">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="1c133-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="1c133-118">ハンドシェイク操作に使用されるランダム値 (エントロピ) を指定する省略可能な文字列属性。</span><span class="sxs-lookup"><span data-stu-id="1c133-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="1c133-119">値には、`ClientEntropy`、`ServerEntropy`、および `CombinedEntropy` があります。既定値は `CombinedEntropy` です。</span><span class="sxs-lookup"><span data-stu-id="1c133-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="1c133-120">この属性は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="1c133-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="1c133-121">トークンが更新されるまでに待機できる有効な期間 (トークン発行者によって提供される) のパーセンテージを指定する省略可能な整数属性。</span><span class="sxs-lookup"><span data-stu-id="1c133-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="1c133-122">値は 0 ～ 100 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="1c133-122">Values are from 0 to 100.</span></span> <span data-ttu-id="1c133-123">既定値は 60 で、更新の実行までに待機できる期間の 60% を示します。</span><span class="sxs-lookup"><span data-stu-id="1c133-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="1c133-124">発行者との通信時に使用するチャネル動作を指定する省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="1c133-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="1c133-125">ローカル発行者との通信時に使用するチャネル動作を指定する省略可能な属性。</span><span class="sxs-lookup"><span data-stu-id="1c133-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="1c133-126">トークン発行者 (STS) が期間を指定しない場合に、発行済みトークンがキャッシュされる期間を指定する省略可能な Timespan 属性。</span><span class="sxs-lookup"><span data-stu-id="1c133-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="1c133-127">既定値は「10675199.02:48:05.4775807」です。</span><span class="sxs-lookup"><span data-stu-id="1c133-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c133-128">子要素</span><span class="sxs-lookup"><span data-stu-id="1c133-128">Child Elements</span></span>  
  
|<span data-ttu-id="1c133-129">要素</span><span class="sxs-lookup"><span data-stu-id="1c133-129">Element</span></span>|<span data-ttu-id="1c133-130">説明</span><span class="sxs-lookup"><span data-stu-id="1c133-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c133-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="1c133-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="1c133-132">トークンのローカル発行者のアドレスと、エンドポイントとの通信に使用されるバインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c133-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="1c133-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1c133-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="1c133-134">ローカル発行者に接続するときに使用するエンドポイント動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c133-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c133-135">親要素</span><span class="sxs-lookup"><span data-stu-id="1c133-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1c133-136">要素</span><span class="sxs-lookup"><span data-stu-id="1c133-136">Element</span></span>|<span data-ttu-id="1c133-137">説明</span><span class="sxs-lookup"><span data-stu-id="1c133-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c133-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1c133-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="1c133-139">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c133-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c133-140">コメント</span><span class="sxs-lookup"><span data-stu-id="1c133-140">Remarks</span></span>  
 <span data-ttu-id="1c133-141">発行済みトークンは、フェデレーション シナリオでセキュリティ トークン サービス (STS) を使用して認証するときに使用されるカスタム資格情報の種類です。</span><span class="sxs-lookup"><span data-stu-id="1c133-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="1c133-142">既定ではトークンは、SAML トークンです。</span><span class="sxs-lookup"><span data-stu-id="1c133-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="1c133-143">詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c133-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="1c133-144">および[フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c133-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="1c133-145">このセクションには、トークンのローカル発行者やセキュリティ トークン サービスで使用する動作の構成に使用する要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c133-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="1c133-146">クライアントを構成するのにはローカル発行者を使用する方法について、次を参照してください。[する方法: ローカル発行者を構成する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c133-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c133-147">参照</span><span class="sxs-lookup"><span data-stu-id="1c133-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="1c133-148">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="1c133-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="1c133-149">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="1c133-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1c133-150">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="1c133-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1c133-151">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="1c133-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="1c133-152">方法 : フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="1c133-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="1c133-153">方法 : ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="1c133-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="1c133-154">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="1c133-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

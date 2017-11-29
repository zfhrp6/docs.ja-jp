---
title: "&lt;allowedAudienceUris&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4de490107ed905b5acbda057f2cd53a306e6d75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a><span data-ttu-id="b1cec-102">&lt;allowedAudienceUris&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="b1cec-102">&lt;add&gt; of &lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="b1cec-103"><xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1cec-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="b1cec-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b1cec-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1cec-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="b1cec-105">\<behaviors></span></span>  
<span data-ttu-id="b1cec-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b1cec-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b1cec-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="b1cec-107">\<behavior></span></span>  
<span data-ttu-id="b1cec-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="b1cec-108">\<serviceCredentials></span></span>  
<span data-ttu-id="b1cec-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b1cec-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="b1cec-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="b1cec-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="b1cec-111">\<追加 > 要素を\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="b1cec-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1cec-112">構文</span><span class="sxs-lookup"><span data-stu-id="b1cec-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1cec-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b1cec-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b1cec-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1cec-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1cec-115">属性</span><span class="sxs-lookup"><span data-stu-id="b1cec-115">Attributes</span></span>  
  
|<span data-ttu-id="b1cec-116">属性</span><span class="sxs-lookup"><span data-stu-id="b1cec-116">Attribute</span></span>|<span data-ttu-id="b1cec-117">説明</span><span class="sxs-lookup"><span data-stu-id="b1cec-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1cec-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="b1cec-118">allowedAudienceUri</span></span>|<span data-ttu-id="b1cec-119"><xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI を含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="b1cec-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1cec-120">子要素</span><span class="sxs-lookup"><span data-stu-id="b1cec-120">Child Elements</span></span>  
 <span data-ttu-id="b1cec-121">なし。</span><span class="sxs-lookup"><span data-stu-id="b1cec-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1cec-122">親要素</span><span class="sxs-lookup"><span data-stu-id="b1cec-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b1cec-123">要素</span><span class="sxs-lookup"><span data-stu-id="b1cec-123">Element</span></span>|<span data-ttu-id="b1cec-124">説明</span><span class="sxs-lookup"><span data-stu-id="b1cec-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1cec-125">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="b1cec-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="b1cec-126"><xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b1cec-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1cec-127">コメント</span><span class="sxs-lookup"><span data-stu-id="b1cec-127">Remarks</span></span>  
 <span data-ttu-id="b1cec-128">このコレクションは、<xref:System.IdentityModel.Tokens.SamlSecurityToken> セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を利用するフェデレーション アプリケーションで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1cec-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="b1cec-129">STS がセキュリティ トークンを発行する場合、このセキュリティ トークンに <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> を追加して、セキュリティ トークンの提供先となる Web サービスの URI を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b1cec-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="b1cec-130">これにより、受け取り側 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web サービスは、次のようにしてこのチェックが行われるように指定することで、発行されたセキュリティ トークンがこの Web サービスを対象としていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b1cec-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="b1cec-131">`audienceUriMode` の `<issuedTokenAuthentication>` 属性を <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> または <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b1cec-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="b1cec-132">このコレクションに URI を追加して、有効な URI のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1cec-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="b1cec-133">詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1cec-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="b1cec-134">この構成要素を使用する方法については、次を参照してください。[する方法: フェデレーション サービスの資格情報の構成](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1cec-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cec-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1cec-135">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="b1cec-136">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="b1cec-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [<span data-ttu-id="b1cec-137">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b1cec-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="b1cec-138">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="b1cec-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b1cec-139">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b1cec-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b1cec-140">方法: フェデレーション サービスの資格情報を構成します。</span><span class="sxs-lookup"><span data-stu-id="b1cec-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)

---
title: '&lt;allowedAudienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b48449df95e9cf927cad805043c7419ec8c13be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="358b7-102">&lt;allowedAudienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="358b7-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="358b7-103"><xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="358b7-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="358b7-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="358b7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="358b7-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="358b7-105">\<behaviors></span></span>  
<span data-ttu-id="358b7-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="358b7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="358b7-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="358b7-107">\<behavior></span></span>  
<span data-ttu-id="358b7-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="358b7-108">\<serviceCredentials></span></span>  
<span data-ttu-id="358b7-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="358b7-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="358b7-110">\<allowedAudienceUris ></span><span class="sxs-lookup"><span data-stu-id="358b7-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358b7-111">構文</span><span class="sxs-lookup"><span data-stu-id="358b7-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="358b7-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="358b7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="358b7-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="358b7-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="358b7-114">属性</span><span class="sxs-lookup"><span data-stu-id="358b7-114">Attributes</span></span>  
 <span data-ttu-id="358b7-115">なし。</span><span class="sxs-lookup"><span data-stu-id="358b7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="358b7-116">子要素</span><span class="sxs-lookup"><span data-stu-id="358b7-116">Child Elements</span></span>  
  
|<span data-ttu-id="358b7-117">要素</span><span class="sxs-lookup"><span data-stu-id="358b7-117">Element</span></span>|<span data-ttu-id="358b7-118">説明</span><span class="sxs-lookup"><span data-stu-id="358b7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="358b7-119">\<add></span><span class="sxs-lookup"><span data-stu-id="358b7-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="358b7-120"><xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI を追加します。</span><span class="sxs-lookup"><span data-stu-id="358b7-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="358b7-121">親要素</span><span class="sxs-lookup"><span data-stu-id="358b7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="358b7-122">要素</span><span class="sxs-lookup"><span data-stu-id="358b7-122">Element</span></span>|<span data-ttu-id="358b7-123">説明</span><span class="sxs-lookup"><span data-stu-id="358b7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="358b7-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="358b7-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="358b7-125">サービス資格情報として発行されるトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="358b7-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="358b7-126">コメント</span><span class="sxs-lookup"><span data-stu-id="358b7-126">Remarks</span></span>  
 <span data-ttu-id="358b7-127">このコレクションは、<xref:System.IdentityModel.Tokens.SamlSecurityToken> セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を利用するフェデレーション アプリケーションで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358b7-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="358b7-128">STS がセキュリティ トークンを発行する場合、このセキュリティ トークンに <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> を追加して、セキュリティ トークンの提供先となる Web サービスの URI を指定できます。</span><span class="sxs-lookup"><span data-stu-id="358b7-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="358b7-129">これにより、受け取り側 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web サービスは、次のようにしてこのチェックが行われるように指定することで、発行されたセキュリティ トークンがこの Web サービスを対象としていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="358b7-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="358b7-130">`audienceUriMode` の `<issuedTokenAuthentication>` 属性を <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> または <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> に設定します。</span><span class="sxs-lookup"><span data-stu-id="358b7-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="358b7-131">このコレクションに URI を追加して、有効な URI のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="358b7-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="358b7-132">詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="358b7-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="358b7-133">この構成要素を使用する方法については、次を参照してください。[する方法: フェデレーション サービスの資格情報の構成](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="358b7-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358b7-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="358b7-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="358b7-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="358b7-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="358b7-136">\<add></span><span class="sxs-lookup"><span data-stu-id="358b7-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="358b7-137">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="358b7-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="358b7-138">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="358b7-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="358b7-139">方法: フェデレーション サービスの資格情報を構成します。</span><span class="sxs-lookup"><span data-stu-id="358b7-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)

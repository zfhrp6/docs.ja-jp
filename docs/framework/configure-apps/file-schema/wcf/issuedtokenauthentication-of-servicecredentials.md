---
title: "&lt;serviceCredentials&gt; の &lt;issuedTokenAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1007abbb91787ed7be4fe3a7f8c1b0173191d60e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="18368-102">&lt;serviceCredentials&gt; の &lt;issuedTokenAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="18368-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="18368-103">サービス資格情報として発行されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="18368-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="18368-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="18368-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18368-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="18368-105">\<behaviors></span></span>  
<span data-ttu-id="18368-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="18368-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="18368-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="18368-107">\<behavior></span></span>  
<span data-ttu-id="18368-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="18368-108">\<serviceCredentials></span></span>  
<span data-ttu-id="18368-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="18368-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18368-110">構文</span><span class="sxs-lookup"><span data-stu-id="18368-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18368-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="18368-111">Attributes and Elements</span></span>  
 <span data-ttu-id="18368-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="18368-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18368-113">属性</span><span class="sxs-lookup"><span data-stu-id="18368-113">Attributes</span></span>  
  
|<span data-ttu-id="18368-114">属性</span><span class="sxs-lookup"><span data-stu-id="18368-114">Attribute</span></span>|<span data-ttu-id="18368-115">説明</span><span class="sxs-lookup"><span data-stu-id="18368-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="18368-116"><xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI のセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="18368-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="18368-117">この属性の使い方の詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18368-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="18368-118">信頼できない RSA 証明書の発行者を許可するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="18368-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="18368-119">証明書は、信頼性を検証する証明機関 (CA) によって署名されます。</span><span class="sxs-lookup"><span data-stu-id="18368-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="18368-120">信頼できない発行者とは、証明書の署名が信頼できると指定されていない CA です。</span><span class="sxs-lookup"><span data-stu-id="18368-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="18368-121"><xref:System.IdentityModel.Tokens.SamlSecurityToken> セキュリティ トークンの <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> を検証するかどうかを指定する値を取得します。</span><span class="sxs-lookup"><span data-stu-id="18368-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="18368-122">この値は、<xref:System.IdentityModel.Selectors.AudienceUriMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="18368-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="18368-123">この属性の使い方の詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18368-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="18368-124">証明書検証モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="18368-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="18368-125"><xref:System.ServiceModel.Security.X509CertificateValidationMode> の有効な値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="18368-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="18368-126">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18368-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="18368-127">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="18368-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="18368-128">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="18368-128">Optional string.</span></span> <span data-ttu-id="18368-129">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="18368-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="18368-130">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18368-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="18368-131">失効状態の検証を行うかどうかに加え、検証をオンラインで実行するか、オフラインで実行するかを指定する失効モードを設定します。</span><span class="sxs-lookup"><span data-stu-id="18368-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="18368-132">この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="18368-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="18368-133">サービス資格情報に使用される SamlSerializer の型を指定する省略可能な文字列属性。</span><span class="sxs-lookup"><span data-stu-id="18368-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="18368-134">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="18368-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="18368-135">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="18368-135">Optional enumeration.</span></span> <span data-ttu-id="18368-136">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="18368-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18368-137">子要素</span><span class="sxs-lookup"><span data-stu-id="18368-137">Child Elements</span></span>  
  
|<span data-ttu-id="18368-138">要素</span><span class="sxs-lookup"><span data-stu-id="18368-138">Element</span></span>|<span data-ttu-id="18368-139">説明</span><span class="sxs-lookup"><span data-stu-id="18368-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="18368-140">サービス資格情報の信頼できる発行者を指定する <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 要素のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="18368-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18368-141">親要素</span><span class="sxs-lookup"><span data-stu-id="18368-141">Parent Elements</span></span>  
  
|<span data-ttu-id="18368-142">要素</span><span class="sxs-lookup"><span data-stu-id="18368-142">Element</span></span>|<span data-ttu-id="18368-143">説明</span><span class="sxs-lookup"><span data-stu-id="18368-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18368-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="18368-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="18368-145">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="18368-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18368-146">コメント</span><span class="sxs-lookup"><span data-stu-id="18368-146">Remarks</span></span>  
 <span data-ttu-id="18368-147">発行されるトークンのシナリオには、3 つの段階があります。</span><span class="sxs-lookup"><span data-stu-id="18368-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="18368-148">最初の段階で、サービスにアクセスしようとしているクライアントは呼びます、*トークン サービスをセキュリティで保護された*です。</span><span class="sxs-lookup"><span data-stu-id="18368-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="18368-149">次に、セキュリティ トークン サービスがクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。</span><span class="sxs-lookup"><span data-stu-id="18368-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="18368-150">最後に、クライアントがトークンを持ってサービスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="18368-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="18368-151">サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="18368-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="18368-152">トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="18368-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="18368-153">この要素は、このようなセキュリティ トークン サービス証明書のリポジトリです。</span><span class="sxs-lookup"><span data-stu-id="18368-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="18368-154">証明書を追加するには、使用、 [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="18368-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="18368-155">挿入、 [\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)証明書ごとに、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="18368-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="18368-156">既定では、証明書はセキュリティ トークン サービスから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18368-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="18368-157">このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="18368-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="18368-158">この構成要素を使用する方法については、次を参照してください。[する方法: フェデレーション サービスの資格情報の構成](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="18368-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18368-159">参照</span><span class="sxs-lookup"><span data-stu-id="18368-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="18368-160">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="18368-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="18368-161">方法 : フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="18368-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)

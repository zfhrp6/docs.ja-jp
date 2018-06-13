---
title: '&lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 394ae246ad29a0747f3814b36fae2557b04c235a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748244"
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="17158-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="17158-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="17158-103">セキュリティ トークン サービス (STS) から発行されるセキュリティ資格情報を認証するために提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="17158-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="17158-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="17158-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="17158-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="17158-105">\<behaviors></span></span>  
<span data-ttu-id="17158-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="17158-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="17158-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="17158-107">\<behavior></span></span>  
<span data-ttu-id="17158-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="17158-108">\<serviceCredentials></span></span>  
<span data-ttu-id="17158-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="17158-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="17158-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="17158-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17158-111">構文</span><span class="sxs-lookup"><span data-stu-id="17158-111">Syntax</span></span>  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17158-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="17158-112">Attributes and Elements</span></span>  
 <span data-ttu-id="17158-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="17158-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17158-114">属性</span><span class="sxs-lookup"><span data-stu-id="17158-114">Attributes</span></span>  
 <span data-ttu-id="17158-115">なし。</span><span class="sxs-lookup"><span data-stu-id="17158-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17158-116">子要素</span><span class="sxs-lookup"><span data-stu-id="17158-116">Child Elements</span></span>  
  
|<span data-ttu-id="17158-117">要素</span><span class="sxs-lookup"><span data-stu-id="17158-117">Element</span></span>|<span data-ttu-id="17158-118">説明</span><span class="sxs-lookup"><span data-stu-id="17158-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17158-119">\<add></span><span class="sxs-lookup"><span data-stu-id="17158-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="17158-120">コレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="17158-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17158-121">親要素</span><span class="sxs-lookup"><span data-stu-id="17158-121">Parent Elements</span></span>  
  
|<span data-ttu-id="17158-122">要素</span><span class="sxs-lookup"><span data-stu-id="17158-122">Element</span></span>|<span data-ttu-id="17158-123">説明</span><span class="sxs-lookup"><span data-stu-id="17158-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17158-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="17158-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="17158-125">サービス資格情報として発行されるトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="17158-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17158-126">コメント</span><span class="sxs-lookup"><span data-stu-id="17158-126">Remarks</span></span>  
 <span data-ttu-id="17158-127">発行されるトークンのシナリオには、3 つの段階があります。</span><span class="sxs-lookup"><span data-stu-id="17158-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="17158-128">最初の段階で、サービスにアクセスしようとしているクライアントは呼びます、*トークン サービスをセキュリティで保護された*です。</span><span class="sxs-lookup"><span data-stu-id="17158-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="17158-129">次に、セキュリティ トークン サービスがクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。</span><span class="sxs-lookup"><span data-stu-id="17158-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="17158-130">最後に、クライアントがトークンを持ってサービスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="17158-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="17158-131">サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。</span><span class="sxs-lookup"><span data-stu-id="17158-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="17158-132">トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="17158-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="17158-133">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)要素は、このようなセキュリティ トークン サービスの証明書のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="17158-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="17158-134">証明書を追加するには、使用、 [ \<knownCertificates > 要素](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="17158-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="17158-135">挿入、 [\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)証明書ごとに、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="17158-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="17158-136">既定では、証明書はセキュリティ トークン サービスから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17158-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="17158-137">このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="17158-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="17158-138">この構成要素の使用方法の詳細と同様に、フェデレーション サービスによって認証されるクライアントに必要な条件を確認するを参照してください。[する方法: フェデレーション サービスの資格情報の構成](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="17158-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="17158-139">フェデレーション シナリオの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)です。</span><span class="sxs-lookup"><span data-stu-id="17158-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="17158-140">例については、コレクションの構成を設定する方法を示しています、次を参照してください。 [\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="17158-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17158-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="17158-141">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="17158-142">\<add></span><span class="sxs-lookup"><span data-stu-id="17158-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="17158-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="17158-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="17158-144">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="17158-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="17158-145">方法 : フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="17158-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="17158-146">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="17158-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="17158-147">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="17158-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="17158-148">\<add></span><span class="sxs-lookup"><span data-stu-id="17158-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="17158-149">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="17158-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

---
title: '&lt;scopedCertificates&gt; 要素の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 0eb2f116fc0a2c7d59b90cea71150c7b46ee39fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746645"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="8cc79-102">&lt;scopedCertificates&gt; 要素の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="8cc79-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="8cc79-103">範囲指定された証明書のコレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="8cc79-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="8cc79-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8cc79-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cc79-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="8cc79-105">\<behaviors></span></span>  
<span data-ttu-id="8cc79-106">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="8cc79-106">endpointBehaviors section</span></span>  
<span data-ttu-id="8cc79-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8cc79-107">\<behavior></span></span>  
<span data-ttu-id="8cc79-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8cc79-108">\<clientCredentials></span></span>  
<span data-ttu-id="8cc79-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="8cc79-109">\<serviceCertificate></span></span>  
<span data-ttu-id="8cc79-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="8cc79-110">\<scopedCertificates></span></span>  
<span data-ttu-id="8cc79-111">\<追加 > 要素を\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="8cc79-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc79-112">構文</span><span class="sxs-lookup"><span data-stu-id="8cc79-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cc79-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8cc79-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8cc79-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cc79-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cc79-115">属性</span><span class="sxs-lookup"><span data-stu-id="8cc79-115">Attributes</span></span>  
  
|<span data-ttu-id="8cc79-116">属性</span><span class="sxs-lookup"><span data-stu-id="8cc79-116">Attribute</span></span>|<span data-ttu-id="8cc79-117">説明</span><span class="sxs-lookup"><span data-stu-id="8cc79-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8cc79-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="8cc79-118">targetUri</span></span>|<span data-ttu-id="8cc79-119">文字列。</span><span class="sxs-lookup"><span data-stu-id="8cc79-119">String.</span></span> <span data-ttu-id="8cc79-120">証明書に関連付けられているサービスの URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="8cc79-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="8cc79-121">findValue</span><span class="sxs-lookup"><span data-stu-id="8cc79-121">findValue</span></span>|<span data-ttu-id="8cc79-122">文字列。</span><span class="sxs-lookup"><span data-stu-id="8cc79-122">String.</span></span> <span data-ttu-id="8cc79-123">検索対象の値。</span><span class="sxs-lookup"><span data-stu-id="8cc79-123">The value to search for.</span></span>|  
|<span data-ttu-id="8cc79-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="8cc79-124">x509FindType</span></span>|<span data-ttu-id="8cc79-125">列挙値。</span><span class="sxs-lookup"><span data-stu-id="8cc79-125">Enumeration.</span></span> <span data-ttu-id="8cc79-126">検索する証明書フィールドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8cc79-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="8cc79-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="8cc79-127">storeLocation</span></span>|<span data-ttu-id="8cc79-128">列挙値。</span><span class="sxs-lookup"><span data-stu-id="8cc79-128">Enumeration.</span></span> <span data-ttu-id="8cc79-129">検索する 2 つの格納場所のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8cc79-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="8cc79-130">storeName</span><span class="sxs-lookup"><span data-stu-id="8cc79-130">storeName</span></span>|<span data-ttu-id="8cc79-131">列挙値。</span><span class="sxs-lookup"><span data-stu-id="8cc79-131">Enumeration.</span></span> <span data-ttu-id="8cc79-132">検索するシステム ストアのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8cc79-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="8cc79-133">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="8cc79-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="8cc79-134">値</span><span class="sxs-lookup"><span data-stu-id="8cc79-134">Value</span></span>|<span data-ttu-id="8cc79-135">説明</span><span class="sxs-lookup"><span data-stu-id="8cc79-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cc79-136">String</span><span class="sxs-lookup"><span data-stu-id="8cc79-136">String</span></span>|<span data-ttu-id="8cc79-137">値は、検索されるフィールド (X509FindType 属性により指定される) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8cc79-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="8cc79-138">たとえば、サムプリント検索する場合、値は 16 進数の文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8cc79-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="8cc79-139">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="8cc79-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="8cc79-140">値</span><span class="sxs-lookup"><span data-stu-id="8cc79-140">Value</span></span>|<span data-ttu-id="8cc79-141">説明</span><span class="sxs-lookup"><span data-stu-id="8cc79-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cc79-142">列挙型</span><span class="sxs-lookup"><span data-stu-id="8cc79-142">Enumeration</span></span>|<span data-ttu-id="8cc79-143">値は、FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier です。</span><span class="sxs-lookup"><span data-stu-id="8cc79-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="8cc79-144">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="8cc79-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="8cc79-145">値</span><span class="sxs-lookup"><span data-stu-id="8cc79-145">Value</span></span>|<span data-ttu-id="8cc79-146">説明</span><span class="sxs-lookup"><span data-stu-id="8cc79-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cc79-147">列挙型</span><span class="sxs-lookup"><span data-stu-id="8cc79-147">Enumeration</span></span>|<span data-ttu-id="8cc79-148">CurrentUser または LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="8cc79-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="8cc79-149">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="8cc79-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="8cc79-150">値</span><span class="sxs-lookup"><span data-stu-id="8cc79-150">Value</span></span>|<span data-ttu-id="8cc79-151">説明</span><span class="sxs-lookup"><span data-stu-id="8cc79-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cc79-152">列挙型</span><span class="sxs-lookup"><span data-stu-id="8cc79-152">Enumeration</span></span>|<span data-ttu-id="8cc79-153">値は、AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople、および TrustedPublisher です。</span><span class="sxs-lookup"><span data-stu-id="8cc79-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cc79-154">子要素</span><span class="sxs-lookup"><span data-stu-id="8cc79-154">Child Elements</span></span>  
 <span data-ttu-id="8cc79-155">なし。</span><span class="sxs-lookup"><span data-stu-id="8cc79-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cc79-156">親要素</span><span class="sxs-lookup"><span data-stu-id="8cc79-156">Parent Elements</span></span>  
  
|<span data-ttu-id="8cc79-157">要素</span><span class="sxs-lookup"><span data-stu-id="8cc79-157">Element</span></span>|<span data-ttu-id="8cc79-158">説明</span><span class="sxs-lookup"><span data-stu-id="8cc79-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cc79-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="8cc79-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="8cc79-160">認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="8cc79-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cc79-161">コメント</span><span class="sxs-lookup"><span data-stu-id="8cc79-161">Remarks</span></span>  
 <span data-ttu-id="8cc79-162">この要素を使用すると、クライアントは、通信するサービスの URL に基づいて、使用するサービス証明書を構成できます。</span><span class="sxs-lookup"><span data-stu-id="8cc79-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="8cc79-163">これは、クライアントが複数のサービス (エンド サービスと中間セキュリティ トークン サービス) と通信している可能性がある発行済みトークンのシナリオで特に便利です。</span><span class="sxs-lookup"><span data-stu-id="8cc79-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="8cc79-164">証明書に基づくメッセージ セキュリティを使用したバインドにおいて、この証明書を使用してサービスへのメッセージを暗号化します。サービスがクライアントへの応答に署名する際には、この証明書を使用することが要求されます。</span><span class="sxs-lookup"><span data-stu-id="8cc79-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="8cc79-165">バインディングにサービスの証明書が必要で、サービスの URL に対する特定の証明書が ScopedCertificates 内に存在しない場合は、既定の証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8cc79-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="8cc79-166">詳細についてを参照してください「証明書のスコープ」の[する方法: フェデレーション クライアントを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="8cc79-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cc79-167">例</span><span class="sxs-lookup"><span data-stu-id="8cc79-167">Example</span></span>  
 <span data-ttu-id="8cc79-168">次の例は、コレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="8cc79-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <serviceCertificate>  
     <scopedCertificates>  
      <add targetUri="http://www.contoso.com"   
       findValue="www.Contoso.com"   
       storeLocation="LocalMachine"  
       storeName="Root"   
       x509FindType="FindByIssuerName" />  
     </scopedCertificates>  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cc79-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cc79-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="8cc79-170">方法 : フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="8cc79-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="8cc79-171">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="8cc79-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="8cc79-172">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="8cc79-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="8cc79-173">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="8cc79-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

---
title: "&lt;scopedCertificates&gt; 要素の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eff535f7eb779a69c2368f3ad815f1eb124946ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="2b035-102">&lt;scopedCertificates&gt; 要素の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="2b035-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="2b035-103">範囲指定された証明書のコレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b035-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="2b035-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2b035-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b035-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="2b035-105">\<behaviors></span></span>  
<span data-ttu-id="2b035-106">endpointBehaviors セクション</span><span class="sxs-lookup"><span data-stu-id="2b035-106">endpointBehaviors section</span></span>  
<span data-ttu-id="2b035-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="2b035-107">\<behavior></span></span>  
<span data-ttu-id="2b035-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2b035-108">\<clientCredentials></span></span>  
<span data-ttu-id="2b035-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2b035-109">\<serviceCertificate></span></span>  
<span data-ttu-id="2b035-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2b035-110">\<scopedCertificates></span></span>  
<span data-ttu-id="2b035-111">\<追加 > 要素を\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2b035-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b035-112">構文</span><span class="sxs-lookup"><span data-stu-id="2b035-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b035-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2b035-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2b035-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2b035-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b035-115">属性</span><span class="sxs-lookup"><span data-stu-id="2b035-115">Attributes</span></span>  
  
|<span data-ttu-id="2b035-116">属性</span><span class="sxs-lookup"><span data-stu-id="2b035-116">Attribute</span></span>|<span data-ttu-id="2b035-117">説明</span><span class="sxs-lookup"><span data-stu-id="2b035-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b035-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="2b035-118">targetUri</span></span>|<span data-ttu-id="2b035-119">文字列。</span><span class="sxs-lookup"><span data-stu-id="2b035-119">String.</span></span> <span data-ttu-id="2b035-120">証明書に関連付けられているサービスの URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b035-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="2b035-121">findValue</span><span class="sxs-lookup"><span data-stu-id="2b035-121">findValue</span></span>|<span data-ttu-id="2b035-122">文字列。</span><span class="sxs-lookup"><span data-stu-id="2b035-122">String.</span></span> <span data-ttu-id="2b035-123">検索対象の値。</span><span class="sxs-lookup"><span data-stu-id="2b035-123">The value to search for.</span></span>|  
|<span data-ttu-id="2b035-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="2b035-124">x509FindType</span></span>|<span data-ttu-id="2b035-125">列挙値。</span><span class="sxs-lookup"><span data-stu-id="2b035-125">Enumeration.</span></span> <span data-ttu-id="2b035-126">検索する証明書フィールドのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="2b035-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="2b035-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2b035-127">storeLocation</span></span>|<span data-ttu-id="2b035-128">列挙値。</span><span class="sxs-lookup"><span data-stu-id="2b035-128">Enumeration.</span></span> <span data-ttu-id="2b035-129">検索する 2 つの格納場所のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="2b035-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="2b035-130">storeName</span><span class="sxs-lookup"><span data-stu-id="2b035-130">storeName</span></span>|<span data-ttu-id="2b035-131">列挙値。</span><span class="sxs-lookup"><span data-stu-id="2b035-131">Enumeration.</span></span> <span data-ttu-id="2b035-132">検索するシステム ストアのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="2b035-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="2b035-133">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="2b035-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="2b035-134">値</span><span class="sxs-lookup"><span data-stu-id="2b035-134">Value</span></span>|<span data-ttu-id="2b035-135">説明</span><span class="sxs-lookup"><span data-stu-id="2b035-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b035-136">String</span><span class="sxs-lookup"><span data-stu-id="2b035-136">String</span></span>|<span data-ttu-id="2b035-137">値は、検索されるフィールド (X509FindType 属性により指定される) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2b035-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="2b035-138">たとえば、サムプリント検索する場合、値は 16 進数の文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b035-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="2b035-139">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="2b035-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="2b035-140">値</span><span class="sxs-lookup"><span data-stu-id="2b035-140">Value</span></span>|<span data-ttu-id="2b035-141">説明</span><span class="sxs-lookup"><span data-stu-id="2b035-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b035-142">列挙型</span><span class="sxs-lookup"><span data-stu-id="2b035-142">Enumeration</span></span>|<span data-ttu-id="2b035-143">値は、FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage、FindBySubjectKeyIdentifier です。</span><span class="sxs-lookup"><span data-stu-id="2b035-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="2b035-144">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="2b035-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="2b035-145">値</span><span class="sxs-lookup"><span data-stu-id="2b035-145">Value</span></span>|<span data-ttu-id="2b035-146">説明</span><span class="sxs-lookup"><span data-stu-id="2b035-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b035-147">列挙型</span><span class="sxs-lookup"><span data-stu-id="2b035-147">Enumeration</span></span>|<span data-ttu-id="2b035-148">CurrentUser または LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="2b035-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="2b035-149">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="2b035-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="2b035-150">値</span><span class="sxs-lookup"><span data-stu-id="2b035-150">Value</span></span>|<span data-ttu-id="2b035-151">説明</span><span class="sxs-lookup"><span data-stu-id="2b035-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b035-152">列挙型</span><span class="sxs-lookup"><span data-stu-id="2b035-152">Enumeration</span></span>|<span data-ttu-id="2b035-153">値は、AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople、および TrustedPublisher です。</span><span class="sxs-lookup"><span data-stu-id="2b035-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b035-154">子要素</span><span class="sxs-lookup"><span data-stu-id="2b035-154">Child Elements</span></span>  
 <span data-ttu-id="2b035-155">なし。</span><span class="sxs-lookup"><span data-stu-id="2b035-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b035-156">親要素</span><span class="sxs-lookup"><span data-stu-id="2b035-156">Parent Elements</span></span>  
  
|<span data-ttu-id="2b035-157">要素</span><span class="sxs-lookup"><span data-stu-id="2b035-157">Element</span></span>|<span data-ttu-id="2b035-158">説明</span><span class="sxs-lookup"><span data-stu-id="2b035-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b035-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2b035-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="2b035-160">認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2b035-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b035-161">コメント</span><span class="sxs-lookup"><span data-stu-id="2b035-161">Remarks</span></span>  
 <span data-ttu-id="2b035-162">この要素を使用すると、クライアントは、通信するサービスの URL に基づいて、使用するサービス証明書を構成できます。</span><span class="sxs-lookup"><span data-stu-id="2b035-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="2b035-163">これは、クライアントが複数のサービス (エンド サービスと中間セキュリティ トークン サービス) と通信している可能性がある発行済みトークンのシナリオで特に便利です。</span><span class="sxs-lookup"><span data-stu-id="2b035-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="2b035-164">証明書に基づくメッセージ セキュリティを使用したバインドにおいて、この証明書を使用してサービスへのメッセージを暗号化します。サービスがクライアントへの応答に署名する際には、この証明書を使用することが要求されます。</span><span class="sxs-lookup"><span data-stu-id="2b035-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="2b035-165">バインディングにサービスの証明書が必要で、サービスの URL に対する特定の証明書が ScopedCertificates 内に存在しない場合は、既定の証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b035-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="2b035-166">詳細についてを参照してください「証明書のスコープ」の[する方法: フェデレーション クライアントを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b035-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b035-167">例</span><span class="sxs-lookup"><span data-stu-id="2b035-167">Example</span></span>  
 <span data-ttu-id="2b035-168">次の例は、コレクションに X.509 証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b035-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b035-169">参照</span><span class="sxs-lookup"><span data-stu-id="2b035-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="2b035-170">方法 : フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="2b035-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="2b035-171">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="2b035-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2b035-172">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2b035-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="2b035-173">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2b035-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

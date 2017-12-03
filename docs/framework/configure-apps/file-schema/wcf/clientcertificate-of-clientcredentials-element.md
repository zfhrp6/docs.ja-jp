---
title: "&lt;clientCredentials&gt; 要素の &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b42167491de72eff5f17dfd8f25ad862c118c23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="80fc8-102">&lt;clientCredentials&gt; 要素の &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="80fc8-102">&lt;clientCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="80fc8-103">サービスに対するクライアントの認証に使用する X.509 証明書を定義します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-103">Defines an X.509 certificate used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="80fc8-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="80fc8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80fc8-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="80fc8-105">\<behaviors></span></span>  
<span data-ttu-id="80fc8-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="80fc8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="80fc8-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="80fc8-107">\<behavior></span></span>  
<span data-ttu-id="80fc8-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="80fc8-108">\<clientCredentials></span></span>  
<span data-ttu-id="80fc8-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="80fc8-109">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fc8-110">構文</span><span class="sxs-lookup"><span data-stu-id="80fc8-110">Syntax</span></span>  
  
```xml  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80fc8-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="80fc8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="80fc8-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80fc8-113">属性</span><span class="sxs-lookup"><span data-stu-id="80fc8-113">Attributes</span></span>  
  
|<span data-ttu-id="80fc8-114">属性</span><span class="sxs-lookup"><span data-stu-id="80fc8-114">Attribute</span></span>|<span data-ttu-id="80fc8-115">説明</span><span class="sxs-lookup"><span data-stu-id="80fc8-115">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="80fc8-116">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="80fc8-116">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="80fc8-117">属性に格納されている型は、`X509FindType` 属性値の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="80fc8-117">The type contained in the attribute must satisfy the requirements of the `X509FindType` attribute value.</span></span> <span data-ttu-id="80fc8-118">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-118">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="80fc8-119">クライアントがサービスに対して自身を認証するために使用する X.509 証明書の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-119">Specifies the location of the X.509 certificate that the client uses to authenticate itself to the service.</span></span> <span data-ttu-id="80fc8-120">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="80fc8-121">-LocalMachine: ローカル マシンに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="80fc8-121">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="80fc8-122">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="80fc8-122">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="80fc8-123">既定は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-123">The default is LocalMachine.</span></span> <span data-ttu-id="80fc8-124">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-124">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|`storeName`|<span data-ttu-id="80fc8-125">検索する X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-125">Specifies the name of the X.509 certificate store to search.</span></span> <span data-ttu-id="80fc8-126">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="80fc8-127">-AddressBook: 他のユーザーのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="80fc8-128">-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="80fc8-129">-証明書ストアを CertificateAuthority: 中間証明機関 (Ca)。</span><span class="sxs-lookup"><span data-stu-id="80fc8-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="80fc8-130">-Disallowed: 失効した証明書のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="80fc8-131">-My: 証明書しますストアの個人用証明書。</span><span class="sxs-lookup"><span data-stu-id="80fc8-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="80fc8-132">信頼されたルート証明機関 (Ca) のルート: 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="80fc8-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="80fc8-133">-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="80fc8-134">-TrustedPublisher: 直接信頼された発行者のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="80fc8-135">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-135">The default is My.</span></span> <span data-ttu-id="80fc8-136">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreName> 型です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="80fc8-137">X509FindType</span><span class="sxs-lookup"><span data-stu-id="80fc8-137">X509FindType</span></span>|<span data-ttu-id="80fc8-138">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-138">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="80fc8-139">`findValue` 属性に格納されている型は、この属性の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="80fc8-139">The type contained in the `findValue` attribute must satisfy the requirements of this attribute.</span></span> <span data-ttu-id="80fc8-140">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="80fc8-141">は、FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="80fc8-141">-   FindByThumbPrint</span></span><br /><span data-ttu-id="80fc8-142">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="80fc8-142">-   FindBySubjectName</span></span><br /><span data-ttu-id="80fc8-143">-Findbysubjectdistinguishedname です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-143">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="80fc8-144">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="80fc8-144">-   FindByIssuerName</span></span><br /><span data-ttu-id="80fc8-145">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="80fc8-145">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="80fc8-146">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="80fc8-146">-   FindBySerialNumber</span></span><br /><span data-ttu-id="80fc8-147">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="80fc8-147">-   FindByTimeValid</span></span><br /><span data-ttu-id="80fc8-148">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="80fc8-148">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="80fc8-149">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="80fc8-149">-   FindByTemplateName</span></span><br /><span data-ttu-id="80fc8-150">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="80fc8-150">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="80fc8-151">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="80fc8-151">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="80fc8-152">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="80fc8-152">-   FindByExtension</span></span><br /><span data-ttu-id="80fc8-153">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="80fc8-153">-   FindByKeyUsage</span></span><br /><span data-ttu-id="80fc8-154">-Findbysubjectkeyidentifier です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-154">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="80fc8-155">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-155">The default value is FindBySubjectDistinguishedName.</span></span> <span data-ttu-id="80fc8-156">この属性は <xref:System.Security.Cryptography.X509Certificates.X509FindType> 型です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-156">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80fc8-157">子要素</span><span class="sxs-lookup"><span data-stu-id="80fc8-157">Child Elements</span></span>  
 <span data-ttu-id="80fc8-158">なし。</span><span class="sxs-lookup"><span data-stu-id="80fc8-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80fc8-159">親要素</span><span class="sxs-lookup"><span data-stu-id="80fc8-159">Parent Elements</span></span>  
  
|<span data-ttu-id="80fc8-160">要素</span><span class="sxs-lookup"><span data-stu-id="80fc8-160">Element</span></span>|<span data-ttu-id="80fc8-161">説明</span><span class="sxs-lookup"><span data-stu-id="80fc8-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80fc8-162">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="80fc8-162">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="80fc8-163">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-163">Specifies the credentials used to authenticate the client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80fc8-164">コメント</span><span class="sxs-lookup"><span data-stu-id="80fc8-164">Remarks</span></span>  
 <span data-ttu-id="80fc8-165">この構成要素は、この要素によるクライアントの認証に使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="80fc8-165">This configuration element specifies the certificate used to authenticate the client with this element.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="80fc8-166">[する方法: クライアント資格情報の値を指定](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)です。</span><span class="sxs-lookup"><span data-stu-id="80fc8-166"> [How to: Specify Client Credential Values](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80fc8-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="80fc8-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="80fc8-168">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="80fc8-168">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="80fc8-169">方法: クライアントの資格情報の値を指定する</span><span class="sxs-lookup"><span data-stu-id="80fc8-169">How to: Specify Client Credential Values</span></span>](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [<span data-ttu-id="80fc8-170">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="80fc8-170">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="80fc8-171">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="80fc8-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="80fc8-172">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="80fc8-172">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

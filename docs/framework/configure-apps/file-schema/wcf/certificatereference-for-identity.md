---
title: "&lt;identity&gt; の &lt;certificateReference&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 883ae318e32493013f009f3580ef102e4d39b3e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificatereferencegt-for-ltidentitygt"></a><span data-ttu-id="38b70-102">&lt;identity&gt; の &lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="38b70-102">&lt;certificateReference&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="38b70-103">X.509 証明書検証の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="38b70-103">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="38b70-104">この ID を持つエンドポイントに接続するセキュリティで保護された [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアントは、サーバーによって提示されるクレームに、この ID を構築するために使用された ID クレームが含まれていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="38b70-104">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity verifies that the claims presented by the server contain the identity claim used to construct this identity.</span></span>  
  
 <span data-ttu-id="38b70-105">\<id ></span><span class="sxs-lookup"><span data-stu-id="38b70-105">\<identity></span></span>  
<span data-ttu-id="38b70-106">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="38b70-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b70-107">構文</span><span class="sxs-lookup"><span data-stu-id="38b70-107">Syntax</span></span>  
  
```xml  
<certificateReference   
        findValue="String"   
    isChainIncluded="Boolean"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
  
    storeLocation="LocalMachine/CurrentUser"  
  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
</certificateReference>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38b70-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="38b70-108">Attributes and Elements</span></span>  
 <span data-ttu-id="38b70-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="38b70-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38b70-110">属性</span><span class="sxs-lookup"><span data-stu-id="38b70-110">Attributes</span></span>  
  
|<span data-ttu-id="38b70-111">属性</span><span class="sxs-lookup"><span data-stu-id="38b70-111">Attribute</span></span>|<span data-ttu-id="38b70-112">説明</span><span class="sxs-lookup"><span data-stu-id="38b70-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38b70-113">findValue</span><span class="sxs-lookup"><span data-stu-id="38b70-113">findValue</span></span>|<span data-ttu-id="38b70-114">X.509 証明書ストアで検索する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="38b70-114">Specifies the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="38b70-115">この属性に格納されている型は、指定された `X509FindType` 値の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="38b70-115">The type contained in this attribute must satisfy the requirements of the specified `X509FindType` value.</span></span> <span data-ttu-id="38b70-116">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="38b70-116">The default is an empty string.</span></span>|  
|<span data-ttu-id="38b70-117">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="38b70-117">isChainIncluded</span></span>|<span data-ttu-id="38b70-118">証明書チェーンを使用して検証を行うかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="38b70-118">A Boolean value that specifies if the validation is done using a certificate chain.</span></span>|  
|<span data-ttu-id="38b70-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="38b70-119">storeLocation</span></span>|<span data-ttu-id="38b70-120">クライアントがサーバーの証明書の検証に使用できる証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="38b70-120">Specifies the location of the certificate store that the client can use to validate the server’s certificate.</span></span><br /><br /> <span data-ttu-id="38b70-121">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="38b70-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="38b70-122">-LocalMachine: ローカル マシンに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="38b70-122">-   LocalMachine: The cert store assigned to the local machine.</span></span><br /><span data-ttu-id="38b70-123">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="38b70-123">-   CurrentUser: The cert store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="38b70-124">既定値は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="38b70-124">The default value is LocalMachine.</span></span><br /><br /> <span data-ttu-id="38b70-125">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="38b70-125">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|<span data-ttu-id="38b70-126">storeName</span><span class="sxs-lookup"><span data-stu-id="38b70-126">storeName</span></span>|<span data-ttu-id="38b70-127">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="38b70-127">Specifies the name of the X.509 certificate store to open.</span></span><br /><br /> <span data-ttu-id="38b70-128">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="38b70-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="38b70-129">-AddressBook: 他のユーザーのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="38b70-129">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="38b70-130">-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="38b70-130">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="38b70-131">-CertificateAuthority: 中間 Ca 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="38b70-131">-   CertificateAuthority: Certificate store for intermediate CAs.</span></span><br /><span data-ttu-id="38b70-132">-Disallowed: 失効した証明書のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="38b70-132">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="38b70-133">-My: 証明書しますストアの個人用証明書。</span><span class="sxs-lookup"><span data-stu-id="38b70-133">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="38b70-134">信頼されたルート Ca のルート: 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="38b70-134">-   Root: Certificate store for trusted root CAs.</span></span><br /><span data-ttu-id="38b70-135">-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="38b70-135">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="38b70-136">-TrustedPublisher: 直接信頼された発行者のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="38b70-136">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="38b70-137">既定値は、My です。</span><span class="sxs-lookup"><span data-stu-id="38b70-137">The default value is My.</span></span><br /><br /> <span data-ttu-id="38b70-138">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreName> 型です。</span><span class="sxs-lookup"><span data-stu-id="38b70-138">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="38b70-139">X509FindType</span><span class="sxs-lookup"><span data-stu-id="38b70-139">X509FindType</span></span>|<span data-ttu-id="38b70-140">実行する X.509 検索の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="38b70-140">Specifies the type of X.509 search to be executed.</span></span> <span data-ttu-id="38b70-141">`findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="38b70-141">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="38b70-142">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="38b70-142">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="38b70-143">は、FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="38b70-143">-   FindByThumbPrint</span></span><br /><span data-ttu-id="38b70-144">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="38b70-144">-   FindBySubjectName</span></span><br /><span data-ttu-id="38b70-145">-Findbysubjectdistinguishedname です。</span><span class="sxs-lookup"><span data-stu-id="38b70-145">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="38b70-146">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="38b70-146">-   FindByIssuerName</span></span><br /><span data-ttu-id="38b70-147">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="38b70-147">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="38b70-148">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="38b70-148">-   FindBySerialNumber</span></span><br /><span data-ttu-id="38b70-149">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="38b70-149">-   FindByTimeValid</span></span><br /><span data-ttu-id="38b70-150">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="38b70-150">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="38b70-151">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="38b70-151">-   FindByTemplateName</span></span><br /><span data-ttu-id="38b70-152">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="38b70-152">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="38b70-153">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="38b70-153">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="38b70-154">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="38b70-154">-   FindByExtension</span></span><br /><span data-ttu-id="38b70-155">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="38b70-155">-   FindByKeyUsage</span></span><br /><span data-ttu-id="38b70-156">-Findbysubjectkeyidentifier です。</span><span class="sxs-lookup"><span data-stu-id="38b70-156">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="38b70-157">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="38b70-157">The default value is FindBySubjectDistinguishedName.</span></span><br /><br /> <span data-ttu-id="38b70-158">この属性は <xref:System.Security.Cryptography.X509Certificates.X509FindType> 型です。</span><span class="sxs-lookup"><span data-stu-id="38b70-158">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38b70-159">子要素</span><span class="sxs-lookup"><span data-stu-id="38b70-159">Child Elements</span></span>  
 <span data-ttu-id="38b70-160">なし。</span><span class="sxs-lookup"><span data-stu-id="38b70-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38b70-161">親要素</span><span class="sxs-lookup"><span data-stu-id="38b70-161">Parent Elements</span></span>  
  
|<span data-ttu-id="38b70-162">要素</span><span class="sxs-lookup"><span data-stu-id="38b70-162">Element</span></span>|<span data-ttu-id="38b70-163">説明</span><span class="sxs-lookup"><span data-stu-id="38b70-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38b70-164">\<id ></span><span class="sxs-lookup"><span data-stu-id="38b70-164">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="38b70-165">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="38b70-165">Specifies settings that enable the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38b70-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="38b70-166">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>

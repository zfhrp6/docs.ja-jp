---
title: "&lt;peer&gt; の &lt;certificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf53ec9538834fc6fdb098bff4f78ef1c726ef5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-of-ltpeergt"></a><span data-ttu-id="be9da-102">&lt;peer&gt; の &lt;certificate&gt;</span><span class="sxs-lookup"><span data-stu-id="be9da-102">&lt;certificate&gt; of &lt;peer&gt;</span></span>
<span data-ttu-id="be9da-103">ピアで使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="be9da-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="be9da-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="be9da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be9da-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="be9da-105">\<behaviors></span></span>  
<span data-ttu-id="be9da-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="be9da-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="be9da-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="be9da-107">\<behavior></span></span>  
<span data-ttu-id="be9da-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="be9da-108">\<serviceCredentials></span></span>  
<span data-ttu-id="be9da-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="be9da-109">\<peer></span></span>  
<span data-ttu-id="be9da-110">\<証明書 ></span><span class="sxs-lookup"><span data-stu-id="be9da-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9da-111">構文</span><span class="sxs-lookup"><span data-stu-id="be9da-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be9da-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="be9da-112">Attributes and Elements</span></span>  
 <span data-ttu-id="be9da-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="be9da-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be9da-114">属性</span><span class="sxs-lookup"><span data-stu-id="be9da-114">Attributes</span></span>  
  
|<span data-ttu-id="be9da-115">属性</span><span class="sxs-lookup"><span data-stu-id="be9da-115">Attribute</span></span>|<span data-ttu-id="be9da-116">説明</span><span class="sxs-lookup"><span data-stu-id="be9da-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="be9da-117">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="be9da-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="be9da-118">属性に格納されている型は、指定された `x509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="be9da-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="be9da-119">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="be9da-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="be9da-120">クライアントがピアの証明書の検証に使用する X.509 証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="be9da-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="be9da-121">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="be9da-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="be9da-122">-LocalMachine: ローカル マシンに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="be9da-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="be9da-123">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="be9da-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="be9da-124">既定は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="be9da-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="be9da-125">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="be9da-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="be9da-126">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="be9da-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="be9da-127">-AddressBook: 他のユーザーのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="be9da-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="be9da-128">-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="be9da-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="be9da-129">-証明書ストアを CertificateAuthority: 中間証明機関 (Ca)。</span><span class="sxs-lookup"><span data-stu-id="be9da-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="be9da-130">-Disallowed: 失効した証明書のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="be9da-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="be9da-131">-My: 証明書しますストアの個人用証明書。</span><span class="sxs-lookup"><span data-stu-id="be9da-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="be9da-132">信頼されたルート証明機関 (Ca) のルート: 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="be9da-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="be9da-133">-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="be9da-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="be9da-134">-TrustedPublisher: 直接信頼された発行者のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="be9da-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="be9da-135">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="be9da-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="be9da-136">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="be9da-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="be9da-137">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="be9da-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="be9da-138">は、FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="be9da-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="be9da-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="be9da-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="be9da-140">-Findbysubjectdistinguishedname です。</span><span class="sxs-lookup"><span data-stu-id="be9da-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="be9da-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="be9da-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="be9da-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="be9da-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="be9da-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="be9da-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="be9da-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="be9da-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="be9da-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="be9da-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="be9da-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="be9da-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="be9da-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="be9da-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="be9da-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="be9da-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="be9da-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="be9da-149">-   FindByExtension</span></span><br /><span data-ttu-id="be9da-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="be9da-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="be9da-151">-Findbysubjectkeyidentifier です。</span><span class="sxs-lookup"><span data-stu-id="be9da-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="be9da-152">`findValue` 属性に格納されている型は、指定された `X509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="be9da-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="be9da-153">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="be9da-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be9da-154">子要素</span><span class="sxs-lookup"><span data-stu-id="be9da-154">Child Elements</span></span>  
 <span data-ttu-id="be9da-155">なし。</span><span class="sxs-lookup"><span data-stu-id="be9da-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be9da-156">親要素</span><span class="sxs-lookup"><span data-stu-id="be9da-156">Parent Elements</span></span>  
  
|<span data-ttu-id="be9da-157">要素</span><span class="sxs-lookup"><span data-stu-id="be9da-157">Element</span></span>|<span data-ttu-id="be9da-158">説明</span><span class="sxs-lookup"><span data-stu-id="be9da-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be9da-159">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="be9da-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="be9da-160">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="be9da-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be9da-161">コメント</span><span class="sxs-lookup"><span data-stu-id="be9da-161">Remarks</span></span>  
 <span data-ttu-id="be9da-162">この構成要素には、ピア メッシュ内の近隣ノードを認証するときに使用される `X509Certificate2` インスタンスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="be9da-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="be9da-163">ピア ツー ピア プログラミングの詳細については、次を参照してください。[ピア ツー ピア ネットワー キング](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)です。</span><span class="sxs-lookup"><span data-stu-id="be9da-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9da-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="be9da-164">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="be9da-165">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="be9da-165">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="be9da-166">ピア ツー ピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="be9da-166">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="be9da-167">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="be9da-167">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="be9da-168">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="be9da-168">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="be9da-169">ピア チャネル アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="be9da-169">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="be9da-170">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="be9da-170">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

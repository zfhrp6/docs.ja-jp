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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f46ebab92cbca616b06db5be6dc155a44558aa7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificategt-of-ltpeergt"></a><span data-ttu-id="0d964-102">&lt;peer&gt; の &lt;certificate&gt;</span><span class="sxs-lookup"><span data-stu-id="0d964-102">&lt;certificate&gt; of &lt;peer&gt;</span></span>
<span data-ttu-id="0d964-103">ピアで使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d964-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="0d964-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0d964-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d964-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="0d964-105">\<behaviors></span></span>  
<span data-ttu-id="0d964-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0d964-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0d964-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="0d964-107">\<behavior></span></span>  
<span data-ttu-id="0d964-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="0d964-108">\<serviceCredentials></span></span>  
<span data-ttu-id="0d964-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="0d964-109">\<peer></span></span>  
<span data-ttu-id="0d964-110">\<証明書 ></span><span class="sxs-lookup"><span data-stu-id="0d964-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d964-111">構文</span><span class="sxs-lookup"><span data-stu-id="0d964-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d964-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0d964-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0d964-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0d964-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d964-114">属性</span><span class="sxs-lookup"><span data-stu-id="0d964-114">Attributes</span></span>  
  
|<span data-ttu-id="0d964-115">属性</span><span class="sxs-lookup"><span data-stu-id="0d964-115">Attribute</span></span>|<span data-ttu-id="0d964-116">説明</span><span class="sxs-lookup"><span data-stu-id="0d964-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="0d964-117">X.509 証明書ストアで検索する値を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="0d964-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="0d964-118">属性に格納されている型は、指定された `x509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d964-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="0d964-119">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="0d964-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="0d964-120">クライアントがピアの証明書の検証に使用する X.509 証明書ストアの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d964-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="0d964-121">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="0d964-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0d964-122">-LocalMachine: ローカル マシンに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="0d964-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="0d964-123">-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="0d964-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="0d964-124">既定は LocalMachine です。</span><span class="sxs-lookup"><span data-stu-id="0d964-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="0d964-125">開く X.509 証明書ストアの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d964-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="0d964-126">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="0d964-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0d964-127">-AddressBook: 他のユーザーのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="0d964-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="0d964-128">-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="0d964-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="0d964-129">-証明書ストアを CertificateAuthority: 中間証明機関 (Ca)。</span><span class="sxs-lookup"><span data-stu-id="0d964-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="0d964-130">-Disallowed: 失効した証明書のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="0d964-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="0d964-131">-My: 証明書しますストアの個人用証明書。</span><span class="sxs-lookup"><span data-stu-id="0d964-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="0d964-132">信頼されたルート証明機関 (Ca) のルート: 証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="0d964-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="0d964-133">-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="0d964-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="0d964-134">-TrustedPublisher: 直接信頼された発行者のストアの証明書します。</span><span class="sxs-lookup"><span data-stu-id="0d964-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="0d964-135">既定値は My です。</span><span class="sxs-lookup"><span data-stu-id="0d964-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="0d964-136">実行する X.509 検索の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="0d964-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="0d964-137">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="0d964-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0d964-138">は、FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="0d964-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="0d964-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="0d964-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="0d964-140">-Findbysubjectdistinguishedname です。</span><span class="sxs-lookup"><span data-stu-id="0d964-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="0d964-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="0d964-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="0d964-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="0d964-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="0d964-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="0d964-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="0d964-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="0d964-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="0d964-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="0d964-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="0d964-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="0d964-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="0d964-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="0d964-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="0d964-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="0d964-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="0d964-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="0d964-149">-   FindByExtension</span></span><br /><span data-ttu-id="0d964-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="0d964-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="0d964-151">-Findbysubjectkeyidentifier です。</span><span class="sxs-lookup"><span data-stu-id="0d964-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="0d964-152">`findValue` 属性に格納されている型は、指定された `X509FindType` の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d964-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="0d964-153">既定値は FindBySubjectDistinguishedName です。</span><span class="sxs-lookup"><span data-stu-id="0d964-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d964-154">子要素</span><span class="sxs-lookup"><span data-stu-id="0d964-154">Child Elements</span></span>  
 <span data-ttu-id="0d964-155">なし。</span><span class="sxs-lookup"><span data-stu-id="0d964-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d964-156">親要素</span><span class="sxs-lookup"><span data-stu-id="0d964-156">Parent Elements</span></span>  
  
|<span data-ttu-id="0d964-157">要素</span><span class="sxs-lookup"><span data-stu-id="0d964-157">Element</span></span>|<span data-ttu-id="0d964-158">説明</span><span class="sxs-lookup"><span data-stu-id="0d964-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d964-159">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="0d964-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="0d964-160">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d964-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d964-161">コメント</span><span class="sxs-lookup"><span data-stu-id="0d964-161">Remarks</span></span>  
 <span data-ttu-id="0d964-162">この構成要素には、ピア メッシュ内の近隣ノードを認証するときに使用される `X509Certificate2` インスタンスが格納されます。</span><span class="sxs-lookup"><span data-stu-id="0d964-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="0d964-163">ピア ツー ピア プログラミングの詳細については、次を参照してください。[ピア ツー ピア ネットワー キング](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d964-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d964-164">参照</span><span class="sxs-lookup"><span data-stu-id="0d964-164">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="0d964-165">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="0d964-165">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="0d964-166">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="0d964-166">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="0d964-167">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="0d964-167">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="0d964-168">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="0d964-168">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="0d964-169">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="0d964-169">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="0d964-170">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="0d964-170">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

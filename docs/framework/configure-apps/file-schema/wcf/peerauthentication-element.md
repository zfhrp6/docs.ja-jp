---
title: "&lt;peerAuthentication&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eed1bac41babb970e3d85a8ae1aa5132f44e3621
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="1d266-102">&lt;peerAuthentication&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="1d266-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="1d266-103">ピアツーピア クライアントの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d266-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="1d266-104">ピア ツー ピア プログラミングを参照してください[ピア ツー ピア ネットワー キング](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)です。</span><span class="sxs-lookup"><span data-stu-id="1d266-104"> peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="1d266-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1d266-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d266-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="1d266-106">\<behaviors></span></span>  
<span data-ttu-id="1d266-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1d266-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="1d266-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1d266-108">\<behavior></span></span>  
<span data-ttu-id="1d266-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="1d266-109">\<clientCredentials></span></span>  
<span data-ttu-id="1d266-110">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="1d266-110">\<peer></span></span>  
<span data-ttu-id="1d266-111">\<PeerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1d266-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d266-112">構文</span><span class="sxs-lookup"><span data-stu-id="1d266-112">Syntax</span></span>  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d266-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1d266-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1d266-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d266-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d266-115">属性</span><span class="sxs-lookup"><span data-stu-id="1d266-115">Attributes</span></span>  
  
|<span data-ttu-id="1d266-116">属性</span><span class="sxs-lookup"><span data-stu-id="1d266-116">Attribute</span></span>|<span data-ttu-id="1d266-117">説明</span><span class="sxs-lookup"><span data-stu-id="1d266-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="1d266-118">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="1d266-118">Optional string.</span></span> <span data-ttu-id="1d266-119">カスタム型の検証に使用される型およびアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="1d266-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="1d266-120">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d266-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="1d266-121">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="1d266-121">Optional enumeration.</span></span> <span data-ttu-id="1d266-122">資格情報の検証に使用される 3 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d266-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1d266-123">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d266-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="1d266-124">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="1d266-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="1d266-125">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="1d266-125">Optional enumeration.</span></span> <span data-ttu-id="1d266-126">証明書失効リスト (CRL) のチェックに使用されるモードのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1d266-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="1d266-127">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="1d266-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="1d266-128">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="1d266-128">Optional enumeration.</span></span> <span data-ttu-id="1d266-129">2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="1d266-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1d266-130">この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d266-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="1d266-131">に対して検証が実行、**信頼されたユーザー**指定されたストアの場所に格納します。</span><span class="sxs-lookup"><span data-stu-id="1d266-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="1d266-132">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="1d266-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="1d266-133">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="1d266-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="1d266-134">値</span><span class="sxs-lookup"><span data-stu-id="1d266-134">Value</span></span>|<span data-ttu-id="1d266-135">説明</span><span class="sxs-lookup"><span data-stu-id="1d266-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d266-136">String</span><span class="sxs-lookup"><span data-stu-id="1d266-136">String</span></span>|<span data-ttu-id="1d266-137">タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d266-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="1d266-138">少なくとも、名前空間とタイプ名が必要です。</span><span class="sxs-lookup"><span data-stu-id="1d266-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="1d266-139">省略可能な情報は、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンです。</span><span class="sxs-lookup"><span data-stu-id="1d266-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="1d266-140">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="1d266-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="1d266-141">値</span><span class="sxs-lookup"><span data-stu-id="1d266-141">Value</span></span>|<span data-ttu-id="1d266-142">説明</span><span class="sxs-lookup"><span data-stu-id="1d266-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d266-143">列挙型</span><span class="sxs-lookup"><span data-stu-id="1d266-143">Enumeration</span></span>|<span data-ttu-id="1d266-144">`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="1d266-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="1d266-145">既定値は、`ChainTrust` です。</span><span class="sxs-lookup"><span data-stu-id="1d266-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="1d266-146">詳細については、次を参照してください。[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="1d266-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="1d266-147">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="1d266-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="1d266-148">値</span><span class="sxs-lookup"><span data-stu-id="1d266-148">Value</span></span>|<span data-ttu-id="1d266-149">説明</span><span class="sxs-lookup"><span data-stu-id="1d266-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d266-150">列挙型</span><span class="sxs-lookup"><span data-stu-id="1d266-150">Enumeration</span></span>|<span data-ttu-id="1d266-151">`NoCheck`、`Online`、`Offline` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="1d266-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="1d266-152">既定値は、`Online` です。</span><span class="sxs-lookup"><span data-stu-id="1d266-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="1d266-153">詳細については、次を参照してください。[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="1d266-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="1d266-154">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="1d266-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="1d266-155">値</span><span class="sxs-lookup"><span data-stu-id="1d266-155">Value</span></span>|<span data-ttu-id="1d266-156">説明</span><span class="sxs-lookup"><span data-stu-id="1d266-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1d266-157">列挙型</span><span class="sxs-lookup"><span data-stu-id="1d266-157">Enumeration</span></span>|<span data-ttu-id="1d266-158">`LocalMachine` または `CurrentUser` のいずれかの値にします。</span><span class="sxs-lookup"><span data-stu-id="1d266-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1d266-159">既定値は、`CurrentUser` です。</span><span class="sxs-lookup"><span data-stu-id="1d266-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="1d266-160">クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="1d266-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="1d266-161">クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。</span><span class="sxs-lookup"><span data-stu-id="1d266-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d266-162">子要素</span><span class="sxs-lookup"><span data-stu-id="1d266-162">Child Elements</span></span>  
 <span data-ttu-id="1d266-163">なし。</span><span class="sxs-lookup"><span data-stu-id="1d266-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d266-164">親要素</span><span class="sxs-lookup"><span data-stu-id="1d266-164">Parent Elements</span></span>  
  
|<span data-ttu-id="1d266-165">要素</span><span class="sxs-lookup"><span data-stu-id="1d266-165">Element</span></span>|<span data-ttu-id="1d266-166">説明</span><span class="sxs-lookup"><span data-stu-id="1d266-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d266-167">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="1d266-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="1d266-168">ピア サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="1d266-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d266-169">コメント</span><span class="sxs-lookup"><span data-stu-id="1d266-169">Remarks</span></span>  
 <span data-ttu-id="1d266-170">`<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。</span><span class="sxs-lookup"><span data-stu-id="1d266-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="1d266-171">この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="1d266-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="1d266-172">新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。</span><span class="sxs-lookup"><span data-stu-id="1d266-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="1d266-173">リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1d266-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="1d266-174">メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1d266-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d266-175">例</span><span class="sxs-lookup"><span data-stu-id="1d266-175">Example</span></span>  
 <span data-ttu-id="1d266-176">次のコードは、証明書検証モードを `PeerOrChainTrust` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1d266-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d266-177">参照</span><span class="sxs-lookup"><span data-stu-id="1d266-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="1d266-178">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="1d266-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1d266-179">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1d266-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="1d266-180">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="1d266-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="1d266-181">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="1d266-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="1d266-182">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="1d266-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)

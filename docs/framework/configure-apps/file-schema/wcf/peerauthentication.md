---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 103ee50e86a809ee4a5e36451fd9e6b99fc3bb2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="72a4a-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="72a4a-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="72a4a-103">ピア ノードで使用されるピア証明書の認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="72a4a-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="72a4a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72a4a-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="72a4a-105">\<behaviors></span></span>  
<span data-ttu-id="72a4a-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="72a4a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="72a4a-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="72a4a-107">\<behavior></span></span>  
<span data-ttu-id="72a4a-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="72a4a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="72a4a-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="72a4a-109">\<peer></span></span>  
<span data-ttu-id="72a4a-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="72a4a-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a4a-111">構文</span><span class="sxs-lookup"><span data-stu-id="72a4a-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72a4a-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="72a4a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="72a4a-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72a4a-114">属性</span><span class="sxs-lookup"><span data-stu-id="72a4a-114">Attributes</span></span>  
  
|<span data-ttu-id="72a4a-115">属性</span><span class="sxs-lookup"><span data-stu-id="72a4a-115">Attribute</span></span>|<span data-ttu-id="72a4a-116">説明</span><span class="sxs-lookup"><span data-stu-id="72a4a-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="72a4a-117">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-117">Optional enumeration.</span></span> <span data-ttu-id="72a4a-118">資格情報の検証に使用される 3 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="72a4a-119">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="72a4a-120">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72a4a-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="72a4a-121">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="72a4a-121">Optional string.</span></span> <span data-ttu-id="72a4a-122">ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="72a4a-123">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72a4a-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="72a4a-124">この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="72a4a-125"> には、信頼されたユーザーのストアに対してピア証明書を検証する既定のピア証明書検証が用意されており、</span><span class="sxs-lookup"><span data-stu-id="72a4a-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="72a4a-126">証明書が有効なルートまでつながっていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="72a4a-127">カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="72a4a-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="72a4a-128">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-128">Optional enumeration.</span></span> <span data-ttu-id="72a4a-129">証明書失効モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="72a4a-130">この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="72a4a-131">システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="72a4a-132">このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="72a4a-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="72a4a-133">失効チェックは、この属性を NoCheck に設定することにより無効にできます。</span><span class="sxs-lookup"><span data-stu-id="72a4a-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="72a4a-134">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-134">Optional enumeration.</span></span> <span data-ttu-id="72a4a-135">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] セキュリティ システムによりピア証明書を検証する、信頼されているユーザー ストアを指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="72a4a-136">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="72a4a-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72a4a-137">子要素</span><span class="sxs-lookup"><span data-stu-id="72a4a-137">Child Elements</span></span>  
 <span data-ttu-id="72a4a-138">なし。</span><span class="sxs-lookup"><span data-stu-id="72a4a-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72a4a-139">親要素</span><span class="sxs-lookup"><span data-stu-id="72a4a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="72a4a-140">要素</span><span class="sxs-lookup"><span data-stu-id="72a4a-140">Element</span></span>|<span data-ttu-id="72a4a-141">説明</span><span class="sxs-lookup"><span data-stu-id="72a4a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72a4a-142">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="72a4a-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="72a4a-143">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a4a-144">コメント</span><span class="sxs-lookup"><span data-stu-id="72a4a-144">Remarks</span></span>  
 <span data-ttu-id="72a4a-145">`<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="72a4a-146">この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="72a4a-147">新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。</span><span class="sxs-lookup"><span data-stu-id="72a4a-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="72a4a-148">リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="72a4a-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="72a4a-149">メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="72a4a-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a4a-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="72a4a-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="72a4a-151">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="72a4a-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="72a4a-152">ピア ツー ピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="72a4a-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="72a4a-153">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="72a4a-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="72a4a-154">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="72a4a-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="72a4a-155">ピア チャネル アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="72a4a-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)

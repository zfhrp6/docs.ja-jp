---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 656543ee1908c8fa332e373863aa4dc7ddecaba7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="c552c-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="c552c-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="c552c-103">メッセージ送信者により使用されるピア証明書の認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c552c-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="c552c-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c552c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c552c-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="c552c-105">\<behaviors></span></span>  
<span data-ttu-id="c552c-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c552c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c552c-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c552c-107">\<behavior></span></span>  
<span data-ttu-id="c552c-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c552c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c552c-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="c552c-109">\<peer></span></span>  
<span data-ttu-id="c552c-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="c552c-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c552c-111">構文</span><span class="sxs-lookup"><span data-stu-id="c552c-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c552c-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c552c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c552c-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c552c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c552c-114">属性</span><span class="sxs-lookup"><span data-stu-id="c552c-114">Attributes</span></span>  
  
|<span data-ttu-id="c552c-115">属性</span><span class="sxs-lookup"><span data-stu-id="c552c-115">Attribute</span></span>|<span data-ttu-id="c552c-116">説明</span><span class="sxs-lookup"><span data-stu-id="c552c-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="c552c-117">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c552c-117">Optional enumeration.</span></span> <span data-ttu-id="c552c-118">資格情報の検証に使用される 5 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c552c-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="c552c-119">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="c552c-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c552c-120">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c552c-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c552c-121">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="c552c-121">Optional string.</span></span> <span data-ttu-id="c552c-122">ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c552c-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c552c-123">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c552c-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="c552c-124">この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。</span><span class="sxs-lookup"><span data-stu-id="c552c-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c552c-125">Windows Communication Foundation (WCF) は、既定のピア証明書を確認するバリデーターは、信頼されたユーザー ストアに対してピア証明書を提供します。</span><span class="sxs-lookup"><span data-stu-id="c552c-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="c552c-126">証明書が有効なルートまでつながっていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="c552c-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="c552c-127">カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c552c-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="c552c-128">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c552c-128">Optional enumeration.</span></span> <span data-ttu-id="c552c-129">証明書失効モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c552c-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="c552c-130">この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="c552c-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="c552c-131">システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。</span><span class="sxs-lookup"><span data-stu-id="c552c-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="c552c-132">このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="c552c-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="c552c-133">失効チェックは、この属性を NoCheck に設定することにより無効にできます。</span><span class="sxs-lookup"><span data-stu-id="c552c-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c552c-134">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="c552c-134">Optional enumeration.</span></span> <span data-ttu-id="c552c-135">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] セキュリティ システムによりピア証明書を検証する、信頼されているユーザー ストアを指定します。</span><span class="sxs-lookup"><span data-stu-id="c552c-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="c552c-136">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="c552c-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c552c-137">子要素</span><span class="sxs-lookup"><span data-stu-id="c552c-137">Child Elements</span></span>  
 <span data-ttu-id="c552c-138">なし。</span><span class="sxs-lookup"><span data-stu-id="c552c-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c552c-139">親要素</span><span class="sxs-lookup"><span data-stu-id="c552c-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c552c-140">要素</span><span class="sxs-lookup"><span data-stu-id="c552c-140">Element</span></span>|<span data-ttu-id="c552c-141">説明</span><span class="sxs-lookup"><span data-stu-id="c552c-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c552c-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="c552c-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="c552c-143">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="c552c-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c552c-144">コメント</span><span class="sxs-lookup"><span data-stu-id="c552c-144">Remarks</span></span>  
 <span data-ttu-id="c552c-145">メッセージ認証を選択した場合は、この要素を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c552c-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="c552c-146">出力チャネルの各メッセージに署名によって提供される証明書を使って[\<証明書 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="c552c-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="c552c-147">すべてのメッセージは、アプリケーションに配信される前に、この要素の `customCertificateValidatorType` 属性で指定した検証を使用してメッセージ資格情報がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="c552c-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="c552c-148">検証は、資格情報を受け入れることも拒否することもできます。</span><span class="sxs-lookup"><span data-stu-id="c552c-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c552c-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="c552c-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="c552c-150">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="c552c-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c552c-151">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="c552c-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="c552c-152">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="c552c-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="c552c-153">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="c552c-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="c552c-154">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="c552c-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)

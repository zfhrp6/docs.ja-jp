---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 734deddc2924814b081ce80b8504fb77e78c095c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="562cc-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="562cc-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="562cc-103">メッセージ送信者により使用されるピア証明書の認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="562cc-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="562cc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="562cc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="562cc-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="562cc-105">\<behaviors></span></span>  
<span data-ttu-id="562cc-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="562cc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="562cc-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="562cc-107">\<behavior></span></span>  
<span data-ttu-id="562cc-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="562cc-108">\<serviceCredentials></span></span>  
<span data-ttu-id="562cc-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="562cc-109">\<peer></span></span>  
<span data-ttu-id="562cc-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="562cc-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="562cc-111">構文</span><span class="sxs-lookup"><span data-stu-id="562cc-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="562cc-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="562cc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="562cc-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="562cc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="562cc-114">属性</span><span class="sxs-lookup"><span data-stu-id="562cc-114">Attributes</span></span>  
  
|<span data-ttu-id="562cc-115">属性</span><span class="sxs-lookup"><span data-stu-id="562cc-115">Attribute</span></span>|<span data-ttu-id="562cc-116">説明</span><span class="sxs-lookup"><span data-stu-id="562cc-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="562cc-117">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="562cc-117">Optional enumeration.</span></span> <span data-ttu-id="562cc-118">資格情報の検証に使用される 5 つのモードのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="562cc-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="562cc-119">この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="562cc-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="562cc-120">`Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="562cc-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="562cc-121">省略可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="562cc-121">Optional string.</span></span> <span data-ttu-id="562cc-122">ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="562cc-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="562cc-123">`certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="562cc-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="562cc-124">この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。</span><span class="sxs-lookup"><span data-stu-id="562cc-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="562cc-125"> には、信頼されたユーザーのストアに対してピア証明書を検証する既定のピア証明書検証が用意されており、</span><span class="sxs-lookup"><span data-stu-id="562cc-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="562cc-126">証明書が有効なルートまでつながっていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="562cc-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="562cc-127">カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="562cc-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="562cc-128">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="562cc-128">Optional enumeration.</span></span> <span data-ttu-id="562cc-129">証明書失効モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="562cc-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="562cc-130">この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="562cc-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="562cc-131">システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。</span><span class="sxs-lookup"><span data-stu-id="562cc-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="562cc-132">このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。</span><span class="sxs-lookup"><span data-stu-id="562cc-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="562cc-133">失効チェックは、この属性を NoCheck に設定することにより無効にできます。</span><span class="sxs-lookup"><span data-stu-id="562cc-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="562cc-134">省略可能な列挙体です。</span><span class="sxs-lookup"><span data-stu-id="562cc-134">Optional enumeration.</span></span> <span data-ttu-id="562cc-135">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] セキュリティ システムによりピア証明書を検証する、信頼されているユーザー ストアを指定します。</span><span class="sxs-lookup"><span data-stu-id="562cc-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="562cc-136">この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。</span><span class="sxs-lookup"><span data-stu-id="562cc-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="562cc-137">子要素</span><span class="sxs-lookup"><span data-stu-id="562cc-137">Child Elements</span></span>  
 <span data-ttu-id="562cc-138">なし。</span><span class="sxs-lookup"><span data-stu-id="562cc-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="562cc-139">親要素</span><span class="sxs-lookup"><span data-stu-id="562cc-139">Parent Elements</span></span>  
  
|<span data-ttu-id="562cc-140">要素</span><span class="sxs-lookup"><span data-stu-id="562cc-140">Element</span></span>|<span data-ttu-id="562cc-141">説明</span><span class="sxs-lookup"><span data-stu-id="562cc-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="562cc-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="562cc-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="562cc-143">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="562cc-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="562cc-144">コメント</span><span class="sxs-lookup"><span data-stu-id="562cc-144">Remarks</span></span>  
 <span data-ttu-id="562cc-145">メッセージ認証を選択した場合は、この要素を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="562cc-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="562cc-146">出力チャネルの各メッセージに署名によって提供される証明書を使って[\<証明書 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="562cc-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="562cc-147">すべてのメッセージは、アプリケーションに配信される前に、この要素の `customCertificateValidatorType` 属性で指定した検証を使用してメッセージ資格情報がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="562cc-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="562cc-148">検証は、資格情報を受け入れることも拒否することもできます。</span><span class="sxs-lookup"><span data-stu-id="562cc-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562cc-149">参照</span><span class="sxs-lookup"><span data-stu-id="562cc-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="562cc-150">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="562cc-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="562cc-151">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="562cc-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="562cc-152">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="562cc-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="562cc-153">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="562cc-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="562cc-154">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="562cc-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)

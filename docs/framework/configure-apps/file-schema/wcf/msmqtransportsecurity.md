---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: eee2cb916d79bf3b79e882cd757b10344121f6b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="bcc59-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="bcc59-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="bcc59-103">カスタム バインドの MSMQ トランスポート セキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="bcc59-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bcc59-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bcc59-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="bcc59-105">\<bindings></span></span>  
<span data-ttu-id="bcc59-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bcc59-106">\<customBinding></span></span>  
<span data-ttu-id="bcc59-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="bcc59-107">\<binding></span></span>  
<span data-ttu-id="bcc59-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="bcc59-108">\<msmqIntegration></span></span>  
<span data-ttu-id="bcc59-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="bcc59-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc59-110">構文</span><span class="sxs-lookup"><span data-stu-id="bcc59-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcc59-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bcc59-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bcc59-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcc59-113">属性</span><span class="sxs-lookup"><span data-stu-id="bcc59-113">Attributes</span></span>  
  
|<span data-ttu-id="bcc59-114">属性</span><span class="sxs-lookup"><span data-stu-id="bcc59-114">Attribute</span></span>|<span data-ttu-id="bcc59-115">説明</span><span class="sxs-lookup"><span data-stu-id="bcc59-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="bcc59-116">MSMQ トランスポートによるメッセージの認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="bcc59-117">これが `None` に設定されている場合、`msmqProtectionLevel` 属性の値も `None` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcc59-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="bcc59-118">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bcc59-119">-None: 認証は行われません。</span><span class="sxs-lookup"><span data-stu-id="bcc59-119">-   None: No authentication.</span></span><br /><span data-ttu-id="bcc59-120">-Windows: 認証機構では、メッセージに関連付けられた SID の X.509 証明書を取得するのに Active Directory を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="bcc59-121">次に、これを使用してキューの ACL がチェックされ、ユーザーがキューに書き込む権限を持っていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="bcc59-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="bcc59-122">-Certificate: チャネルは、証明書ストアから証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="bcc59-123">既定値は Windows です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-123">The default value is Windows.</span></span> <span data-ttu-id="bcc59-124">この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="bcc59-125">メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="bcc59-126">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bcc59-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="bcc59-127">-   RC4Stream</span></span><br /><span data-ttu-id="bcc59-128">-AES</span><span class="sxs-lookup"><span data-stu-id="bcc59-128">-   AES</span></span><br /><br /> <span data-ttu-id="bcc59-129">既定値は RC4Stream です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-129">The default value is RC4Stream.</span></span> <span data-ttu-id="bcc59-130">この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="bcc59-131">MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="bcc59-132">暗号化を行うとメッセージの整合性が確保されますが、EncryptAndSign を使用するとメッセージの整合性と否認防止の両方が確保されます。つまり、メッセージは本当にその送信者から送信されていることになり、記載されている送信者が実際の送信者になります。</span><span class="sxs-lookup"><span data-stu-id="bcc59-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="bcc59-133">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bcc59-134">-None: 保護されません。</span><span class="sxs-lookup"><span data-stu-id="bcc59-134">-   None: No protection.</span></span><br /><span data-ttu-id="bcc59-135">-Sign: メッセージは署名されます。</span><span class="sxs-lookup"><span data-stu-id="bcc59-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="bcc59-136">-EncryptAndSign: メッセージが暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="bcc59-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="bcc59-137">既定値は Sign です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-137">The default value is Sign.</span></span> <span data-ttu-id="bcc59-138">この属性は <xref:System.Net.Security.ProtectionLevel> 型です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="bcc59-139">署名の一部としてダイジェストの計算に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="bcc59-140">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bcc59-141">MD5</span><span class="sxs-lookup"><span data-stu-id="bcc59-141">-   MD5</span></span><br /><span data-ttu-id="bcc59-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="bcc59-142">-   SHA1</span></span><br /><span data-ttu-id="bcc59-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="bcc59-143">-   SHA256</span></span><br /><span data-ttu-id="bcc59-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="bcc59-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="bcc59-145">既定値は SHA1 です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-145">The default value is SHA1.</span></span> <span data-ttu-id="bcc59-146">この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcc59-147">子要素</span><span class="sxs-lookup"><span data-stu-id="bcc59-147">Child Elements</span></span>  
 <span data-ttu-id="bcc59-148">なし。</span><span class="sxs-lookup"><span data-stu-id="bcc59-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcc59-149">親要素</span><span class="sxs-lookup"><span data-stu-id="bcc59-149">Parent Elements</span></span>  
  
|<span data-ttu-id="bcc59-150">要素</span><span class="sxs-lookup"><span data-stu-id="bcc59-150">Element</span></span>|<span data-ttu-id="bcc59-151">説明</span><span class="sxs-lookup"><span data-stu-id="bcc59-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcc59-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="bcc59-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="bcc59-153">Message Queuing (MSMQ) の送信側または受信側とのやり取りに必要な設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="bcc59-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="bcc59-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="bcc59-155">ネイティブ MSMQ プロトコルを使用する Windows Communication Foundation (WCF) サービスのキュー通信プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcc59-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcc59-156">コメント</span><span class="sxs-lookup"><span data-stu-id="bcc59-156">Remarks</span></span>  
 <span data-ttu-id="bcc59-157">トランスポート セキュリティの詳細については、次を参照してください。[トランスポート セキュリティ](../../../../../docs/framework/wcf/feature-details/transport-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="bcc59-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc59-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcc59-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bcc59-159">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="bcc59-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="bcc59-160">トランスポート</span><span class="sxs-lookup"><span data-stu-id="bcc59-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="bcc59-161">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="bcc59-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="bcc59-162">バインディング</span><span class="sxs-lookup"><span data-stu-id="bcc59-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bcc59-163">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="bcc59-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bcc59-164">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="bcc59-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bcc59-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bcc59-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="bcc59-166">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bcc59-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)

---
title: "&lt;netMsmqBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 51dcdc268a012cb8298dbc380c9c5d33a9db8d02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="1c279-102">&lt;netMsmqBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="1c279-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="1c279-103">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="1c279-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="1c279-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1c279-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c279-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="1c279-105">\<bindings></span></span>  
<span data-ttu-id="1c279-106">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="1c279-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="1c279-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="1c279-107">\<binding></span></span>  
<span data-ttu-id="1c279-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="1c279-108">\<security></span></span>  
<span data-ttu-id="1c279-109">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="1c279-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c279-110">構文</span><span class="sxs-lookup"><span data-stu-id="1c279-110">Syntax</span></span>  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c279-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1c279-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1c279-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c279-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c279-113">属性</span><span class="sxs-lookup"><span data-stu-id="1c279-113">Attributes</span></span>  
  
|<span data-ttu-id="1c279-114">属性</span><span class="sxs-lookup"><span data-stu-id="1c279-114">Attribute</span></span>|<span data-ttu-id="1c279-115">説明</span><span class="sxs-lookup"><span data-stu-id="1c279-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c279-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="1c279-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="1c279-117">MSMQ トランスポートによるメッセージの認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c279-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="1c279-118">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="1c279-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c279-119">-None: 認証は行われません。</span><span class="sxs-lookup"><span data-stu-id="1c279-119">-   None: No authentication.</span></span><br /><span data-ttu-id="1c279-120">-WindowsDomain: 認証機構は、メッセージに関連付けられたセキュリティ識別子の X.509 証明書を取得するのに Active Directory を使用します。</span><span class="sxs-lookup"><span data-stu-id="1c279-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="1c279-121">次に、これを使用してキューの ACL がチェックされ、ユーザーがキューへの書き込み権限を持っていることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="1c279-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="1c279-122">-Certificate: チャネルは、証明書ストアから証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c279-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="1c279-123">既定値は、`WindowsDomain` です。</span><span class="sxs-lookup"><span data-stu-id="1c279-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="1c279-124">この属性が `None` に設定されている場合、`msmqProtectionLevel` 属性も `None` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c279-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="1c279-125">この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="1c279-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="1c279-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="1c279-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="1c279-127">メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c279-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="1c279-128">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="1c279-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c279-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="1c279-129">-   RC4Stream</span></span><br /><span data-ttu-id="1c279-130">-AES</span><span class="sxs-lookup"><span data-stu-id="1c279-130">-   AES</span></span><br /><span data-ttu-id="1c279-131">-既定値は`RC4Stream`します。</span><span class="sxs-lookup"><span data-stu-id="1c279-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="1c279-132">この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="1c279-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="1c279-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="1c279-133">msmqProtectionLevel</span></span>|<span data-ttu-id="1c279-134">MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c279-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="1c279-135">暗号化を行うとメッセージの整合性が確保されますが、署名および暗号化を使用するとメッセージの整合性と否認防止の両方が確保されます。</span><span class="sxs-lookup"><span data-stu-id="1c279-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="1c279-136">つまり、メッセージは本当にその送信者から送信されていることになり、記載されている送信者が実際の送信者になります。</span><span class="sxs-lookup"><span data-stu-id="1c279-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="1c279-137">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="1c279-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c279-138">-None: 保護されません。</span><span class="sxs-lookup"><span data-stu-id="1c279-138">-   None: No protection.</span></span><br /><span data-ttu-id="1c279-139">-Sign: メッセージは署名されます。</span><span class="sxs-lookup"><span data-stu-id="1c279-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1c279-140">-EncryptAndSign: メッセージが暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="1c279-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="1c279-141">-既定値は`Sign`します。</span><span class="sxs-lookup"><span data-stu-id="1c279-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="1c279-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="1c279-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="1c279-143">メッセージ ダイジェストの計算に使用されるハッシュ アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c279-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="1c279-144">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="1c279-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c279-145">MD5</span><span class="sxs-lookup"><span data-stu-id="1c279-145">-   MD5</span></span><br /><span data-ttu-id="1c279-146">-SHA1</span><span class="sxs-lookup"><span data-stu-id="1c279-146">-   SHA1</span></span><br /><span data-ttu-id="1c279-147">-SHA256</span><span class="sxs-lookup"><span data-stu-id="1c279-147">-   SHA256</span></span><br /><span data-ttu-id="1c279-148">-SHA512</span><span class="sxs-lookup"><span data-stu-id="1c279-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="1c279-149">既定値は、`SHA1` です。</span><span class="sxs-lookup"><span data-stu-id="1c279-149">The default is `SHA1`.</span></span> <span data-ttu-id="1c279-150">この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。</span><span class="sxs-lookup"><span data-stu-id="1c279-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c279-151">子要素</span><span class="sxs-lookup"><span data-stu-id="1c279-151">Child Elements</span></span>  
 <span data-ttu-id="1c279-152">なし</span><span class="sxs-lookup"><span data-stu-id="1c279-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c279-153">親要素</span><span class="sxs-lookup"><span data-stu-id="1c279-153">Parent Elements</span></span>  
  
|<span data-ttu-id="1c279-154">要素</span><span class="sxs-lookup"><span data-stu-id="1c279-154">Element</span></span>|<span data-ttu-id="1c279-155">説明</span><span class="sxs-lookup"><span data-stu-id="1c279-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c279-156">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="1c279-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="1c279-157">キューに置かれているトランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="1c279-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c279-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c279-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="1c279-159">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="1c279-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="1c279-160">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="1c279-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1c279-161">バインディング</span><span class="sxs-lookup"><span data-stu-id="1c279-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1c279-162">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="1c279-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1c279-163">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="1c279-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1c279-164">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="1c279-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: "&lt;netTcpBinding&gt; の &lt;message&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab40ab1cd889665829e42072803010ad49e717a9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a><span data-ttu-id="634cf-102">&lt;netTcpBinding&gt; の &lt;message&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="634cf-102">&lt;message&gt; element of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="634cf-103">構成されているエンドポイントのメッセージ レベルのセキュリティ要件の種類を定義、 [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="634cf-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="634cf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="634cf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="634cf-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="634cf-105">\<bindings></span></span>  
<span data-ttu-id="634cf-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="634cf-106">\<netTcpBinding></span></span>  
<span data-ttu-id="634cf-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="634cf-107">\<binding></span></span>  
<span data-ttu-id="634cf-108">\<security></span><span class="sxs-lookup"><span data-stu-id="634cf-108">\<security></span></span>  
<span data-ttu-id="634cf-109">\<message></span><span class="sxs-lookup"><span data-stu-id="634cf-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="634cf-110">構文</span><span class="sxs-lookup"><span data-stu-id="634cf-110">Syntax</span></span>  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="634cf-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="634cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="634cf-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="634cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="634cf-113">属性</span><span class="sxs-lookup"><span data-stu-id="634cf-113">Attributes</span></span>  
  
|<span data-ttu-id="634cf-114">属性</span><span class="sxs-lookup"><span data-stu-id="634cf-114">Attribute</span></span>|<span data-ttu-id="634cf-115">説明</span><span class="sxs-lookup"><span data-stu-id="634cf-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="634cf-116">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="634cf-116">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="634cf-117">アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。</span><span class="sxs-lookup"><span data-stu-id="634cf-117">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="634cf-118">これらのアルゴリズムは、Security Policy Language (WS-SecurityPolicy) の仕様で指定されているアルゴリズムに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="634cf-118">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="634cf-119">指定できる値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="634cf-119">Possible values are shown in the following table.</span></span> <span data-ttu-id="634cf-120">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="634cf-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="634cf-121">サービス バインディングで指定されている `algorithmSuite` 値が既定値と異なると、Svcutil.exe を使用して構成ファイルを生成したときにファイルが正しく生成されません。この場合は、構成ファイルを手動で編集して、この属性を適切な値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="634cf-121">If the service binding specifies an `algorithmSuite` value that is not equal to the default, and you generate the configuration file using Svcutil.exe, then it is not generated correctly, and you must manually edit the configuration file to set this attribute to the desired value.</span></span>|  
|`clientCredentialType`|<span data-ttu-id="634cf-122">メッセージ ベースのセキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="634cf-122">Specifies the type of credential to be used when performing client authentication using Message-based security.</span></span> <span data-ttu-id="634cf-123">指定できる値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="634cf-123">Possible values are shown in the following table.</span></span> <span data-ttu-id="634cf-124">既定値は `UserName` です。</span><span class="sxs-lookup"><span data-stu-id="634cf-124">The default value is `UserName`.</span></span> <span data-ttu-id="634cf-125">この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="634cf-125">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="634cf-126">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="634cf-126">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="634cf-127">値</span><span class="sxs-lookup"><span data-stu-id="634cf-127">Value</span></span>|<span data-ttu-id="634cf-128">説明</span><span class="sxs-lookup"><span data-stu-id="634cf-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="634cf-129">Basic128</span><span class="sxs-lookup"><span data-stu-id="634cf-129">Basic128</span></span>|<span data-ttu-id="634cf-130">Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-130">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-131">Basic192</span><span class="sxs-lookup"><span data-stu-id="634cf-131">Basic192</span></span>|<span data-ttu-id="634cf-132">Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-132">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-133">Basic256</span><span class="sxs-lookup"><span data-stu-id="634cf-133">Basic256</span></span>|<span data-ttu-id="634cf-134">Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-134">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-135">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-135">Basic256Rsa15</span></span>|<span data-ttu-id="634cf-136">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-136">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-137">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-137">Basic192Rsa15</span></span>|<span data-ttu-id="634cf-138">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-138">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-139">TripleDes</span><span class="sxs-lookup"><span data-stu-id="634cf-139">TripleDes</span></span>|<span data-ttu-id="634cf-140">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-140">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-141">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-141">Basic128Rsa15</span></span>|<span data-ttu-id="634cf-142">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-142">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-143">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-143">TripleDesRsa15</span></span>|<span data-ttu-id="634cf-144">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-144">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-145">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="634cf-145">Basic128Sha256</span></span>|<span data-ttu-id="634cf-146">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-146">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-147">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="634cf-147">Basic192Sha256</span></span>|<span data-ttu-id="634cf-148">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-148">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-149">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="634cf-149">Basic256Sha256</span></span>|<span data-ttu-id="634cf-150">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-150">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-151">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="634cf-151">TripleDesSha256</span></span>|<span data-ttu-id="634cf-152">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-152">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="634cf-153">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-153">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="634cf-154">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-154">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-155">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-155">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="634cf-156">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-157">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-157">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="634cf-158">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="634cf-159">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="634cf-159">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="634cf-160">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="634cf-161">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="634cf-161">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="634cf-162">値</span><span class="sxs-lookup"><span data-stu-id="634cf-162">Value</span></span>|<span data-ttu-id="634cf-163">説明</span><span class="sxs-lookup"><span data-stu-id="634cf-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="634cf-164">なし</span><span class="sxs-lookup"><span data-stu-id="634cf-164">None</span></span>|<span data-ttu-id="634cf-165">サービスが匿名クライアントと対話できるようになります。</span><span class="sxs-lookup"><span data-stu-id="634cf-165">This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="634cf-166">サービス側では、サービスがクライアントの資格情報を必要としないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="634cf-166">On the service, this indicates that the service does not require any client credential.</span></span> <span data-ttu-id="634cf-167">クライアント側では、クライアントがクライアントの資格情報を提示しないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="634cf-167">On the client, this indicates that the client does not provide any client credential.</span></span>|  
|<span data-ttu-id="634cf-168">Windows</span><span class="sxs-lookup"><span data-stu-id="634cf-168">Windows</span></span>|<span data-ttu-id="634cf-169">SOAP 交換を、Windows 資格情報の認証されたコンテキストで行うことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="634cf-169">Allows the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span>|  
|<span data-ttu-id="634cf-170">UserName</span><span class="sxs-lookup"><span data-stu-id="634cf-170">UserName</span></span>|<span data-ttu-id="634cf-171">サービスが、UserName 資格情報を使用したクライアントの認証を要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="634cf-171">Allows the service to require that the client be authenticated using a UserName credential.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="634cf-172"> は、パスワード ダイジェストの送信、またはパスワードを使用したキーの派生、およびメッセージ セキュリティでのそのようなキーの使用をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="634cf-172"> does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="634cf-173">そのため、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では UserName 資格情報を使用する場合は、トランスポートが強制的にセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="634cf-173">As such, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport is secured when using UserName credentials.</span></span> <span data-ttu-id="634cf-174">この資格情報モードは、`negotiateServiceCredential` 属性に基づいて、同時実行可能な交換か、同時実行できないネゴシエーションのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="634cf-174">This credential mode results in either an interoperable exchange or a non-interoperable negotiation based on the `negotiateServiceCredential` attribute.</span></span>|  
|<span data-ttu-id="634cf-175">証明書</span><span class="sxs-lookup"><span data-stu-id="634cf-175">Certificate</span></span>|<span data-ttu-id="634cf-176">証明書を使用したクライアントの認証を、サービスで要求することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="634cf-176">Allows the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="634cf-177">メッセージ セキュリティ モードが使用され、`negotiateServiceCredential` 属性が `false` に設定されている場合、クライアントにサービス証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="634cf-177">If message security mode is used and the `negotiateServiceCredential` attribute is set to `false`, the client must be provisioned with the service certificate.</span></span>|  
|<span data-ttu-id="634cf-178">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="634cf-178">IssuedToken</span></span>|<span data-ttu-id="634cf-179">通常はセキュリティ トークン サービス (STS) により発行されるカスタム トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="634cf-179">Specifies a custom token, usually issued by a Security Token Service (STS).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="634cf-180">子要素</span><span class="sxs-lookup"><span data-stu-id="634cf-180">Child Elements</span></span>  
 <span data-ttu-id="634cf-181">なし</span><span class="sxs-lookup"><span data-stu-id="634cf-181">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="634cf-182">親要素</span><span class="sxs-lookup"><span data-stu-id="634cf-182">Parent Elements</span></span>  
  
|<span data-ttu-id="634cf-183">要素</span><span class="sxs-lookup"><span data-stu-id="634cf-183">Element</span></span>|<span data-ttu-id="634cf-184">説明</span><span class="sxs-lookup"><span data-stu-id="634cf-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="634cf-185">\<security></span><span class="sxs-lookup"><span data-stu-id="634cf-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="634cf-186"><xref:System.ServiceModel.Configuration.NetTcpBindingElement>のセキュリティ機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="634cf-186">Defines the security capabilities for the <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="634cf-187">コメント</span><span class="sxs-lookup"><span data-stu-id="634cf-187">Remarks</span></span>  
 <span data-ttu-id="634cf-188">メッセージは、SOAP メッセージの整合性と機密性を確保し、通信ピアの相互認証を行うために、メッセージ レベルのセキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="634cf-188">Message uses message-level security for the integrity and confidentiality of the SOAP message, and for mutual authentication of the communication peers.</span></span> <span data-ttu-id="634cf-189">バインディング上でこのセキュリティ モードが選択された場合、チャネル スタックは、メッセージ セキュリティ バインド要素を使用して構成され、SOAP メッセージは WS-Security\* 標準に従って保護されます。</span><span class="sxs-lookup"><span data-stu-id="634cf-189">If this security mode is selected on a binding, the channel stack is configured with message security binding elements and the SOAP messages are secured in compliance with WS-Security\* standards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634cf-190">参照</span><span class="sxs-lookup"><span data-stu-id="634cf-190">See Also</span></span>  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="634cf-191">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="634cf-191">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="634cf-192">バインディング</span><span class="sxs-lookup"><span data-stu-id="634cf-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="634cf-193">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="634cf-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="634cf-194">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="634cf-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="634cf-195">\<binding></span><span class="sxs-lookup"><span data-stu-id="634cf-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: "&lt;wsFederationHttpBinding&gt; の &lt;message&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb12cc0162cabd75f176c636b9cd4d00309bb594
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="73167-102">&lt;wsFederationHttpBinding&gt; の &lt;message&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="73167-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="73167-103">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="73167-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="73167-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="73167-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73167-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="73167-105">\<bindings></span></span>  
<span data-ttu-id="73167-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="73167-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="73167-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="73167-107">\<binding></span></span>  
<span data-ttu-id="73167-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="73167-108">\<security></span></span>  
<span data-ttu-id="73167-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="73167-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73167-110">構文</span><span class="sxs-lookup"><span data-stu-id="73167-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
     <binding >  
         <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                              <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
         </message>  
      </security>  
   </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73167-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="73167-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73167-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="73167-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73167-113">属性</span><span class="sxs-lookup"><span data-stu-id="73167-113">Attributes</span></span>  
  
|<span data-ttu-id="73167-114">属性</span><span class="sxs-lookup"><span data-stu-id="73167-114">Attribute</span></span>|<span data-ttu-id="73167-115">説明</span><span class="sxs-lookup"><span data-stu-id="73167-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73167-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="73167-116">algorithmSuite</span></span>|<span data-ttu-id="73167-117">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="73167-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="73167-118">この属性の有効な値については、「algorithmSuite 属性」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73167-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="73167-119">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="73167-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="73167-120">この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="73167-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="73167-121">これらのアルゴリズムは、Security Policy Language (WS-SecurityPolicy) の仕様で指定されているアルゴリズムに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="73167-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="73167-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="73167-122">issuedKeyType</span></span>|<span data-ttu-id="73167-123">発行されるキーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="73167-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="73167-124">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="73167-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="73167-125">SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="73167-125">-   SymmetricKey</span></span><br /><span data-ttu-id="73167-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="73167-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="73167-127">既定値は、`SymmetricKey` です。</span><span class="sxs-lookup"><span data-stu-id="73167-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="73167-128">この属性は <xref:System.IdentityModel.Tokens.SecurityKeyType> 型です。</span><span class="sxs-lookup"><span data-stu-id="73167-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="73167-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="73167-129">issuedTokenType</span></span>|<span data-ttu-id="73167-130">発行されるトークンの型を指定する URI を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="73167-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="73167-131">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="73167-131">The default is `null`.</span></span>|  
|<span data-ttu-id="73167-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="73167-132">negotiateServiceCredential</span></span>|<span data-ttu-id="73167-133">サービス資格情報がネゴシエーションの一部として交換されるか、帯域外で使用できるかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="73167-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="73167-134">既定値は `true` で、サービス資格情報がネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="73167-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="73167-135">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="73167-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="73167-136">値</span><span class="sxs-lookup"><span data-stu-id="73167-136">Value</span></span>|<span data-ttu-id="73167-137">説明</span><span class="sxs-lookup"><span data-stu-id="73167-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="73167-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="73167-138">Basic128</span></span>|<span data-ttu-id="73167-139">Basic128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="73167-140">Basic192</span></span>|<span data-ttu-id="73167-141">Basic192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="73167-142">Basic256</span></span>|<span data-ttu-id="73167-143">Basic256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-144">Basic256Rsa15</span></span>|<span data-ttu-id="73167-145">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-146">Basic192Rsa15</span></span>|<span data-ttu-id="73167-147">メッセージの暗号化には Basic192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="73167-148">TripleDes</span></span>|<span data-ttu-id="73167-149">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-150">Basic128Rsa15</span></span>|<span data-ttu-id="73167-151">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="73167-152">TripleDesRsa15</span></span>|<span data-ttu-id="73167-153">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="73167-154">Basic128Sha256</span></span>|<span data-ttu-id="73167-155">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="73167-156">Basic192Sha256</span></span>|<span data-ttu-id="73167-157">メッセージの暗号化には Basic192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="73167-158">Basic256Sha256</span></span>|<span data-ttu-id="73167-159">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="73167-160">TripleDesSha256</span></span>|<span data-ttu-id="73167-161">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="73167-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="73167-163">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="73167-165">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="73167-167">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="73167-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="73167-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="73167-169">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="73167-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73167-170">子要素</span><span class="sxs-lookup"><span data-stu-id="73167-170">Child Elements</span></span>  
  
|<span data-ttu-id="73167-171">要素</span><span class="sxs-lookup"><span data-stu-id="73167-171">Element</span></span>|<span data-ttu-id="73167-172">説明</span><span class="sxs-lookup"><span data-stu-id="73167-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73167-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="73167-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="73167-174">このバインディングのクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="73167-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="73167-175">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="73167-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="73167-176">issuer</span><span class="sxs-lookup"><span data-stu-id="73167-176">issuer</span></span>|<span data-ttu-id="73167-177">セキュリティ トークンを発行するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="73167-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="73167-178">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="73167-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="73167-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="73167-179">issuerMetadata</span></span>|<span data-ttu-id="73167-180">発行者のエンドポイント アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="73167-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="73167-181">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="73167-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="73167-182">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="73167-182">A collection of token request parameters.</span></span> <span data-ttu-id="73167-183">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="73167-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73167-184">親要素</span><span class="sxs-lookup"><span data-stu-id="73167-184">Parent Elements</span></span>  
  
|<span data-ttu-id="73167-185">要素</span><span class="sxs-lookup"><span data-stu-id="73167-185">Element</span></span>|<span data-ttu-id="73167-186">説明</span><span class="sxs-lookup"><span data-stu-id="73167-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73167-187">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="73167-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="73167-188">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="73167-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73167-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="73167-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="73167-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement`[サービスとクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="73167-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="73167-191">バインディング</span><span class="sxs-lookup"><span data-stu-id="73167-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="73167-192">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="73167-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="73167-193">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="73167-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="73167-194">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="73167-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

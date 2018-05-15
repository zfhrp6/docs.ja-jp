---
title: '&lt;wsFederationHttpBinding&gt; の &lt;message&gt; 要素'
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 24d7370eaadba08d449b886a09cb9903ca0a64c2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="c1e2d-102">&lt;wsFederationHttpBinding&gt; の &lt;message&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="c1e2d-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="c1e2d-103">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="c1e2d-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c1e2d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1e2d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c1e2d-105">\<bindings></span></span>  
<span data-ttu-id="c1e2d-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="c1e2d-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="c1e2d-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="c1e2d-107">\<binding></span></span>  
<span data-ttu-id="c1e2d-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="c1e2d-108">\<security></span></span>  
<span data-ttu-id="c1e2d-109">\<message></span><span class="sxs-lookup"><span data-stu-id="c1e2d-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e2d-110">構文</span><span class="sxs-lookup"><span data-stu-id="c1e2d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1e2d-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c1e2d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c1e2d-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1e2d-113">属性</span><span class="sxs-lookup"><span data-stu-id="c1e2d-113">Attributes</span></span>  
  
|<span data-ttu-id="c1e2d-114">属性</span><span class="sxs-lookup"><span data-stu-id="c1e2d-114">Attribute</span></span>|<span data-ttu-id="c1e2d-115">説明</span><span class="sxs-lookup"><span data-stu-id="c1e2d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1e2d-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="c1e2d-116">algorithmSuite</span></span>|<span data-ttu-id="c1e2d-117">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="c1e2d-118">この属性の有効な値については、「algorithmSuite 属性」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="c1e2d-119">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="c1e2d-120">この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="c1e2d-121">これらのアルゴリズムは、Security Policy Language (WS-SecurityPolicy) の仕様で指定されているアルゴリズムに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="c1e2d-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="c1e2d-122">issuedKeyType</span></span>|<span data-ttu-id="c1e2d-123">発行されるキーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="c1e2d-124">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c1e2d-125">SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="c1e2d-125">-   SymmetricKey</span></span><br /><span data-ttu-id="c1e2d-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="c1e2d-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="c1e2d-127">既定値は、`SymmetricKey` です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="c1e2d-128">この属性は <xref:System.IdentityModel.Tokens.SecurityKeyType> 型です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="c1e2d-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="c1e2d-129">issuedTokenType</span></span>|<span data-ttu-id="c1e2d-130">発行されるトークンの型を指定する URI を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="c1e2d-131">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-131">The default is `null`.</span></span>|  
|<span data-ttu-id="c1e2d-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="c1e2d-132">negotiateServiceCredential</span></span>|<span data-ttu-id="c1e2d-133">サービス資格情報がネゴシエーションの一部として交換されるか、帯域外で使用できるかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="c1e2d-134">既定値は `true` で、サービス資格情報がネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="c1e2d-135">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="c1e2d-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="c1e2d-136">値</span><span class="sxs-lookup"><span data-stu-id="c1e2d-136">Value</span></span>|<span data-ttu-id="c1e2d-137">説明</span><span class="sxs-lookup"><span data-stu-id="c1e2d-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1e2d-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="c1e2d-138">Basic128</span></span>|<span data-ttu-id="c1e2d-139">Basic128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="c1e2d-140">Basic192</span></span>|<span data-ttu-id="c1e2d-141">Basic192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="c1e2d-142">Basic256</span></span>|<span data-ttu-id="c1e2d-143">Basic256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-144">Basic256Rsa15</span></span>|<span data-ttu-id="c1e2d-145">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-146">Basic192Rsa15</span></span>|<span data-ttu-id="c1e2d-147">メッセージの暗号化には Basic192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="c1e2d-148">TripleDes</span></span>|<span data-ttu-id="c1e2d-149">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-150">Basic128Rsa15</span></span>|<span data-ttu-id="c1e2d-151">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-152">TripleDesRsa15</span></span>|<span data-ttu-id="c1e2d-153">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="c1e2d-154">Basic128Sha256</span></span>|<span data-ttu-id="c1e2d-155">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="c1e2d-156">Basic192Sha256</span></span>|<span data-ttu-id="c1e2d-157">メッセージの暗号化には Basic192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="c1e2d-158">Basic256Sha256</span></span>|<span data-ttu-id="c1e2d-159">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="c1e2d-160">TripleDesSha256</span></span>|<span data-ttu-id="c1e2d-161">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="c1e2d-163">メッセージの暗号化には Basic128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="c1e2d-165">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="c1e2d-167">メッセージの暗号化には Basic256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="c1e2d-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="c1e2d-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="c1e2d-169">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1e2d-170">子要素</span><span class="sxs-lookup"><span data-stu-id="c1e2d-170">Child Elements</span></span>  
  
|<span data-ttu-id="c1e2d-171">要素</span><span class="sxs-lookup"><span data-stu-id="c1e2d-171">Element</span></span>|<span data-ttu-id="c1e2d-172">説明</span><span class="sxs-lookup"><span data-stu-id="c1e2d-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1e2d-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="c1e2d-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="c1e2d-174">このバインディングのクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="c1e2d-175">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="c1e2d-176">issuer</span><span class="sxs-lookup"><span data-stu-id="c1e2d-176">issuer</span></span>|<span data-ttu-id="c1e2d-177">セキュリティ トークンを発行するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="c1e2d-178">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="c1e2d-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="c1e2d-179">issuerMetadata</span></span>|<span data-ttu-id="c1e2d-180">発行者のエンドポイント アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="c1e2d-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="c1e2d-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="c1e2d-182">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-182">A collection of token request parameters.</span></span> <span data-ttu-id="c1e2d-183">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1e2d-184">親要素</span><span class="sxs-lookup"><span data-stu-id="c1e2d-184">Parent Elements</span></span>  
  
|<span data-ttu-id="c1e2d-185">要素</span><span class="sxs-lookup"><span data-stu-id="c1e2d-185">Element</span></span>|<span data-ttu-id="c1e2d-186">説明</span><span class="sxs-lookup"><span data-stu-id="c1e2d-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1e2d-187">\<security></span><span class="sxs-lookup"><span data-stu-id="c1e2d-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="c1e2d-188">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="c1e2d-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1e2d-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1e2d-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="c1e2d-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [サービスとクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="c1e2d-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="c1e2d-191">バインディング</span><span class="sxs-lookup"><span data-stu-id="c1e2d-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c1e2d-192">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="c1e2d-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c1e2d-193">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="c1e2d-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c1e2d-194">\<binding></span><span class="sxs-lookup"><span data-stu-id="c1e2d-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: "&lt;ws2007FederationHttpBinding&gt; の &lt;message&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32361347665ee506b13d3be8a4257ca71e2629f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="8a1e5-102">&lt;ws2007FederationHttpBinding&gt; の &lt;message&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="8a1e5-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="8a1e5-103">メッセージ レベルのセキュリティの設定を定義、 [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="8a1e5-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8a1e5-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-105">\<bindings></span></span>  
<span data-ttu-id="8a1e5-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="8a1e5-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-107">\<binding></span></span>  
<span data-ttu-id="8a1e5-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-108">\<security></span></span>  
<span data-ttu-id="8a1e5-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a1e5-110">構文</span><span class="sxs-lookup"><span data-stu-id="8a1e5-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
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
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a1e5-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8a1e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8a1e5-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a1e5-113">属性</span><span class="sxs-lookup"><span data-stu-id="8a1e5-113">Attributes</span></span>  
  
|<span data-ttu-id="8a1e5-114">属性</span><span class="sxs-lookup"><span data-stu-id="8a1e5-114">Attribute</span></span>|<span data-ttu-id="8a1e5-115">説明</span><span class="sxs-lookup"><span data-stu-id="8a1e5-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="8a1e5-116">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-116">Optional.</span></span> <span data-ttu-id="8a1e5-117">メッセージの暗号化、署名、およびキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="8a1e5-118">アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="8a1e5-119">これらのアルゴリズムは、Security Policy Language (WS-SecurityPolicy) の仕様で指定されているアルゴリズムに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="8a1e5-120">それぞれの値については次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-120">See the following table for possible values.</span></span> <span data-ttu-id="8a1e5-121">既定値は Basic256 です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="8a1e5-122">発行されるキーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="8a1e5-123">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8a1e5-124">SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="8a1e5-124">-   SymmetricKey</span></span><br /><span data-ttu-id="8a1e5-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="8a1e5-125">-   PublicKey</span></span><br /><span data-ttu-id="8a1e5-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="8a1e5-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="8a1e5-127">既定値は SymmetricKey です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-127">The default is SymmetricKey.</span></span> <span data-ttu-id="8a1e5-128">この属性は <xref:System.IdentityModel.Tokens.SecurityKeyType> 型です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="8a1e5-129">発行されるトークンの型を指定する URI。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="8a1e5-130">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="8a1e5-131">サービス資格情報がネゴシエーションの一部として交換されるか、帯域外で使用できるかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="8a1e5-132">既定値は `true` で、サービス資格情報がネゴシエートされます。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="8a1e5-133">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="8a1e5-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="8a1e5-134">値</span><span class="sxs-lookup"><span data-stu-id="8a1e5-134">Value</span></span>|<span data-ttu-id="8a1e5-135">説明</span><span class="sxs-lookup"><span data-stu-id="8a1e5-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a1e5-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="8a1e5-136">Basic128</span></span>|<span data-ttu-id="8a1e5-137">Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="8a1e5-138">Basic192</span></span>|<span data-ttu-id="8a1e5-139">Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="8a1e5-140">Basic256</span></span>|<span data-ttu-id="8a1e5-141">Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-142">Basic256Rsa15</span></span>|<span data-ttu-id="8a1e5-143">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-144">Basic192Rsa15</span></span>|<span data-ttu-id="8a1e5-145">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="8a1e5-146">TripleDes</span></span>|<span data-ttu-id="8a1e5-147">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-148">Basic128Rsa15</span></span>|<span data-ttu-id="8a1e5-149">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-150">TripleDesRsa15</span></span>|<span data-ttu-id="8a1e5-151">TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="8a1e5-152">Basic128Sha256</span></span>|<span data-ttu-id="8a1e5-153">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="8a1e5-154">Basic192Sha256</span></span>|<span data-ttu-id="8a1e5-155">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="8a1e5-156">Basic256Sha256</span></span>|<span data-ttu-id="8a1e5-157">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="8a1e5-158">TripleDesSha256</span></span>|<span data-ttu-id="8a1e5-159">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="8a1e5-161">メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="8a1e5-163">メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="8a1e5-165">メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="8a1e5-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="8a1e5-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="8a1e5-167">メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a1e5-168">子要素</span><span class="sxs-lookup"><span data-stu-id="8a1e5-168">Child Elements</span></span>  
  
|<span data-ttu-id="8a1e5-169">要素</span><span class="sxs-lookup"><span data-stu-id="8a1e5-169">Element</span></span>|<span data-ttu-id="8a1e5-170">説明</span><span class="sxs-lookup"><span data-stu-id="8a1e5-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a1e5-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="8a1e5-172">このバインディングのクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="8a1e5-173">各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="8a1e5-174">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="8a1e5-175">セキュリティ トークンを発行するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="8a1e5-176">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="8a1e5-177">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="8a1e5-178">発行者のエンドポイント アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="8a1e5-179">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="8a1e5-180">トークン要求パラメーターのコレクション。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-180">A collection of token request parameters.</span></span> <span data-ttu-id="8a1e5-181">各パラメーターは、XML 要素です。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8a1e5-182">親要素</span><span class="sxs-lookup"><span data-stu-id="8a1e5-182">Parent Elements</span></span>  
  
|<span data-ttu-id="8a1e5-183">要素</span><span class="sxs-lookup"><span data-stu-id="8a1e5-183">Element</span></span>|<span data-ttu-id="8a1e5-184">説明</span><span class="sxs-lookup"><span data-stu-id="8a1e5-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a1e5-185">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="8a1e5-186">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a1e5-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a1e5-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="8a1e5-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement`[サービスとクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="8a1e5-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="8a1e5-189">バインディング</span><span class="sxs-lookup"><span data-stu-id="8a1e5-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8a1e5-190">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="8a1e5-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8a1e5-191">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="8a1e5-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8a1e5-192">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8a1e5-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

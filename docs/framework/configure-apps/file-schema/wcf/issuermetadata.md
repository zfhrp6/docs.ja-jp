---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 5f6b8d2f861c4d64a3b81407de4ce13b42d9b864
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="fc1dd-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="fc1dd-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="fc1dd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fc1dd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="fc1dd-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="fc1dd-104">\<bindings></span></span>  
<span data-ttu-id="fc1dd-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="fc1dd-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="fc1dd-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="fc1dd-106">\<binding></span></span>  
<span data-ttu-id="fc1dd-107">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="fc1dd-107">\<security></span></span>  
<span data-ttu-id="fc1dd-108">\<message></span><span class="sxs-lookup"><span data-stu-id="fc1dd-108">\<message></span></span>  
<span data-ttu-id="fc1dd-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="fc1dd-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc1dd-110">構文</span><span class="sxs-lookup"><span data-stu-id="fc1dd-110">Syntax</span></span>  
  
```xml  
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
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc1dd-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fc1dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fc1dd-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc1dd-113">属性</span><span class="sxs-lookup"><span data-stu-id="fc1dd-113">Attributes</span></span>  
  
|<span data-ttu-id="fc1dd-114">属性</span><span class="sxs-lookup"><span data-stu-id="fc1dd-114">Attribute</span></span>|<span data-ttu-id="fc1dd-115">説明</span><span class="sxs-lookup"><span data-stu-id="fc1dd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc1dd-116">address</span><span class="sxs-lookup"><span data-stu-id="fc1dd-116">address</span></span>|<span data-ttu-id="fc1dd-117">必須の `string` 属性です。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="fc1dd-118">エンドポイントのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="fc1dd-119">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-119">The address must be an absolute URI.</span></span> <span data-ttu-id="fc1dd-120">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc1dd-121">子要素</span><span class="sxs-lookup"><span data-stu-id="fc1dd-121">Child Elements</span></span>  
  
|<span data-ttu-id="fc1dd-122">要素</span><span class="sxs-lookup"><span data-stu-id="fc1dd-122">Element</span></span>|<span data-ttu-id="fc1dd-123">説明</span><span class="sxs-lookup"><span data-stu-id="fc1dd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc1dd-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="fc1dd-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="fc1dd-125">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="fc1dd-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="fc1dd-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="fc1dd-127">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc1dd-128">親要素</span><span class="sxs-lookup"><span data-stu-id="fc1dd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="fc1dd-129">要素</span><span class="sxs-lookup"><span data-stu-id="fc1dd-129">Element</span></span>|<span data-ttu-id="fc1dd-130">説明</span><span class="sxs-lookup"><span data-stu-id="fc1dd-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc1dd-131">\<message></span><span class="sxs-lookup"><span data-stu-id="fc1dd-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="fc1dd-132">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fc1dd-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc1dd-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc1dd-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="fc1dd-134">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="fc1dd-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="fc1dd-135">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="fc1dd-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="fc1dd-136">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="fc1dd-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="fc1dd-137">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="fc1dd-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

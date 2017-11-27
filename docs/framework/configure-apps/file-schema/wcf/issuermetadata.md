---
title: '&lt;issuerMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7e96c41348dea40806c2aca331d7f8ca9499a78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="9f6b5-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="9f6b5-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="9f6b5-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="9f6b5-104">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-104">\<bindings></span></span>  
<span data-ttu-id="9f6b5-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="9f6b5-106">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-106">\<binding></span></span>  
<span data-ttu-id="9f6b5-107">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-107">\<security></span></span>  
<span data-ttu-id="9f6b5-108">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-108">\<message></span></span>  
<span data-ttu-id="9f6b5-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f6b5-110">構文</span><span class="sxs-lookup"><span data-stu-id="9f6b5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f6b5-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9f6b5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f6b5-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f6b5-113">属性</span><span class="sxs-lookup"><span data-stu-id="9f6b5-113">Attributes</span></span>  
  
|<span data-ttu-id="9f6b5-114">属性</span><span class="sxs-lookup"><span data-stu-id="9f6b5-114">Attribute</span></span>|<span data-ttu-id="9f6b5-115">説明</span><span class="sxs-lookup"><span data-stu-id="9f6b5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f6b5-116">address</span><span class="sxs-lookup"><span data-stu-id="9f6b5-116">address</span></span>|<span data-ttu-id="9f6b5-117">必須の `string` 属性です。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="9f6b5-118">エンドポイントのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="9f6b5-119">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-119">The address must be an absolute URI.</span></span> <span data-ttu-id="9f6b5-120">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f6b5-121">子要素</span><span class="sxs-lookup"><span data-stu-id="9f6b5-121">Child Elements</span></span>  
  
|<span data-ttu-id="9f6b5-122">要素</span><span class="sxs-lookup"><span data-stu-id="9f6b5-122">Element</span></span>|<span data-ttu-id="9f6b5-123">説明</span><span class="sxs-lookup"><span data-stu-id="9f6b5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f6b5-124">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="9f6b5-125">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="9f6b5-126">\<id ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9f6b5-127">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f6b5-128">親要素</span><span class="sxs-lookup"><span data-stu-id="9f6b5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9f6b5-129">要素</span><span class="sxs-lookup"><span data-stu-id="9f6b5-129">Element</span></span>|<span data-ttu-id="9f6b5-130">説明</span><span class="sxs-lookup"><span data-stu-id="9f6b5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f6b5-131">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="9f6b5-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="9f6b5-132">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="9f6b5-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f6b5-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f6b5-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="9f6b5-134">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="9f6b5-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9f6b5-135">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="9f6b5-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9f6b5-136">カスタム バインドのセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="9f6b5-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="9f6b5-137">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="9f6b5-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

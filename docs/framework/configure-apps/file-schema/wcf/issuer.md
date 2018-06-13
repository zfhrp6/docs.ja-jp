---
title: '&lt;発行者&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 638b206f5372a654eca68d2f6ebb69bb0ac9e241
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750558"
---
# <a name="ltissuergt"></a><span data-ttu-id="b5469-102">&lt;発行者&gt;</span><span class="sxs-lookup"><span data-stu-id="b5469-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="b5469-103">セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5469-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="b5469-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b5469-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b5469-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="b5469-105">\<bindings></span></span>  
<span data-ttu-id="b5469-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b5469-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="b5469-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="b5469-107">\<binding></span></span>  
<span data-ttu-id="b5469-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="b5469-108">\<security></span></span>  
<span data-ttu-id="b5469-109">\<message></span><span class="sxs-lookup"><span data-stu-id="b5469-109">\<message></span></span>  
<span data-ttu-id="b5469-110">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="b5469-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5469-111">構文</span><span class="sxs-lookup"><span data-stu-id="b5469-111">Syntax</span></span>  
  
```xml  
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
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5469-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b5469-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b5469-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b5469-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5469-114">属性</span><span class="sxs-lookup"><span data-stu-id="b5469-114">Attributes</span></span>  
  
|<span data-ttu-id="b5469-115">属性</span><span class="sxs-lookup"><span data-stu-id="b5469-115">Attribute</span></span>|<span data-ttu-id="b5469-116">説明</span><span class="sxs-lookup"><span data-stu-id="b5469-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5469-117">address</span><span class="sxs-lookup"><span data-stu-id="b5469-117">address</span></span>|<span data-ttu-id="b5469-118">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="b5469-118">Required string.</span></span> <span data-ttu-id="b5469-119">STS の URL です。</span><span class="sxs-lookup"><span data-stu-id="b5469-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5469-120">子要素</span><span class="sxs-lookup"><span data-stu-id="b5469-120">Child Elements</span></span>  
  
|<span data-ttu-id="b5469-121">要素</span><span class="sxs-lookup"><span data-stu-id="b5469-121">Element</span></span>|<span data-ttu-id="b5469-122">説明</span><span class="sxs-lookup"><span data-stu-id="b5469-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5469-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="b5469-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="b5469-124">ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b5469-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="b5469-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="b5469-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b5469-126">発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="b5469-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5469-127">親要素</span><span class="sxs-lookup"><span data-stu-id="b5469-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b5469-128">要素</span><span class="sxs-lookup"><span data-stu-id="b5469-128">Element</span></span>|<span data-ttu-id="b5469-129">説明</span><span class="sxs-lookup"><span data-stu-id="b5469-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5469-130">\<message></span><span class="sxs-lookup"><span data-stu-id="b5469-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="b5469-131">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b5469-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5469-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5469-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="b5469-133">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="b5469-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b5469-134">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="b5469-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b5469-135">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="b5469-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b5469-136">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="b5469-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b5469-137">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="b5469-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="b5469-138">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="b5469-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

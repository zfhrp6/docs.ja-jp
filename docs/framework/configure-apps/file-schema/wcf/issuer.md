---
title: "&lt;発行者&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 235888aa97238489a51c2ea065efa0575e0d3724
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="c36c7-102">&lt;発行者&gt;</span><span class="sxs-lookup"><span data-stu-id="c36c7-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="c36c7-103">セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c36c7-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="c36c7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c36c7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c36c7-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="c36c7-105">\<bindings></span></span>  
<span data-ttu-id="c36c7-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="c36c7-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="c36c7-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="c36c7-107">\<binding></span></span>  
<span data-ttu-id="c36c7-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="c36c7-108">\<security></span></span>  
<span data-ttu-id="c36c7-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="c36c7-109">\<message></span></span>  
<span data-ttu-id="c36c7-110">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="c36c7-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c36c7-111">構文</span><span class="sxs-lookup"><span data-stu-id="c36c7-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c36c7-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c36c7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c36c7-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c36c7-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c36c7-114">属性</span><span class="sxs-lookup"><span data-stu-id="c36c7-114">Attributes</span></span>  
  
|<span data-ttu-id="c36c7-115">属性</span><span class="sxs-lookup"><span data-stu-id="c36c7-115">Attribute</span></span>|<span data-ttu-id="c36c7-116">説明</span><span class="sxs-lookup"><span data-stu-id="c36c7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c36c7-117">address</span><span class="sxs-lookup"><span data-stu-id="c36c7-117">address</span></span>|<span data-ttu-id="c36c7-118">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="c36c7-118">Required string.</span></span> <span data-ttu-id="c36c7-119">STS の URL です。</span><span class="sxs-lookup"><span data-stu-id="c36c7-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c36c7-120">子要素</span><span class="sxs-lookup"><span data-stu-id="c36c7-120">Child Elements</span></span>  
  
|<span data-ttu-id="c36c7-121">要素</span><span class="sxs-lookup"><span data-stu-id="c36c7-121">Element</span></span>|<span data-ttu-id="c36c7-122">説明</span><span class="sxs-lookup"><span data-stu-id="c36c7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c36c7-123">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="c36c7-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="c36c7-124">ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="c36c7-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="c36c7-125">\<id ></span><span class="sxs-lookup"><span data-stu-id="c36c7-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c36c7-126">発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="c36c7-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c36c7-127">親要素</span><span class="sxs-lookup"><span data-stu-id="c36c7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c36c7-128">要素</span><span class="sxs-lookup"><span data-stu-id="c36c7-128">Element</span></span>|<span data-ttu-id="c36c7-129">説明</span><span class="sxs-lookup"><span data-stu-id="c36c7-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c36c7-130">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="c36c7-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c36c7-131">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="c36c7-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c36c7-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="c36c7-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="c36c7-133">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="c36c7-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c36c7-134">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c36c7-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c36c7-135">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="c36c7-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c36c7-136">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c36c7-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="c36c7-137">カスタム バインドのセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="c36c7-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="c36c7-138">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="c36c7-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

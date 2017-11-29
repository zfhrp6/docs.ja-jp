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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dcd85443a802db2b6f2e0b1823dd6cb60ed8f705
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="8ee19-102">&lt;発行者&gt;</span><span class="sxs-lookup"><span data-stu-id="8ee19-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="8ee19-103">セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。</span><span class="sxs-lookup"><span data-stu-id="8ee19-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="8ee19-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8ee19-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8ee19-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8ee19-105">\<bindings></span></span>  
<span data-ttu-id="8ee19-106">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="8ee19-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="8ee19-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8ee19-107">\<binding></span></span>  
<span data-ttu-id="8ee19-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="8ee19-108">\<security></span></span>  
<span data-ttu-id="8ee19-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="8ee19-109">\<message></span></span>  
<span data-ttu-id="8ee19-110">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="8ee19-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee19-111">構文</span><span class="sxs-lookup"><span data-stu-id="8ee19-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ee19-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8ee19-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8ee19-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ee19-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ee19-114">属性</span><span class="sxs-lookup"><span data-stu-id="8ee19-114">Attributes</span></span>  
  
|<span data-ttu-id="8ee19-115">属性</span><span class="sxs-lookup"><span data-stu-id="8ee19-115">Attribute</span></span>|<span data-ttu-id="8ee19-116">説明</span><span class="sxs-lookup"><span data-stu-id="8ee19-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ee19-117">address</span><span class="sxs-lookup"><span data-stu-id="8ee19-117">address</span></span>|<span data-ttu-id="8ee19-118">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="8ee19-118">Required string.</span></span> <span data-ttu-id="8ee19-119">STS の URL です。</span><span class="sxs-lookup"><span data-stu-id="8ee19-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ee19-120">子要素</span><span class="sxs-lookup"><span data-stu-id="8ee19-120">Child Elements</span></span>  
  
|<span data-ttu-id="8ee19-121">要素</span><span class="sxs-lookup"><span data-stu-id="8ee19-121">Element</span></span>|<span data-ttu-id="8ee19-122">説明</span><span class="sxs-lookup"><span data-stu-id="8ee19-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ee19-123">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="8ee19-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="8ee19-124">ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="8ee19-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="8ee19-125">\<id ></span><span class="sxs-lookup"><span data-stu-id="8ee19-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8ee19-126">発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="8ee19-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ee19-127">親要素</span><span class="sxs-lookup"><span data-stu-id="8ee19-127">Parent Elements</span></span>  
  
|<span data-ttu-id="8ee19-128">要素</span><span class="sxs-lookup"><span data-stu-id="8ee19-128">Element</span></span>|<span data-ttu-id="8ee19-129">説明</span><span class="sxs-lookup"><span data-stu-id="8ee19-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ee19-130">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="8ee19-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8ee19-131">メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="8ee19-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ee19-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ee19-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="8ee19-133">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="8ee19-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8ee19-134">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="8ee19-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="8ee19-135">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="8ee19-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8ee19-136">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="8ee19-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="8ee19-137">カスタム バインドのセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="8ee19-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="8ee19-138">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="8ee19-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

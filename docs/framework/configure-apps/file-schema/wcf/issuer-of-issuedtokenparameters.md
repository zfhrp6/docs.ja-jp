---
title: "&lt;issuedTokenParameters&gt; の &lt;issuer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1eae3b472e33d4d0504ba487c8c871165af8cdf9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuergt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="bf4c2-102">&lt;issuedTokenParameters&gt; の &lt;issuer&gt;</span><span class="sxs-lookup"><span data-stu-id="bf4c2-102">&lt;issuer&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="bf4c2-103">セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="bf4c2-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bf4c2-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-105">\<bindings></span></span>  
<span data-ttu-id="bf4c2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-106">\<customBinding></span></span>  
<span data-ttu-id="bf4c2-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-107">\<binding></span></span>  
<span data-ttu-id="bf4c2-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-108">\<security></span></span>  
<span data-ttu-id="bf4c2-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-109">\<issuedTokenParameters></span></span>  
<span data-ttu-id="bf4c2-110">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf4c2-111">構文</span><span class="sxs-lookup"><span data-stu-id="bf4c2-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf4c2-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bf4c2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bf4c2-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf4c2-114">属性</span><span class="sxs-lookup"><span data-stu-id="bf4c2-114">Attributes</span></span>  
  
|<span data-ttu-id="bf4c2-115">属性</span><span class="sxs-lookup"><span data-stu-id="bf4c2-115">Attribute</span></span>|<span data-ttu-id="bf4c2-116">説明</span><span class="sxs-lookup"><span data-stu-id="bf4c2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf4c2-117">address</span><span class="sxs-lookup"><span data-stu-id="bf4c2-117">address</span></span>|<span data-ttu-id="bf4c2-118">必須の文字列。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-118">Required string.</span></span> <span data-ttu-id="bf4c2-119">STS の URL です。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf4c2-120">子要素</span><span class="sxs-lookup"><span data-stu-id="bf4c2-120">Child Elements</span></span>  
  
|<span data-ttu-id="bf4c2-121">要素</span><span class="sxs-lookup"><span data-stu-id="bf4c2-121">Element</span></span>|<span data-ttu-id="bf4c2-122">説明</span><span class="sxs-lookup"><span data-stu-id="bf4c2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf4c2-123">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="bf4c2-124">ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="bf4c2-125">\<id ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="bf4c2-126">発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf4c2-127">親要素</span><span class="sxs-lookup"><span data-stu-id="bf4c2-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bf4c2-128">要素</span><span class="sxs-lookup"><span data-stu-id="bf4c2-128">Element</span></span>|<span data-ttu-id="bf4c2-129">説明</span><span class="sxs-lookup"><span data-stu-id="bf4c2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf4c2-130">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-130">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="bf4c2-131">現在発行されているトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-131">Specifies the current issued token.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf4c2-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf4c2-132">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bf4c2-133">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="bf4c2-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="bf4c2-134">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="bf4c2-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="bf4c2-135">カスタム バインドのセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="bf4c2-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="bf4c2-136">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="bf4c2-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="bf4c2-137">バインディング</span><span class="sxs-lookup"><span data-stu-id="bf4c2-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bf4c2-138">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="bf4c2-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bf4c2-139">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="bf4c2-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bf4c2-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bf4c2-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="bf4c2-141">方法: SecurityBindingElement を使用してカスタム バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="bf4c2-141">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="bf4c2-142">カスタム バインディングのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="bf4c2-142">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

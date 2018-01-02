---
title: "&lt;issuedTokenParameters&gt; の &lt;issuerMetadata&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee0f6b2abe6ddfa81f236da47425ae586b56f0ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="90eb7-102">&lt;issuedTokenParameters&gt; の &lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="90eb7-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="90eb7-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="90eb7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="90eb7-104">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="90eb7-104">\<bindings></span></span>  
<span data-ttu-id="90eb7-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="90eb7-105">\<customBinding></span></span>  
<span data-ttu-id="90eb7-106">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="90eb7-106">\<binding></span></span>  
<span data-ttu-id="90eb7-107">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="90eb7-107">\<security></span></span>  
<span data-ttu-id="90eb7-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="90eb7-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="90eb7-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="90eb7-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90eb7-110">構文</span><span class="sxs-lookup"><span data-stu-id="90eb7-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90eb7-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="90eb7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="90eb7-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90eb7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90eb7-113">属性</span><span class="sxs-lookup"><span data-stu-id="90eb7-113">Attributes</span></span>  
  
|<span data-ttu-id="90eb7-114">属性</span><span class="sxs-lookup"><span data-stu-id="90eb7-114">Attribute</span></span>|<span data-ttu-id="90eb7-115">説明</span><span class="sxs-lookup"><span data-stu-id="90eb7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90eb7-116">address</span><span class="sxs-lookup"><span data-stu-id="90eb7-116">address</span></span>|<span data-ttu-id="90eb7-117">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb7-117">Required.</span></span> <span data-ttu-id="90eb7-118">エンドポイントのアドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="90eb7-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="90eb7-119">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90eb7-119">The address must be an absolute URI.</span></span> <span data-ttu-id="90eb7-120">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="90eb7-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90eb7-121">子要素</span><span class="sxs-lookup"><span data-stu-id="90eb7-121">Child Elements</span></span>  
  
|<span data-ttu-id="90eb7-122">要素</span><span class="sxs-lookup"><span data-stu-id="90eb7-122">Element</span></span>|<span data-ttu-id="90eb7-123">説明</span><span class="sxs-lookup"><span data-stu-id="90eb7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90eb7-124">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="90eb7-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="90eb7-125">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="90eb7-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="90eb7-126">\<id ></span><span class="sxs-lookup"><span data-stu-id="90eb7-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="90eb7-127">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="90eb7-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90eb7-128">親要素</span><span class="sxs-lookup"><span data-stu-id="90eb7-128">Parent Elements</span></span>  
  
|<span data-ttu-id="90eb7-129">要素</span><span class="sxs-lookup"><span data-stu-id="90eb7-129">Element</span></span>|<span data-ttu-id="90eb7-130">説明</span><span class="sxs-lookup"><span data-stu-id="90eb7-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90eb7-131">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="90eb7-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="90eb7-132">フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="90eb7-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90eb7-133">参照</span><span class="sxs-lookup"><span data-stu-id="90eb7-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="90eb7-134">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="90eb7-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="90eb7-135">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="90eb7-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="90eb7-136">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="90eb7-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="90eb7-137">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="90eb7-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="90eb7-138">バインディング</span><span class="sxs-lookup"><span data-stu-id="90eb7-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="90eb7-139">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="90eb7-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="90eb7-140">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="90eb7-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="90eb7-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="90eb7-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="90eb7-142">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="90eb7-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="90eb7-143">カスタム バインド セキュリティ</span><span class="sxs-lookup"><span data-stu-id="90eb7-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

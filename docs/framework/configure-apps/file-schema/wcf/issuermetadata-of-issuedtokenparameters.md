---
title: '&lt;issuedTokenParameters&gt; の &lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: 82c04fe71ec67b2c539dae9c41eb35350c72d923
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746515"
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a><span data-ttu-id="37cf8-102">&lt;issuedTokenParameters&gt; の &lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="37cf8-102">&lt;issuerMetadata&gt; of &lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="37cf8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37cf8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="37cf8-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="37cf8-104">\<bindings></span></span>  
<span data-ttu-id="37cf8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="37cf8-105">\<customBinding></span></span>  
<span data-ttu-id="37cf8-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="37cf8-106">\<binding></span></span>  
<span data-ttu-id="37cf8-107">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="37cf8-107">\<security></span></span>  
<span data-ttu-id="37cf8-108">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="37cf8-108">\<issuedTokenParameters></span></span>  
<span data-ttu-id="37cf8-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="37cf8-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37cf8-110">構文</span><span class="sxs-lookup"><span data-stu-id="37cf8-110">Syntax</span></span>  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37cf8-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="37cf8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="37cf8-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="37cf8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37cf8-113">属性</span><span class="sxs-lookup"><span data-stu-id="37cf8-113">Attributes</span></span>  
  
|<span data-ttu-id="37cf8-114">属性</span><span class="sxs-lookup"><span data-stu-id="37cf8-114">Attribute</span></span>|<span data-ttu-id="37cf8-115">説明</span><span class="sxs-lookup"><span data-stu-id="37cf8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37cf8-116">address</span><span class="sxs-lookup"><span data-stu-id="37cf8-116">address</span></span>|<span data-ttu-id="37cf8-117">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="37cf8-117">Required.</span></span> <span data-ttu-id="37cf8-118">エンドポイントのアドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="37cf8-118">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="37cf8-119">アドレスは、絶対 URI にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37cf8-119">The address must be an absolute URI.</span></span> <span data-ttu-id="37cf8-120">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="37cf8-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37cf8-121">子要素</span><span class="sxs-lookup"><span data-stu-id="37cf8-121">Child Elements</span></span>  
  
|<span data-ttu-id="37cf8-122">要素</span><span class="sxs-lookup"><span data-stu-id="37cf8-122">Element</span></span>|<span data-ttu-id="37cf8-123">説明</span><span class="sxs-lookup"><span data-stu-id="37cf8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37cf8-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="37cf8-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="37cf8-125">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="37cf8-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="37cf8-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="37cf8-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="37cf8-127">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="37cf8-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37cf8-128">親要素</span><span class="sxs-lookup"><span data-stu-id="37cf8-128">Parent Elements</span></span>  
  
|<span data-ttu-id="37cf8-129">要素</span><span class="sxs-lookup"><span data-stu-id="37cf8-129">Element</span></span>|<span data-ttu-id="37cf8-130">説明</span><span class="sxs-lookup"><span data-stu-id="37cf8-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37cf8-131">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="37cf8-131">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="37cf8-132">フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="37cf8-132">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37cf8-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="37cf8-133">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="37cf8-134">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="37cf8-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="37cf8-135">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="37cf8-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="37cf8-136">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="37cf8-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="37cf8-137">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="37cf8-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="37cf8-138">バインディング</span><span class="sxs-lookup"><span data-stu-id="37cf8-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="37cf8-139">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="37cf8-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="37cf8-140">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="37cf8-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="37cf8-141">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="37cf8-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="37cf8-142">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="37cf8-142">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="37cf8-143">カスタム バインド セキュリティ</span><span class="sxs-lookup"><span data-stu-id="37cf8-143">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

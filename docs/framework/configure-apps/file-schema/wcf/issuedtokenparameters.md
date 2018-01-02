---
title: '&lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac725e0c4fe590623ac82ec45bcf669a2e57179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="1c1e7-102">&lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="1c1e7-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="1c1e7-103">フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="1c1e7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1c1e7-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-105">\<bindings></span></span>  
<span data-ttu-id="1c1e7-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-106">\<customBinding></span></span>  
<span data-ttu-id="1c1e7-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-107">\<binding></span></span>  
<span data-ttu-id="1c1e7-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-108">\<security></span></span>  
<span data-ttu-id="1c1e7-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1e7-110">構文</span><span class="sxs-lookup"><span data-stu-id="1c1e7-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="1c1e7-111">型</span><span class="sxs-lookup"><span data-stu-id="1c1e7-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c1e7-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1c1e7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1c1e7-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c1e7-114">属性</span><span class="sxs-lookup"><span data-stu-id="1c1e7-114">Attributes</span></span>  
  
|<span data-ttu-id="1c1e7-115">属性</span><span class="sxs-lookup"><span data-stu-id="1c1e7-115">Attribute</span></span>|<span data-ttu-id="1c1e7-116">説明</span><span class="sxs-lookup"><span data-stu-id="1c1e7-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c1e7-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="1c1e7-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="1c1e7-118">バインドでサポートする必要があるセキュリティ仕様 (WS-Security、WS-Trust、WS-Secure Conversation、および WS-Security Policy) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="1c1e7-119">この値は、<xref:System.ServiceModel.MessageSecurityVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="1c1e7-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="1c1e7-120">inclusionMode</span></span>|<span data-ttu-id="1c1e7-121">トークン包含要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="1c1e7-122">この属性は <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="1c1e7-123">keySize</span><span class="sxs-lookup"><span data-stu-id="1c1e7-123">keySize</span></span>|<span data-ttu-id="1c1e7-124">トークン キー サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="1c1e7-125">既定値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-125">The default value is 256.</span></span>|  
|<span data-ttu-id="1c1e7-126">keyType</span><span class="sxs-lookup"><span data-stu-id="1c1e7-126">keyType</span></span>|<span data-ttu-id="1c1e7-127">キーの型を指定する <xref:System.IdentityModel.Tokens.SecurityKeyType> の有効な値。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="1c1e7-128">既定値は、`SymmetricKey` です。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="1c1e7-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="1c1e7-129">tokenType</span></span>|<span data-ttu-id="1c1e7-130">トークンの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-130">A string that specifies the token type.</span></span> <span data-ttu-id="1c1e7-131">既定値は、"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML" です。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c1e7-132">子要素</span><span class="sxs-lookup"><span data-stu-id="1c1e7-132">Child Elements</span></span>  
  
|<span data-ttu-id="1c1e7-133">要素</span><span class="sxs-lookup"><span data-stu-id="1c1e7-133">Element</span></span>|<span data-ttu-id="1c1e7-134">説明</span><span class="sxs-lookup"><span data-stu-id="1c1e7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c1e7-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="1c1e7-136">追加の要求パラメーターを指定する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="1c1e7-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="1c1e7-138">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="1c1e7-139">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1c1e7-140">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1c1e7-141">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="1c1e7-142">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="1c1e7-143">現在のトークンを発行するエンドポイントを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="1c1e7-144">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="1c1e7-145">トークン発行者のメタデータのエンドポイント アドレスを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1c1e7-146">親要素</span><span class="sxs-lookup"><span data-stu-id="1c1e7-146">Parent Elements</span></span>  
  
|<span data-ttu-id="1c1e7-147">要素</span><span class="sxs-lookup"><span data-stu-id="1c1e7-147">Element</span></span>|<span data-ttu-id="1c1e7-148">説明</span><span class="sxs-lookup"><span data-stu-id="1c1e7-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c1e7-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="1c1e7-150">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="1c1e7-151">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="1c1e7-152">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1c1e7-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c1e7-153">参照</span><span class="sxs-lookup"><span data-stu-id="1c1e7-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1c1e7-154">バインディング</span><span class="sxs-lookup"><span data-stu-id="1c1e7-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1c1e7-155">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="1c1e7-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1c1e7-156">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="1c1e7-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1c1e7-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1c1e7-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="1c1e7-158">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="1c1e7-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="1c1e7-159">カスタム バインド セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1c1e7-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="1c1e7-160">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="1c1e7-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1c1e7-161">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="1c1e7-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="1c1e7-162">カスタム バインドを使用したセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="1c1e7-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="1c1e7-163">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="1c1e7-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

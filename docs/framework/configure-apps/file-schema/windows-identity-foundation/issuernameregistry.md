---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b695cc6d66e5b9e45bb6a5fd22d594bc22ea3cba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="29daf-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="29daf-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="29daf-103">トークン ハンドラーはコレクション内のハンドラーによって使用される発行者名レジストリを構成します。</span><span class="sxs-lookup"><span data-stu-id="29daf-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="29daf-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="29daf-104">\<system.identityModel></span></span>  
<span data-ttu-id="29daf-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="29daf-105">\<identityConfiguration></span></span>  
<span data-ttu-id="29daf-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="29daf-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="29daf-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="29daf-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="29daf-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="29daf-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29daf-109">構文</span><span class="sxs-lookup"><span data-stu-id="29daf-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29daf-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="29daf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="29daf-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="29daf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29daf-112">属性</span><span class="sxs-lookup"><span data-stu-id="29daf-112">Attributes</span></span>  
  
|<span data-ttu-id="29daf-113">属性</span><span class="sxs-lookup"><span data-stu-id="29daf-113">Attribute</span></span>|<span data-ttu-id="29daf-114">説明</span><span class="sxs-lookup"><span data-stu-id="29daf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29daf-115">型</span><span class="sxs-lookup"><span data-stu-id="29daf-115">type</span></span>|<span data-ttu-id="29daf-116">派生する型、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラスです。</span><span class="sxs-lookup"><span data-stu-id="29daf-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="29daf-117">詳細については、ユーザー設定を指定する方法についての`type`、[カスタム型の参照] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29daf-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29daf-118">子要素</span><span class="sxs-lookup"><span data-stu-id="29daf-118">Child Elements</span></span>  
  
|<span data-ttu-id="29daf-119">要素</span><span class="sxs-lookup"><span data-stu-id="29daf-119">Element</span></span>|<span data-ttu-id="29daf-120">説明</span><span class="sxs-lookup"><span data-stu-id="29daf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29daf-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="29daf-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="29daf-122">ときに、`type`属性構成ベースの発行者名レジストリの指定 (、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラス) では、 [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29daf-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="29daf-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)要素がかかることが`<add>`、 `<clear>`、または`<remove>`子要素としての要素。</span><span class="sxs-lookup"><span data-stu-id="29daf-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29daf-124">親要素</span><span class="sxs-lookup"><span data-stu-id="29daf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="29daf-125">要素</span><span class="sxs-lookup"><span data-stu-id="29daf-125">Element</span></span>|<span data-ttu-id="29daf-126">説明</span><span class="sxs-lookup"><span data-stu-id="29daf-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29daf-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="29daf-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="29daf-128">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="29daf-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29daf-129">コメント</span><span class="sxs-lookup"><span data-stu-id="29daf-129">Remarks</span></span>  
 <span data-ttu-id="29daf-130">すべての発行者トークンは、発行者名レジストリを使用して検証されます。</span><span class="sxs-lookup"><span data-stu-id="29daf-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="29daf-131">これはから派生するオブジェクト、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>クラスです。</span><span class="sxs-lookup"><span data-stu-id="29daf-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="29daf-132">発行者名レジストリを使用して、対応する発行元によって生成されるトークンの署名を確認するために必要な暗号化マテリアルをニーモニック名を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="29daf-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="29daf-133">発行者名レジストリでは、証明書利用者 (rp) アプリケーションで信頼される発行者の一覧を管理します。</span><span class="sxs-lookup"><span data-stu-id="29daf-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="29daf-134">使用して、発行者名レジストリの型を指定、`type`属性。</span><span class="sxs-lookup"><span data-stu-id="29daf-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="29daf-135">`<issuerNameRegistry>`要素は、指定した種類の構成を提供する 1 つまたは複数の子要素を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="29daf-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="29daf-136">オーバーライドすることでこれらの子要素を処理するロジックを提供する、<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="29daf-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="29daf-137">WIF では、単一の発行者名レジストリの型を既定で、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラスです。</span><span class="sxs-lookup"><span data-stu-id="29daf-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="29daf-138">このクラスは、一連の構成で指定されている信頼された発行者の証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="29daf-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="29daf-139">構成の子要素では、必要な`<trustedIssuers>`、信頼された発行者の証明書のコレクションが構成されています。</span><span class="sxs-lookup"><span data-stu-id="29daf-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="29daf-140">信頼された証明書が、ASN.1 を使用してエンコードされた証明書の拇印の形式とが追加または削除をコレクションからを使用して指定`<add>`、 `<clear>`、または`<remove>`要素。</span><span class="sxs-lookup"><span data-stu-id="29daf-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="29daf-141">`<issuerNameRegistry>`要素として表されます、<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="29daf-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29daf-142">指定する、`<issuerNameRegistry>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。</span><span class="sxs-lookup"><span data-stu-id="29daf-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="29daf-143">上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="29daf-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29daf-144">例</span><span class="sxs-lookup"><span data-stu-id="29daf-144">Example</span></span>  
 <span data-ttu-id="29daf-145">次の XML では、名前のレジストリをベースの構成の発行者を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29daf-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29daf-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="29daf-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>

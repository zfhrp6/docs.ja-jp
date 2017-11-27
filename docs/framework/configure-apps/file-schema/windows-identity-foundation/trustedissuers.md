---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="9d963-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="9d963-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="9d963-103">構成ベースの発行者名レジストリによって使用される信頼された発行者の証明書の一覧の構成 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。</span><span class="sxs-lookup"><span data-stu-id="9d963-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="9d963-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="9d963-104">\<system.identityModel></span></span>  
<span data-ttu-id="9d963-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9d963-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9d963-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="9d963-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9d963-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9d963-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="9d963-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="9d963-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="9d963-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="9d963-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d963-110">構文</span><span class="sxs-lookup"><span data-stu-id="9d963-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d963-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9d963-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9d963-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d963-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d963-113">属性</span><span class="sxs-lookup"><span data-stu-id="9d963-113">Attributes</span></span>  
 <span data-ttu-id="9d963-114">なし</span><span class="sxs-lookup"><span data-stu-id="9d963-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d963-115">子要素</span><span class="sxs-lookup"><span data-stu-id="9d963-115">Child Elements</span></span>  
  
|<span data-ttu-id="9d963-116">要素</span><span class="sxs-lookup"><span data-stu-id="9d963-116">Element</span></span>|<span data-ttu-id="9d963-117">説明</span><span class="sxs-lookup"><span data-stu-id="9d963-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="9d963-118">証明書を信頼された発行者のコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="9d963-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="9d963-119">証明書を指定した、`thumbprint`属性。</span><span class="sxs-lookup"><span data-stu-id="9d963-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="9d963-120">この属性は必須であり、証明書の拇印のエンコードされた ASN.1 フォームを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d963-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="9d963-121">`name`属性は省略可能、証明書のフレンドリ名を指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d963-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="9d963-122">信頼された発行者のコレクションからすべての証明書をクリアします。</span><span class="sxs-lookup"><span data-stu-id="9d963-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="9d963-123">証明書を信頼された発行者のコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="9d963-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="9d963-124">証明書を指定した、`thumbprint`属性。</span><span class="sxs-lookup"><span data-stu-id="9d963-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="9d963-125">この属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="9d963-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d963-126">親要素</span><span class="sxs-lookup"><span data-stu-id="9d963-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9d963-127">要素</span><span class="sxs-lookup"><span data-stu-id="9d963-127">Element</span></span>|<span data-ttu-id="9d963-128">説明</span><span class="sxs-lookup"><span data-stu-id="9d963-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d963-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="9d963-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="9d963-130">発行者名レジストリを構成します。</span><span class="sxs-lookup"><span data-stu-id="9d963-130">Configures the issuer name registry.</span></span> <span data-ttu-id="9d963-131">**重要:** 、`type`の属性、`<issuerNameRegistry>`要素を参照する必要があります、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>のクラス、`<trustedIssuers>`を有効にする要素。</span><span class="sxs-lookup"><span data-stu-id="9d963-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d963-132">コメント</span><span class="sxs-lookup"><span data-stu-id="9d963-132">Remarks</span></span>  
 <span data-ttu-id="9d963-133">Windows Identity Foundation (WIF) の単一実装を提供する、<xref:System.IdentityModel.Tokens.IssuerNameRegistry>すぐ、クラス、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>クラスです。</span><span class="sxs-lookup"><span data-stu-id="9d963-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="9d963-134">発行者名レジストリの構成は、構成から読み込まれる信頼された発行者の一覧を保持します。</span><span class="sxs-lookup"><span data-stu-id="9d963-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="9d963-135">一覧は、各発行者名を発行元によって生成されるトークンの署名を検証するために必要な X.509 証明書に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="9d963-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="9d963-136">信頼された発行者の証明書の一覧を指定、`<trustedIssuers>`要素。</span><span class="sxs-lookup"><span data-stu-id="9d963-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="9d963-137">リスト内の各要素は、その発行者によって生成されるトークンの署名を検証するために必要な X.509 証明書にニーモニック発行者名を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="9d963-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="9d963-138">信頼された証明書が証明書の拇印の形式でエンコードされた ASN.1 を使用して指定されを使用して、コレクションに追加されます`<add>`要素。</span><span class="sxs-lookup"><span data-stu-id="9d963-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="9d963-139">オフまたはを使用して、一覧から発行者 (証明書) を削除することができます、`<clear>`と`<remove>`要素。</span><span class="sxs-lookup"><span data-stu-id="9d963-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="9d963-140">`type`の属性、`<issuerNameRegistry>`要素を参照する必要があります、<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>のクラス、`<trustedIssuers>`を有効にする要素。</span><span class="sxs-lookup"><span data-stu-id="9d963-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d963-141">例</span><span class="sxs-lookup"><span data-stu-id="9d963-141">Example</span></span>  
 <span data-ttu-id="9d963-142">次の XML では、名前のレジストリをベースの構成の発行者を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d963-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d963-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d963-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>

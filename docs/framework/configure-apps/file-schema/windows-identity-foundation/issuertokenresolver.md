---
title: '&lt;issuerTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02e2beb285cb0c4d88f98c3155ab5a3ff5e31e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="264d4-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="264d4-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="264d4-103">トークン ハンドラーはコレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="264d4-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="264d4-104">発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="264d4-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="264d4-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="264d4-105">\<system.identityModel></span></span>  
<span data-ttu-id="264d4-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="264d4-106">\<identityConfiguration></span></span>  
<span data-ttu-id="264d4-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="264d4-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="264d4-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="264d4-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="264d4-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="264d4-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264d4-110">構文</span><span class="sxs-lookup"><span data-stu-id="264d4-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="264d4-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="264d4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="264d4-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="264d4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="264d4-113">属性</span><span class="sxs-lookup"><span data-stu-id="264d4-113">Attributes</span></span>  
  
|<span data-ttu-id="264d4-114">属性</span><span class="sxs-lookup"><span data-stu-id="264d4-114">Attribute</span></span>|<span data-ttu-id="264d4-115">説明</span><span class="sxs-lookup"><span data-stu-id="264d4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="264d4-116">型</span><span class="sxs-lookup"><span data-stu-id="264d4-116">type</span></span>|<span data-ttu-id="264d4-117">発行者トークン リゾルバーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="264d4-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="264d4-118">いずれかである必要があります、<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスまたはその派生型、<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスです。</span><span class="sxs-lookup"><span data-stu-id="264d4-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="264d4-119">必須です。</span><span class="sxs-lookup"><span data-stu-id="264d4-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="264d4-120">子要素</span><span class="sxs-lookup"><span data-stu-id="264d4-120">Child Elements</span></span>  
 <span data-ttu-id="264d4-121">なし</span><span class="sxs-lookup"><span data-stu-id="264d4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="264d4-122">親要素</span><span class="sxs-lookup"><span data-stu-id="264d4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="264d4-123">要素</span><span class="sxs-lookup"><span data-stu-id="264d4-123">Element</span></span>|<span data-ttu-id="264d4-124">説明</span><span class="sxs-lookup"><span data-stu-id="264d4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="264d4-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="264d4-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="264d4-126">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="264d4-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="264d4-127">コメント</span><span class="sxs-lookup"><span data-stu-id="264d4-127">Remarks</span></span>  
 <span data-ttu-id="264d4-128">発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="264d4-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="264d4-129">これを使用して、署名の確認のために使用される暗号化マテリアルを取得します。</span><span class="sxs-lookup"><span data-stu-id="264d4-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="264d4-130">指定する必要があります、`type`属性。</span><span class="sxs-lookup"><span data-stu-id="264d4-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="264d4-131">指定された型には、いずれかを指定できる<xref:System.IdentityModel.Tokens.IssuerTokenResolver>やカスタム型から派生した、<xref:System.IdentityModel.Tokens.IssuerTokenResolver>クラスです。</span><span class="sxs-lookup"><span data-stu-id="264d4-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="264d4-132">いくつかのトークン ハンドラーを使用すると、構成内の発行者トークン リゾルバーの設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="264d4-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="264d4-133">セキュリティ トークン ハンドラーのコレクションで指定された個々 のトークン ハンドラーの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="264d4-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="264d4-134">指定する、`<issuerTokenResolver>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。</span><span class="sxs-lookup"><span data-stu-id="264d4-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="264d4-135">上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="264d4-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="264d4-136">例</span><span class="sxs-lookup"><span data-stu-id="264d4-136">Example</span></span>  
 <span data-ttu-id="264d4-137">次の XML から派生するカスタム クラスに基づいている発行者トークン リゾルバーの構成を表示する<xref:System.IdentityModel.Tokens.IssuerTokenResolver>です。</span><span class="sxs-lookup"><span data-stu-id="264d4-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="264d4-138">トークン リゾルバーは、カスタム構成要素から初期化された対象ユーザー キーのペアのディクショナリを保持 (`<AddAudienceKeyPair>`) クラスに対して定義されています。</span><span class="sxs-lookup"><span data-stu-id="264d4-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="264d4-139">クラスのオーバーライド、<xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A>この要素を処理するメソッド。</span><span class="sxs-lookup"><span data-stu-id="264d4-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="264d4-140">次の例で、上書きを表示します。ただし、それが呼び出すメソッドは、簡略化のためには表示されません。</span><span class="sxs-lookup"><span data-stu-id="264d4-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="264d4-141">完全な例については、`CustomToken`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="264d4-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="264d4-142">例</span><span class="sxs-lookup"><span data-stu-id="264d4-142">Example</span></span>  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="264d4-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="264d4-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>

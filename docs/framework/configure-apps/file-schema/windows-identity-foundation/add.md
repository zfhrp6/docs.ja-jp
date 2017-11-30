---
title: '&lt;add&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: cc1907d5f6117307ebadd04641c9eddc48e77cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt"></a><span data-ttu-id="d65af-102">&lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="d65af-102">&lt;add&gt;</span></span>
<span data-ttu-id="d65af-103">トークン ハンドラー コレクションに指定されたセキュリティ トークン ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="d65af-103">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="d65af-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="d65af-104">\<system.identityModel></span></span>  
<span data-ttu-id="d65af-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d65af-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d65af-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d65af-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d65af-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d65af-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d65af-108">構文</span><span class="sxs-lookup"><span data-stu-id="d65af-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d65af-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d65af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d65af-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d65af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d65af-111">属性</span><span class="sxs-lookup"><span data-stu-id="d65af-111">Attributes</span></span>  
  
|<span data-ttu-id="d65af-112">属性</span><span class="sxs-lookup"><span data-stu-id="d65af-112">Attribute</span></span>|<span data-ttu-id="d65af-113">説明</span><span class="sxs-lookup"><span data-stu-id="d65af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d65af-114">型</span><span class="sxs-lookup"><span data-stu-id="d65af-114">type</span></span>|<span data-ttu-id="d65af-115">追加するトークン ハンドラーの CLR 型名。</span><span class="sxs-lookup"><span data-stu-id="d65af-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="d65af-116">指定する方法について、`type`属性は、「[カスタム型の参照](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24)です。</span><span class="sxs-lookup"><span data-stu-id="d65af-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d65af-117">子要素</span><span class="sxs-lookup"><span data-stu-id="d65af-117">Child Elements</span></span>  
  
|<span data-ttu-id="d65af-118">要素</span><span class="sxs-lookup"><span data-stu-id="d65af-118">Element</span></span>|<span data-ttu-id="d65af-119">説明</span><span class="sxs-lookup"><span data-stu-id="d65af-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d65af-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d65af-120">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="d65af-121">構成を提供、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラス。</span><span class="sxs-lookup"><span data-stu-id="d65af-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="d65af-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d65af-122">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="d65af-123">構成を提供、<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>クラスまたは派生クラス。</span><span class="sxs-lookup"><span data-stu-id="d65af-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="d65af-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d65af-124">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="d65af-125">構成を提供、<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>クラスまたは派生クラス。</span><span class="sxs-lookup"><span data-stu-id="d65af-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="d65af-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d65af-126">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="d65af-127">省略可能な構成を提供、<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>クラスまたは派生クラス。</span><span class="sxs-lookup"><span data-stu-id="d65af-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d65af-128">親要素</span><span class="sxs-lookup"><span data-stu-id="d65af-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d65af-129">要素</span><span class="sxs-lookup"><span data-stu-id="d65af-129">Element</span></span>|<span data-ttu-id="d65af-130">説明</span><span class="sxs-lookup"><span data-stu-id="d65af-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d65af-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d65af-131">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="d65af-132">エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d65af-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d65af-133">コメント</span><span class="sxs-lookup"><span data-stu-id="d65af-133">Remarks</span></span>  
 <span data-ttu-id="d65af-134">`<add>`要素は、トークン ハンドラーの構成を指定する 1 つの子要素を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="d65af-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="d65af-135">これはを通じてハンドラー クラスを参照するかどうかに依存する、`type`の属性、`<add>`要素は、この機能のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="d65af-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="d65af-136">この機能を提供するトークン ハンドラー クラスを受け取るコンス トラクターを公開する必要があります、<xref:System.Xml.XmlElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d65af-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="d65af-137">この機能を提供、組み込みのセキュリティ トークン ハンドラーのクラスのいくつかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="d65af-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="d65af-138">これらのクラスは<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、および<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>です。</span><span class="sxs-lookup"><span data-stu-id="d65af-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d65af-139">トークン ハンドラー コレクションには、特定の型の 1 つのハンドラーのみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d65af-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="d65af-140">つまり、たとえば、派生元のハンドラーを追加する場合、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、コレクションを削除する必要あります、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>は既定では、コレクションから存在します。</span><span class="sxs-lookup"><span data-stu-id="d65af-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="d65af-141">使用することができます、 [\<削除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)コレクションまたは使用から 1 つのハンドラーを削除する要素、 [\<オフ >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)コレクションからすべてのイベント ハンドラーを削除する要素。</span><span class="sxs-lookup"><span data-stu-id="d65af-141">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="d65af-142">ハンドラーに指定された設定がの下にトークン ハンドラー コレクションに指定した同等の設定を上書き、 [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)要素とその下にあるサービス レベルで指定されています。[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="d65af-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d65af-143">例</span><span class="sxs-lookup"><span data-stu-id="d65af-143">Example</span></span>  
 <span data-ttu-id="d65af-144">次の XML の使用方法を示します、`<add>`と`<remove>`に既定のセッション トークン ハンドラーをカスタム セッション トークン ハンドラーに置き換える要素。</span><span class="sxs-lookup"><span data-stu-id="d65af-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d65af-145">XML を取得、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="d65af-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

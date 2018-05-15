---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="0eef2-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="0eef2-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="0eef2-103">トークン ハンドラーはコレクション内のハンドラーによって使用されるサービスのトークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="0eef2-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="0eef2-104">サービスのトークン リゾルバーを使用して、入力方向のトークンとメッセージの暗号化トークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="0eef2-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="0eef2-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0eef2-105">\<system.identityModel></span></span>  
<span data-ttu-id="0eef2-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0eef2-106">\<identityConfiguration></span></span>  
<span data-ttu-id="0eef2-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0eef2-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0eef2-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0eef2-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="0eef2-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="0eef2-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eef2-110">構文</span><span class="sxs-lookup"><span data-stu-id="0eef2-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eef2-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="0eef2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0eef2-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="0eef2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eef2-113">属性</span><span class="sxs-lookup"><span data-stu-id="0eef2-113">Attributes</span></span>  
  
|<span data-ttu-id="0eef2-114">属性</span><span class="sxs-lookup"><span data-stu-id="0eef2-114">Attribute</span></span>|<span data-ttu-id="0eef2-115">説明</span><span class="sxs-lookup"><span data-stu-id="0eef2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0eef2-116">型</span><span class="sxs-lookup"><span data-stu-id="0eef2-116">type</span></span>|<span data-ttu-id="0eef2-117">サービスのトークン リゾルバーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eef2-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="0eef2-118">いずれか、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>型または型から派生した、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0eef2-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="0eef2-119">指定する方法について、`type`属性 [カスタム型の参照] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0eef2-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="0eef2-120">必須。</span><span class="sxs-lookup"><span data-stu-id="0eef2-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eef2-121">子要素</span><span class="sxs-lookup"><span data-stu-id="0eef2-121">Child Elements</span></span>  
 <span data-ttu-id="0eef2-122">なし</span><span class="sxs-lookup"><span data-stu-id="0eef2-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eef2-123">親要素</span><span class="sxs-lookup"><span data-stu-id="0eef2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0eef2-124">要素</span><span class="sxs-lookup"><span data-stu-id="0eef2-124">Element</span></span>|<span data-ttu-id="0eef2-125">説明</span><span class="sxs-lookup"><span data-stu-id="0eef2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eef2-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0eef2-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="0eef2-127">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="0eef2-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eef2-128">コメント</span><span class="sxs-lookup"><span data-stu-id="0eef2-128">Remarks</span></span>  
 <span data-ttu-id="0eef2-129">入力方向のトークンとメッセージの暗号化トークンを解決するのには、サービスのトークン リゾルバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eef2-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="0eef2-130">着信トークン暗号化解除に使用されるキーの取得に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0eef2-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="0eef2-131">指定する必要があります、`type`属性。</span><span class="sxs-lookup"><span data-stu-id="0eef2-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="0eef2-132">指定された型には、いずれかを指定できる<xref:System.IdentityModel.Selectors.SecurityTokenResolver>やカスタム型から派生した、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0eef2-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="0eef2-133">いくつかのトークン ハンドラーを使用すると、構成でサービスのトークン リゾルバーの設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0eef2-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="0eef2-134">セキュリティ トークン ハンドラーのコレクションで指定された個々 のトークン ハンドラーの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="0eef2-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0eef2-135">指定する、`<serviceTokenResolver>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。</span><span class="sxs-lookup"><span data-stu-id="0eef2-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="0eef2-136">上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="0eef2-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eef2-137">例</span><span class="sxs-lookup"><span data-stu-id="0eef2-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```

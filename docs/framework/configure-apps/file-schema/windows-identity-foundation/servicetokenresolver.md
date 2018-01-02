---
title: '&lt;serviceTokenResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cd981c8e48f003060c74787fdd2f29557c07901d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="3d991-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="3d991-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="3d991-103">トークン ハンドラーはコレクション内のハンドラーによって使用されるサービスのトークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="3d991-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3d991-104">サービスのトークン リゾルバーを使用して、入力方向のトークンとメッセージの暗号化トークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="3d991-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="3d991-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="3d991-105">\<system.identityModel></span></span>  
<span data-ttu-id="3d991-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3d991-106">\<identityConfiguration></span></span>  
<span data-ttu-id="3d991-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3d991-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3d991-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3d991-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="3d991-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="3d991-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d991-110">構文</span><span class="sxs-lookup"><span data-stu-id="3d991-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d991-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3d991-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3d991-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3d991-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d991-113">属性</span><span class="sxs-lookup"><span data-stu-id="3d991-113">Attributes</span></span>  
  
|<span data-ttu-id="3d991-114">属性</span><span class="sxs-lookup"><span data-stu-id="3d991-114">Attribute</span></span>|<span data-ttu-id="3d991-115">説明</span><span class="sxs-lookup"><span data-stu-id="3d991-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d991-116">型</span><span class="sxs-lookup"><span data-stu-id="3d991-116">type</span></span>|<span data-ttu-id="3d991-117">サービスのトークン リゾルバーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d991-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="3d991-118">いずれか、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>型または型から派生した、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3d991-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="3d991-119">指定する方法について、`type`属性 [カスタム型の参照] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d991-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="3d991-120">必須。</span><span class="sxs-lookup"><span data-stu-id="3d991-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d991-121">子要素</span><span class="sxs-lookup"><span data-stu-id="3d991-121">Child Elements</span></span>  
 <span data-ttu-id="3d991-122">なし</span><span class="sxs-lookup"><span data-stu-id="3d991-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d991-123">親要素</span><span class="sxs-lookup"><span data-stu-id="3d991-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3d991-124">要素</span><span class="sxs-lookup"><span data-stu-id="3d991-124">Element</span></span>|<span data-ttu-id="3d991-125">説明</span><span class="sxs-lookup"><span data-stu-id="3d991-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d991-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3d991-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="3d991-127">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="3d991-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d991-128">コメント</span><span class="sxs-lookup"><span data-stu-id="3d991-128">Remarks</span></span>  
 <span data-ttu-id="3d991-129">入力方向のトークンとメッセージの暗号化トークンを解決するのには、サービスのトークン リゾルバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d991-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="3d991-130">着信トークン暗号化解除に使用されるキーの取得に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3d991-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="3d991-131">指定する必要があります、`type`属性。</span><span class="sxs-lookup"><span data-stu-id="3d991-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="3d991-132">指定された型には、いずれかを指定できる<xref:System.IdentityModel.Selectors.SecurityTokenResolver>やカスタム型から派生した、<xref:System.IdentityModel.Selectors.SecurityTokenResolver>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3d991-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="3d991-133">いくつかのトークン ハンドラーを使用すると、構成でサービスのトークン リゾルバーの設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3d991-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="3d991-134">セキュリティ トークン ハンドラーのコレクションで指定された個々 のトークン ハンドラーの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="3d991-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d991-135">指定する、`<serviceTokenResolver>`要素の子要素として、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素は推奨されていませんもは旧バージョンとの互換性のため、引き続きサポートします。</span><span class="sxs-lookup"><span data-stu-id="3d991-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="3d991-136">上の設定、`<securityTokenHandlerConfiguration>`要素をオーバーライドで、`<identityConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="3d991-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d991-137">例</span><span class="sxs-lookup"><span data-stu-id="3d991-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```

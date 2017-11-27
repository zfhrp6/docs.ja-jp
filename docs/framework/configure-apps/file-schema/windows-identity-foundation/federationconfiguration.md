---
title: '&lt;federationConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9abe07c065dbea67c5ebc4a4490d9f88258130c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltfederationconfigurationgt"></a><span data-ttu-id="31db4-102">&lt;federationConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="31db4-102">&lt;federationConfiguration&gt;</span></span>
<span data-ttu-id="31db4-103">構成、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) を使用する場合は、Ws-federation プロトコルを使用した認証をフェデレーションします。</span><span class="sxs-lookup"><span data-stu-id="31db4-103">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="31db4-104">構成、<xref:System.Security.Claims.ClaimsAuthorizationManager>を使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クレームに基づくアクセス制御を提供するクラス。</span><span class="sxs-lookup"><span data-stu-id="31db4-104">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
 <span data-ttu-id="31db4-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="31db4-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="31db4-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="31db4-106">\<federationConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31db4-107">構文</span><span class="sxs-lookup"><span data-stu-id="31db4-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31db4-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="31db4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="31db4-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="31db4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31db4-110">属性</span><span class="sxs-lookup"><span data-stu-id="31db4-110">Attributes</span></span>  
  
|<span data-ttu-id="31db4-111">属性</span><span class="sxs-lookup"><span data-stu-id="31db4-111">Attribute</span></span>|<span data-ttu-id="31db4-112">説明</span><span class="sxs-lookup"><span data-stu-id="31db4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31db4-113">name</span><span class="sxs-lookup"><span data-stu-id="31db4-113">name</span></span>|<span data-ttu-id="31db4-114">このフェデレーションの構成要素の名前。</span><span class="sxs-lookup"><span data-stu-id="31db4-114">The name of this federation configuration element.</span></span> <span data-ttu-id="31db4-115">この属性は、主の将来のプロトコル機能拡張ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="31db4-115">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="31db4-116">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="31db4-116">Optional.</span></span>|  
|<span data-ttu-id="31db4-117">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="31db4-117">identityConfigurationName</span></span>|<span data-ttu-id="31db4-118">指定された id の構成セクションの名前、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="31db4-118">The name of the identity configuration section as specified in an [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element to use.</span></span> <span data-ttu-id="31db4-119">この属性が指定されていない場合、既定の id 構成セクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31db4-119">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="31db4-120">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="31db4-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31db4-121">子要素</span><span class="sxs-lookup"><span data-stu-id="31db4-121">Child Elements</span></span>  
  
|<span data-ttu-id="31db4-122">要素</span><span class="sxs-lookup"><span data-stu-id="31db4-122">Element</span></span>|<span data-ttu-id="31db4-123">説明</span><span class="sxs-lookup"><span data-stu-id="31db4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31db4-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="31db4-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="31db4-125">SAM によって使用されるクッキー ハンドラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="31db4-125">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="31db4-126">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="31db4-126">Optional.</span></span>|  
|[<span data-ttu-id="31db4-127">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="31db4-127">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="31db4-128">暗号化し、トークン暗号化解除に使用される証明書を構成します。</span><span class="sxs-lookup"><span data-stu-id="31db4-128">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="31db4-129">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="31db4-129">Optional.</span></span>|  
|[<span data-ttu-id="31db4-130">\<wsFederation ></span><span class="sxs-lookup"><span data-stu-id="31db4-130">\<wsFederation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|<span data-ttu-id="31db4-131">Ws-federation 認証モジュール (WSFAM) を構成します。</span><span class="sxs-lookup"><span data-stu-id="31db4-131">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="31db4-132">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="31db4-132">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31db4-133">親要素</span><span class="sxs-lookup"><span data-stu-id="31db4-133">Parent Elements</span></span>  
  
|<span data-ttu-id="31db4-134">要素</span><span class="sxs-lookup"><span data-stu-id="31db4-134">Element</span></span>|<span data-ttu-id="31db4-135">説明</span><span class="sxs-lookup"><span data-stu-id="31db4-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31db4-136">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="31db4-136">\<system.identityModel.services></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|<span data-ttu-id="31db4-137">Ws-federation プロトコルを使用して認証用の構成セクション。</span><span class="sxs-lookup"><span data-stu-id="31db4-137">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31db4-138">コメント</span><span class="sxs-lookup"><span data-stu-id="31db4-138">Remarks</span></span>  
 <span data-ttu-id="31db4-139">\<FederationConfiguration > 要素が 2 つの異なるシナリオでの設定を提供します。</span><span class="sxs-lookup"><span data-stu-id="31db4-139">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
-   <span data-ttu-id="31db4-140">要素に構成設定が含まれる WS フェデレーション パッシブ Web アプリケーションを使用する場合、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="31db4-140">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="31db4-141">セキュリティ トークン ハンドラーと証明書、および要求の承認マネージャーと要求認証マネージャーなどのコンポーネントを構成するために使用される id の構成も参照します。</span><span class="sxs-lookup"><span data-stu-id="31db4-141">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
-   <span data-ttu-id="31db4-142">使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コード内のクレーム ベースのアクセス制御を提供するクラス、要素参照 id の構成要求承認マネージャーおよび承認に使用されるポリシーを構成します。決定します。</span><span class="sxs-lookup"><span data-stu-id="31db4-142">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="31db4-143">これが true の場合は受動的な Web シナリオ以外ではないシナリオであってもたとえば、Windows Communication Foundation (WCF) アプリケーションまたは Web ベースではないアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="31db4-143">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="31db4-144">アプリケーションが、パッシブ Web アプリケーションではない場合、 [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素 (とその子ポリシー要素、存在する場合) によって参照される id の構成の`<federationConfiguration>`要素唯一の設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="31db4-144">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="31db4-145">他の属性はすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="31db4-145">All others are ignored.</span></span>  
  
 <span data-ttu-id="31db4-146">シナリオに関係なく、ランタイムは既定のフェデレーションの構成を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="31db4-146">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="31db4-147">動作の定義は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31db4-147">The behavior is defined as follows:</span></span>  
  
1.  <span data-ttu-id="31db4-148">ある場合ありません`<federationConfiguration>`要素が存在、ランタイムは、フェデレーションの構成を作成し、既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="31db4-148">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="31db4-149">この既定のフェデレーションの構成では、既定の id 構成を参照します。</span><span class="sxs-lookup"><span data-stu-id="31db4-149">This default federation configuration will reference the default identity configuration.</span></span>  
  
2.  <span data-ttu-id="31db4-150">場合、1 つ`<federationConfiguration>`要素が存在、という名前または名前のないに関係なく、既定のフェデレーション構成します。</span><span class="sxs-lookup"><span data-stu-id="31db4-150">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="31db4-151">場合、`identityConfiguration`属性を指定すると、名前付きの id の構成が参照されている以外の場合は、既定の id 構成が参照されています。</span><span class="sxs-lookup"><span data-stu-id="31db4-151">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3.  <span data-ttu-id="31db4-152">場合は、名前のない`<federationConfiguration>`要素が、これは既定のフェデレーション構成します。</span><span class="sxs-lookup"><span data-stu-id="31db4-152">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="31db4-153">場合、`identityConfiguration`属性を指定すると、名前付きの id の構成が参照されている以外の場合は、既定の id 構成が参照されています。</span><span class="sxs-lookup"><span data-stu-id="31db4-153">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4.  <span data-ttu-id="31db4-154">複数の名前を付けて場合`<federationConfiguration>`要素が存在しない名前のない`<federationConfiguration>`要素が、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="31db4-154">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="31db4-155">通常、1 つだけ`<federationConfiguration>`セクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="31db4-155">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="31db4-156">このセクションでは、既定のフェデレーション構成です。</span><span class="sxs-lookup"><span data-stu-id="31db4-156">This section is the default federation configuration.</span></span> <span data-ttu-id="31db4-157">複数の一意な名前を指定することがあります`<federationConfiguration>`要素です。 ただし、この場合、名前のない別のフェデレーションの構成を読み込む場合は、する必要がありますハンドラーを提供します。</span><span class="sxs-lookup"><span data-stu-id="31db4-157">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="31db4-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>イベントとセット、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>にハンドラー内のプロパティ、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトから、適切な値で初期化`<federationConfiguration>`構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="31db4-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="31db4-159">`<federationConfiguration>`要素として表されます、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="31db4-159">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="31db4-160">構成オブジェクト自体がによって表される、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>クラスです。</span><span class="sxs-lookup"><span data-stu-id="31db4-160">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="31db4-161">1 つ<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>インスタンスに設定されて、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティし、フェデレーション アプリケーションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="31db4-161">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31db4-162">例</span><span class="sxs-lookup"><span data-stu-id="31db4-162">Example</span></span>  
 <span data-ttu-id="31db4-163">次の XML に示します、 `<federationConfiguration>` 、WSFAM の設定を指定し、ことを指定する要素既定のクッキー ハンドラー (のインスタンス、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス)、SAM で使用します。</span><span class="sxs-lookup"><span data-stu-id="31db4-163">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="31db4-164">この例では、HTTPS を使用するクッキー ハンドラーも WSFAM が必要です。</span><span class="sxs-lookup"><span data-stu-id="31db4-164">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="31db4-165">これは、ため、`requireHttps`属性を`<wsFederation>`要素および`requireSsl`属性を`<cookieHandlerElement>`は`false`します。</span><span class="sxs-lookup"><span data-stu-id="31db4-165">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="31db4-166">これらの設定は、セキュリティ上のリスクを伴うことがありますが、ほとんどの実稼働環境には推奨されません。</span><span class="sxs-lookup"><span data-stu-id="31db4-166">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="31db4-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="31db4-167">See Also</span></span>  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="31db4-168">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="31db4-168">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)

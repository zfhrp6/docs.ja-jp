---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: be98c93452c9c7a37ecad5b03f5160ea08f2c82e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="5f4c6-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="5f4c6-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="5f4c6-103">トークン ハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="5f4c6-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-104">\<system.identityModel></span></span>  
<span data-ttu-id="5f4c6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5f4c6-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5f4c6-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4c6-108">構文</span><span class="sxs-lookup"><span data-stu-id="5f4c6-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f4c6-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5f4c6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5f4c6-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f4c6-111">属性</span><span class="sxs-lookup"><span data-stu-id="5f4c6-111">Attributes</span></span>  
  
|<span data-ttu-id="5f4c6-112">属性</span><span class="sxs-lookup"><span data-stu-id="5f4c6-112">Attribute</span></span>|<span data-ttu-id="5f4c6-113">説明</span><span class="sxs-lookup"><span data-stu-id="5f4c6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f4c6-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="5f4c6-114">saveBootstrapContext</span></span>|<span data-ttu-id="5f4c6-115">セッション トークンにブートス トラップ トークンを含める必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="5f4c6-116">設定して、値がトークン ハンドラー コレクションに設定することも可能性があります、`saveBootstrapContext`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="5f4c6-117">トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="5f4c6-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="5f4c6-118">maximumClockSkew</span></span>|<span data-ttu-id="5f4c6-119">A<xref:System.TimeSpan>最大許容される時計の誤差を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="5f4c6-120">サインイン セッションの有効期限の検証などの時間が重要な操作を実行するときは、最大許容される時計の誤差を制御します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="5f4c6-121">既定値は 5 分、"00: 継続"です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="5f4c6-122">指定する方法について<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="5f4c6-123">設定して、最大の時刻のずれがサービス レベルで設定することも可能性があります、`maximumClockSkew`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="5f4c6-124">トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f4c6-125">子要素</span><span class="sxs-lookup"><span data-stu-id="5f4c6-125">Child Elements</span></span>  
  
|<span data-ttu-id="5f4c6-126">要素</span><span class="sxs-lookup"><span data-stu-id="5f4c6-126">Element</span></span>|<span data-ttu-id="5f4c6-127">説明</span><span class="sxs-lookup"><span data-stu-id="5f4c6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f4c6-128">\<Audienceuri ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="5f4c6-129">この証明書利用者の許容可能な識別子 Uri のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="5f4c6-130">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-130">Optional.</span></span>|  
|[<span data-ttu-id="5f4c6-131">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="5f4c6-132">セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="5f4c6-133">サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="5f4c6-134">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-134">Optional.</span></span>|  
|[<span data-ttu-id="5f4c6-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="5f4c6-136">トークン ハンドラーを使用して証明書の検証の設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="5f4c6-137">サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="5f4c6-138">特定のハンドラーが、独自の検証コントロールで構成されている場合、これらの設定は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="5f4c6-139">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-139">Optional.</span></span>|  
|[<span data-ttu-id="5f4c6-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="5f4c6-141">トークン ハンドラーはコレクション内のハンドラーによって使用される発行者名レジストリを構成します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5f4c6-142">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-142">Optional.</span></span>|  
|[<span data-ttu-id="5f4c6-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="5f4c6-144">トークン ハンドラーはコレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5f4c6-145">発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="5f4c6-146">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-146">Optional.</span></span>|  
|[<span data-ttu-id="5f4c6-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="5f4c6-148">トークン ハンドラーはコレクション内のハンドラーによって使用されるサービスのトークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5f4c6-149">サービスのトークン リゾルバーを使用して、入力方向のトークンとメッセージの暗号化トークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="5f4c6-150">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-150">Optional.</span></span>|  
|[<span data-ttu-id="5f4c6-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="5f4c6-152">トークン リプレイ検出を有効にし、トークンの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="5f4c6-153">サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="5f4c6-154">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f4c6-155">親要素</span><span class="sxs-lookup"><span data-stu-id="5f4c6-155">Parent Elements</span></span>  
  
|<span data-ttu-id="5f4c6-156">要素</span><span class="sxs-lookup"><span data-stu-id="5f4c6-156">Element</span></span>|<span data-ttu-id="5f4c6-157">説明</span><span class="sxs-lookup"><span data-stu-id="5f4c6-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f4c6-158">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5f4c6-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="5f4c6-159">エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f4c6-160">コメント</span><span class="sxs-lookup"><span data-stu-id="5f4c6-160">Remarks</span></span>  
 <span data-ttu-id="5f4c6-161">このセクションで説明のプロパティの値、<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="5f4c6-162">このセクションで構成した設定は、サービスで構成されているものをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="5f4c6-163">これらの設定の一部は、ハンドラーがセキュリティ トークン ハンドラーのコレクションに追加されたときに指定されている設定によってさらに、オーバーライド、できます。</span><span class="sxs-lookup"><span data-stu-id="5f4c6-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f4c6-164">例</span><span class="sxs-lookup"><span data-stu-id="5f4c6-164">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```

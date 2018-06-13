---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 168bdc4fbf640b201ebc61462d04727c23f838f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758426"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="a7d8c-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="a7d8c-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="a7d8c-103">トークン ハンドラーのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="a7d8c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a7d8c-104">\<system.identityModel></span></span>  
<span data-ttu-id="a7d8c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a7d8c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a7d8c-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a7d8c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a7d8c-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d8c-108">構文</span><span class="sxs-lookup"><span data-stu-id="a7d8c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7d8c-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a7d8c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7d8c-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7d8c-111">属性</span><span class="sxs-lookup"><span data-stu-id="a7d8c-111">Attributes</span></span>  
  
|<span data-ttu-id="a7d8c-112">属性</span><span class="sxs-lookup"><span data-stu-id="a7d8c-112">Attribute</span></span>|<span data-ttu-id="a7d8c-113">説明</span><span class="sxs-lookup"><span data-stu-id="a7d8c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7d8c-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="a7d8c-114">saveBootstrapContext</span></span>|<span data-ttu-id="a7d8c-115">セッション トークンにブートス トラップ トークンを含める必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="a7d8c-116">設定して、値がトークン ハンドラー コレクションに設定することも可能性があります、`saveBootstrapContext`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="a7d8c-117">トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="a7d8c-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="a7d8c-118">maximumClockSkew</span></span>|<span data-ttu-id="a7d8c-119">A<xref:System.TimeSpan>最大許容される時計の誤差を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="a7d8c-120">サインイン セッションの有効期限の検証などの時間が重要な操作を実行するときは、最大許容される時計の誤差を制御します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="a7d8c-121">既定値は 5 分、"00: 継続"です。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="a7d8c-122">指定する方法について<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="a7d8c-123">設定して、最大の時刻のずれがサービス レベルで設定することも可能性があります、`maximumClockSkew`属性を[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="a7d8c-124">トークン ハンドラー コレクションに設定値は、サービスで設定された値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7d8c-125">子要素</span><span class="sxs-lookup"><span data-stu-id="a7d8c-125">Child Elements</span></span>  
  
|<span data-ttu-id="a7d8c-126">要素</span><span class="sxs-lookup"><span data-stu-id="a7d8c-126">Element</span></span>|<span data-ttu-id="a7d8c-127">説明</span><span class="sxs-lookup"><span data-stu-id="a7d8c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7d8c-128">\<Audienceuri ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="a7d8c-129">この証明書利用者の許容可能な識別子 Uri のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="a7d8c-130">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-130">Optional.</span></span>|  
|[<span data-ttu-id="a7d8c-131">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="a7d8c-132">セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="a7d8c-133">サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a7d8c-134">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-134">Optional.</span></span>|  
|[<span data-ttu-id="a7d8c-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="a7d8c-136">トークン ハンドラーを使用して証明書の検証の設定を制御します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="a7d8c-137">サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a7d8c-138">特定のハンドラーが、独自の検証コントロールで構成されている場合、これらの設定は上書きされます。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="a7d8c-139">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-139">Optional.</span></span>|  
|[<span data-ttu-id="a7d8c-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="a7d8c-141">トークン ハンドラーはコレクション内のハンドラーによって使用される発行者名レジストリを構成します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a7d8c-142">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-142">Optional.</span></span>|  
|[<span data-ttu-id="a7d8c-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="a7d8c-144">トークン ハンドラーはコレクション内のハンドラーによって使用される発行者トークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a7d8c-145">発行者トークン リゾルバーを使用して、入力方向のトークンとメッセージの署名のトークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="a7d8c-146">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-146">Optional.</span></span>|  
|[<span data-ttu-id="a7d8c-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="a7d8c-148">トークン ハンドラーはコレクション内のハンドラーによって使用されるサービスのトークン リゾルバーを登録します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="a7d8c-149">サービスのトークン リゾルバーを使用して、入力方向のトークンとメッセージの暗号化トークンを解決します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="a7d8c-150">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-150">Optional.</span></span>|  
|[<span data-ttu-id="a7d8c-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="a7d8c-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="a7d8c-152">トークン リプレイ検出を有効にし、トークンの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="a7d8c-153">サービス レベルまたはセキュリティ トークン ハンドラーのコレクションで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="a7d8c-154">任意。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7d8c-155">親要素</span><span class="sxs-lookup"><span data-stu-id="a7d8c-155">Parent Elements</span></span>  
  
|<span data-ttu-id="a7d8c-156">要素</span><span class="sxs-lookup"><span data-stu-id="a7d8c-156">Element</span></span>|<span data-ttu-id="a7d8c-157">説明</span><span class="sxs-lookup"><span data-stu-id="a7d8c-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7d8c-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a7d8c-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="a7d8c-159">エンドポイントに登録されているセキュリティ トークン ハンドラーのコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7d8c-160">コメント</span><span class="sxs-lookup"><span data-stu-id="a7d8c-160">Remarks</span></span>  
 <span data-ttu-id="a7d8c-161">このセクションで説明のプロパティの値、<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="a7d8c-162">このセクションで構成した設定は、サービスで構成されているものをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="a7d8c-163">これらの設定の一部は、ハンドラーがセキュリティ トークン ハンドラーのコレクションに追加されたときに指定されている設定によってさらに、オーバーライド、できます。</span><span class="sxs-lookup"><span data-stu-id="a7d8c-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7d8c-164">例</span><span class="sxs-lookup"><span data-stu-id="a7d8c-164">Example</span></span>  
  
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

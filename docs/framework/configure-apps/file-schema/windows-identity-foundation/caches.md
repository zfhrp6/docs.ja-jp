---
title: '&lt;キャッシュ&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a9766b826eb7a708b4b4e99b6bd984f9fc76812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcachesgt"></a><span data-ttu-id="60704-102">&lt;キャッシュ&gt;</span><span class="sxs-lookup"><span data-stu-id="60704-102">&lt;caches&gt;</span></span>
<span data-ttu-id="60704-103">セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="60704-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="60704-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="60704-104">\<system.identityModel></span></span>  
<span data-ttu-id="60704-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="60704-105">\<identityConfiguration></span></span>  
<span data-ttu-id="60704-106">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="60704-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60704-107">構文</span><span class="sxs-lookup"><span data-stu-id="60704-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60704-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="60704-108">Attributes and Elements</span></span>  
 <span data-ttu-id="60704-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="60704-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60704-110">属性</span><span class="sxs-lookup"><span data-stu-id="60704-110">Attributes</span></span>  
 <span data-ttu-id="60704-111">なし</span><span class="sxs-lookup"><span data-stu-id="60704-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60704-112">子要素</span><span class="sxs-lookup"><span data-stu-id="60704-112">Child Elements</span></span>  
  
|<span data-ttu-id="60704-113">要素</span><span class="sxs-lookup"><span data-stu-id="60704-113">Element</span></span>|<span data-ttu-id="60704-114">説明</span><span class="sxs-lookup"><span data-stu-id="60704-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60704-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="60704-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="60704-116">サービスまたはセキュリティ トークン ハンドラーはコレクションのセッション トークンのキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="60704-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="60704-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="60704-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="60704-118">トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="60704-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60704-119">親要素</span><span class="sxs-lookup"><span data-stu-id="60704-119">Parent Elements</span></span>  
  
|<span data-ttu-id="60704-120">要素</span><span class="sxs-lookup"><span data-stu-id="60704-120">Element</span></span>|<span data-ttu-id="60704-121">説明</span><span class="sxs-lookup"><span data-stu-id="60704-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60704-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60704-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="60704-123">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="60704-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="60704-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60704-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="60704-125">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="60704-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60704-126">コメント</span><span class="sxs-lookup"><span data-stu-id="60704-126">Remarks</span></span>  
 <span data-ttu-id="60704-127">A`<caches>`下にあるサービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラーのコレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="60704-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="60704-128">サービスに指定されたトークン ハンドラーはコレクションの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="60704-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="60704-129">`<caches>`要素として表されます、<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="60704-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="60704-130">構成済みのキャッシュがによって表される、<xref:System.IdentityModel.Configuration.IdentityModelCaches>クラスです。</span><span class="sxs-lookup"><span data-stu-id="60704-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60704-131">例</span><span class="sxs-lookup"><span data-stu-id="60704-131">Example</span></span>  
 <span data-ttu-id="60704-132">次の XML は、セッション セキュリティ トークンを保持するためのカスタム キャッシュの構成を示します (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="60704-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="60704-133">構成がから取得した、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="60704-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

---
title: "&lt;キャッシュ&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a><span data-ttu-id="ab185-102">&lt;キャッシュ&gt;</span><span class="sxs-lookup"><span data-stu-id="ab185-102">&lt;caches&gt;</span></span>
<span data-ttu-id="ab185-103">セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="ab185-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="ab185-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="ab185-104">\<system.identityModel></span></span>  
<span data-ttu-id="ab185-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ab185-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ab185-106">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="ab185-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab185-107">構文</span><span class="sxs-lookup"><span data-stu-id="ab185-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab185-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ab185-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ab185-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab185-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab185-110">属性</span><span class="sxs-lookup"><span data-stu-id="ab185-110">Attributes</span></span>  
 <span data-ttu-id="ab185-111">なし</span><span class="sxs-lookup"><span data-stu-id="ab185-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab185-112">子要素</span><span class="sxs-lookup"><span data-stu-id="ab185-112">Child Elements</span></span>  
  
|<span data-ttu-id="ab185-113">要素</span><span class="sxs-lookup"><span data-stu-id="ab185-113">Element</span></span>|<span data-ttu-id="ab185-114">説明</span><span class="sxs-lookup"><span data-stu-id="ab185-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab185-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="ab185-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="ab185-116">サービスまたはセキュリティ トークン ハンドラーはコレクションのセッション トークンのキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="ab185-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="ab185-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="ab185-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="ab185-118">トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="ab185-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab185-119">親要素</span><span class="sxs-lookup"><span data-stu-id="ab185-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ab185-120">要素</span><span class="sxs-lookup"><span data-stu-id="ab185-120">Element</span></span>|<span data-ttu-id="ab185-121">説明</span><span class="sxs-lookup"><span data-stu-id="ab185-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab185-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ab185-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="ab185-123">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab185-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="ab185-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ab185-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="ab185-125">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab185-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab185-126">コメント</span><span class="sxs-lookup"><span data-stu-id="ab185-126">Remarks</span></span>  
 <span data-ttu-id="ab185-127">A`<caches>`下にあるサービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラーのコレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="ab185-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="ab185-128">サービスに指定されたトークン ハンドラーはコレクションの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ab185-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="ab185-129">`<caches>`要素として表されます、<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="ab185-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="ab185-130">構成済みのキャッシュがによって表される、<xref:System.IdentityModel.Configuration.IdentityModelCaches>クラスです。</span><span class="sxs-lookup"><span data-stu-id="ab185-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab185-131">例</span><span class="sxs-lookup"><span data-stu-id="ab185-131">Example</span></span>  
 <span data-ttu-id="ab185-132">次の XML は、セッション セキュリティ トークンを保持するためのカスタム キャッシュの構成を示します (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="ab185-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="ab185-133">構成がから取得した、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="ab185-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

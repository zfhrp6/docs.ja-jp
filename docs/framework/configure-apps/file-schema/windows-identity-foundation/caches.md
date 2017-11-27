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
ms.openlocfilehash: f0c46532cb7716f4dc066f0e96c14534d7fa0b42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltcachesgt"></a><span data-ttu-id="5aaab-102">&lt;キャッシュ&gt;</span><span class="sxs-lookup"><span data-stu-id="5aaab-102">&lt;caches&gt;</span></span>
<span data-ttu-id="5aaab-103">セッション トークンやトークン リプレイ検出のために使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="5aaab-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="5aaab-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="5aaab-104">\<system.identityModel></span></span>  
<span data-ttu-id="5aaab-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5aaab-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5aaab-106">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="5aaab-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aaab-107">構文</span><span class="sxs-lookup"><span data-stu-id="5aaab-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aaab-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5aaab-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5aaab-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5aaab-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aaab-110">属性</span><span class="sxs-lookup"><span data-stu-id="5aaab-110">Attributes</span></span>  
 <span data-ttu-id="5aaab-111">なし</span><span class="sxs-lookup"><span data-stu-id="5aaab-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5aaab-112">子要素</span><span class="sxs-lookup"><span data-stu-id="5aaab-112">Child Elements</span></span>  
  
|<span data-ttu-id="5aaab-113">要素</span><span class="sxs-lookup"><span data-stu-id="5aaab-113">Element</span></span>|<span data-ttu-id="5aaab-114">説明</span><span class="sxs-lookup"><span data-stu-id="5aaab-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5aaab-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="5aaab-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="5aaab-116">サービスまたはセキュリティ トークン ハンドラーはコレクションのセッション トークンのキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="5aaab-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="5aaab-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="5aaab-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="5aaab-118">トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="5aaab-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5aaab-119">親要素</span><span class="sxs-lookup"><span data-stu-id="5aaab-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5aaab-120">要素</span><span class="sxs-lookup"><span data-stu-id="5aaab-120">Element</span></span>|<span data-ttu-id="5aaab-121">説明</span><span class="sxs-lookup"><span data-stu-id="5aaab-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5aaab-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5aaab-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="5aaab-123">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="5aaab-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="5aaab-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5aaab-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="5aaab-125">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="5aaab-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aaab-126">コメント</span><span class="sxs-lookup"><span data-stu-id="5aaab-126">Remarks</span></span>  
 <span data-ttu-id="5aaab-127">A`<caches>`下にあるサービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラーのコレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="5aaab-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="5aaab-128">サービスに指定されたトークン ハンドラーはコレクションの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5aaab-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="5aaab-129">`<caches>`要素として表されます、<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5aaab-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="5aaab-130">構成済みのキャッシュがによって表される、<xref:System.IdentityModel.Configuration.IdentityModelCaches>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5aaab-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aaab-131">例</span><span class="sxs-lookup"><span data-stu-id="5aaab-131">Example</span></span>  
 <span data-ttu-id="5aaab-132">次の XML は、セッション セキュリティ トークンを保持するためのカスタム キャッシュの構成を示します (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="5aaab-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="5aaab-133">構成がから取得した、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="5aaab-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

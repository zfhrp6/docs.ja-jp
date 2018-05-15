---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0b0d3c01a81f110f79f64d75aa2ab2ff2873fedd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="976db-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="976db-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="976db-103">サービスまたはセキュリティ トークン ハンドラーはコレクションのセッション トークンのキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="976db-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="976db-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="976db-104">\<system.identityModel></span></span>  
<span data-ttu-id="976db-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="976db-105">\<identityConfiguration></span></span>  
<span data-ttu-id="976db-106">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="976db-106">\<caches></span></span>  
<span data-ttu-id="976db-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="976db-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976db-108">構文</span><span class="sxs-lookup"><span data-stu-id="976db-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="976db-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="976db-109">Attributes and Elements</span></span>  
 <span data-ttu-id="976db-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="976db-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="976db-111">属性</span><span class="sxs-lookup"><span data-stu-id="976db-111">Attributes</span></span>  
  
|<span data-ttu-id="976db-112">属性</span><span class="sxs-lookup"><span data-stu-id="976db-112">Attribute</span></span>|<span data-ttu-id="976db-113">説明</span><span class="sxs-lookup"><span data-stu-id="976db-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="976db-114">型</span><span class="sxs-lookup"><span data-stu-id="976db-114">type</span></span>|<span data-ttu-id="976db-115">派生する型、<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>クラスです。</span><span class="sxs-lookup"><span data-stu-id="976db-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="976db-116">子要素</span><span class="sxs-lookup"><span data-stu-id="976db-116">Child Elements</span></span>  
 <span data-ttu-id="976db-117">なし</span><span class="sxs-lookup"><span data-stu-id="976db-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="976db-118">親要素</span><span class="sxs-lookup"><span data-stu-id="976db-118">Parent Elements</span></span>  
  
|<span data-ttu-id="976db-119">要素</span><span class="sxs-lookup"><span data-stu-id="976db-119">Element</span></span>|<span data-ttu-id="976db-120">説明</span><span class="sxs-lookup"><span data-stu-id="976db-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="976db-121">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="976db-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="976db-122">サービスまたはセキュリティ トークン ハンドラーのコレクションによって使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="976db-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="976db-123">例</span><span class="sxs-lookup"><span data-stu-id="976db-123">Example</span></span>  
 <span data-ttu-id="976db-124">次の XML は、セッション セキュリティ トークンを保持するためのカスタム キャッシュの構成を示します (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="976db-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="976db-125">構成がから取得した、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="976db-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="976db-126">このサンプルの詳細については、次を参照してください。 [WIF コード サンプル インデックス](../../../../../docs/framework/security/wif-code-sample-index.md)です。</span><span class="sxs-lookup"><span data-stu-id="976db-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="976db-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="976db-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>

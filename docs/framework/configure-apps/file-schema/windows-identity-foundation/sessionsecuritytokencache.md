---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 9f4b87d6c620a07ee831888086bdab75a689875e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="854f2-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="854f2-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="854f2-103">サービスまたはセキュリティ トークン ハンドラーはコレクションのセッション トークンのキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="854f2-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="854f2-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="854f2-104">\<system.identityModel></span></span>  
<span data-ttu-id="854f2-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="854f2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="854f2-106">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="854f2-106">\<caches></span></span>  
<span data-ttu-id="854f2-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="854f2-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854f2-108">構文</span><span class="sxs-lookup"><span data-stu-id="854f2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="854f2-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="854f2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="854f2-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="854f2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="854f2-111">属性</span><span class="sxs-lookup"><span data-stu-id="854f2-111">Attributes</span></span>  
  
|<span data-ttu-id="854f2-112">属性</span><span class="sxs-lookup"><span data-stu-id="854f2-112">Attribute</span></span>|<span data-ttu-id="854f2-113">説明</span><span class="sxs-lookup"><span data-stu-id="854f2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="854f2-114">型</span><span class="sxs-lookup"><span data-stu-id="854f2-114">type</span></span>|<span data-ttu-id="854f2-115">派生する型、<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>クラスです。</span><span class="sxs-lookup"><span data-stu-id="854f2-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="854f2-116">子要素</span><span class="sxs-lookup"><span data-stu-id="854f2-116">Child Elements</span></span>  
 <span data-ttu-id="854f2-117">なし</span><span class="sxs-lookup"><span data-stu-id="854f2-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="854f2-118">親要素</span><span class="sxs-lookup"><span data-stu-id="854f2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="854f2-119">要素</span><span class="sxs-lookup"><span data-stu-id="854f2-119">Element</span></span>|<span data-ttu-id="854f2-120">説明</span><span class="sxs-lookup"><span data-stu-id="854f2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="854f2-121">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="854f2-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="854f2-122">サービスまたはセキュリティ トークン ハンドラーのコレクションによって使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="854f2-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="854f2-123">例</span><span class="sxs-lookup"><span data-stu-id="854f2-123">Example</span></span>  
 <span data-ttu-id="854f2-124">次の XML は、セッション セキュリティ トークンを保持するためのカスタム キャッシュの構成を示します (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="854f2-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="854f2-125">構成がから取得した、`ClaimsAwareWebFarm`サンプルです。</span><span class="sxs-lookup"><span data-stu-id="854f2-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="854f2-126">このサンプルの詳細については、次を参照してください。 [WIF コード サンプル インデックス](../../../../../docs/framework/security/wif-code-sample-index.md)です。</span><span class="sxs-lookup"><span data-stu-id="854f2-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="854f2-127">参照</span><span class="sxs-lookup"><span data-stu-id="854f2-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>

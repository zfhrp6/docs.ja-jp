---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f388369d4dc2e590473ad98189ade70b77551b10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="1a574-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="1a574-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="1a574-103">トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。</span><span class="sxs-lookup"><span data-stu-id="1a574-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="1a574-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="1a574-104">\<system.identityModel></span></span>  
<span data-ttu-id="1a574-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1a574-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1a574-106">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="1a574-106">\<caches></span></span>  
<span data-ttu-id="1a574-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="1a574-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a574-108">構文</span><span class="sxs-lookup"><span data-stu-id="1a574-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a574-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1a574-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a574-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a574-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a574-111">属性</span><span class="sxs-lookup"><span data-stu-id="1a574-111">Attributes</span></span>  
  
|<span data-ttu-id="1a574-112">属性</span><span class="sxs-lookup"><span data-stu-id="1a574-112">Attribute</span></span>|<span data-ttu-id="1a574-113">説明</span><span class="sxs-lookup"><span data-stu-id="1a574-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a574-114">型</span><span class="sxs-lookup"><span data-stu-id="1a574-114">type</span></span>|<span data-ttu-id="1a574-115">派生する型、<xref:System.IdentityModel.Tokens.TokenReplayCache>クラスです。</span><span class="sxs-lookup"><span data-stu-id="1a574-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="1a574-116">詳細については、ユーザー設定を指定する方法についての`type`、[カスタム型の参照] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a574-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="1a574-117">子要素</span><span class="sxs-lookup"><span data-stu-id="1a574-117">Child Elements</span></span>  
 <span data-ttu-id="1a574-118">なし</span><span class="sxs-lookup"><span data-stu-id="1a574-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a574-119">親要素</span><span class="sxs-lookup"><span data-stu-id="1a574-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a574-120">要素</span><span class="sxs-lookup"><span data-stu-id="1a574-120">Element</span></span>|<span data-ttu-id="1a574-121">説明</span><span class="sxs-lookup"><span data-stu-id="1a574-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a574-122">\<キャッシュ ></span><span class="sxs-lookup"><span data-stu-id="1a574-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="1a574-123">サービスまたはセキュリティ トークン ハンドラーのコレクションによって使用されるキャッシュに登録します。</span><span class="sxs-lookup"><span data-stu-id="1a574-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a574-124">コメント</span><span class="sxs-lookup"><span data-stu-id="1a574-124">Remarks</span></span>  
 <span data-ttu-id="1a574-125">トークン リプレイ キャッシュを使用して、再生されたトークンを検出できます。</span><span class="sxs-lookup"><span data-stu-id="1a574-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="1a574-126">トークン リプレイ検出が有効になって、 [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)もトークンの最大有効期限を指定する要素。</span><span class="sxs-lookup"><span data-stu-id="1a574-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a574-127">例</span><span class="sxs-lookup"><span data-stu-id="1a574-127">Example</span></span>  
 <span data-ttu-id="1a574-128">次の XML では、再生されたトークンを検出するためのカスタム キャッシュの構成を示します。</span><span class="sxs-lookup"><span data-stu-id="1a574-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a574-129">参照</span><span class="sxs-lookup"><span data-stu-id="1a574-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="1a574-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="1a574-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)

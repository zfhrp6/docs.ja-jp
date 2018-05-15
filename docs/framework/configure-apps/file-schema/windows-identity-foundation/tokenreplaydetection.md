---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7f0cef2590bb301e6897aa4922454942ecdd0957
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="fd204-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="fd204-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="fd204-103">トークン リプレイ検出を有効にし、トークンの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd204-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="fd204-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fd204-104">\<system.identityModel></span></span>  
<span data-ttu-id="fd204-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fd204-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fd204-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="fd204-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd204-107">構文</span><span class="sxs-lookup"><span data-stu-id="fd204-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="fd204-108">型</span><span class="sxs-lookup"><span data-stu-id="fd204-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd204-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fd204-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fd204-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd204-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd204-111">属性</span><span class="sxs-lookup"><span data-stu-id="fd204-111">Attributes</span></span>  
  
|<span data-ttu-id="fd204-112">属性</span><span class="sxs-lookup"><span data-stu-id="fd204-112">Attribute</span></span>|<span data-ttu-id="fd204-113">説明</span><span class="sxs-lookup"><span data-stu-id="fd204-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd204-114">enabled</span><span class="sxs-lookup"><span data-stu-id="fd204-114">enabled</span></span>|<span data-ttu-id="fd204-115">トークン リプレイ検出が有効かどうかを指定する値トークンを有効にするには"true"にリプレイ検出を示します。</span><span class="sxs-lookup"><span data-stu-id="fd204-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="fd204-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="fd204-116">expirationPeriod</span></span>|<span data-ttu-id="fd204-117">A<xref:System.TimeSpan>項目が期限切れになり、キャッシュから削除されたと見なされるまでの時間の最大の大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd204-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="fd204-118">指定する方法について<xref:System.TimeSpan>値を参照してください[Timespan 値](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd204-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd204-119">子要素</span><span class="sxs-lookup"><span data-stu-id="fd204-119">Child Elements</span></span>  
 <span data-ttu-id="fd204-120">なし</span><span class="sxs-lookup"><span data-stu-id="fd204-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd204-121">親要素</span><span class="sxs-lookup"><span data-stu-id="fd204-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fd204-122">要素</span><span class="sxs-lookup"><span data-stu-id="fd204-122">Element</span></span>|<span data-ttu-id="fd204-123">説明</span><span class="sxs-lookup"><span data-stu-id="fd204-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd204-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fd204-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="fd204-125">サービス レベルの id 設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="fd204-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="fd204-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fd204-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="fd204-127">トークン ハンドラーのセキュリティのコレクションの構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="fd204-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd204-128">コメント</span><span class="sxs-lookup"><span data-stu-id="fd204-128">Remarks</span></span>  
 <span data-ttu-id="fd204-129">A`<tokenReplayDetection>`下にあるサービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラーのコレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。</span><span class="sxs-lookup"><span data-stu-id="fd204-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="fd204-130">サービスに指定されたトークン ハンドラーはコレクションの設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="fd204-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="fd204-131">トークン リプレイ キャッシュの型がで指定された、 [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fd204-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>

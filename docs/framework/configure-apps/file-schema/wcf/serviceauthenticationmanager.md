---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3b58214a1fd7a50fb1a9ab3dfee0a14870f8a476
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="20a69-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="20a69-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="20a69-103">サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="20a69-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="20a69-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="20a69-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="20a69-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="20a69-105">\<behaviors></span></span>  
<span data-ttu-id="20a69-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="20a69-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="20a69-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="20a69-107">\<behavior></span></span>  
<span data-ttu-id="20a69-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="20a69-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a69-109">構文</span><span class="sxs-lookup"><span data-stu-id="20a69-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20a69-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="20a69-110">Attributes and Elements</span></span>  
 <span data-ttu-id="20a69-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="20a69-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20a69-112">属性</span><span class="sxs-lookup"><span data-stu-id="20a69-112">Attributes</span></span>  
  
|<span data-ttu-id="20a69-113">属性</span><span class="sxs-lookup"><span data-stu-id="20a69-113">Attribute</span></span>|<span data-ttu-id="20a69-114">説明</span><span class="sxs-lookup"><span data-stu-id="20a69-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20a69-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="20a69-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="20a69-116">現在の動作の認証ポリシーの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="20a69-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20a69-117">子要素</span><span class="sxs-lookup"><span data-stu-id="20a69-117">Child Elements</span></span>  
 <span data-ttu-id="20a69-118">なし。</span><span class="sxs-lookup"><span data-stu-id="20a69-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20a69-119">親要素</span><span class="sxs-lookup"><span data-stu-id="20a69-119">Parent Elements</span></span>  
  
|<span data-ttu-id="20a69-120">要素</span><span class="sxs-lookup"><span data-stu-id="20a69-120">Element</span></span>|<span data-ttu-id="20a69-121">説明</span><span class="sxs-lookup"><span data-stu-id="20a69-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20a69-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="20a69-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="20a69-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="20a69-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20a69-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="20a69-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

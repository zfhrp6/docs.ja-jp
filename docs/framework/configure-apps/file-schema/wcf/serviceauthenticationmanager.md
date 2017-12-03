---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 077878ae1746008532c3bee6b12913f98afc343f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="32ecd-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="32ecd-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="32ecd-103">サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="32ecd-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="32ecd-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="32ecd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32ecd-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="32ecd-105">\<behaviors></span></span>  
<span data-ttu-id="32ecd-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="32ecd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="32ecd-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="32ecd-107">\<behavior></span></span>  
<span data-ttu-id="32ecd-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="32ecd-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ecd-109">構文</span><span class="sxs-lookup"><span data-stu-id="32ecd-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32ecd-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="32ecd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32ecd-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="32ecd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32ecd-112">属性</span><span class="sxs-lookup"><span data-stu-id="32ecd-112">Attributes</span></span>  
  
|<span data-ttu-id="32ecd-113">属性</span><span class="sxs-lookup"><span data-stu-id="32ecd-113">Attribute</span></span>|<span data-ttu-id="32ecd-114">説明</span><span class="sxs-lookup"><span data-stu-id="32ecd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32ecd-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="32ecd-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="32ecd-116">現在の動作の認証ポリシーの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="32ecd-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32ecd-117">子要素</span><span class="sxs-lookup"><span data-stu-id="32ecd-117">Child Elements</span></span>  
 <span data-ttu-id="32ecd-118">なし。</span><span class="sxs-lookup"><span data-stu-id="32ecd-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32ecd-119">親要素</span><span class="sxs-lookup"><span data-stu-id="32ecd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="32ecd-120">要素</span><span class="sxs-lookup"><span data-stu-id="32ecd-120">Element</span></span>|<span data-ttu-id="32ecd-121">説明</span><span class="sxs-lookup"><span data-stu-id="32ecd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32ecd-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="32ecd-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="32ecd-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="32ecd-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32ecd-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="32ecd-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

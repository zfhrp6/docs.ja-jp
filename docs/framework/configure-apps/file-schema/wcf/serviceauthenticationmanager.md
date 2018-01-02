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
ms.workload: dotnet
ms.openlocfilehash: b46df4f069259ae4bb2d2769e20c6ad9e6090c00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="a57f9-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="a57f9-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="a57f9-103">サービス レベルで転送、メッセージ、または送信元の有効性を確立するワークフロー構成要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="a57f9-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="a57f9-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a57f9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a57f9-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="a57f9-105">\<behaviors></span></span>  
<span data-ttu-id="a57f9-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a57f9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a57f9-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="a57f9-107">\<behavior></span></span>  
<span data-ttu-id="a57f9-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="a57f9-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a57f9-109">構文</span><span class="sxs-lookup"><span data-stu-id="a57f9-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a57f9-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a57f9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a57f9-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a57f9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a57f9-112">属性</span><span class="sxs-lookup"><span data-stu-id="a57f9-112">Attributes</span></span>  
  
|<span data-ttu-id="a57f9-113">属性</span><span class="sxs-lookup"><span data-stu-id="a57f9-113">Attribute</span></span>|<span data-ttu-id="a57f9-114">説明</span><span class="sxs-lookup"><span data-stu-id="a57f9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a57f9-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="a57f9-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="a57f9-116">現在の動作の認証ポリシーの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="a57f9-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a57f9-117">子要素</span><span class="sxs-lookup"><span data-stu-id="a57f9-117">Child Elements</span></span>  
 <span data-ttu-id="a57f9-118">なし。</span><span class="sxs-lookup"><span data-stu-id="a57f9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a57f9-119">親要素</span><span class="sxs-lookup"><span data-stu-id="a57f9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a57f9-120">要素</span><span class="sxs-lookup"><span data-stu-id="a57f9-120">Element</span></span>|<span data-ttu-id="a57f9-121">説明</span><span class="sxs-lookup"><span data-stu-id="a57f9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a57f9-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="a57f9-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a57f9-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="a57f9-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a57f9-124">参照</span><span class="sxs-lookup"><span data-stu-id="a57f9-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>

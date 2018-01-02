---
title: '&lt;clientVia&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a1870a8c331aae16ab14da62c64d6fb15ecd3bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientviagt"></a><span data-ttu-id="66fae-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="66fae-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="66fae-103">トランスポート チャネルの作成対象となる URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="66fae-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="66fae-104">詳細については、「<xref:System.ServiceModel.Description.ClientViaBehavior>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66fae-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="66fae-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="66fae-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="66fae-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="66fae-106">\<behaviors></span></span>  
<span data-ttu-id="66fae-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="66fae-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="66fae-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="66fae-108">\<behavior></span></span>  
<span data-ttu-id="66fae-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="66fae-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66fae-110">構文</span><span class="sxs-lookup"><span data-stu-id="66fae-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66fae-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="66fae-111">Attributes and Elements</span></span>  
 <span data-ttu-id="66fae-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="66fae-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66fae-113">属性</span><span class="sxs-lookup"><span data-stu-id="66fae-113">Attributes</span></span>  
  
|<span data-ttu-id="66fae-114">属性</span><span class="sxs-lookup"><span data-stu-id="66fae-114">Attribute</span></span>|<span data-ttu-id="66fae-115">説明</span><span class="sxs-lookup"><span data-stu-id="66fae-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="66fae-116">メッセージの経路を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="66fae-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66fae-117">子要素</span><span class="sxs-lookup"><span data-stu-id="66fae-117">Child Elements</span></span>  
 <span data-ttu-id="66fae-118">なし</span><span class="sxs-lookup"><span data-stu-id="66fae-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66fae-119">親要素</span><span class="sxs-lookup"><span data-stu-id="66fae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="66fae-120">要素</span><span class="sxs-lookup"><span data-stu-id="66fae-120">Element</span></span>|<span data-ttu-id="66fae-121">説明</span><span class="sxs-lookup"><span data-stu-id="66fae-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66fae-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="66fae-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="66fae-123">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="66fae-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66fae-124">参照</span><span class="sxs-lookup"><span data-stu-id="66fae-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>

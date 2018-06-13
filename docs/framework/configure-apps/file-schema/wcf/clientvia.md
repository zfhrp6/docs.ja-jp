---
title: '&lt;clientVia&gt;'
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 6218bb3f205f2825eb3f10fabf834cfd0396ac87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754133"
---
# <a name="ltclientviagt"></a><span data-ttu-id="a858c-102">&lt;clientVia&gt;</span><span class="sxs-lookup"><span data-stu-id="a858c-102">&lt;clientVia&gt;</span></span>
<span data-ttu-id="a858c-103">トランスポート チャネルの作成対象となる URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="a858c-103">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="a858c-104">詳細については、「<xref:System.ServiceModel.Description.ClientViaBehavior>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a858c-104">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="a858c-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a858c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a858c-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="a858c-106">\<behaviors></span></span>  
<span data-ttu-id="a858c-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a858c-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a858c-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a858c-108">\<behavior></span></span>  
<span data-ttu-id="a858c-109">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="a858c-109">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a858c-110">構文</span><span class="sxs-lookup"><span data-stu-id="a858c-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a858c-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a858c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a858c-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a858c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a858c-113">属性</span><span class="sxs-lookup"><span data-stu-id="a858c-113">Attributes</span></span>  
  
|<span data-ttu-id="a858c-114">属性</span><span class="sxs-lookup"><span data-stu-id="a858c-114">Attribute</span></span>|<span data-ttu-id="a858c-115">説明</span><span class="sxs-lookup"><span data-stu-id="a858c-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="a858c-116">メッセージの経路を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="a858c-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a858c-117">子要素</span><span class="sxs-lookup"><span data-stu-id="a858c-117">Child Elements</span></span>  
 <span data-ttu-id="a858c-118">なし</span><span class="sxs-lookup"><span data-stu-id="a858c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a858c-119">親要素</span><span class="sxs-lookup"><span data-stu-id="a858c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a858c-120">要素</span><span class="sxs-lookup"><span data-stu-id="a858c-120">Element</span></span>|<span data-ttu-id="a858c-121">説明</span><span class="sxs-lookup"><span data-stu-id="a858c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a858c-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a858c-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a858c-123">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="a858c-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a858c-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a858c-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientViaElement>  
 <xref:System.ServiceModel.Description.ClientViaBehavior>

---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7e637a744d24ed32be71d0ecf3f5d93144d32aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="a66da-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="a66da-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="a66da-103">この要素は、ASP.NET AJAX Web ページからサービスを使用できるようにするエンドポイントの動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="a66da-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="a66da-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a66da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a66da-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="a66da-105">\<behaviors></span></span>  
<span data-ttu-id="a66da-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a66da-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a66da-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="a66da-107">\<behavior></span></span>  
<span data-ttu-id="a66da-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="a66da-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66da-109">構文</span><span class="sxs-lookup"><span data-stu-id="a66da-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a66da-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a66da-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a66da-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a66da-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a66da-112">属性</span><span class="sxs-lookup"><span data-stu-id="a66da-112">Attributes</span></span>  
 <span data-ttu-id="a66da-113">なし。</span><span class="sxs-lookup"><span data-stu-id="a66da-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a66da-114">子要素</span><span class="sxs-lookup"><span data-stu-id="a66da-114">Child Elements</span></span>  
 <span data-ttu-id="a66da-115">なし。</span><span class="sxs-lookup"><span data-stu-id="a66da-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a66da-116">親要素</span><span class="sxs-lookup"><span data-stu-id="a66da-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a66da-117">要素</span><span class="sxs-lookup"><span data-stu-id="a66da-117">Element</span></span>|<span data-ttu-id="a66da-118">説明</span><span class="sxs-lookup"><span data-stu-id="a66da-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a66da-119">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="a66da-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a66da-120">エンドポイントの動作のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="a66da-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a66da-121">コメント</span><span class="sxs-lookup"><span data-stu-id="a66da-121">Remarks</span></span>  
 <span data-ttu-id="a66da-122">この動作は、いずれかと組み合わせてのみ使用する必要があります、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準バインディングまたは[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)バインド要素。</span><span class="sxs-lookup"><span data-stu-id="a66da-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="a66da-123">この動作の詳細については、「<xref:System.ServiceModel.Description.WebScriptEnablingBehavior>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a66da-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66da-124">参照</span><span class="sxs-lookup"><span data-stu-id="a66da-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="a66da-125">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="a66da-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="a66da-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="a66da-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)

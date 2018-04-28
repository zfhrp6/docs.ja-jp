---
title: '&lt;webHttp&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bf92421d09f25c760f8edc5062b7b7d6276902f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="d17a5-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="d17a5-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="d17a5-103">この要素は、構成によってエンドポイントに <xref:System.ServiceModel.Description.WebHttpBehavior> を指定します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="d17a5-104">この動作と組み合わせて使用すると、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)の Web プログラミング モデルにより、標準のバインディング、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]サービス。</span><span class="sxs-lookup"><span data-stu-id="d17a5-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>  
  
 <span data-ttu-id="d17a5-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d17a5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d17a5-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="d17a5-106">\<behaviors></span></span>  
<span data-ttu-id="d17a5-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d17a5-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="d17a5-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d17a5-108">\<behavior></span></span>  
<span data-ttu-id="d17a5-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="d17a5-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d17a5-110">構文</span><span class="sxs-lookup"><span data-stu-id="d17a5-110">Syntax</span></span>  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d17a5-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d17a5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d17a5-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d17a5-113">属性</span><span class="sxs-lookup"><span data-stu-id="d17a5-113">Attributes</span></span>  
  
|<span data-ttu-id="d17a5-114">属性</span><span class="sxs-lookup"><span data-stu-id="d17a5-114">Attribute</span></span>|<span data-ttu-id="d17a5-115">説明</span><span class="sxs-lookup"><span data-stu-id="d17a5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d17a5-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="d17a5-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="d17a5-117">このプロパティが `true` に設定されている場合は、使用する最適な形式が WCF インフラストラクチャで決定されます。</span><span class="sxs-lookup"><span data-stu-id="d17a5-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="d17a5-118">形式の自動選択は、既定で、下位互換性のために無効になっています。</span><span class="sxs-lookup"><span data-stu-id="d17a5-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="d17a5-119">形式の自動選択は、プログラムで有効にすることも、構成ファイルを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d17a5-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="d17a5-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="d17a5-120">defaultBodyStyle</span></span>|<span data-ttu-id="d17a5-121">返されたメッセージの既定の本文のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="d17a5-122">詳細については、次を参照してください。<xref:System.ServiceModel.Web.WebMessageBodyStyle>と[WCF Web HTTP 書式](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)です。</span><span class="sxs-lookup"><span data-stu-id="d17a5-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d17a5-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="d17a5-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="d17a5-124">メッセージの既定の送信応答形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="d17a5-125">詳細については、次を参照してください。 [WCF Web HTTP 書式](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)です。</span><span class="sxs-lookup"><span data-stu-id="d17a5-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="d17a5-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="d17a5-126">faultExceptionEnabled</span></span>|<span data-ttu-id="d17a5-127">内部サーバー エラー (HTTP ステータス コード: 500) が発生したときに FaultException が生成されるかどうかを指定するフラグを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="d17a5-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="d17a5-128">helpEnabled</span></span>|<span data-ttu-id="d17a5-129">ヘルプ ページが有効かどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d17a5-130">子要素</span><span class="sxs-lookup"><span data-stu-id="d17a5-130">Child Elements</span></span>  
 <span data-ttu-id="d17a5-131">なし。</span><span class="sxs-lookup"><span data-stu-id="d17a5-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d17a5-132">親要素</span><span class="sxs-lookup"><span data-stu-id="d17a5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d17a5-133">要素</span><span class="sxs-lookup"><span data-stu-id="d17a5-133">Element</span></span>|<span data-ttu-id="d17a5-134">説明</span><span class="sxs-lookup"><span data-stu-id="d17a5-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d17a5-135">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d17a5-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d17a5-136">エンドポイントの動作のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="d17a5-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d17a5-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="d17a5-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="d17a5-138">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="d17a5-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="d17a5-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d17a5-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)

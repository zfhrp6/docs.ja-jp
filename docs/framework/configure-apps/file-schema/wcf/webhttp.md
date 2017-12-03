---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b5388a680816bca6051525f5130308a3c7c2dc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="cf87c-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="cf87c-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="cf87c-103">この要素は、構成によってエンドポイントに <xref:System.ServiceModel.Description.WebHttpBehavior> を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="cf87c-104">この動作と組み合わせて使用すると、 [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)の Web プログラミング モデルにより、標準のバインディング、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]サービス。</span><span class="sxs-lookup"><span data-stu-id="cf87c-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>  
  
 <span data-ttu-id="cf87c-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="cf87c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf87c-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="cf87c-106">\<behaviors></span></span>  
<span data-ttu-id="cf87c-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cf87c-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="cf87c-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="cf87c-108">\<behavior></span></span>  
<span data-ttu-id="cf87c-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="cf87c-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf87c-110">構文</span><span class="sxs-lookup"><span data-stu-id="cf87c-110">Syntax</span></span>  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf87c-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cf87c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf87c-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf87c-113">属性</span><span class="sxs-lookup"><span data-stu-id="cf87c-113">Attributes</span></span>  
  
|<span data-ttu-id="cf87c-114">属性</span><span class="sxs-lookup"><span data-stu-id="cf87c-114">Attribute</span></span>|<span data-ttu-id="cf87c-115">説明</span><span class="sxs-lookup"><span data-stu-id="cf87c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf87c-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="cf87c-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="cf87c-117">このプロパティが `true` に設定されている場合は、使用する最適な形式が WCF インフラストラクチャで決定されます。</span><span class="sxs-lookup"><span data-stu-id="cf87c-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="cf87c-118">形式の自動選択は、既定で、下位互換性のために無効になっています。</span><span class="sxs-lookup"><span data-stu-id="cf87c-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="cf87c-119">形式の自動選択は、プログラムで有効にすることも、構成ファイルを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cf87c-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="cf87c-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="cf87c-120">defaultBodyStyle</span></span>|<span data-ttu-id="cf87c-121">返されたメッセージの既定の本文のスタイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-121">Specifies the default body style of returned messages.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="cf87c-122"><xref:System.ServiceModel.Web.WebMessageBodyStyle>と[WCF Web HTTP 形式](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf87c-122"> <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="cf87c-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="cf87c-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="cf87c-124">メッセージの既定の送信応答形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-124">Specifies the default outgoing response format for messages.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="cf87c-125">[WCF Web HTTP 形式](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf87c-125"> [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="cf87c-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="cf87c-126">faultExceptionEnabled</span></span>|<span data-ttu-id="cf87c-127">内部サーバー エラー (HTTP ステータス コード: 500) が発生したときに FaultException が生成されるかどうかを指定するフラグを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="cf87c-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="cf87c-128">helpEnabled</span></span>|<span data-ttu-id="cf87c-129">ヘルプ ページが有効かどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf87c-130">子要素</span><span class="sxs-lookup"><span data-stu-id="cf87c-130">Child Elements</span></span>  
 <span data-ttu-id="cf87c-131">なし。</span><span class="sxs-lookup"><span data-stu-id="cf87c-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf87c-132">親要素</span><span class="sxs-lookup"><span data-stu-id="cf87c-132">Parent Elements</span></span>  
  
|<span data-ttu-id="cf87c-133">要素</span><span class="sxs-lookup"><span data-stu-id="cf87c-133">Element</span></span>|<span data-ttu-id="cf87c-134">説明</span><span class="sxs-lookup"><span data-stu-id="cf87c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf87c-135">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="cf87c-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cf87c-136">エンドポイントの動作のセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf87c-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf87c-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf87c-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="cf87c-138">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="cf87c-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="cf87c-139">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cf87c-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)

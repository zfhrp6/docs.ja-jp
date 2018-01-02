---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc45511e0e7b4644704a834f0bc08d64ff3367f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="f18ec-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="f18ec-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="f18ec-103">この構成要素が固定の標準エンドポイントを定義[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)自動的にバインディングを追加、 [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)動作します。</span><span class="sxs-lookup"><span data-stu-id="f18ec-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="f18ec-104">このエンドポイントは、REST サービスを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="f18ec-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="f18ec-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f18ec-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f18ec-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f18ec-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18ec-107">構文</span><span class="sxs-lookup"><span data-stu-id="f18ec-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18ec-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f18ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f18ec-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f18ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18ec-110">属性</span><span class="sxs-lookup"><span data-stu-id="f18ec-110">Attributes</span></span>  
  
|<span data-ttu-id="f18ec-111">属性</span><span class="sxs-lookup"><span data-stu-id="f18ec-111">Attribute</span></span>|<span data-ttu-id="f18ec-112">説明</span><span class="sxs-lookup"><span data-stu-id="f18ec-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f18ec-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="f18ec-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="f18ec-114">形式の自動選択が有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="f18ec-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="f18ec-115">形式の自動選択が有効な場合、インフラストラクチャが要求メッセージの `Accept` ヘッダーを解析し、最適な応答形式を判断します。</span><span class="sxs-lookup"><span data-stu-id="f18ec-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="f18ec-116">適切な応答形式が `Accept` ヘッダーに指定されていなかった場合は、要求メッセージの `Content-Type` または操作の既定の応答形式がインフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="f18ec-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="f18ec-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="f18ec-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="f18ec-118">既定の送信応答形式を指定する属性。</span><span class="sxs-lookup"><span data-stu-id="f18ec-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="f18ec-119">この属性は <xref:System.ServiceModel.Web.WebMessageFormat> 型です。</span><span class="sxs-lookup"><span data-stu-id="f18ec-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="f18ec-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="f18ec-120">helpEnabled</span></span>|<span data-ttu-id="f18ec-121">エンドポイントに対して HTTP ヘルプ ページが有効になっているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="f18ec-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="f18ec-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="f18ec-122">webEndpointType</span></span>|<span data-ttu-id="f18ec-123">エンドポイントの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="f18ec-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f18ec-124">子要素</span><span class="sxs-lookup"><span data-stu-id="f18ec-124">Child Elements</span></span>  
 <span data-ttu-id="f18ec-125">なし。</span><span class="sxs-lookup"><span data-stu-id="f18ec-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f18ec-126">親要素</span><span class="sxs-lookup"><span data-stu-id="f18ec-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f18ec-127">要素</span><span class="sxs-lookup"><span data-stu-id="f18ec-127">Element</span></span>|<span data-ttu-id="f18ec-128">説明</span><span class="sxs-lookup"><span data-stu-id="f18ec-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18ec-129">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f18ec-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f18ec-130">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="f18ec-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f18ec-131">参照</span><span class="sxs-lookup"><span data-stu-id="f18ec-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>

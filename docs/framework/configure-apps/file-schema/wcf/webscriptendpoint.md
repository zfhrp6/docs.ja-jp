---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b53b7cc3ce812b72830c0ad83c5cc2b42bfc25a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="310a5-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="310a5-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="310a5-103">この構成要素が固定の標準エンドポイントを定義[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)自動的にバインディングを追加、 [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)動作します。</span><span class="sxs-lookup"><span data-stu-id="310a5-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="310a5-104">このエンドポイントは、ASP.NET AJAX アプリケーションから呼び出されるサービスを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="310a5-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="310a5-105">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="310a5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="310a5-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="310a5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310a5-107">構文</span><span class="sxs-lookup"><span data-stu-id="310a5-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="310a5-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="310a5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="310a5-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="310a5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="310a5-110">属性</span><span class="sxs-lookup"><span data-stu-id="310a5-110">Attributes</span></span>  
  
|<span data-ttu-id="310a5-111">属性</span><span class="sxs-lookup"><span data-stu-id="310a5-111">Attribute</span></span>|<span data-ttu-id="310a5-112">説明</span><span class="sxs-lookup"><span data-stu-id="310a5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="310a5-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="310a5-113">webEndpointType</span></span>|<span data-ttu-id="310a5-114">エンドポイントの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="310a5-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="310a5-115">子要素</span><span class="sxs-lookup"><span data-stu-id="310a5-115">Child Elements</span></span>  
 <span data-ttu-id="310a5-116">なし。</span><span class="sxs-lookup"><span data-stu-id="310a5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="310a5-117">親要素</span><span class="sxs-lookup"><span data-stu-id="310a5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="310a5-118">要素</span><span class="sxs-lookup"><span data-stu-id="310a5-118">Element</span></span>|<span data-ttu-id="310a5-119">説明</span><span class="sxs-lookup"><span data-stu-id="310a5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="310a5-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="310a5-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="310a5-121">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="310a5-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="310a5-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="310a5-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>

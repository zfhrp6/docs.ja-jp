---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e127935977795181411dfa6b03d8b09fe88e0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="61297-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="61297-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="61297-103">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="61297-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="61297-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="61297-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="61297-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="61297-105">\<behaviors></span></span>  
<span data-ttu-id="61297-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="61297-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="61297-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="61297-107">\<behavior></span></span>  
<span data-ttu-id="61297-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="61297-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="61297-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="61297-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61297-110">構文</span><span class="sxs-lookup"><span data-stu-id="61297-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61297-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="61297-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61297-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="61297-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61297-113">属性</span><span class="sxs-lookup"><span data-stu-id="61297-113">Attributes</span></span>  
 <span data-ttu-id="61297-114">なし。</span><span class="sxs-lookup"><span data-stu-id="61297-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="61297-115">子要素</span><span class="sxs-lookup"><span data-stu-id="61297-115">Child Elements</span></span>  
  
|<span data-ttu-id="61297-116">要素</span><span class="sxs-lookup"><span data-stu-id="61297-116">Element</span></span>|<span data-ttu-id="61297-117">説明</span><span class="sxs-lookup"><span data-stu-id="61297-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61297-118">\<追加 > の\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="61297-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="61297-119">クライアント アプリケーションがリッスンする既定の通信エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="61297-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61297-120">親要素</span><span class="sxs-lookup"><span data-stu-id="61297-120">Parent Elements</span></span>  
  
|<span data-ttu-id="61297-121">要素</span><span class="sxs-lookup"><span data-stu-id="61297-121">Element</span></span>|<span data-ttu-id="61297-122">説明</span><span class="sxs-lookup"><span data-stu-id="61297-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61297-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="61297-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="61297-124">既定のポートの一覧。</span><span class="sxs-lookup"><span data-stu-id="61297-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61297-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="61297-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

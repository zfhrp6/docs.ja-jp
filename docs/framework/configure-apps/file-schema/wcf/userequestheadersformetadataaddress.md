---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e7f69da871376f83422fb330f8babd56bb1fdcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="fddef-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="fddef-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="fddef-103">メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fddef-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="fddef-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fddef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fddef-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="fddef-105">\<behaviors></span></span>  
<span data-ttu-id="fddef-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fddef-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fddef-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="fddef-107">\<behavior></span></span>  
<span data-ttu-id="fddef-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="fddef-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fddef-109">構文</span><span class="sxs-lookup"><span data-stu-id="fddef-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fddef-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fddef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fddef-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fddef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fddef-112">属性</span><span class="sxs-lookup"><span data-stu-id="fddef-112">Attributes</span></span>  
 <span data-ttu-id="fddef-113">なし。</span><span class="sxs-lookup"><span data-stu-id="fddef-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fddef-114">子要素</span><span class="sxs-lookup"><span data-stu-id="fddef-114">Child Elements</span></span>  
  
|<span data-ttu-id="fddef-115">要素</span><span class="sxs-lookup"><span data-stu-id="fddef-115">Element</span></span>|<span data-ttu-id="fddef-116">説明</span><span class="sxs-lookup"><span data-stu-id="fddef-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fddef-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="fddef-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="fddef-118">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="fddef-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fddef-119">親要素</span><span class="sxs-lookup"><span data-stu-id="fddef-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fddef-120">要素</span><span class="sxs-lookup"><span data-stu-id="fddef-120">Element</span></span>|<span data-ttu-id="fddef-121">説明</span><span class="sxs-lookup"><span data-stu-id="fddef-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fddef-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="fddef-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fddef-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="fddef-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fddef-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fddef-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

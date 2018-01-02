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
ms.workload: dotnet
ms.openlocfilehash: 94dafcfa68463a0e82696cf16a96abe45632e72a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="4b0f3-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="4b0f3-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="4b0f3-103">メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4b0f3-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="4b0f3-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b0f3-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-105">\<behaviors></span></span>  
<span data-ttu-id="4b0f3-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4b0f3-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-107">\<behavior></span></span>  
<span data-ttu-id="4b0f3-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0f3-109">構文</span><span class="sxs-lookup"><span data-stu-id="4b0f3-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b0f3-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4b0f3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4b0f3-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b0f3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b0f3-112">属性</span><span class="sxs-lookup"><span data-stu-id="4b0f3-112">Attributes</span></span>  
 <span data-ttu-id="4b0f3-113">なし。</span><span class="sxs-lookup"><span data-stu-id="4b0f3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b0f3-114">子要素</span><span class="sxs-lookup"><span data-stu-id="4b0f3-114">Child Elements</span></span>  
  
|<span data-ttu-id="4b0f3-115">要素</span><span class="sxs-lookup"><span data-stu-id="4b0f3-115">Element</span></span>|<span data-ttu-id="4b0f3-116">説明</span><span class="sxs-lookup"><span data-stu-id="4b0f3-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b0f3-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="4b0f3-118">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="4b0f3-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b0f3-119">親要素</span><span class="sxs-lookup"><span data-stu-id="4b0f3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4b0f3-120">要素</span><span class="sxs-lookup"><span data-stu-id="4b0f3-120">Element</span></span>|<span data-ttu-id="4b0f3-121">説明</span><span class="sxs-lookup"><span data-stu-id="4b0f3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b0f3-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="4b0f3-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4b0f3-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="4b0f3-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b0f3-124">参照</span><span class="sxs-lookup"><span data-stu-id="4b0f3-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

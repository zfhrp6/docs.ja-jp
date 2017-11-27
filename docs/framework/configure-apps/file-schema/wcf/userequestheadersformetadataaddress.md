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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="ab620-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="ab620-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="ab620-103">メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ab620-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="ab620-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ab620-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab620-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="ab620-105">\<behaviors></span></span>  
<span data-ttu-id="ab620-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ab620-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ab620-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="ab620-107">\<behavior></span></span>  
<span data-ttu-id="ab620-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="ab620-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab620-109">構文</span><span class="sxs-lookup"><span data-stu-id="ab620-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab620-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ab620-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ab620-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab620-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab620-112">属性</span><span class="sxs-lookup"><span data-stu-id="ab620-112">Attributes</span></span>  
 <span data-ttu-id="ab620-113">なし。</span><span class="sxs-lookup"><span data-stu-id="ab620-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab620-114">子要素</span><span class="sxs-lookup"><span data-stu-id="ab620-114">Child Elements</span></span>  
  
|<span data-ttu-id="ab620-115">要素</span><span class="sxs-lookup"><span data-stu-id="ab620-115">Element</span></span>|<span data-ttu-id="ab620-116">説明</span><span class="sxs-lookup"><span data-stu-id="ab620-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab620-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ab620-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="ab620-118">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="ab620-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab620-119">親要素</span><span class="sxs-lookup"><span data-stu-id="ab620-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ab620-120">要素</span><span class="sxs-lookup"><span data-stu-id="ab620-120">Element</span></span>|<span data-ttu-id="ab620-121">説明</span><span class="sxs-lookup"><span data-stu-id="ab620-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab620-122">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="ab620-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ab620-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab620-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab620-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab620-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

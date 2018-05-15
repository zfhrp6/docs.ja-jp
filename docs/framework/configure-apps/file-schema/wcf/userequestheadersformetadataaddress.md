---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 7e661570f8b94b979595a615b3f6819d41ed5e35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="b6da1-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="b6da1-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="b6da1-103">メタデータのアドレス情報を要求メッセージ ヘッダーから取得できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b6da1-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="b6da1-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b6da1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6da1-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="b6da1-105">\<behaviors></span></span>  
<span data-ttu-id="b6da1-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b6da1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b6da1-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b6da1-107">\<behavior></span></span>  
<span data-ttu-id="b6da1-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="b6da1-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6da1-109">構文</span><span class="sxs-lookup"><span data-stu-id="b6da1-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6da1-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b6da1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6da1-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6da1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6da1-112">属性</span><span class="sxs-lookup"><span data-stu-id="b6da1-112">Attributes</span></span>  
 <span data-ttu-id="b6da1-113">なし。</span><span class="sxs-lookup"><span data-stu-id="b6da1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6da1-114">子要素</span><span class="sxs-lookup"><span data-stu-id="b6da1-114">Child Elements</span></span>  
  
|<span data-ttu-id="b6da1-115">要素</span><span class="sxs-lookup"><span data-stu-id="b6da1-115">Element</span></span>|<span data-ttu-id="b6da1-116">説明</span><span class="sxs-lookup"><span data-stu-id="b6da1-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6da1-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="b6da1-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="b6da1-118">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="b6da1-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6da1-119">親要素</span><span class="sxs-lookup"><span data-stu-id="b6da1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b6da1-120">要素</span><span class="sxs-lookup"><span data-stu-id="b6da1-120">Element</span></span>|<span data-ttu-id="b6da1-121">説明</span><span class="sxs-lookup"><span data-stu-id="b6da1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6da1-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b6da1-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b6da1-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6da1-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6da1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6da1-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

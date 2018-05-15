---
title: '&lt;defaultPorts&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 28ddc98bd66c1f74f857448aa710d3998ddbd3dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="9e4ef-102">&lt;defaultPorts&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="9e4ef-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="9e4ef-103">クライアント アプリケーションがリッスンする既定の通信エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="9e4ef-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="9e4ef-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9e4ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e4ef-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="9e4ef-105">\<behaviors></span></span>  
<span data-ttu-id="9e4ef-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9e4ef-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9e4ef-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9e4ef-107">\<behavior></span></span>  
<span data-ttu-id="9e4ef-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="9e4ef-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="9e4ef-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="9e4ef-109">\<defaultPorts></span></span>  
<span data-ttu-id="9e4ef-110">\<add></span><span class="sxs-lookup"><span data-stu-id="9e4ef-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4ef-111">構文</span><span class="sxs-lookup"><span data-stu-id="9e4ef-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e4ef-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9e4ef-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9e4ef-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e4ef-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e4ef-114">属性</span><span class="sxs-lookup"><span data-stu-id="9e4ef-114">Attributes</span></span>  
  
|<span data-ttu-id="9e4ef-115">属性</span><span class="sxs-lookup"><span data-stu-id="9e4ef-115">Attribute</span></span>|<span data-ttu-id="9e4ef-116">説明</span><span class="sxs-lookup"><span data-stu-id="9e4ef-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e4ef-117">ポート</span><span class="sxs-lookup"><span data-stu-id="9e4ef-117">port</span></span>|<span data-ttu-id="9e4ef-118">既定の通信ポート番号を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="9e4ef-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="9e4ef-119">scheme</span><span class="sxs-lookup"><span data-stu-id="9e4ef-119">scheme</span></span>|<span data-ttu-id="9e4ef-120">通信ポートに関連付けられているプロトコル設定のグループを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="9e4ef-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e4ef-121">子要素</span><span class="sxs-lookup"><span data-stu-id="9e4ef-121">Child Elements</span></span>  
 <span data-ttu-id="9e4ef-122">なし。</span><span class="sxs-lookup"><span data-stu-id="9e4ef-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e4ef-123">親要素</span><span class="sxs-lookup"><span data-stu-id="9e4ef-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9e4ef-124">要素</span><span class="sxs-lookup"><span data-stu-id="9e4ef-124">Element</span></span>|<span data-ttu-id="9e4ef-125">説明</span><span class="sxs-lookup"><span data-stu-id="9e4ef-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e4ef-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="9e4ef-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="9e4ef-127">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="9e4ef-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e4ef-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e4ef-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>

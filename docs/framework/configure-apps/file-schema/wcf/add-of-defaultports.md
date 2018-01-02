---
title: "&lt;defaultPorts&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1efe61bf5f4276836c65e9c81d316dc0664f3de2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="32536-102">&lt;defaultPorts&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="32536-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="32536-103">クライアント アプリケーションがリッスンする既定の通信エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="32536-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="32536-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="32536-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32536-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="32536-105">\<behaviors></span></span>  
<span data-ttu-id="32536-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="32536-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="32536-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="32536-107">\<behavior></span></span>  
<span data-ttu-id="32536-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="32536-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="32536-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="32536-109">\<defaultPorts></span></span>  
<span data-ttu-id="32536-110">\<add></span><span class="sxs-lookup"><span data-stu-id="32536-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32536-111">構文</span><span class="sxs-lookup"><span data-stu-id="32536-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32536-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="32536-112">Attributes and Elements</span></span>  
 <span data-ttu-id="32536-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="32536-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32536-114">属性</span><span class="sxs-lookup"><span data-stu-id="32536-114">Attributes</span></span>  
  
|<span data-ttu-id="32536-115">属性</span><span class="sxs-lookup"><span data-stu-id="32536-115">Attribute</span></span>|<span data-ttu-id="32536-116">説明</span><span class="sxs-lookup"><span data-stu-id="32536-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32536-117">ポート</span><span class="sxs-lookup"><span data-stu-id="32536-117">port</span></span>|<span data-ttu-id="32536-118">既定の通信ポート番号を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="32536-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="32536-119">scheme</span><span class="sxs-lookup"><span data-stu-id="32536-119">scheme</span></span>|<span data-ttu-id="32536-120">通信ポートに関連付けられているプロトコル設定のグループを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="32536-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32536-121">子要素</span><span class="sxs-lookup"><span data-stu-id="32536-121">Child Elements</span></span>  
 <span data-ttu-id="32536-122">なし。</span><span class="sxs-lookup"><span data-stu-id="32536-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32536-123">親要素</span><span class="sxs-lookup"><span data-stu-id="32536-123">Parent Elements</span></span>  
  
|<span data-ttu-id="32536-124">要素</span><span class="sxs-lookup"><span data-stu-id="32536-124">Element</span></span>|<span data-ttu-id="32536-125">説明</span><span class="sxs-lookup"><span data-stu-id="32536-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32536-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="32536-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="32536-127">クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。</span><span class="sxs-lookup"><span data-stu-id="32536-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32536-128">参照</span><span class="sxs-lookup"><span data-stu-id="32536-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>

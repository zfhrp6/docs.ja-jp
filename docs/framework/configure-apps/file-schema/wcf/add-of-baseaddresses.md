---
title: "&lt;baseAddresses&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf417653652c2a0f28fe5c6491a7da9949678140
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="74369-102">&lt;baseAddresses&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="74369-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="74369-103">サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="74369-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="74369-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="74369-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="74369-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="74369-105">\<client></span></span>  
<span data-ttu-id="74369-106">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="74369-106">\<endpoint></span></span>  
<span data-ttu-id="74369-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="74369-107">\<host></span></span>  
<span data-ttu-id="74369-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="74369-108">\<baseAddresses></span></span>  
<span data-ttu-id="74369-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="74369-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74369-110">構文</span><span class="sxs-lookup"><span data-stu-id="74369-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="74369-111">型</span><span class="sxs-lookup"><span data-stu-id="74369-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74369-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="74369-112">Attributes and Elements</span></span>  
 <span data-ttu-id="74369-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="74369-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74369-114">属性</span><span class="sxs-lookup"><span data-stu-id="74369-114">Attributes</span></span>  
  
|<span data-ttu-id="74369-115">属性</span><span class="sxs-lookup"><span data-stu-id="74369-115">Attribute</span></span>|<span data-ttu-id="74369-116">説明</span><span class="sxs-lookup"><span data-stu-id="74369-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="74369-117">サービス ホストによって使用されるベース アドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="74369-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74369-118">子要素</span><span class="sxs-lookup"><span data-stu-id="74369-118">Child Elements</span></span>  
 <span data-ttu-id="74369-119">なし。</span><span class="sxs-lookup"><span data-stu-id="74369-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74369-120">親要素</span><span class="sxs-lookup"><span data-stu-id="74369-120">Parent Elements</span></span>  
  
|<span data-ttu-id="74369-121">要素</span><span class="sxs-lookup"><span data-stu-id="74369-121">Element</span></span>|<span data-ttu-id="74369-122">説明</span><span class="sxs-lookup"><span data-stu-id="74369-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74369-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="74369-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="74369-124">`baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="74369-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74369-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="74369-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="74369-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="74369-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

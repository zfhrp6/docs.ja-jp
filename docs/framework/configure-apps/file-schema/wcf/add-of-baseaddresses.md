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
ms.workload: dotnet
ms.openlocfilehash: 516c615248c95ef3107664b996f457fb80b46373
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="27a88-102">&lt;baseAddresses&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="27a88-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="27a88-103">サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="27a88-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="27a88-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="27a88-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27a88-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="27a88-105">\<client></span></span>  
<span data-ttu-id="27a88-106">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="27a88-106">\<endpoint></span></span>  
<span data-ttu-id="27a88-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="27a88-107">\<host></span></span>  
<span data-ttu-id="27a88-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="27a88-108">\<baseAddresses></span></span>  
<span data-ttu-id="27a88-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="27a88-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a88-110">構文</span><span class="sxs-lookup"><span data-stu-id="27a88-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="27a88-111">型</span><span class="sxs-lookup"><span data-stu-id="27a88-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27a88-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="27a88-112">Attributes and Elements</span></span>  
 <span data-ttu-id="27a88-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="27a88-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27a88-114">属性</span><span class="sxs-lookup"><span data-stu-id="27a88-114">Attributes</span></span>  
  
|<span data-ttu-id="27a88-115">属性</span><span class="sxs-lookup"><span data-stu-id="27a88-115">Attribute</span></span>|<span data-ttu-id="27a88-116">説明</span><span class="sxs-lookup"><span data-stu-id="27a88-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="27a88-117">サービス ホストによって使用されるベース アドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="27a88-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27a88-118">子要素</span><span class="sxs-lookup"><span data-stu-id="27a88-118">Child Elements</span></span>  
 <span data-ttu-id="27a88-119">なし。</span><span class="sxs-lookup"><span data-stu-id="27a88-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27a88-120">親要素</span><span class="sxs-lookup"><span data-stu-id="27a88-120">Parent Elements</span></span>  
  
|<span data-ttu-id="27a88-121">要素</span><span class="sxs-lookup"><span data-stu-id="27a88-121">Element</span></span>|<span data-ttu-id="27a88-122">説明</span><span class="sxs-lookup"><span data-stu-id="27a88-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27a88-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="27a88-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="27a88-124">`baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="27a88-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27a88-125">参照</span><span class="sxs-lookup"><span data-stu-id="27a88-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="27a88-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="27a88-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e941b63e42af9237388df6be8223acbad8db745
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="f0e85-102">&lt;baseAddresses&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="f0e85-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="f0e85-103">サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="f0e85-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="f0e85-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f0e85-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f0e85-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="f0e85-105">\<client></span></span>  
<span data-ttu-id="f0e85-106">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="f0e85-106">\<endpoint></span></span>  
<span data-ttu-id="f0e85-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="f0e85-107">\<host></span></span>  
<span data-ttu-id="f0e85-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="f0e85-108">\<baseAddresses></span></span>  
<span data-ttu-id="f0e85-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="f0e85-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e85-110">構文</span><span class="sxs-lookup"><span data-stu-id="f0e85-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="f0e85-111">型</span><span class="sxs-lookup"><span data-stu-id="f0e85-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0e85-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f0e85-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f0e85-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f0e85-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0e85-114">属性</span><span class="sxs-lookup"><span data-stu-id="f0e85-114">Attributes</span></span>  
  
|<span data-ttu-id="f0e85-115">属性</span><span class="sxs-lookup"><span data-stu-id="f0e85-115">Attribute</span></span>|<span data-ttu-id="f0e85-116">説明</span><span class="sxs-lookup"><span data-stu-id="f0e85-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="f0e85-117">サービス ホストによって使用されるベース アドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="f0e85-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0e85-118">子要素</span><span class="sxs-lookup"><span data-stu-id="f0e85-118">Child Elements</span></span>  
 <span data-ttu-id="f0e85-119">なし。</span><span class="sxs-lookup"><span data-stu-id="f0e85-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0e85-120">親要素</span><span class="sxs-lookup"><span data-stu-id="f0e85-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f0e85-121">要素</span><span class="sxs-lookup"><span data-stu-id="f0e85-121">Element</span></span>|<span data-ttu-id="f0e85-122">説明</span><span class="sxs-lookup"><span data-stu-id="f0e85-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0e85-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="f0e85-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="f0e85-124">`baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="f0e85-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0e85-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0e85-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="f0e85-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="f0e85-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

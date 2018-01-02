---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69a049e1daacce901685050ab9fbe99a9c4d3428
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="a7811-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="a7811-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="a7811-103">自己ホスト環境でのサービス ホストのベース アドレスである `baseAddress` 要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="a7811-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="a7811-104">ベース アドレスが存在すると、そのベース アドレスに関連したアドレスを使用してエンドポイントを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a7811-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="a7811-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a7811-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7811-106">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="a7811-106">\<client></span></span>  
<span data-ttu-id="a7811-107">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="a7811-107">\<endpoint></span></span>  
<span data-ttu-id="a7811-108">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="a7811-108">\<host></span></span>  
<span data-ttu-id="a7811-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="a7811-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7811-110">構文</span><span class="sxs-lookup"><span data-stu-id="a7811-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="a7811-111">型</span><span class="sxs-lookup"><span data-stu-id="a7811-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7811-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a7811-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a7811-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7811-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7811-114">属性</span><span class="sxs-lookup"><span data-stu-id="a7811-114">Attributes</span></span>  
 <span data-ttu-id="a7811-115">なし。</span><span class="sxs-lookup"><span data-stu-id="a7811-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7811-116">子要素</span><span class="sxs-lookup"><span data-stu-id="a7811-116">Child Elements</span></span>  
  
|<span data-ttu-id="a7811-117">要素</span><span class="sxs-lookup"><span data-stu-id="a7811-117">Element</span></span>|<span data-ttu-id="a7811-118">説明</span><span class="sxs-lookup"><span data-stu-id="a7811-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7811-119">\<add></span><span class="sxs-lookup"><span data-stu-id="a7811-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="a7811-120">サービス ホストによって使用されるベース アドレスを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="a7811-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7811-121">親要素</span><span class="sxs-lookup"><span data-stu-id="a7811-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a7811-122">要素</span><span class="sxs-lookup"><span data-stu-id="a7811-122">Element</span></span>|<span data-ttu-id="a7811-123">説明</span><span class="sxs-lookup"><span data-stu-id="a7811-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7811-124">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="a7811-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="a7811-125">サービス ホストの設定を指定する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="a7811-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7811-126">参照</span><span class="sxs-lookup"><span data-stu-id="a7811-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="a7811-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a7811-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)

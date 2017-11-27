---
title: '&lt;serviceTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecefda0a3447aa029079fbb3633b05054f42195a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="8c8ba-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="8c8ba-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="8c8ba-103">サービスのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c8ba-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="8c8ba-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8c8ba-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c8ba-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="8c8ba-105">\<behaviors></span></span>  
<span data-ttu-id="8c8ba-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8c8ba-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8c8ba-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="8c8ba-107">\<behavior></span></span>  
<span data-ttu-id="8c8ba-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="8c8ba-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8ba-109">構文</span><span class="sxs-lookup"><span data-stu-id="8c8ba-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="8c8ba-110">型</span><span class="sxs-lookup"><span data-stu-id="8c8ba-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c8ba-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8c8ba-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8c8ba-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c8ba-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c8ba-113">属性</span><span class="sxs-lookup"><span data-stu-id="8c8ba-113">Attributes</span></span>  
  
|<span data-ttu-id="8c8ba-114">属性</span><span class="sxs-lookup"><span data-stu-id="8c8ba-114">Attribute</span></span>|<span data-ttu-id="8c8ba-115">説明</span><span class="sxs-lookup"><span data-stu-id="8c8ba-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="8c8ba-116">クライアントからサーバーへのトランザクションが発生するまでに待機できる時間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="8c8ba-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="8c8ba-117">既定値は"00: 00:00"です。</span><span class="sxs-lookup"><span data-stu-id="8c8ba-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c8ba-118">子要素</span><span class="sxs-lookup"><span data-stu-id="8c8ba-118">Child Elements</span></span>  
 <span data-ttu-id="8c8ba-119">なし。</span><span class="sxs-lookup"><span data-stu-id="8c8ba-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c8ba-120">親要素</span><span class="sxs-lookup"><span data-stu-id="8c8ba-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8c8ba-121">要素</span><span class="sxs-lookup"><span data-stu-id="8c8ba-121">Element</span></span>|<span data-ttu-id="8c8ba-122">説明</span><span class="sxs-lookup"><span data-stu-id="8c8ba-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c8ba-123">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="8c8ba-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8c8ba-124">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="8c8ba-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c8ba-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c8ba-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

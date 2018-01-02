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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d8bfde535eb417614eee4ec6a2db7985152be33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="e67df-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="e67df-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="e67df-103">サービスのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="e67df-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="e67df-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e67df-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e67df-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e67df-105">\<behaviors></span></span>  
<span data-ttu-id="e67df-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e67df-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e67df-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e67df-107">\<behavior></span></span>  
<span data-ttu-id="e67df-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="e67df-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e67df-109">構文</span><span class="sxs-lookup"><span data-stu-id="e67df-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="e67df-110">型</span><span class="sxs-lookup"><span data-stu-id="e67df-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e67df-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e67df-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e67df-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e67df-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e67df-113">属性</span><span class="sxs-lookup"><span data-stu-id="e67df-113">Attributes</span></span>  
  
|<span data-ttu-id="e67df-114">属性</span><span class="sxs-lookup"><span data-stu-id="e67df-114">Attribute</span></span>|<span data-ttu-id="e67df-115">説明</span><span class="sxs-lookup"><span data-stu-id="e67df-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="e67df-116">クライアントからサーバーへのトランザクションが発生するまでに待機できる時間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="e67df-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="e67df-117">既定値は"00: 00:00"です。</span><span class="sxs-lookup"><span data-stu-id="e67df-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e67df-118">子要素</span><span class="sxs-lookup"><span data-stu-id="e67df-118">Child Elements</span></span>  
 <span data-ttu-id="e67df-119">なし。</span><span class="sxs-lookup"><span data-stu-id="e67df-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e67df-120">親要素</span><span class="sxs-lookup"><span data-stu-id="e67df-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e67df-121">要素</span><span class="sxs-lookup"><span data-stu-id="e67df-121">Element</span></span>|<span data-ttu-id="e67df-122">説明</span><span class="sxs-lookup"><span data-stu-id="e67df-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e67df-123">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e67df-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e67df-124">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="e67df-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e67df-125">参照</span><span class="sxs-lookup"><span data-stu-id="e67df-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>

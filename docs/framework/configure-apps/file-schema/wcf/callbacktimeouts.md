---
title: '&lt;callbackTimeouts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a030a615aae0159e1426bdf4c640ddfab7287dd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcallbacktimeoutsgt"></a><span data-ttu-id="1d9b5-102">&lt;callbackTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="1d9b5-102">&lt;callbackTimeouts&gt;</span></span>
<span data-ttu-id="1d9b5-103">双方向コールバック コントラクト シナリオでトランザクションをサーバーからクライアントに転送する際のタイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="1d9b5-103">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
 <span data-ttu-id="1d9b5-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1d9b5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d9b5-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="1d9b5-105">\<behaviors></span></span>  
<span data-ttu-id="1d9b5-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1d9b5-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1d9b5-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1d9b5-107">\<behavior></span></span>  
<span data-ttu-id="1d9b5-108">\<callbackTimeOuts ></span><span class="sxs-lookup"><span data-stu-id="1d9b5-108">\<callbackTimeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d9b5-109">構文</span><span class="sxs-lookup"><span data-stu-id="1d9b5-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="1d9b5-110">型</span><span class="sxs-lookup"><span data-stu-id="1d9b5-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d9b5-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1d9b5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1d9b5-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d9b5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d9b5-113">属性</span><span class="sxs-lookup"><span data-stu-id="1d9b5-113">Attributes</span></span>  
  
|<span data-ttu-id="1d9b5-114">属性</span><span class="sxs-lookup"><span data-stu-id="1d9b5-114">Attribute</span></span>|<span data-ttu-id="1d9b5-115">説明</span><span class="sxs-lookup"><span data-stu-id="1d9b5-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="1d9b5-116">トランザクションが完了する必要があるまたは自動的に終了される必要がある制限時間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="1d9b5-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="1d9b5-117">既定値は"00: 00:00"です。</span><span class="sxs-lookup"><span data-stu-id="1d9b5-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d9b5-118">子要素</span><span class="sxs-lookup"><span data-stu-id="1d9b5-118">Child Elements</span></span>  
 <span data-ttu-id="1d9b5-119">なし。</span><span class="sxs-lookup"><span data-stu-id="1d9b5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d9b5-120">親要素</span><span class="sxs-lookup"><span data-stu-id="1d9b5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1d9b5-121">要素</span><span class="sxs-lookup"><span data-stu-id="1d9b5-121">Element</span></span>|<span data-ttu-id="1d9b5-122">説明</span><span class="sxs-lookup"><span data-stu-id="1d9b5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d9b5-123">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="1d9b5-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1d9b5-124">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="1d9b5-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d9b5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d9b5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>

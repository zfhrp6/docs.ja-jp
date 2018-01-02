---
title: "&lt;synchronousReceive&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a><span data-ttu-id="35525-102">&lt;synchronousReceive&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="35525-102">&lt;synchronousReceive&gt; element</span></span>
<span data-ttu-id="35525-103">この構成要素は、サービスまたはクライアント アプリケーションでメッセージを受信する場合のランタイム動作を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="35525-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="35525-104">属性や子要素はありません。</span><span class="sxs-lookup"><span data-stu-id="35525-104">It does not have any attributes or child elements.</span></span>  
  
 <span data-ttu-id="35525-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="35525-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="35525-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="35525-106">\<behaviors></span></span>  
<span data-ttu-id="35525-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="35525-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="35525-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="35525-108">\<behavior></span></span>  
<span data-ttu-id="35525-109">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="35525-109">\<synchronousReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35525-110">構文</span><span class="sxs-lookup"><span data-stu-id="35525-110">Syntax</span></span>  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35525-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="35525-111">Attributes and Elements</span></span>  
 <span data-ttu-id="35525-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="35525-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35525-113">属性</span><span class="sxs-lookup"><span data-stu-id="35525-113">Attributes</span></span>  
 <span data-ttu-id="35525-114">なし。</span><span class="sxs-lookup"><span data-stu-id="35525-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="35525-115">子要素</span><span class="sxs-lookup"><span data-stu-id="35525-115">Child Elements</span></span>  
 <span data-ttu-id="35525-116">なし。</span><span class="sxs-lookup"><span data-stu-id="35525-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35525-117">親要素</span><span class="sxs-lookup"><span data-stu-id="35525-117">Parent Elements</span></span>  
  
|<span data-ttu-id="35525-118">要素</span><span class="sxs-lookup"><span data-stu-id="35525-118">Element</span></span>|<span data-ttu-id="35525-119">説明</span><span class="sxs-lookup"><span data-stu-id="35525-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35525-120">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="35525-120">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="35525-121">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="35525-121">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35525-122">コメント</span><span class="sxs-lookup"><span data-stu-id="35525-122">Remarks</span></span>  
 <span data-ttu-id="35525-123">この動作を使用して、既定の非同期受信ではなく同期受信を使用するようにチャネル リスナーに指示します。</span><span class="sxs-lookup"><span data-stu-id="35525-123">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="35525-124"> は、受け入れた各チャネルに対して新しい処理スレッドを発行します。</span><span class="sxs-lookup"><span data-stu-id="35525-124"> issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="35525-125">チャネルが多数ある場合は、スレッドが不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35525-125">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35525-126">参照</span><span class="sxs-lookup"><span data-stu-id="35525-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

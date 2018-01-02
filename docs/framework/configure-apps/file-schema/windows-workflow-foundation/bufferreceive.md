---
title: '&lt;bufferReceive&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b5b6176e7c5b982bc9f41b13c669af104bf784f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="6c831-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="6c831-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="6c831-103">サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="6c831-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="6c831-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6c831-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c831-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="6c831-105">\<behaviors></span></span>  
<span data-ttu-id="6c831-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6c831-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6c831-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="6c831-107">\<behavior></span></span>  
<span data-ttu-id="6c831-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="6c831-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c831-109">構文</span><span class="sxs-lookup"><span data-stu-id="6c831-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c831-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6c831-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6c831-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c831-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c831-112">属性</span><span class="sxs-lookup"><span data-stu-id="6c831-112">Attributes</span></span>  
  
|<span data-ttu-id="6c831-113">属性</span><span class="sxs-lookup"><span data-stu-id="6c831-113">Attribute</span></span>|<span data-ttu-id="6c831-114">説明</span><span class="sxs-lookup"><span data-stu-id="6c831-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c831-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="6c831-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="6c831-116">各チャネルで許容される保留状態のメッセージの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="6c831-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="6c831-117">既定値は 512 です。</span><span class="sxs-lookup"><span data-stu-id="6c831-117">The default value is 512.</span></span> <span data-ttu-id="6c831-118">このプロパティは、ワークフロー サービスで受信できる、順番を無視したメッセージの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="6c831-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c831-119">子要素</span><span class="sxs-lookup"><span data-stu-id="6c831-119">Child Elements</span></span>  
 <span data-ttu-id="6c831-120">なし。</span><span class="sxs-lookup"><span data-stu-id="6c831-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c831-121">親要素</span><span class="sxs-lookup"><span data-stu-id="6c831-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6c831-122">要素</span><span class="sxs-lookup"><span data-stu-id="6c831-122">Element</span></span>|<span data-ttu-id="6c831-123">説明</span><span class="sxs-lookup"><span data-stu-id="6c831-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c831-124">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6c831-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6c831-125">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c831-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c831-126">参照</span><span class="sxs-lookup"><span data-stu-id="6c831-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>

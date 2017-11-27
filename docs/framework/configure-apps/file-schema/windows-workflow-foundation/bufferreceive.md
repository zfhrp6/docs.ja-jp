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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 623ff924e171282c399bddcdc212a0606a3416d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="28b77-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="28b77-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="28b77-103">サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="28b77-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="28b77-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="28b77-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="28b77-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="28b77-105">\<behaviors></span></span>  
<span data-ttu-id="28b77-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28b77-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="28b77-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="28b77-107">\<behavior></span></span>  
<span data-ttu-id="28b77-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="28b77-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b77-109">構文</span><span class="sxs-lookup"><span data-stu-id="28b77-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28b77-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="28b77-110">Attributes and Elements</span></span>  
 <span data-ttu-id="28b77-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b77-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28b77-112">属性</span><span class="sxs-lookup"><span data-stu-id="28b77-112">Attributes</span></span>  
  
|<span data-ttu-id="28b77-113">属性</span><span class="sxs-lookup"><span data-stu-id="28b77-113">Attribute</span></span>|<span data-ttu-id="28b77-114">説明</span><span class="sxs-lookup"><span data-stu-id="28b77-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28b77-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="28b77-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="28b77-116">各チャネルで許容される保留状態のメッセージの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="28b77-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="28b77-117">既定値は 512 です。</span><span class="sxs-lookup"><span data-stu-id="28b77-117">The default value is 512.</span></span> <span data-ttu-id="28b77-118">このプロパティは、ワークフロー サービスで受信できる、順番を無視したメッセージの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="28b77-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28b77-119">子要素</span><span class="sxs-lookup"><span data-stu-id="28b77-119">Child Elements</span></span>  
 <span data-ttu-id="28b77-120">なし。</span><span class="sxs-lookup"><span data-stu-id="28b77-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28b77-121">親要素</span><span class="sxs-lookup"><span data-stu-id="28b77-121">Parent Elements</span></span>  
  
|<span data-ttu-id="28b77-122">要素</span><span class="sxs-lookup"><span data-stu-id="28b77-122">Element</span></span>|<span data-ttu-id="28b77-123">説明</span><span class="sxs-lookup"><span data-stu-id="28b77-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28b77-124">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="28b77-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="28b77-125">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="28b77-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28b77-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="28b77-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>

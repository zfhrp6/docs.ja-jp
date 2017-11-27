---
title: '&lt;workflowIdle&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5f9b4989de57204d9ec97d69475121c30ae82644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="512c7-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="512c7-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="512c7-103">アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。</span><span class="sxs-lookup"><span data-stu-id="512c7-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="512c7-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="512c7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="512c7-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="512c7-105">\<behaviors></span></span>  
<span data-ttu-id="512c7-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="512c7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="512c7-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="512c7-107">\<behavior></span></span>  
<span data-ttu-id="512c7-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="512c7-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512c7-109">構文</span><span class="sxs-lookup"><span data-stu-id="512c7-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="512c7-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="512c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="512c7-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="512c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="512c7-112">属性</span><span class="sxs-lookup"><span data-stu-id="512c7-112">Attributes</span></span>  
  
|<span data-ttu-id="512c7-113">属性</span><span class="sxs-lookup"><span data-stu-id="512c7-113">Attribute</span></span>|<span data-ttu-id="512c7-114">説明</span><span class="sxs-lookup"><span data-stu-id="512c7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="512c7-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="512c7-115">timeToPersist</span></span>|<span data-ttu-id="512c7-116">ワークフローがアイドル状態になりが永続化されるまでの間の期間を指定する Timespan 値です。</span><span class="sxs-lookup"><span data-stu-id="512c7-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="512c7-117">既定値は、TimeSpan.MaxValue です。</span><span class="sxs-lookup"><span data-stu-id="512c7-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="512c7-118">継続時間は、ワークフロー インスタンスがアイドル状態になった時点から開始します。</span><span class="sxs-lookup"><span data-stu-id="512c7-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="512c7-119">この属性はできるだけ長く用のメモリ内インスタンスも保持しながら、ワークフロー インスタンスをより積極的に永続化する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="512c7-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="512c7-120">この属性は有効なは、その値がある場合のみより小さい**timeToUnload**属性。</span><span class="sxs-lookup"><span data-stu-id="512c7-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="512c7-121">それより大きい場合は無視されます。</span><span class="sxs-lookup"><span data-stu-id="512c7-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="512c7-122">この属性が値を指定する前に経過すると、 **timeToUnload**属性に、ワークフローが読み込まれる前に、永続化を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="512c7-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="512c7-123">これは、ワークフローを永続化するまでアンロード操作に遅延が生じる場合があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="512c7-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="512c7-124">永続化レイヤーは一時的なエラーの再試行処理は行いますが、回復不可能なエラーに対しては例外をスローするだけです。</span><span class="sxs-lookup"><span data-stu-id="512c7-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="512c7-125">したがって、永続化中にスローされる例外は致命的な例外として処理され、ワークフロー インスタンスが中止されます。</span><span class="sxs-lookup"><span data-stu-id="512c7-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="512c7-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="512c7-126">timeToUnload</span></span>|<span data-ttu-id="512c7-127">ワークフローがアイドル状態からアンロードされるまでの継続時間を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="512c7-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="512c7-128">既定値は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="512c7-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="512c7-129">ワークフローをアンロードすることは、同時に、永続化することも意味します。</span><span class="sxs-lookup"><span data-stu-id="512c7-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="512c7-130">この属性は、ワークフロー インスタンスが永続化し、アンロードした直後にゼロに設定されている場合、ワークフローはアイドル状態になります。</span><span class="sxs-lookup"><span data-stu-id="512c7-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="512c7-131">この属性を TimeSpan.MaxValue を効果的に設定すると、アンロード操作が無効にします。</span><span class="sxs-lookup"><span data-stu-id="512c7-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="512c7-132">アイドル状態になったワークフロー インスタンスはアンロードされません。</span><span class="sxs-lookup"><span data-stu-id="512c7-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="512c7-133">子要素</span><span class="sxs-lookup"><span data-stu-id="512c7-133">Child Elements</span></span>  
 <span data-ttu-id="512c7-134">なし。</span><span class="sxs-lookup"><span data-stu-id="512c7-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="512c7-135">親要素</span><span class="sxs-lookup"><span data-stu-id="512c7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="512c7-136">要素</span><span class="sxs-lookup"><span data-stu-id="512c7-136">Element</span></span>|<span data-ttu-id="512c7-137">説明</span><span class="sxs-lookup"><span data-stu-id="512c7-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="512c7-138">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="512c7-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="512c7-139">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="512c7-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="512c7-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="512c7-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>

---
title: '&lt;workflowUnhandledException&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4266eb6480c98c7ea1b96f2325a018b0fdcba041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="e9e7c-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="e9e7c-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="e9e7c-103">ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="e9e7c-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="e9e7c-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e9e7c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9e7c-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e9e7c-105">\<behaviors></span></span>  
<span data-ttu-id="e9e7c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9e7c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e9e7c-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e9e7c-107">\<behavior></span></span>  
<span data-ttu-id="e9e7c-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="e9e7c-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e7c-109">構文</span><span class="sxs-lookup"><span data-stu-id="e9e7c-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9e7c-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9e7c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e9e7c-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9e7c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9e7c-112">属性</span><span class="sxs-lookup"><span data-stu-id="e9e7c-112">Attributes</span></span>  
  
|<span data-ttu-id="e9e7c-113">属性</span><span class="sxs-lookup"><span data-stu-id="e9e7c-113">Attribute</span></span>|<span data-ttu-id="e9e7c-114">説明</span><span class="sxs-lookup"><span data-stu-id="e9e7c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9e7c-115">アクション</span><span class="sxs-lookup"><span data-stu-id="e9e7c-115">action</span></span>|<span data-ttu-id="e9e7c-116">未処理の例外が発生した場合のアクションを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e9e7c-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="e9e7c-117">この属性は <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="e9e7c-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9e7c-118">子要素</span><span class="sxs-lookup"><span data-stu-id="e9e7c-118">Child Elements</span></span>  
 <span data-ttu-id="e9e7c-119">なし。</span><span class="sxs-lookup"><span data-stu-id="e9e7c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9e7c-120">親要素</span><span class="sxs-lookup"><span data-stu-id="e9e7c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e9e7c-121">要素</span><span class="sxs-lookup"><span data-stu-id="e9e7c-121">Element</span></span>|<span data-ttu-id="e9e7c-122">説明</span><span class="sxs-lookup"><span data-stu-id="e9e7c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9e7c-123">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9e7c-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e9e7c-124">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9e7c-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9e7c-125">参照</span><span class="sxs-lookup"><span data-stu-id="e9e7c-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>

---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: d9db6ecc2e95e0d1ec5738f1d2f4a09a89c57f21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="159ce-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="159ce-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="159ce-103">ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="159ce-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="159ce-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="159ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="159ce-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="159ce-105">\<behaviors></span></span>  
<span data-ttu-id="159ce-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="159ce-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="159ce-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="159ce-107">\<behavior></span></span>  
<span data-ttu-id="159ce-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="159ce-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="159ce-109">構文</span><span class="sxs-lookup"><span data-stu-id="159ce-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="159ce-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="159ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="159ce-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="159ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="159ce-112">属性</span><span class="sxs-lookup"><span data-stu-id="159ce-112">Attributes</span></span>  
  
|<span data-ttu-id="159ce-113">属性</span><span class="sxs-lookup"><span data-stu-id="159ce-113">Attribute</span></span>|<span data-ttu-id="159ce-114">説明</span><span class="sxs-lookup"><span data-stu-id="159ce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="159ce-115">アクション</span><span class="sxs-lookup"><span data-stu-id="159ce-115">action</span></span>|<span data-ttu-id="159ce-116">未処理の例外が発生した場合のアクションを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="159ce-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="159ce-117">この属性は <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="159ce-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="159ce-118">子要素</span><span class="sxs-lookup"><span data-stu-id="159ce-118">Child Elements</span></span>  
 <span data-ttu-id="159ce-119">なし。</span><span class="sxs-lookup"><span data-stu-id="159ce-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="159ce-120">親要素</span><span class="sxs-lookup"><span data-stu-id="159ce-120">Parent Elements</span></span>  
  
|<span data-ttu-id="159ce-121">要素</span><span class="sxs-lookup"><span data-stu-id="159ce-121">Element</span></span>|<span data-ttu-id="159ce-122">説明</span><span class="sxs-lookup"><span data-stu-id="159ce-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="159ce-123">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="159ce-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="159ce-124">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="159ce-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="159ce-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="159ce-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>

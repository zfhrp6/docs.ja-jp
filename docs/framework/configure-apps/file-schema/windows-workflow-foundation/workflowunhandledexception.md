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
ms.openlocfilehash: 03123081c16a94d006ebee6373cf744d7d46b5b8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="8f917-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="8f917-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="8f917-103">ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="8f917-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="8f917-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8f917-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8f917-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="8f917-105">\<behaviors></span></span>  
<span data-ttu-id="8f917-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8f917-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8f917-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="8f917-107">\<behavior></span></span>  
<span data-ttu-id="8f917-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="8f917-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f917-109">構文</span><span class="sxs-lookup"><span data-stu-id="8f917-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f917-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8f917-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8f917-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8f917-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f917-112">属性</span><span class="sxs-lookup"><span data-stu-id="8f917-112">Attributes</span></span>  
  
|<span data-ttu-id="8f917-113">属性</span><span class="sxs-lookup"><span data-stu-id="8f917-113">Attribute</span></span>|<span data-ttu-id="8f917-114">説明</span><span class="sxs-lookup"><span data-stu-id="8f917-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f917-115">アクション</span><span class="sxs-lookup"><span data-stu-id="8f917-115">action</span></span>|<span data-ttu-id="8f917-116">未処理の例外が発生した場合のアクションを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="8f917-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="8f917-117">この属性は <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> 型です。</span><span class="sxs-lookup"><span data-stu-id="8f917-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f917-118">子要素</span><span class="sxs-lookup"><span data-stu-id="8f917-118">Child Elements</span></span>  
 <span data-ttu-id="8f917-119">なし。</span><span class="sxs-lookup"><span data-stu-id="8f917-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f917-120">親要素</span><span class="sxs-lookup"><span data-stu-id="8f917-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8f917-121">要素</span><span class="sxs-lookup"><span data-stu-id="8f917-121">Element</span></span>|<span data-ttu-id="8f917-122">説明</span><span class="sxs-lookup"><span data-stu-id="8f917-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f917-123">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8f917-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8f917-124">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="8f917-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f917-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f917-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>

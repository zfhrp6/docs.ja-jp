---
title: "&lt;services&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60a717513689aeba1bfbd6229d4eef28024df8c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="31240-102">&lt;services&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="31240-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="31240-103">ワークフロー ベースの <xref:System.Workflow.Runtime.WorkflowRuntime> サービスをホストする [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] のインスタンスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="31240-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="31240-104">この要素は <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="31240-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="31240-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="31240-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="31240-106">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="31240-106">\<behaviors></span></span>  
<span data-ttu-id="31240-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="31240-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="31240-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="31240-108">\<behavior></span></span>  
<span data-ttu-id="31240-109">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="31240-109">\<services></span></span>  
<span data-ttu-id="31240-110">\<add></span><span class="sxs-lookup"><span data-stu-id="31240-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31240-111">構文</span><span class="sxs-lookup"><span data-stu-id="31240-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31240-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="31240-112">Attributes and Elements</span></span>  
 <span data-ttu-id="31240-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="31240-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31240-114">属性</span><span class="sxs-lookup"><span data-stu-id="31240-114">Attributes</span></span>  
  
|<span data-ttu-id="31240-115">属性</span><span class="sxs-lookup"><span data-stu-id="31240-115">Attribute</span></span>|<span data-ttu-id="31240-116">説明</span><span class="sxs-lookup"><span data-stu-id="31240-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31240-117">型</span><span class="sxs-lookup"><span data-stu-id="31240-117">type</span></span>|<span data-ttu-id="31240-118">初期化するサービスのアセンブリ修飾型名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="31240-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="31240-119">指定されたサービスは、そのコンストラクターのシグネチャに関して一定の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="31240-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="31240-120">詳細については、「<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31240-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31240-121">子要素</span><span class="sxs-lookup"><span data-stu-id="31240-121">Child Elements</span></span>  
 <span data-ttu-id="31240-122">なし。</span><span class="sxs-lookup"><span data-stu-id="31240-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31240-123">親要素</span><span class="sxs-lookup"><span data-stu-id="31240-123">Parent Elements</span></span>  
  
|<span data-ttu-id="31240-124">要素</span><span class="sxs-lookup"><span data-stu-id="31240-124">Element</span></span>|<span data-ttu-id="31240-125">説明</span><span class="sxs-lookup"><span data-stu-id="31240-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31240-126">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="31240-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="31240-127"><xref:System.Workflow.Runtime.WorkflowRuntime> エンジンに追加されるサービスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="31240-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="31240-128">要素は、<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="31240-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="31240-129">コレクションで指定されたサービスはワークフロー ランタイム エンジンによって初期化され、適切な <xref:System.Workflow.Runtime.WorkflowRuntime> コンストラクターが呼び出されるとワークフロー ランタイム エンジンのサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="31240-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="31240-130">したがって、コレクションで指定されたサービスは、そのコンストラクターのシグネチャに関して一定の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="31240-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="31240-131">詳細については、「<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31240-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31240-132">コメント</span><span class="sxs-lookup"><span data-stu-id="31240-132">Remarks</span></span>  
 <span data-ttu-id="31240-133">この要素で指定されたサービスはワークフロー ランタイム エンジンによって初期化され、適切な <xref:System.Workflow.Runtime.WorkflowRuntime> コンストラクターが呼び出されるとワークフロー ランタイム エンジンのサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="31240-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="31240-134">したがって、指定されたサービスは、そのコンストラクターのシグネチャに関して一定の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="31240-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="31240-135">詳細については、「<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31240-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31240-136">例</span><span class="sxs-lookup"><span data-stu-id="31240-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="31240-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="31240-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="31240-138">ワークフロー構成ファイル</span><span class="sxs-lookup"><span data-stu-id="31240-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)

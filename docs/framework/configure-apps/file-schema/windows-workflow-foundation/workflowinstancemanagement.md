---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3be696133bff5c1fc8858ab31093866ed05c98a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="b87f5-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="b87f5-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="b87f5-103">ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b87f5-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="b87f5-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b87f5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b87f5-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="b87f5-105">\<behaviors></span></span>  
<span data-ttu-id="b87f5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b87f5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b87f5-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="b87f5-107">\<behavior></span></span>  
<span data-ttu-id="b87f5-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="b87f5-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b87f5-109">構文</span><span class="sxs-lookup"><span data-stu-id="b87f5-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b87f5-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b87f5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b87f5-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b87f5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b87f5-112">属性</span><span class="sxs-lookup"><span data-stu-id="b87f5-112">Attributes</span></span>  
  
|<span data-ttu-id="b87f5-113">属性</span><span class="sxs-lookup"><span data-stu-id="b87f5-113">Attribute</span></span>|<span data-ttu-id="b87f5-114">説明</span><span class="sxs-lookup"><span data-stu-id="b87f5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b87f5-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="b87f5-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="b87f5-116">子要素</span><span class="sxs-lookup"><span data-stu-id="b87f5-116">Child Elements</span></span>  
 <span data-ttu-id="b87f5-117">なし。</span><span class="sxs-lookup"><span data-stu-id="b87f5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b87f5-118">親要素</span><span class="sxs-lookup"><span data-stu-id="b87f5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b87f5-119">要素</span><span class="sxs-lookup"><span data-stu-id="b87f5-119">Element</span></span>|<span data-ttu-id="b87f5-120">説明</span><span class="sxs-lookup"><span data-stu-id="b87f5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b87f5-121">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b87f5-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b87f5-122">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="b87f5-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b87f5-123">参照</span><span class="sxs-lookup"><span data-stu-id="b87f5-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>

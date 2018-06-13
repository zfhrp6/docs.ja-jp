---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: d86b0f61c6741fa156e04da75a62853f459324d1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767103"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="b0ec3-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="b0ec3-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="b0ec3-103">ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b0ec3-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="b0ec3-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b0ec3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0ec3-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="b0ec3-105">\<behaviors></span></span>  
<span data-ttu-id="b0ec3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b0ec3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b0ec3-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b0ec3-107">\<behavior></span></span>  
<span data-ttu-id="b0ec3-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="b0ec3-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ec3-109">構文</span><span class="sxs-lookup"><span data-stu-id="b0ec3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0ec3-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b0ec3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b0ec3-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b0ec3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0ec3-112">属性</span><span class="sxs-lookup"><span data-stu-id="b0ec3-112">Attributes</span></span>  
  
|<span data-ttu-id="b0ec3-113">属性</span><span class="sxs-lookup"><span data-stu-id="b0ec3-113">Attribute</span></span>|<span data-ttu-id="b0ec3-114">説明</span><span class="sxs-lookup"><span data-stu-id="b0ec3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b0ec3-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="b0ec3-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="b0ec3-116">子要素</span><span class="sxs-lookup"><span data-stu-id="b0ec3-116">Child Elements</span></span>  
 <span data-ttu-id="b0ec3-117">なし。</span><span class="sxs-lookup"><span data-stu-id="b0ec3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0ec3-118">親要素</span><span class="sxs-lookup"><span data-stu-id="b0ec3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b0ec3-119">要素</span><span class="sxs-lookup"><span data-stu-id="b0ec3-119">Element</span></span>|<span data-ttu-id="b0ec3-120">説明</span><span class="sxs-lookup"><span data-stu-id="b0ec3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0ec3-121">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b0ec3-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b0ec3-122">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0ec3-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0ec3-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0ec3-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>

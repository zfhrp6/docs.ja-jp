---
title: "ワークフローの &lt;behaviors&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40278c0a3d99dd5c37df1d642b8a2e13e9f62633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="e222b-102">ワークフローの &lt;behaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="e222b-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="e222b-103">この要素が含まれています、 **serviceBehaviors**コレクション。</span><span class="sxs-lookup"><span data-stu-id="e222b-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="e222b-104">コレクション内の各要素は、ワークフロー サービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="e222b-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="e222b-105">各動作要素は、独自のによって識別される**名前**属性。</span><span class="sxs-lookup"><span data-stu-id="e222b-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="e222b-106">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e222b-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e222b-107">構文</span><span class="sxs-lookup"><span data-stu-id="e222b-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e222b-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e222b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e222b-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e222b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e222b-110">属性</span><span class="sxs-lookup"><span data-stu-id="e222b-110">Attributes</span></span>  
 <span data-ttu-id="e222b-111">なし</span><span class="sxs-lookup"><span data-stu-id="e222b-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e222b-112">子要素</span><span class="sxs-lookup"><span data-stu-id="e222b-112">Child Elements</span></span>  
  
|<span data-ttu-id="e222b-113">要素</span><span class="sxs-lookup"><span data-stu-id="e222b-113">Element</span></span>|<span data-ttu-id="e222b-114">説明</span><span class="sxs-lookup"><span data-stu-id="e222b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e222b-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e222b-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="e222b-116">この構成セクションは、特定のワークフロー サービスに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="e222b-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e222b-117">親要素</span><span class="sxs-lookup"><span data-stu-id="e222b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e222b-118">要素</span><span class="sxs-lookup"><span data-stu-id="e222b-118">Element</span></span>|<span data-ttu-id="e222b-119">説明</span><span class="sxs-lookup"><span data-stu-id="e222b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e222b-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e222b-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e222b-121">すべてのワークフロー構成要素のルート要素。</span><span class="sxs-lookup"><span data-stu-id="e222b-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e222b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e222b-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="e222b-123">構成して、ランタイムのビヘイビアーの使用を拡張します。</span><span class="sxs-lookup"><span data-stu-id="e222b-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

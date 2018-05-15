---
title: ワークフローの &lt;behaviors&gt;
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 762fd1ff0de7980848ac3921706f406932c7f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="6d9f0-102">ワークフローの &lt;behaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="6d9f0-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="6d9f0-103">この要素が含まれています、 **serviceBehaviors**コレクション。</span><span class="sxs-lookup"><span data-stu-id="6d9f0-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="6d9f0-104">コレクション内の各要素は、ワークフロー サービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d9f0-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="6d9f0-105">各動作要素は、独自のによって識別される**名前**属性。</span><span class="sxs-lookup"><span data-stu-id="6d9f0-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="6d9f0-106">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6d9f0-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9f0-107">構文</span><span class="sxs-lookup"><span data-stu-id="6d9f0-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d9f0-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6d9f0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6d9f0-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d9f0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d9f0-110">属性</span><span class="sxs-lookup"><span data-stu-id="6d9f0-110">Attributes</span></span>  
 <span data-ttu-id="6d9f0-111">なし</span><span class="sxs-lookup"><span data-stu-id="6d9f0-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6d9f0-112">子要素</span><span class="sxs-lookup"><span data-stu-id="6d9f0-112">Child Elements</span></span>  
  
|<span data-ttu-id="6d9f0-113">要素</span><span class="sxs-lookup"><span data-stu-id="6d9f0-113">Element</span></span>|<span data-ttu-id="6d9f0-114">説明</span><span class="sxs-lookup"><span data-stu-id="6d9f0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d9f0-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6d9f0-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="6d9f0-116">この構成セクションは、特定のワークフロー サービスに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="6d9f0-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d9f0-117">親要素</span><span class="sxs-lookup"><span data-stu-id="6d9f0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6d9f0-118">要素</span><span class="sxs-lookup"><span data-stu-id="6d9f0-118">Element</span></span>|<span data-ttu-id="6d9f0-119">説明</span><span class="sxs-lookup"><span data-stu-id="6d9f0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d9f0-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6d9f0-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="6d9f0-121">すべてのワークフロー構成要素のルート要素。</span><span class="sxs-lookup"><span data-stu-id="6d9f0-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d9f0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d9f0-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="6d9f0-123">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="6d9f0-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

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
ms.locfileid: "32767311"
---
# <a name="ltbehaviorsgt-of-workflow"></a>ワークフローの &lt;behaviors&gt;
この要素が含まれています、 **serviceBehaviors**コレクション。  コレクション内の各要素は、ワークフロー サービスによって使用されるそれぞれの動作要素を定義します。 各動作要素は、独自のによって識別される**名前**属性。  
  
 \<system.ServiceModel >  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|この構成セクションは、特定のワークフロー サービスに対して定義されたすべての動作を表します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべてのワークフロー構成要素のルート要素。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [動作を使用したランタイムの構成と拡張](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

---
title: "ワークフローの &lt;behaviors&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# ワークフローの &lt;behaviors&gt;
この要素には、**serviceBehaviors** コレクションが含まれています。  コレクション内の各要素は、ワークフロー サービスによって使用されるそれぞれの動作要素を定義します。  各動作要素は、その一意の **name** 属性で識別されます。  
  
 \<system.ServiceModel\>  
  
## 構文  
  
```  
  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|この構成セクションは、特定のワークフロー サービスに対して定義されたすべての動作を表します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべてのワークフロー構成要素のルート要素。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>   
 [動作を使用したランタイムの構成と拡張](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
---
title: "WCF の &lt;cancelRequestedQueries&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF の &lt;cancelRequestedQueries&gt;
親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。  追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。  
  
 追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)」を参照してください。  
  
## 構文  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
       </workflow>  
   </trackingProfile>  
</tracking>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<cancelRequestedQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<workflow\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。|  
  
## 参照  
 <xref:System.Activities.Tracking.CancelRequestedQuery>   
 [ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)
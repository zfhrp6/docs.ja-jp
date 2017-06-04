---
title: "&lt;activityStateQuery&gt; の &lt;states&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;activityStateQuery&gt; の &lt;states&gt;
追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素のコレクション。  
  
 追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)」を参照してください。  
  
## 構文  
  
```vb  
  
<tracking>  
   <trackingProfile name="Name">  
       <workflow>  
          <activityStateQueries>  
             <activityStateQuery activityName="String" />  
                <states>  
                   <state name="String"/>  
                </states>  
          </activityStateQueries>  
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
|[\<state\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<activityStateQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素を表します。  追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。|  
  
## 解説  
 ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。  これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。  [\<arguments\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md) 要素、[\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) 要素、および [\<states\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) 要素を使用して、ワークフロー内の任意のアクティビティから任意の変数または引数を抽出できます。次の例は、アクティビティの `Closed` 追跡レコードが生成されたときに変数と引数を抽出する、アクティビティ状態クエリを示しています。  変数と引数は、ActivityStateRecord でのみ抽出できるため、[\<activityStateQuery\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md) を使用して追跡プロファイル内で定期受信されます。  
  
```  
  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
  
```  
  
## 参照  
 [System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection](assetId:///System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.Activities.Tracking.ActivityStateQuery](assetId:///System.Activities.Tracking.ActivityStateQuery?qualifyHint=False&amp;autoUpgrade=True)   
 [ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)
---
title: '&lt;trackingProfile&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 154830ff-ddd3-4397-a3b5-5b334907777f
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6acc4e5b71d94b712ae27e540df073828285b0aa
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="lttrackingprofilegt"></a>&lt;trackingProfile&gt;
ワークフロー追跡参加要素内のレコードを追跡するサブスクリプションを作成するための構成セクションを表します。 追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。 追跡プロファイル セクション内で定義されたクエリでは、サブスクリプションによって返されるイベントの種類が定義されます。  
  
 ワークフロー追跡とその構成の詳細については、次を参照してください。[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)と[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。  
  
\<system.serviceModel>  
\<tracking>  
\<trackingProfile>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|追跡プロファイルの名前を指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|によって識別される特定のワークフローのすべてのクエリを格納する構成要素、**ハイパーリンク"http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx"ctivityDefinitionId**プロパティです。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<tracking>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|ワークフロー サービスの追跡設定を定義する構成セクションを表します。|  
  
## <a name="remarks"></a>コメント  
 追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。 監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、大まかなプロファイルを作成できます。 それとは反対に、結果として得られるイベントが、後で詳細な実行フローを十分に再構築できるほど豊富な、詳細なプロファイルを作成することもできます。  
  
 追跡プロファイルは、特定の追跡レコードを対象としてワークフロー ランタイムを照会できる、追跡レコード用の宣言型のサブスクリプションとして構築されます。 いくつかのハイパーリンクのさまざまなクラスを定期受信できるクエリの種類の"http://msdn.microsoft.com/library/system.activities.tracking.trackingrecord(VS.100).aspx"TrackingRecord オブジェクト。 クエリの一覧については、次を参照してください[\<参加者 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)と[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).。  
  
 次の例では、追跡プロファイルを示しますをサブスクライブする追跡参加要素をできるようにする構成ファイルで、`Started`と`Completed`ワークフロー イベント。  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

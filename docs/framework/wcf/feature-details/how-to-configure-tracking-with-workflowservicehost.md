---
title: "方法: WorkflowServiceHost を使用して追跡を構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法: WorkflowServiceHost を使用して追跡を構成する
このトピックでは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされている [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ワークフロー サービスの追跡を構成する方法について説明します。  これは、Web.config ファイルにサービスの動作を指定することによって指定します。  
  
### 構成での追跡の構成  
  
1.  次の例に示すように、\<`behavior`\> 要素を構成ファイルで使用し、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加します。  
  
    ```  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
  
    ```  
  
    > [!NOTE]
    >  前の構成サンプルでは、簡略化された構成を使用しています。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     前の構成サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。  追跡プロファイルは、\<`tracking`\> 要素内の \<`trackingProfile`\> 要素で作成されます。  追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。  追跡プロファイルを作成する方法を次の例に示します。  
  
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
       </tracking>  
    </system.serviceModel>  
  
    ```  
  
     追跡プロファイル[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[追跡プロファイル](../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)」を参照してください。  
  
     追跡全般[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)」を参照してください。  
  
### コードでの追跡の構成  
  
1.  次の例に示すように、コードで <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> を動作を使用して <xref:System.Activities.Tracking.EtwTrackingParticipant> を追加します。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     前のコード サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。  追跡プロファイルは、前のセクションで説明したように \<`tracking`\> 要素内の \<`trackingProfile`\> 要素で作成されます。  
  
     追跡プロファイル[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[追跡プロファイル](../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)」を参照してください。  
  
     追跡全般[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)」を参照してください。  プログラムによる追跡の構成例については、「[ワークフローの追跡の構成](../../../../docs/framework/windows-workflow-foundation//configuring-tracking-for-a-workflow.md)」を参照してください。  
  
## 参照  
 [WCF サービスの簡略化された構成](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)   
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [追跡プロファイル](../../../../docs/framework/windows-workflow-foundation//tracking-profiles.md)
---
title: "方法: WorkflowServiceHost を使用して追跡を構成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42b5621275b9d27983619d18990e3d8e22c4e9db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>方法: WorkflowServiceHost を使用して追跡を構成する
このトピックでは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] でホストされている <xref:System.ServiceModel.Activities.WorkflowServiceHost> ワークフロー サービスの追跡を構成する方法について説明します。 これは、Web.config ファイルにサービスの動作を指定することによって指定します。  
  
### <a name="configure-tracking-in-configuration"></a>構成での追跡の構成  
  
1.  次の例に示すように、<<xref:System.Activities.Tracking.EtwTrackingParticipant>> 要素を構成ファイルで使用し、`behavior` を追加します。  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    >  前の構成サンプルでは、簡略化された構成を使用しています。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][構成を簡略化](../../../../docs/framework/wcf/simplified-configuration.md)です。  
  
     前の構成サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。 追跡プロファイルは、<`trackingProfile`> 要素内の <`tracking`> 要素で作成されます。 追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。 追跡プロファイルを作成する方法を次の例に示します。  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追跡プロファイルを参照してください[追跡プロファイル](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]一般に、追跡を参照してください[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)です。  
  
### <a name="configure-tracking-in-code"></a>コードでの追跡の構成  
  
1.  次の例に示すように、コードで <xref:System.Activities.Tracking.EtwTrackingParticipant> を動作を使用して <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> を追加します。  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     前のコード サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。 追跡プロファイルは、前のセクションで説明したように <`trackingProfile`> 要素内の <`tracking`> 要素で作成されます。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]追跡プロファイルを参照してください[追跡プロファイル](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]一般に、追跡を参照してください[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)です。 プログラムで追跡を構成する例を参照してください。[ワークフローの追跡を構成する](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスの簡略化された構成](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [追跡プロファイル](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

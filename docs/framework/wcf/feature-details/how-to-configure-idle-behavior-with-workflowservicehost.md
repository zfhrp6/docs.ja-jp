---
title: "WorkflowServiceHost を使用してアイドル動作を構成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# WorkflowServiceHost を使用してアイドル動作を構成する方法
ワークフローは、外部からの働きかけによって再開される必要があるブックマークに遭遇すると、アイドル状態になります。たとえば、<xref:System.ServiceModel.Activities.Receive> アクティビティを使用して配信されるメッセージをワークフローが待機している場合などです。<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> は、サービス インスタンスがアイドル状態になってから、インスタンスが永続化またはアンロードされるまでの時間を指定できる動作です。 これには、これらの時間の範囲を設定する 2 つのプロパティがあります。<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスが永続化されるまでの時間の範囲を指定します。<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスがアンロードされるまでの時間の範囲を指定します。アンロードとは、インスタンスをインスタンス ストアに永続化し、メモリから削除することを意味します。 このトピックでは、<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> を構成ファイルで構成する方法について説明します。  
  
### WorkflowIdleBehavior を構成するには  
  
1.  次の例に示すように、\<`workflowIdle`\> 要素を \<`serviceBehaviors`\> 要素内の \<`behavior`\> 要素に追加します。  
  
    ```xml  
    <behaviors> <serviceBehaviors> <behavior name=""> <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/> </behavior> </serviceBehaviors> </behaviors>  
  
    ```  
  
     `timeToUnload` 属性は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスがアンロードされるまでの時間の範囲を指定します。`timeToPersist` 属性は、ワークフロー サービス インスタンスがアイドル状態になってから、そのワークフロー サービス インスタンスが永続化されるまでの時間の範囲を指定します。`timeToUnload` の既定値は 1 分です。`timeToPersist` の既定値は <xref:System.TimeSpan.MaxValue> です。 インスタンスをメモリ内でアイドル状態を保ちながら信頼性を保持する場合、`timeToPersist` \< `timeToUnload` となるように値を設定します。 アイドル状態のインスタンスがアンロードされないようにするには、`timeToUnload` を <xref:System.TimeSpan.MaxValue> に設定します。<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)」を参照してください  
  
    > [!NOTE]
    >  前の構成サンプルでは、簡略化された構成を使用しています。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)。  
  
### コードのアイドル動作を変更するには  
  
-   次の例では、プログラムによって永続化とアンロードを行う前に待機する時間を変更します。  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## 参照  
 [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)   
 [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)   
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
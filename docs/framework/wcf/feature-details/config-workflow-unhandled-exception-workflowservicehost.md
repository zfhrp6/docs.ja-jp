---
title: "ワークフロー サービスの未処理の例外動作を構成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# ワークフロー サービスの未処理の例外動作を構成する方法
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー内で未処理の例外が発生した場合のアクションを指定できるようにする動作です。このトピックでは、この動作を構成ファイルで構成する方法を示します。  
  
### WorkflowUnhandledExceptionBehavior を構成するには  
  
1.  次の例に示すように、\<`workflowUnhandledException`\> 要素を \<`behavior`\> 要素の \<`serviceBehaviors`\> 要素内に追加し、`action` 属性を使用して、未処理の例外が発生した場合のアクションを指定します。  
  
    ```  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    ```  
  
    > [!NOTE]
    >  前の構成サンプルでは、簡略化された構成を使用しています。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     この動作は、次の例に示すように、コードで構成できます。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
  
    ```  
  
     \<`workflowUnhandledException`\> 要素の `action` 属性は、次のいずれかの値に設定できます。  
  
     **abandon**  
     永続化されているインスタンス状態を変更することなく、メモリ内のインスタンスを中止します \(つまり、最後の永続性ポイントにロールバックします\)。  
  
     **abandonAndSuspend**  
     メモリ内のインスタンスを中止し、永続化されているインスタンスを中断状態に更新します。  
  
     **cancel**  
     インスタンスのキャンセル ハンドラーを呼び出してから、メモリ内のインスタンスを完了状態にします。これにより、そのインスタンスがインスタンス ストアから削除される場合もあります。  
  
     **terminate**  
     メモリ内のインスタンスを完了状態にし、そのインスタンスをインスタンス ストアから削除します。  
  
     <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)」を参照してください。  
  
## 参照  
 [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)   
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)
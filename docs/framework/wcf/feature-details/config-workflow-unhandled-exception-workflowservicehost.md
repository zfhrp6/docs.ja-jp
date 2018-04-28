---
title: ワークフロー サービスの未処理の例外動作を構成する方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5cf06b90169e3915af48396aa2f6c426f1329a95
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>ワークフロー サービスの未処理の例外動作を構成する方法
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> は、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー内で未処理の例外が発生した場合のアクションを指定できるようにする動作です。 このトピックでは、この動作を構成ファイルで構成する方法を示します。  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>WorkflowUnhandledExceptionBehavior を構成するには  
  
1.  追加、<`workflowUnhandledException`> 内の要素、<`behavior`> 内の要素、<`serviceBehaviors`> 要素を使用して、`action`属性を次の例で示すように、ハンドルされない例外が発生したときに実行するアクションを指定します。  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  前の構成サンプルでは、簡略化された構成を使用しています。 詳細については、次を参照してください。[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)です。  
  
     この動作は、次の例に示すように、コードで構成できます。  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action`の属性、<`workflowUnhandledException`> 要素は、次の値のいずれかに設定することができます。  
  
     **破棄します。**  
     永続化されているインスタンス状態を変更することなく、メモリ内のインスタンスを中止します (つまり、最後の永続性ポイントにロールバックします)。  
  
     **abandonAndSuspend**  
     メモリ内のインスタンスを中止し、永続化されているインスタンスを中断状態に更新します。  
  
     **キャンセル**  
     インスタンスのキャンセル ハンドラーを呼び出してから、メモリ内のインスタンスを完了状態にします。これにより、そのインスタンスがインスタンス ストアから削除される場合もあります。  
  
     **terminate**  
     メモリ内のインスタンスを完了状態にし、そのインスタンスをインスタンス ストアから削除します。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>、を参照してください[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)

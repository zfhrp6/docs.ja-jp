---
title: "WorkflowServiceHost を使用して永続性を構成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# WorkflowServiceHost を使用して永続性を構成する方法
このトピックでは、構成ファイルを使用して、<xref:System.ServiceHost.Activities.WorkflowServiceHost> でホストされるワークフローに対して永続化を有効にするように、SQL Workflow Instance Store の機能を構成する方法について説明します。  SQL Workflow Instance Store 機能を使用する前に、ワークフロー インスタンスの永続化に使用する SQL データベースを作成する必要があります。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ワークフローとワークフロー サービスの SQL 永続性を有効にする方法](../../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### 構成において SQL Workflow Instance Store を構成するには  
  
1.  SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、XML 構成で設定を変更するために使用できるサービス動作です。  次の構成例では、構成ファイルで \<`sqlWorkflowInstanceStore`\> という動作要素を使用して SQL Workflow Instance Store を構成する方法について説明します。  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
  
    ```  
  
     SQL Workflow Instance Store を構成する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフローとワークフロー サービスの SQL 永続性を有効にする方法](../../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)」を参照してください。  \<`sqlWorkflowInstanceStore`\> 動作要素の個別の設定の[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 「[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)」を参照してください。  Windows Server AppFabric は自己の永続ストアを提供します。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 「[Windows Server AppFabric の永続化](http://go.microsoft.com/fwlink/?LinkId=193121)」。  
  
    > [!NOTE]
    >  前の構成例では、簡略化された構成を使用しています。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### コードで SQL Workflow Instance Store を構成するには  
  
1.  SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、コードで設定を変更できるサービス動作です。  次の例では、コードで <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> という動作要素を使用して SQL Workflow Instance Store を構成する方法を示します。  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     SQL Workflow Instance Store を構成する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフローとワークフロー サービスの SQL 永続性を有効にする方法](../../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)」を参照してください。  <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 動作要素の個別の設定[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)」を参照してください。  Windows Server AppFabric は自己の永続ストアを提供します。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 「[Windows Server AppFabric の永続化](http://go.microsoft.com/fwlink/?LinkId=193121)」。  
  
    > [!NOTE]
    >  前の構成例では、簡略化された構成を使用しています。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     プログラムによって永続化を構成する方法の例については、「[ワークフローとワークフロー サービスの永続化を有効にする方法](../../../../docs/framework/windows-workflow-foundation//how-to-enable-persistence-for-workflows-and-workflow-services.md)」を参照してください。  
  
## 参照  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)   
 [Windows Server AppFabric の永続化](http://go.microsoft.com/fwlink/?LinkId=193121)
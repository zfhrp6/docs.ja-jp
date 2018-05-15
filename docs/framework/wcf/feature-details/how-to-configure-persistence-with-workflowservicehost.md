---
title: WorkflowServiceHost を使用して永続性を構成する方法
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 9035ded1ca533d9b2107d90f605e15c9ce915965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="efd45-102">WorkflowServiceHost を使用して永続性を構成する方法</span><span class="sxs-lookup"><span data-stu-id="efd45-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="efd45-103">このトピックでは、構成ファイルを使用して、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフローに対して永続化を有効にするように、SQL Workflow Instance Store の機能を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="efd45-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="efd45-104">SQL Workflow Instance Store 機能を使用する前に、ワークフロー インスタンスの永続化に使用する SQL データベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efd45-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="efd45-105">詳細については、次を参照してください。[する方法: SQL 永続化ワークフローとワークフロー サービスを有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="efd45-106">構成において SQL Workflow Instance Store を構成するには</span><span class="sxs-lookup"><span data-stu-id="efd45-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="efd45-107">SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、XML 構成で設定を変更するために使用できるサービス動作です。</span><span class="sxs-lookup"><span data-stu-id="efd45-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="efd45-108">次の構成例では、構成ファイルで <`sqlWorkflowInstanceStore`> という動作要素を使用して SQL Workflow Instance Store を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="efd45-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="efd45-109">SQL workflow instance store を構成する方法の詳細については、次を参照してください。[する方法: SQL 永続化ワークフローとワークフロー サービスを有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="efd45-110">個々 の設定の詳細については、<`sqlWorkflowInstanceStore`> 動作要素を参照してください[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="efd45-111">Windows Server AppFabric は自己の永続ストアを提供します。</span><span class="sxs-lookup"><span data-stu-id="efd45-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="efd45-112">詳細については、次を参照してください。 [Windows Server App Fabric の永続化](http://go.microsoft.com/fwlink/?LinkId=193121)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-112">For more information, see [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="efd45-113">前の構成例では、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="efd45-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="efd45-114">詳細については、次を参照してください[簡略化された構成。](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="efd45-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="efd45-115">コードで SQL Workflow Instance Store を構成するには</span><span class="sxs-lookup"><span data-stu-id="efd45-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="efd45-116">SQL Workflow Instance Store のプロパティは、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> を使用して構成できます。これは、コードで設定を変更できるサービス動作です。</span><span class="sxs-lookup"><span data-stu-id="efd45-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="efd45-117">次の例では、コードで <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> という動作要素を使用して SQL Workflow Instance Store を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="efd45-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="efd45-118">SQL workflow instance store を構成する方法の詳細については、次を参照してください。[する方法: SQL 永続化ワークフローとワークフロー サービスを有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="efd45-119">個々 の設定の詳細については、<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>動作要素を参照してください[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="efd45-120">Windows Server AppFabric は自己の永続ストアを提供します。</span><span class="sxs-lookup"><span data-stu-id="efd45-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="efd45-121">詳細については、次を参照してください。 [Windows Server App Fabric の永続化](http://go.microsoft.com/fwlink/?LinkId=193121)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-121">For more information, see [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="efd45-122">前の構成例では、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="efd45-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="efd45-123">詳細については、次を参照してください[簡略化された構成。](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="efd45-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="efd45-124">永続性をプログラムで構成する方法の例については、次を参照してください。[する方法: ワークフローとワークフロー サービスの永続化を有効にする](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="efd45-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd45-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="efd45-125">See Also</span></span>  
 [<span data-ttu-id="efd45-126">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="efd45-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="efd45-127">ワークフローの永続性</span><span class="sxs-lookup"><span data-stu-id="efd45-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="efd45-128">Windows Server App Fabric の永続化</span><span class="sxs-lookup"><span data-stu-id="efd45-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)

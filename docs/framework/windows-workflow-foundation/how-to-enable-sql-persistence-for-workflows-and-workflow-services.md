---
title: ワークフローとワークフロー サービスの SQL 永続性を有効にする方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e5872be7e8b686a744832bf63a98e97a99cf9b6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="ffe63-102">ワークフローとワークフロー サービスの SQL 永続性を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="ffe63-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="ffe63-103">このトピックでは、ワークフローとワークフロー サービスの永続性をプログラムと構成ファイルの両方から使用して有効にできるように、SQL Workflow Instance Store の機能を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>  
  
 <span data-ttu-id="ffe63-104">Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="ffe63-105">詳細については、次を参照してください[App Fabric の永続化構成。](http://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="ffe63-105">For more information, see [App Fabric Persistence Configuration](http://go.microsoft.com/fwlink/?LinkId=201204)</span></span>  
  
 <span data-ttu-id="ffe63-106">SQL Workflow Instance Store 機能を使用する前に、この機能においてワークフロー インスタンスの永続化に使用するデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="ffe63-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] セットアップ プログラムによって、SQL Workflow Instance Store 機能に関連する SQL スクリプト ファイルが %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="ffe63-108">これらのスクリプト ファイルは、SQL Workflow Instance Store がワークフロー インスタンスの永続化に使用する SQL Server 2005 または SQL Server 2008 のデータベースに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="ffe63-109">最初に SqlWorkflowInstanceStoreSchema.sql ファイルを実行してから、SqlWorkflowInstanceStoreLogic.sql ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffe63-110">永続性データベースをクリーンアップして新しいデータベースにするには、%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN にあるスクリプトを次の順序で実行します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>  
>   
>  1.  <span data-ttu-id="ffe63-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="ffe63-111">SqlWorkflowInstanceStoreSchema.sql</span></span>  
> 2.  <span data-ttu-id="ffe63-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="ffe63-112">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffe63-113">永続性データベースを作成しない場合、ホストがワークフローを永続化しようとしたときに、SQL Workflow Instance Store 機能によって次のような例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>  
>   
>  <span data-ttu-id="ffe63-114">System.Data.SqlClient.SqlException: ストアド プロシージャ 'System.Activities.DurableInstancing.CreateLockOwner' が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ffe63-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>  
  
 <span data-ttu-id="ffe63-115">以下のセクションでは、SQL Workflow Instance Store を使用してワークフローとワークフロー サービスの永続性を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="ffe63-116">SQL Workflow Instance Store のプロパティの詳細については、次を参照してください。 [SQL Workflow Instance Store のプロパティ](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffe63-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="ffe63-117">WorkflowApplication を使用する自己ホスト型ワークフローの永続化の有効化</span><span class="sxs-lookup"><span data-stu-id="ffe63-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>  
 <span data-ttu-id="ffe63-118"><xref:System.Activities.WorkflowApplication> オブジェクト モデルを使用して、プログラムから <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用する自己ホスト型ワークフローの永続化を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="ffe63-119">これを行う手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-119">The following procedure contains steps to do this.</span></span>  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="ffe63-120">自己ホスト型ワークフローの永続化を有効にするには</span><span class="sxs-lookup"><span data-stu-id="ffe63-120">To enable persistence for self-hosted workflows</span></span>  
  
1.  <span data-ttu-id="ffe63-121">System.Activites.DurableInstancing.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-121">Add a reference to System.Activites.DurableInstancing.dll.</span></span>  
  
2.  <span data-ttu-id="ffe63-122">ソース ファイルの先頭にある既存の "using" ステートメントの後に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  <span data-ttu-id="ffe63-123">次のコード例に示すように、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構築して <xref:System.Activities.WorkflowApplication.InstanceStore%2A> の <xref:System.Activities.WorkflowApplication> に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ffe63-124">使用している SQL Server のエディションによって、接続文字列のサーバー名は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ffe63-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
4.  <span data-ttu-id="ffe63-125"><xref:System.Activities.WorkflowApplication.Persist%2A> オブジェクトの <xref:System.Activities.WorkflowApplication> メソッドを呼び出してワークフローを永続化するか、<xref:System.Activities.WorkflowApplication.Unload%2A> メソッドを呼び出してワークフローを永続化およびアンロードします。</span><span class="sxs-lookup"><span data-stu-id="ffe63-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="ffe63-126">また、<xref:System.Activities.WorkflowApplication.PersistableIdle%2A> オブジェクトによって発生した <xref:System.Activities.WorkflowApplication> イベントを処理して、<xref:System.Activities.PersistableIdleAction.Persist> の適切なメンバー (<xref:System.Activities.PersistableIdleAction.Unload> または <xref:System.Activities.PersistableIdleAction>) を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="ffe63-127">参照してください、[ワークフロー アプリケーションの永続化](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md)でサンプル[永続化](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)を使用してワークフローの永続化を有効にする例については、 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>、および[する方法: を作成して、時間の長いの実行ワークフローを実行して](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)の手順、[チュートリアル入門](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)の手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-127">See the [Persisting a Workflow Application](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflows using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, and the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="ffe63-128">WorkflowServiceHost を使用する自己ホスト型ワークフロー サービスの永続化の有効化</span><span class="sxs-lookup"><span data-stu-id="ffe63-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>  
 <span data-ttu-id="ffe63-129"><xref:System.ServiceModel.WorkflowServiceHost> クラスまたは <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> クラスを使用して、プログラムから <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> を使用する自己ホスト型ワークフロー サービスの永続化を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="ffe63-130">SqlWorkflowInstanceStoreBehavior クラスの使用</span><span class="sxs-lookup"><span data-stu-id="ffe63-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>  
 <span data-ttu-id="ffe63-131"><xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> クラスを使用して、自己ホスト型ワークフロー サービスの永続化を有効にする手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="ffe63-132">SqlWorkflowInstanceStoreBehavior を使用して永続化を有効にするには</span><span class="sxs-lookup"><span data-stu-id="ffe63-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>  
  
1.  <span data-ttu-id="ffe63-133">System.ServiceModel.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-133">Add a reference to the System.ServiceModel.dll.</span></span>  
  
2.  <span data-ttu-id="ffe63-134">ソース ファイルの先頭にある既存の "using" ステートメントの後に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  <span data-ttu-id="ffe63-135">`WorkflowServiceHost` のインスタンスを作成し、ワークフロー サービスのエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  <span data-ttu-id="ffe63-136">`SqlWorkflowInstanceStoreBehavior` オブジェクトを作成して、動作オブジェクトのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  <span data-ttu-id="ffe63-137">ワークフロー サービス ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-137">Open the workflow service host.</span></span>  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffe63-138">参照してください、[組み込み設定](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md)でサンプル[永続化](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)を使用してワークフロー サービスの永続化を有効にする例については、`SqlWorkflowInstanceStoreBehavior`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ffe63-138">See the [Built-in Configuration](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflow services using the `SqlWorkflowInstanceStoreBehavior` class.</span></span>  
  
### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="ffe63-139">DurableInstancingOptions プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="ffe63-139">Using the DurableInstancingOptions Property</span></span>  
 <span data-ttu-id="ffe63-140">`SqlWorkflowInstanceStoreBehavior` が適用される場合、`DurableInstancingOptions.InstanceStore` の `WorkflowServiceHost` は構成値を使用して作成された `SqlWorkflowInstanceStore` オブジェクトに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="ffe63-141">同じ内容をプログラムから実行するには、次のコード例に示すように、<xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> クラスを使用せずに `WorkflowServiceHost` の `SqlWorkflowInstanceStoreBehavior` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="ffe63-142">WorkflowServiceHost を使用する WAS でホストされるワークフロー サービスの構成ファイルを使用した永続化の有効化</span><span class="sxs-lookup"><span data-stu-id="ffe63-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>  
 <span data-ttu-id="ffe63-143">構成ファイルを使用することで、自己ホスト型または Windows プロセス アクティブ化サービス (WAS) でホストされるワークフロー サービスの永続化を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="ffe63-144">WAS でホストされるワークフロー サービスは、自己ホスト型ワークフローのように WorkflowServiceHost を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>  
  
 <span data-ttu-id="ffe63-145">`SqlWorkflowInstanceStoreBehavior`、サービスの動作を変更できるようにする、 [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)プロパティ XML 構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="ffe63-146">WAS でホストされるワークフロー サービスの場合は、Web.config ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="ffe63-147">次の構成例では、構成ファイルで `sqlWorkflowInstanceStore` という動作要素を使用して SQL Workflow Instance Store を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>  
  
```xml  
<serviceBehaviors>  
    <behavior name="">  
        <sqlWorkflowInstanceStore   
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                    instanceEncodingOption="GZip | None"  
                    instanceCompletionAction="DeleteAll | DeleteNothing"  
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"  
                    hostLockRenewalPeriod="00:00:30"   
                    runnableInstancesDetectionPeriod="00:00:05">  
  
        <sqlWorkflowInstanceStore/>  
    </behavior>  
</serviceBehaviors>  
```  
  
 <span data-ttu-id="ffe63-148">`connectionString` または `connectionStringName` プロパティの値が設定されていない場合、SQL Workflow Instance Store は既定の名前付き接続文字列 `DefaultSqlWorkflowInstanceStoreConnectionString` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>  
  
 <span data-ttu-id="ffe63-149">`SqlWorkflowInstanceStoreBehavior` が適用される場合、`DurableInstancingOptions.InstanceStore` の `WorkflowServiceHost` は構成値を使用して作成された `SqlWorkflowInstanceStore` オブジェクトに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="ffe63-150">同じ内容をプログラムから実行するには、サービスの動作要素を使用せずに `SqlWorkflowInstanceStore` を `WorkflowServiceHost` と一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="ffe63-151">ユーザー名やパスワードなどの機密情報は、Web.config ファイルに保存しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ffe63-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="ffe63-152">Web.config ファイルに機密情報を保存する場合は、ファイル システムのアクセス制御リスト (ACL) を使用して、Web.config ファイルへのアクセスをセキュリティで保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffe63-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="ffe63-153">さらに、保護することできますも、構成ファイル内の構成値で説明したよう[暗号化の構成情報を使用して保護された構成](http://go.microsoft.com/fwlink/?LinkId=178419)です。</span><span class="sxs-lookup"><span data-stu-id="ffe63-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](http://go.microsoft.com/fwlink/?LinkId=178419).</span></span>  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="ffe63-154">SQL Workflow Instance Store 機能に関連する Machine.config の要素</span><span class="sxs-lookup"><span data-stu-id="ffe63-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>  
 <span data-ttu-id="ffe63-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] のインストールでは、SQL Workflow Instance Store 機能に関連する次の要素が Machine.config ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ffe63-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>  
  
-   <span data-ttu-id="ffe63-156">構成ファイルで <`sqlWorkflowInstanceStore`> サービスの動作要素を使用してサービスの永続化を設定できるように、Machine.config ファイルに次の動作拡張要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffe63-156">Adds the following behavior extension element to the Machine.config file so that you can use the <`sqlWorkflowInstanceStore`> service behavior element in the configuration file to configure persistence for your services.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <extensions>  
                <behaviorExtensions>  
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
                </behaviorExtensions>  
            </extensions>  
        <system.serviceModel>  
    <configuration>  
    ```

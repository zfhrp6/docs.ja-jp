---
title: "中断されたインスタンスの管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02c3d6b3a522dd4337dcdf22f884f63cdddd4aa4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="suspended-instance-management"></a><span data-ttu-id="e8938-102">中断されたインスタンスの管理</span><span class="sxs-lookup"><span data-stu-id="e8938-102">Suspended Instance Management</span></span>
<span data-ttu-id="e8938-103">このサンプルでは、中断されているワークフロー インスタンスを管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e8938-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="e8938-104"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> の既定のアクションは `AbandonAndSuspend` です。</span><span class="sxs-lookup"><span data-stu-id="e8938-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="e8938-105">つまり、既定では、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー インスタンスからスローされた未処理の例外により、インスタンスがメモリから破棄され、インスタンスの永続バージョンが中断状態としてマークされることになります。</span><span class="sxs-lookup"><span data-stu-id="e8938-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="e8938-106">中断されたワークフロー インスタンスは、中断が解除されるまで実行できません。</span><span class="sxs-lookup"><span data-stu-id="e8938-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>  
  
 <span data-ttu-id="e8938-107">このサンプルでは、コマンド ライン ユーティリティを実装して、中断されたインスタンスについてクエリを実行する方法、およびユーザーがインスタンスを再開または終了できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e8938-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="e8938-108">このサンプルでは、ワークフロー サービスから例外が意図的にスローされ、中断状態になります。</span><span class="sxs-lookup"><span data-stu-id="e8938-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="e8938-109">その後、コマンド ライン ユーティリティを使用してインスタンスについてクエリを実行し、さらに、インスタンスを再開または終了できます。</span><span class="sxs-lookup"><span data-stu-id="e8938-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e8938-110">使用例</span><span class="sxs-lookup"><span data-stu-id="e8938-110">Demonstrates</span></span>  
 <span data-ttu-id="e8938-111"><xref:System.ServiceModel.WorkflowServiceHost> の <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> および <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> を使用する [!INCLUDE[wf](../../../../includes/wf-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e8938-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e8938-112">説明</span><span class="sxs-lookup"><span data-stu-id="e8938-112">Discussion</span></span>  
 <span data-ttu-id="e8938-113">このサンプルに実装されているコマンド ライン ユーティリティは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に用意されている SQL インスタンス ストアの実装に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="e8938-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="e8938-114">インスタンス ストアのカスタム実装がある場合は、サンプルの `WorkflowInstanceCommand` の実装を、使用しているインスタンス ストアに固有の実装に置き換えることで、このユーティリティを調整できます。</span><span class="sxs-lookup"><span data-stu-id="e8938-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>  
  
 <span data-ttu-id="e8938-115">用意されている実装では、SQL インスタンス ストアに対して SQL コマンドを直接実行して、中断されたインスタンスのリストを取得し、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> に追加された <xref:System.ServiceModel.WorkflowServiceHost> を使用して、インスタンスを再開または終了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e8938-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8938-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e8938-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e8938-117">このサンプルでは、次の Windows コンポーネントが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8938-117">This sample requires that the following Windows components are enabled:</span></span>  
  
    1.  <span data-ttu-id="e8938-118">Microsoft メッセージ キュー (MSMQ) サーバー</span><span class="sxs-lookup"><span data-stu-id="e8938-118">Microsoft Message Queues (MSMQ) Server</span></span>  
  
    2.  <span data-ttu-id="e8938-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="e8938-119">SQL Server Express</span></span>  
  
2.  <span data-ttu-id="e8938-120">SQL Server データベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="e8938-120">Set up the SQL Server database.</span></span>  
  
    1.  <span data-ttu-id="e8938-121">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]コマンド プロンプトで、次の処理、SuspendedInstanceManagement サンプル ディレクトリから"setup.cmd"を実行します。</span><span class="sxs-lookup"><span data-stu-id="e8938-121">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>  
  
        1.  <span data-ttu-id="e8938-122">SQL Server Express を使用して永続性データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8938-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="e8938-123">永続性データベースが既に存在する場合、データベースは削除され、再作成されます。</span><span class="sxs-lookup"><span data-stu-id="e8938-123">If the persistence database already exists, then it is dropped and re-created</span></span>  
  
        2.  <span data-ttu-id="e8938-124">永続化のためにデータベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="e8938-124">Sets up the database for persistence.</span></span>  
  
        3.  <span data-ttu-id="e8938-125">IIS APPPOOL\DefaultAppPool および NT AUTHORITY\Network Service を、永続化のためにデータベースを設定するときに定義された InstanceStoreUsers ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="e8938-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>  
  
3.  <span data-ttu-id="e8938-126">サービス キューを設定します。</span><span class="sxs-lookup"><span data-stu-id="e8938-126">Set up the service queue.</span></span>  
  
    1.  <span data-ttu-id="e8938-127">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックし、 **SampleWorkflowApp**プロジェクトし、クリックして**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-127">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>  
  
    2.  <span data-ttu-id="e8938-128">コンパイルしてキーを押して SampleWorkflowApp を実行する**f5 キーを押して**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="e8938-129">これにより、必要なキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e8938-129">This will create the required queue.</span></span>  
  
    3.  <span data-ttu-id="e8938-130">キーを押して**Enter** SampleWorkflowApp を停止します。</span><span class="sxs-lookup"><span data-stu-id="e8938-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>  
  
    4.  <span data-ttu-id="e8938-131">コマンド プロンプトから Compmgmt.msc を実行して、[コンピューターの管理] コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="e8938-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>  
  
    5.  <span data-ttu-id="e8938-132">展開**サービスとアプリケーション**、**メッセージ キュー**、**専用キュー**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    6.  <span data-ttu-id="e8938-133">右クリックして、 **ReceiveTx**キューし、選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>  
  
    7.  <span data-ttu-id="e8938-134">選択、**セキュリティ**でき、タブ**Everyone**へのアクセス許可を持つ**メッセージの受信**、**メッセージのピーク**、および**メッセージを送信**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>  
  
4.  <span data-ttu-id="e8938-135">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="e8938-135">Now, run the sample.</span></span>  
  
    1.  <span data-ttu-id="e8938-136">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]、デバッグなしでキーを押して、SampleWorkflowApp プロジェクトを再度実行**ctrl キーを押しながら f5 キーを押して**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-136">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="e8938-137">2 つのエンドポイント アドレスがコンソール ウィンドウに出力されます。1 つはアプリケーション エンドポイントのアドレスで、もう 1 つは <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="e8938-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="e8938-138">その後、ワークフロー インスタンスが作成され、そのインスタンスの追跡レコードがコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8938-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="e8938-139">ワークフロー インスタンスから例外がスローされ、インスタンスは中断されて中止されます。</span><span class="sxs-lookup"><span data-stu-id="e8938-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>  
  
    2.  <span data-ttu-id="e8938-140">次に、コマンド ライン ユーティリティを使用して、これらのインスタンスに対してさらに操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e8938-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="e8938-141">コマンド ライン引数の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e8938-141">The syntax for command line arguments is as follows::</span></span>  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         <span data-ttu-id="e8938-142">サポートされるコマンドは、`Query`、`Resume`、および `Terminate` です。</span><span class="sxs-lookup"><span data-stu-id="e8938-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="e8938-143">InstanceId スイッチを指定する必要があるのは、`Resume` 操作および `Terminate` 操作だけです。</span><span class="sxs-lookup"><span data-stu-id="e8938-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="e8938-144">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="e8938-144">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="e8938-145">`vs2010` コマンド プロンプトから Compmgmt.msc を実行して、[コンピューターの管理] コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="e8938-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>  
  
2.  <span data-ttu-id="e8938-146">展開**サービスとアプリケーション**、**メッセージ キュー**、**専用キュー**です。</span><span class="sxs-lookup"><span data-stu-id="e8938-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="e8938-147">削除、 **ReceiveTx**キュー。</span><span class="sxs-lookup"><span data-stu-id="e8938-147">Delete the **ReceiveTx** queue.</span></span>  
  
4.  <span data-ttu-id="e8938-148">永続性データベースを削除するには、cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="e8938-148">To remove the persistence database, run cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8938-149">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e8938-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8938-150">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e8938-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8938-151">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="e8938-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8938-152">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e8938-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`

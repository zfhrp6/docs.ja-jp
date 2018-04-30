---
title: 組み込みの構成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c414f34da0cd4bbf484c0a439f8832f02a5ae58
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="built-in-configuration"></a><span data-ttu-id="7031e-102">組み込みの構成</span><span class="sxs-lookup"><span data-stu-id="7031e-102">Built-in Configuration</span></span>
<span data-ttu-id="7031e-103">このサンプルでは、SQL Workflow Instance Store の使用法と構成を示します。</span><span class="sxs-lookup"><span data-stu-id="7031e-103">This sample demonstrates the use and configuration of the SQL workflow instance store.</span></span> <span data-ttu-id="7031e-104">SQL Workflow Instance Store は、SQL ベースのインスタンス ストアの実装です。</span><span class="sxs-lookup"><span data-stu-id="7031e-104">The SQL workflow instance store is a SQL-based implementation of an instance store.</span></span> <span data-ttu-id="7031e-105">SQL Workflow Instance Store を使用すると、インスタンスの状態を SQL Server データベースや SQL Server Express データベースに保存したり読み込んだりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7031e-105">It allows an instance to save and load its state to and from a SQL Server or SQL Server Express database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7031e-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7031e-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7031e-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7031e-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7031e-108">このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7031e-108">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7031e-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="7031e-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="7031e-110">Sample Details</span></span>  
 <span data-ttu-id="7031e-111">このサンプルは、カウント サービスを実装するワークフローで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7031e-111">This sample consists of a workflow that implements a counting service.</span></span> <span data-ttu-id="7031e-112">サービスの start メソッドが呼び出されると、0 から 59 までのカウントが行われます。</span><span class="sxs-lookup"><span data-stu-id="7031e-112">Once the service's start method is invoked, the service counts from 0 to 59.</span></span> <span data-ttu-id="7031e-113">カウンターは 2 秒ごとにインクリメントされ、</span><span class="sxs-lookup"><span data-stu-id="7031e-113">The counter is incremented once every 2 seconds.</span></span> <span data-ttu-id="7031e-114">カウントのたびにワークフローが永続化されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-114">After each count, the workflow persists.</span></span>  
  
 <span data-ttu-id="7031e-115">このカウント ワークフローは、ワークフロー サービス ホストによってホストされる自己ホスト型サービスです。</span><span class="sxs-lookup"><span data-stu-id="7031e-115">The counting workflow is self-hosted by a workflow service host.</span></span> <span data-ttu-id="7031e-116">プログラムの `Main` メソッドは、カウント ワークフローをホストするワークフロー サービス ホストのインスタンスを作成し、</span><span class="sxs-lookup"><span data-stu-id="7031e-116">The program's `Main` method creates an instance of the workflow service host that hosts the counting workflow.</span></span> <span data-ttu-id="7031e-117">カウント ワークフローにアクセスできるエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="7031e-117">It defines the endpoints under which the counting workflow can be reached.</span></span> <span data-ttu-id="7031e-118">その後、SQL Workflow Instance Store を構成するために使用される SQL Workflow Instance Store の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="7031e-118">After that, it defines a SQL workflow instance store behavior, which is used to configure the SQL workflow instance store.</span></span> <span data-ttu-id="7031e-119">続いて、カウント ワークフローの start メソッドを呼び出すクライアントがプログラムで作成されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-119">Next, the program creates a client that calls the start method of the counting workflow.</span></span>  
  
 <span data-ttu-id="7031e-120">プログラムを開始すると、カウンターが自動的にカウントを開始します。</span><span class="sxs-lookup"><span data-stu-id="7031e-120">Once the program is started, the counter automatically starts counting.</span></span> <span data-ttu-id="7031e-121">インスタンスを読み込んで SQL Workflow Instance Store を構成するのに数秒かかる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7031e-121">Note that it might take a few seconds to load the instance and configure the SQL workflow instance store.</span></span> <span data-ttu-id="7031e-122">ワークフロー インスタンス ストアの詳細については、次を参照してください。 [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)です。</span><span class="sxs-lookup"><span data-stu-id="7031e-122">For more information about the workflow instance store, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span>  
  
 <span data-ttu-id="7031e-123">このサンプルは、2 つの部分で構成されています。</span><span class="sxs-lookup"><span data-stu-id="7031e-123">The sample consists of two parts:</span></span>  
  
1.  <span data-ttu-id="7031e-124">InstanceStore1 は、C# コードを使用して <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構成する方法を示しています (Program.cs を参照)。</span><span class="sxs-lookup"><span data-stu-id="7031e-124">InstanceStore1 shows how <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is configured using C# code (see Program.cs).</span></span>  
  
2.  <span data-ttu-id="7031e-125">InstanceStore2 は、XML を使用して <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構成する方法を示しています (App.config を参照)。</span><span class="sxs-lookup"><span data-stu-id="7031e-125">InstanceStore2 shows how <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> is configured using XML (see App.config).</span></span>  
  
 <span data-ttu-id="7031e-126">SQL Workflow Instance Store の動作を構成するには次の設定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7031e-126">The following settings are available to configure the SQL Workflow Instance Store behavior:</span></span>  
  
-   <span data-ttu-id="7031e-127">`HostLockRenewalPeriod` を設定します。</span><span class="sxs-lookup"><span data-stu-id="7031e-127">Set the `HostLockRenewalPeriod`.</span></span> <span data-ttu-id="7031e-128">この時間は、ホストで実行されているインスタンスの所有権ロックをホストが更新する間隔を定義します。</span><span class="sxs-lookup"><span data-stu-id="7031e-128">This time defines the interval with which the host renews the ownership lock of the instances it runs.</span></span> <span data-ttu-id="7031e-129">ロックの情報はインスタンス ストアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-129">The lock information is stored in the Instance Store.</span></span> <span data-ttu-id="7031e-130">`HostLockRenewalPeriod` で定義されている間隔が 2 回経過しても所有権が更新されないと、インスタンスが破棄されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="7031e-130">If the ownership is not renewed for two of the intervals defined in `HostLockRenewalPeriod`, the instance is considered abandoned.</span></span> <span data-ttu-id="7031e-131">別の <xref:System.ServiceModel.Activities.WorkflowServiceHost> が同じワークフローを実行し、同じインスタンス ストア (同じコンピューターにあっても別のコンピューターにあってもかまいません) に接続している場合は、その WorkflowServiceHost によってインスタンスが回復されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-131">If another <xref:System.ServiceModel.Activities.WorkflowServiceHost> is running the same workflow and connected to the same instance store (either on the same computer or a different computer), it recovers that instance.</span></span> <span data-ttu-id="7031e-132">(インスタンスの回復はこのサンプルの範囲外です)。</span><span class="sxs-lookup"><span data-stu-id="7031e-132">(Instance Recovery is out of scope for this sample.)</span></span>  
  
-   <span data-ttu-id="7031e-133">`RunnableInstancesDetectionPeriod` を設定します。</span><span class="sxs-lookup"><span data-stu-id="7031e-133">Set the `RunnableInstancesDetectionPeriod`.</span></span> <span data-ttu-id="7031e-134">この期間は、実行可能になったインスタンスをホストがポーリングする間隔を定義します。</span><span class="sxs-lookup"><span data-stu-id="7031e-134">This period defines the interval in which the host polls for instances that have become runnable.</span></span> <span data-ttu-id="7031e-135">インスタンスが実行可能になるのは次の場合です。</span><span class="sxs-lookup"><span data-stu-id="7031e-135">Instances may become runnable if any of the following events occur:</span></span>  
  
    -   <span data-ttu-id="7031e-136">永続的なタイマー (<xref:System.Activities.Statements.Delay>) が切れた場合。</span><span class="sxs-lookup"><span data-stu-id="7031e-136">A Durable Timer (<xref:System.Activities.Statements.Delay>) expires.</span></span>  
  
    -   <span data-ttu-id="7031e-137">別のホストで `HostLockRenewal` のハートビートが (コンピューターがクラッシュしたなどの理由で) 失敗してインスタンスが回復された場合。</span><span class="sxs-lookup"><span data-stu-id="7031e-137">Another host misses its `HostLockRenewal` heartbeat (for example, due to a computer crash) and the instance is recovered.</span></span>  
  
-   <span data-ttu-id="7031e-138">`InstanceCompletionAction` を設定します。</span><span class="sxs-lookup"><span data-stu-id="7031e-138">Set the `InstanceCompletionAction`.</span></span> <span data-ttu-id="7031e-139">このプロパティを `DeleteNothing` に設定すると、完了したインスタンスがインスタンス ストアに保持されます。`DeleteAll` に設定すると、インスタンスが完了時にストアから削除されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-139">This property, if set to `DeleteNothing`, keeps completed instances in the Instance Store; if set to `DeleteAll`, instances are deleted from the store upon completion.</span></span> <span data-ttu-id="7031e-140">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7031e-140">Note that</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7031e-141">カウントが完了する前に Enter キーを押してホストを終了すると、ワークフロー インスタンスが完了しません。</span><span class="sxs-lookup"><span data-stu-id="7031e-141">Terminating the host by pressing ENTER before the counting has completed does not complete the workflow instance.</span></span>  
  
-   <span data-ttu-id="7031e-142">`InstanceLockedExceptionAction` を設定します。</span><span class="sxs-lookup"><span data-stu-id="7031e-142">Set the `InstanceLockedExceptionAction`.</span></span> <span data-ttu-id="7031e-143">この設定は、別のホストによってロックされているインスタンスを読み込もうとした場合の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="7031e-143">This setting defines what a host should do if it wants to load an instance that is locked by another host.</span></span> <span data-ttu-id="7031e-144">次の選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="7031e-144">The following options exist:</span></span>  
  
    -   <span data-ttu-id="7031e-145">`NoRetry`: 読み込みを再試行せずにホストに `InstanceLockedException` を返します。</span><span class="sxs-lookup"><span data-stu-id="7031e-145">If set to `NoRetry`: Do not retry the load and return an `InstanceLockedException` to the host.</span></span>  
  
    -   <span data-ttu-id="7031e-146">`BasicRetry`: インスタンスの読み込みを再試行し続けます。</span><span class="sxs-lookup"><span data-stu-id="7031e-146">If set to `BasicRetry`: Keep retrying to load the instance.</span></span> <span data-ttu-id="7031e-147">再試行のスケジュールは、単純な線形アルゴリズムに従って設定されます (5 秒ごとに再試行するなど)。</span><span class="sxs-lookup"><span data-stu-id="7031e-147">The retries are scheduled according to a simple linear algorithm (for example, retry every 5 seconds).</span></span>  
  
    -   <span data-ttu-id="7031e-148">`AggressiveRetry`: インスタンスの読み込みを再試行し続けます。</span><span class="sxs-lookup"><span data-stu-id="7031e-148">If set to `AggressiveRetry`: Keep retrying to load the instance.</span></span> <span data-ttu-id="7031e-149">再試行のスケジュールは、積極的な指数バックオフ アルゴリズムに従って設定されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-149">The retries are scheduled according to an aggressive exponential back-off algorithm.</span></span>  
  
-   <span data-ttu-id="7031e-150">Encoding オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="7031e-150">Set the Encoding option.</span></span> <span data-ttu-id="7031e-151">この設定は、SQL Workflow Instance Store にインスタンスの状態を格納する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="7031e-151">This setting defines how the instance state is stored in the SQL Workflow Instance Store.</span></span> <span data-ttu-id="7031e-152">次の選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="7031e-152">The following options exist:</span></span>  
  
    -   <span data-ttu-id="7031e-153">GZip 圧縮アルゴリズムを使用してインスタンスの状態を圧縮します。</span><span class="sxs-lookup"><span data-stu-id="7031e-153">The instance state is compressed using the GZip compression algorithm.</span></span>  
  
    -   <span data-ttu-id="7031e-154">インスタンスの状態を圧縮しません。</span><span class="sxs-lookup"><span data-stu-id="7031e-154">The instance state is not compressed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7031e-155">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="7031e-155">To use this sample</span></span>  
  
1.  <span data-ttu-id="7031e-156">アクセス許可がある場合は、管理者として [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="7031e-156">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt as an Administrator if permissions are available.</span></span>  
  
2.  <span data-ttu-id="7031e-157">サンプル ディレクトリ (\WF\Basic\Persistence\BuiltInConfiguration\CS) に移動して、CreateInstanceStore.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="7031e-157">Navigate to the sample directory (\WF\Basic\Persistence\BuiltInConfiguration\CS) and run CreateInstanceStore.cmd.</span></span>  
  
3.  <span data-ttu-id="7031e-158">管理特権がない場合は、SQL Server ログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7031e-158">If Administrator privileges are not available, Create SQL Server login.</span></span> <span data-ttu-id="7031e-159">移動して`Security`、**ログイン**です。</span><span class="sxs-lookup"><span data-stu-id="7031e-159">Go to `Security`, **Logins**.</span></span> <span data-ttu-id="7031e-160">右クリック**ログイン**し、新しいログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="7031e-160">Right-click **Logins** and create a new login.</span></span>  
  
4.  <span data-ttu-id="7031e-161">自分の ACL ユーザーを SQL ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="7031e-161">Add your ACL user to SQL role.</span></span> <span data-ttu-id="7031e-162">開いている**データベース**、 **InstanceStore**、**セキュリティ**です。</span><span class="sxs-lookup"><span data-stu-id="7031e-162">Open **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="7031e-163">右クリック**ユーザー**選択**新規ユーザー**です。</span><span class="sxs-lookup"><span data-stu-id="7031e-163">Right-click **Users** and select **New users**.</span></span> <span data-ttu-id="7031e-164">設定、**ログイン名**前の手順で作成したユーザーにします。</span><span class="sxs-lookup"><span data-stu-id="7031e-164">Set the **Login name** to the user created in the previous step.</span></span> <span data-ttu-id="7031e-165">データベース ロールのメンバーシップにユーザーを追加**System.Activities.DurableInstancing.InstanceStoreUsers** (など)。</span><span class="sxs-lookup"><span data-stu-id="7031e-165">Add the user to the Database role membership **System.Activities.DurableInstancing.InstanceStoreUsers** (and others).</span></span> <span data-ttu-id="7031e-166">ユーザーが既に存在している場合もあります (ユーザー dbo など)。</span><span class="sxs-lookup"><span data-stu-id="7031e-166">Note that the user might exist already (for example, user dbo).</span></span>  
  
5.  <span data-ttu-id="7031e-167">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で InstanceStore.sln ファイルを開き、Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7031e-167">Open the InstanceStore.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="7031e-168">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]は、サンプルの該当する bin \debug ディレクトリ (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug) に移動し、InstanceStore.exe を右クリックして選択**を管理者として実行**.</span><span class="sxs-lookup"><span data-stu-id="7031e-168">In [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the sample’s appropriate bin\debug directory (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), right click InstanceStore.exe and select **Run as administrator**.</span></span> <span data-ttu-id="7031e-169">このサンプルはチャネル リスナーを開くため、管理特権で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7031e-169">This sample must be run with administrative privileges because it opens a channel listener.</span></span>  
  
7.  <span data-ttu-id="7031e-170">ローカルの SQL Server Express 以外のデータベースにインスタンス ストアを作成した場合は、サンプルのデータベース接続文字列 (InstanceStore1 プロジェクトの Program.cs にある `const string ConnectionString` と、InstanceStore2 プロジェクトの App.config にある `connectionString` 属性) を更新してサンプルを再コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7031e-170">If you created the instance store in a database other than a local installation of SQL Server Express you must update the database connection string (`const string ConnectionString` in Program.cs of the InstanceStore1 project, and the `connectionString` attribute in App.config of the InstanceStore2 project) in the sample and recompile the sample.</span></span>  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a><span data-ttu-id="7031e-171">サンプルが正常に実行されていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="7031e-171">To verify the sample is running correctly</span></span>  
  
1.  <span data-ttu-id="7031e-172">サンプルの実行中に、SQL Server Management Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="7031e-172">While the sample is running, start SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="7031e-173">**オブジェクト エクスプ ローラー****データベース**、 **InstanceStore**、**テーブル**、し**System.activities.durableinstancing.instancetable**です。</span><span class="sxs-lookup"><span data-stu-id="7031e-173">In the **Object Explorer**, select **Databases**, **InstanceStore**, **Tables**, and then **System.Activities.DurableInstancing.InstanceTable**.</span></span>  
  
3.  <span data-ttu-id="7031e-174">右クリックして**InstanceTable**選択**上位 1000 行**です。</span><span class="sxs-lookup"><span data-stu-id="7031e-174">Right click **InstanceTable** and select **Select Top 1000 Rows**.</span></span>  
  
4.  <span data-ttu-id="7031e-175">あることと、新しいエントリを確認、**ロックの有効期限**5 秒ごとに変化 (タスク バーのをクリックして**Execute**クエリを更新するボタン)。</span><span class="sxs-lookup"><span data-stu-id="7031e-175">Observe that there is a new entry and that the **Lock Expiration** changes every 5 seconds, (click the taskbar’s **Execute** button to refresh the query).</span></span> <span data-ttu-id="7031e-176">これは、設定の結果、**ホストのロック更新時間**5 にします。</span><span class="sxs-lookup"><span data-stu-id="7031e-176">This is a consequence of setting the **Host Lock Renewal Period** to 5.</span></span>  
  
5.  <span data-ttu-id="7031e-177">カウントの完了後にインスタンス テーブルのエントリが削除されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7031e-177">Observe after the counting completes, that the entry in the instance table is removed.</span></span> <span data-ttu-id="7031e-178">これは、設定の結果、**インスタンス完了アクション**に**DeleteAll**です。</span><span class="sxs-lookup"><span data-stu-id="7031e-178">This is a consequence of setting **Instance Completion Action** to **DeleteAll**.</span></span>  
  
6.  <span data-ttu-id="7031e-179">ワークフロー ホスト アプリケーションが終了されることを確認してから、ENTER キーを押して、 **LockOwnersTable**を削除します。</span><span class="sxs-lookup"><span data-stu-id="7031e-179">Press ENTER to terminate the workflow host application and observe that the **LockOwnersTable** is deleted.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="7031e-180">サンプルをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="7031e-180">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="7031e-181">サンプル ディレクトリ (\WF\Basic\Persistence\BuiltInConfiguration) で RemoveInstanceStore.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="7031e-181">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\BuiltInConfiguration).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7031e-182">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7031e-182">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7031e-183">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7031e-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7031e-184">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7031e-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7031e-185">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7031e-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a><span data-ttu-id="7031e-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="7031e-186">See Also</span></span>  
 [<span data-ttu-id="7031e-187">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="7031e-187">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

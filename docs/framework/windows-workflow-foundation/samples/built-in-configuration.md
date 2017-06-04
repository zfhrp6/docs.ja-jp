---
title: "組み込みの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 組み込みの構成
このサンプルでは、SQL Workflow Instance Store の使用法と構成を示します。SQL Workflow Instance Store は、SQL ベースのインスタンス ストアの実装です。SQL Workflow Instance Store を使用すると、インスタンスの状態を SQL Server データベースや SQL Server Express データベースに保存したり読み込んだりすることができます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## サンプルの詳細  
 このサンプルは、カウント サービスを実装するワークフローで構成されています。サービスの start メソッドが呼び出されると、0 から 59 までのカウントが行われます。カウンターは 2 秒ごとにインクリメントされ、カウントのたびにワークフローが永続化されます。  
  
 このカウント ワークフローは、ワークフロー サービス ホストによってホストされる自己ホスト型サービスです。プログラムの `Main` メソッドは、カウント ワークフローをホストするワークフロー サービス ホストのインスタンスを作成し、カウント ワークフローにアクセスできるエンドポイントを定義します。その後、SQL Workflow Instance Store を構成するために使用される SQL Workflow Instance Store の動作を定義します。続いて、カウント ワークフローの start メソッドを呼び出すクライアントがプログラムで作成されます。  
  
 プログラムを開始すると、カウンターが自動的にカウントを開始します。インスタンスを読み込んで SQL Workflow Instance Store を構成するのに数秒かかる場合もあります。Workflow Instance Store [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)」を参照してください。  
  
 このサンプルは、2 つの部分で構成されています。  
  
1.  InstanceStore1 は、C\# コードを使用して <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構成する方法を示しています \(Program.cs を参照\)。  
  
2.  InstanceStore2 は、XML を使用して <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を構成する方法を示しています \(App.config を参照\)。  
  
 SQL Workflow Instance Store の動作を構成するには次の設定を使用できます。  
  
-   `HostLockRenewalPeriod` を設定します。この時間は、ホストで実行されているインスタンスの所有権ロックをホストが更新する間隔を定義します。ロックの情報はインスタンス ストアに格納されます。`HostLockRenewalPeriod` で定義されている間隔が 2 回経過しても所有権が更新されないと、インスタンスが破棄されたと見なされます。同じワークフローを実行し、同じインスタンス ストア \(同じコンピューターにあっても別のコンピューターにあってもかまいません\) に接続している別の <xref:System.ServiceModel.Activities.WorkflowServiceHost> がある場合は、その WorkflowServiceHost によってインスタンスが回復されます。\(インスタンスの回復はこのサンプルの範囲外です\)。  
  
-   `RunnableInstancesDetectionPeriod` を設定します。この期間は、実行可能になったインスタンスをホストがポーリングする間隔を定義します。インスタンスが実行可能になるのは次の場合です。  
  
    -   永続的なタイマー \(<xref:System.Activities.Statements.Delay>\) が切れた場合。  
  
    -   別のホストで `HostLockRenewal` のハートビートが \(コンピューターがクラッシュしたなどの理由で\) 失敗してインスタンスが回復された場合。  
  
-   `InstanceCompletionAction` を設定します。このプロパティを `DeleteNothing` に設定すると、完了したインスタンスがインスタンス ストアに保持されます。`DeleteAll` に設定すると、インスタンスが完了時にストアから削除されます。次の点に注意してください。  
  
    > [!NOTE]
    >  カウントが完了する前に Enter キーを押してホストを終了すると、ワークフロー インスタンスが完了しません。  
  
-   `InstanceLockedExceptionAction` を設定します。この設定は、別のホストによってロックされているインスタンスを読み込もうとした場合の動作を定義します。次の選択肢があります。  
  
    -   `NoRetry`: 読み込みを再試行せずにホストに `InstanceLockedException` を返します。  
  
    -   `BasicRetry`: インスタンスの読み込みを再試行し続けます。再試行のスケジュールは、単純な線形アルゴリズムに従って設定されます \(5 秒ごとに再試行するなど\)。  
  
    -   `AggressiveRetry`: インスタンスの読み込みを再試行し続けます。再試行のスケジュールは、積極的な指数バックオフ アルゴリズムに従って設定されます。  
  
-   Encoding オプションを設定します。この設定は、SQL Workflow Instance Store にインスタンスの状態を格納する方法を定義します。次の選択肢があります。  
  
    -   GZip 圧縮アルゴリズムを使用してインスタンスの状態を圧縮します。  
  
    -   インスタンスの状態を圧縮しません。  
  
#### このサンプルを使用するには  
  
1.  アクセス許可がある場合は、管理者として [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。  
  
2.  サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\BuiltInConfiguration\\CS\) に移動して、CreateInstanceStore.cmd を実行します。  
  
3.  管理特権がない場合は、SQL Server ログインを作成します。`[セキュリティ]` の **\[ログイン\]** に移動し、**\[ログイン\]** を右クリックして新しいログインを作成します。  
  
4.  自分の ACL ユーザーを SQL ロールに追加します。**\[データベース\]**、**\[InstanceStore\]**、**\[セキュリティ\]** の順に開き、**\[ユーザー\]** を右クリックして **\[新しいユーザー\]** をクリックします。**\[ログイン名\]** を、前の手順で作成したユーザーに設定します。そのユーザーを、**System.Activities.DurableInstancing.InstanceStoreUsers** \(およびその他\) のデータベース ロールのメンバーシップに追加します。ユーザーが既に存在している場合もあります \(ユーザー dbo など\)。  
  
5.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で InstanceStore.sln ファイルを開き、CTRL キー、SHIFT キーを押しながら B キーを押してソリューションをビルドします。  
  
6.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] で、サンプルの該当する bin\\debug ディレクトリ \(\\WF\\Basic\\Persistence\\BuiltInConfiguration\\cs\\InstanceStore\(1 または 2\)\\bin\\debug\) に移動し、InstanceStore.exe を右クリックして **\[管理者として実行\]** をクリックします。このサンプルはチャネル リスナーを開くため、管理特権で実行する必要があります。  
  
7.  ローカルの SQL Server Express 以外のデータベースにインスタンス ストアを作成した場合は、サンプルのデータベース接続文字列 \(InstanceStore1 プロジェクトの Program.cs にある `const string ConnectionString` と、InstanceStore2 プロジェクトの App.config にある `connectionString` 属性\) を更新してサンプルを再コンパイルする必要があります。  
  
#### サンプルが正常に実行されていることを確認するには  
  
1.  サンプルの実行中に、SQL Server Management Studio を起動します。  
  
2.  **\[オブジェクト エクスプローラー\]** で、**\[データベース\]**、**\[InstanceStore\]**、**\[テーブル\]** の順に選択し、**\[System.Activities.DurableInstancing.InstanceTable\]** を選択します。  
  
3.  **\[InstanceTable\]** を右クリックし、**\[上位 1000 行を選択\]** をクリックします。  
  
4.  新しいエントリがあり、**\[ロックの期限\]** が 5 秒ごとに変化していることを確認します \(クエリを更新するには、タスク バーの **\[実行\]** ボタンをクリックします\)。これは、**\[ホストのロック更新時間\]** が 5 に設定されているためです。  
  
5.  カウントの完了後にインスタンス テーブルのエントリが削除されることを確認します。これは、**\[インスタンス完了アクション\]** が **\[DeleteAll\]** に設定されているためです。  
  
6.  Enter キーを押してワークフロー ホスト アプリケーションを終了し、**LockOwnersTable** が削除されることを確認します。  
  
#### サンプルをアンインストールするには  
  
1.  サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\BuiltInConfiguration\) で RemoveInstanceStore.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
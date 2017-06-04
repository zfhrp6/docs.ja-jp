---
title: "ワークフロー アプリケーションの永続化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# ワークフロー アプリケーションの永続化
このサンプルでは、<xref:System.Activities.WorkflowApplication> を実行し、アイドル状態になったときにアンロードしてから、再読み込みしてその実行を継続する方法を示します。  
  
## サンプルの詳細  
 <xref:System.Activities.WorkflowApplication> は、単純なインターフェイスを提供していくつかのより一般的なホスト シナリオを実現する、単一のワークフロー インスタンスのホストです。このようなシナリオの 1 つに、永続化によって容易になる実行時間の長いワークフローがあります。永続化のホスト コントロールは、<xref:System.Activities.WorkflowApplication> で永続化操作を呼び出すか、<xref:System.Activities.WorkflowApplication> イベントを処理して <xref:System.Activities.WorkflowApplication> が永続化することを示すことで実行されます。  
  
 サンプル ワークフローは、ユーザーに名前の入力を求める <xref:System.Activities.Statements.WriteLine> アクティビティ、<xref:System.Activities.Bookmark> の再開を通じて名前を入力として受け取るための `ReadLine` アクティビティ、およびメッセージをユーザーにエコーするためのもう 1 つの <xref:System.Activities.Statements.WriteLine> です。ワークフローが入力を待機しているとき、これは永続化に適したポイントになります。これは <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent> ポイントと呼ばれています。<xref:System.Activities.WorkflowApplication> は、ワークフロー プログラムが永続化可能で、ブックマークの再開待ちの状態で、他の処理が実行されていないとき常に、<xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent> イベントを発生します。このサンプルのワークフローでは、そのポイントが `ReadLine` アクティビティの実行開始直後に発生します。  
  
 <xref:System.Activities.WorkflowApplication> は、<xref:System.Runtime.Persistence.InstanceStore> を使用して永続化を実行するように設定されています。このサンプルでは、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用しています。<xref:System.Runtime.Persistence.InstanceStore> は、<xref:System.Activities.WorkflowApplication> の実行前に <xref:System.Activities.WorkflowApplication.InstanceStore%2A> プロパティに割り当てる必要があります。  
  
 このサンプルでは、<xref:System.Activities.WorkflowApplication.PersistableIdle%2A> イベントにハンドラーを追加します。このイベントのハンドラーは、<xref:System.Activities.PersistableIdleAction> を返すことによって <xref:System.Activities.WorkflowApplication> が行う処理を示します。<xref:System.Activities.PersistableIdleAction> が返された場合、<xref:System.Activities.WorkflowApplication> はアンロードされます。  
  
 その後、このサンプルはユーザーからの入力を受け入れ、永続化されたワークフローを新しい <xref:System.Activities.WorkflowApplication> に読み込みます。これを行うには、新しい <xref:System.Activities.WorkflowApplication> を作成し、<xref:System.Runtime.Persistence.InstanceStore> を再作成します。次に、完了してアンロードされたイベントをインスタンスに関連付けて、対象のワークフロー インスタンスの識別子を使用して <xref:System.Activities.WorkflowApplication.Load%2A> を呼び出します。インスタンスが取得されたら、`ReadLine` アクティビティのブックマークが再開されます。ワークフローは、`ReadLine` アクティビティ内から実行を続け、最後まで実行します。ワークフローが完了してアンロードされると、最後にもう一度 <xref:System.Runtime.Persistence.InstanceStore> が呼び出され、ワークフローが削除されます。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。  
  
     このサンプルを実行するには、既定で [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] と共にインストールされる SQL Server Express が必要です。  
  
2.  サンプル ディレクトリ \(\\WF\\Basic\\Persistence\\InstancePersistence\\CS\) に移動して、CreateInstanceStore.cmd を実行します。  
  
    > [!CAUTION]
    >  CreateInstanceStore.cmd スクリプトは、SQL Server 2008 Express の既定のインスタンスにデータベースを作成しようとします。別のインスタンスにデータベースをインストールする場合は、そのようにスクリプトを変更してください。  
  
3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して Persistence.sln ソリューション ファイルを開き、CTRL キーと SHIFT キーを押しながら B キーを押してビルドします。  
  
    > [!CAUTION]
    >  SQL Server の既定以外のインスタンスにデータベースをインストールした場合は、ソリューションをビルドする前に、コードの接続文字列を更新してください。  
  
4.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] でプロジェクトの bin ディレクトリ \(\\WF\\Basic\\Persistence\\InstancePersistence\\bin\\Debug\) に移動し、Workflow.exe を右クリックして **\[管理者として実行\]** をクリックすることで、サンプルを管理者権限で実行します。  
  
#### インスタンス ストア データベースを削除するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。  
  
2.  サンプル ディレクトリに移動して RemoveInstanceStore.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
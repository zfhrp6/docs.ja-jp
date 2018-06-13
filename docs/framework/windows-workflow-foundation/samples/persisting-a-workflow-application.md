---
title: ワークフロー アプリケーションの永続化
ms.date: 03/30/2017
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
ms.openlocfilehash: e5c0cf23dd238c0c5a81519b5e6c415f4ef75f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519188"
---
# <a name="persisting-a-workflow-application"></a>ワークフロー アプリケーションの永続化
このサンプルでは、<xref:System.Activities.WorkflowApplication> を実行し、アイドル状態になったときにアンロードしてから、再読み込みしてその実行を継続する方法を示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 <xref:System.Activities.WorkflowApplication> は、単純なインターフェイスを提供していくつかのより一般的なホスト シナリオを実現する、単一のワークフロー インスタンスのホストです。 このようなシナリオの 1 つに、永続化によって容易になる実行時間の長いワークフローがあります。 永続化のホスト コントロールは、<xref:System.Activities.WorkflowApplication> で永続化操作を呼び出すか、<xref:System.Activities.WorkflowApplication> イベントを処理して <xref:System.Activities.WorkflowApplication> が永続化することを示すことで実行されます。  
  
 サンプル ワークフローは、ユーザーに名前の入力を求める <xref:System.Activities.Statements.WriteLine> アクティビティ、`ReadLine` の再開を通じて名前を入力として受け取るための <xref:System.Activities.Bookmark> アクティビティ、およびメッセージをユーザーにエコーするためのもう 1 つの <xref:System.Activities.Statements.WriteLine> です。 ワークフローが入力を待機しているとき、これは永続化に適したポイントになります。 これは <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> ポイントと呼ばれています。 <xref:System.Activities.WorkflowApplication> は、ワークフロー プログラムが永続化可能で、ブックマークの再開待ちの状態で、他の処理が実行されていないとき常に、<xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> イベントを発生します。 このサンプルのワークフローでは、そのポイントが `ReadLine` アクティビティの実行開始直後に発生します。  
  
 A<xref:System.Activities.WorkflowApplication>永続化を実行するように設定する<!--zz <xref:System.Runtime.Persistence.InstanceStore> -->`System.Runtime.Persistence.InstanceStore`です。 このサンプルでは、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> を使用しています。 <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`に割り当てる必要があります、<xref:System.Activities.WorkflowApplication.InstanceStore%2A>前に、プロパティ、<xref:System.Activities.WorkflowApplication>を実行します。  
  
 このサンプルでは、<xref:System.Activities.WorkflowApplication.PersistableIdle%2A> イベントにハンドラーを追加します。 このイベントのハンドラーは、<xref:System.Activities.WorkflowApplication> を返すことによって <xref:System.Activities.PersistableIdleAction> が行う処理を示します。 <xref:System.Activities.PersistableIdleAction.Unload> が返された場合、<xref:System.Activities.WorkflowApplication> はアンロードされます。  
  
 その後、このサンプルはユーザーからの入力を受け入れ、永続化されたワークフローを新しい <xref:System.Activities.WorkflowApplication> に読み込みます。 これは、新しい作成によって<xref:System.Activities.WorkflowApplication>、再作成、 <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`、インスタンスに完了してアンロードされたイベントに関連付けると、呼び出すことで、<xref:System.Activities.WorkflowApplication.Load%2A>ターゲット ワークフロー インスタンスの識別子を使用します。 インスタンスが取得されたら、`ReadLine` アクティビティのブックマークが再開されます。 ワークフローは、`ReadLine` アクティビティ内から実行を続け、最後まで実行します。 ワークフローが完了してアンロードするときに、 <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`ワークフローを削除する最後にもう一度と呼びます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
     このサンプルを実行するには、既定で [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] と共にインストールされる SQL Server Express が必要です。  
  
2.  サンプル ディレクトリ (\WF\Basic\Persistence\InstancePersistence\CS) に移動して、CreateInstanceStore.cmd を実行します。  
  
    > [!CAUTION]
    >  CreateInstanceStore.cmd スクリプトは、SQL Server 2008 Express の既定のインスタンスにデータベースを作成しようとします。 別のインスタンスにデータベースをインストールする場合は、そのようにスクリプトを変更してください。  
  
3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して Persistence.sln ソリューション ファイルを開き、Ctrl キーと Shift キーを押しながら B キーを押してビルドします。  
  
    > [!CAUTION]
    >  SQL Server の既定以外のインスタンスにデータベースをインストールした場合は、ソリューションをビルドする前に、コードの接続文字列を更新してください。  
  
4.  管理者特権でのプロジェクトの bin ディレクトリ (\WF\Basic\Persistence\InstancePersistence\bin\Debug) に移動してサンプルを実行[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]Workflow.exe を右クリックしを選択すると、 **を管理者として実行**.  
  
#### <a name="to-remove-the-instance-store-database"></a>インスタンス ストア データベースを削除するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
2.  サンプル ディレクトリに移動して RemoveInstanceStore.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)

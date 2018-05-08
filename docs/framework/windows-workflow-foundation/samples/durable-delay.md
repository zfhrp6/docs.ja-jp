---
title: 永続的な遅延
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 5307b8144e17f91cd3ba8c2e385492f86c167820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="durable-delay"></a>永続的な遅延
このサンプルでは、永続的な遅延を使用する方法を示します。これは、遅延の間、ワークフローを永続的なデバイスに永続化する遅延のことです。 このサンプル ワークフローには、遅延によって分割された 2 つのコンソールへのメッセージが含まれています。 遅延が発生すると、ワークフローがアンロードされ、ワークフローはメモリに再読み込みされるまでワークフロー インスタンス ストアで 5 秒間待機します。  
  
## <a name="workflow-details"></a>ワークフローの詳細  
 ワークフロー サービス ホストは、ワークフローをホストし、読み込みとアンロードを行うことによってワークフロー インスタンスを管理します。 ワークフロー定義のインスタンスを開始するために、このサンプルでは、ワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティにメッセージを送信するプロキシを設定します。 <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> プロパティを `true` に設定し、このプロパティがメッセージを受信したらワークフローの新しいインスタンスを作成できるようにします。  
  
 初期化時のワークフロー サービス ホストによる設定の詳細を次に示します。  
  
1.  アドレスを持つサービス ホストを作成 (http://localhost:8080/Client)です。  
  
2.  ワークフロー内で <xref:System.ServiceModel.Activities.Receive> アクティビティとの通信を可能にする、サービス ホストのエンドポイントを作成します。  
  
3.  SQL インスタンス ストアを設定します。  
  
4.  ワークフロー サービス ホストがワークフロー インスタンスを SQL 永続化ストアにアンロードする条件を指定する、インスタンスのアンロード動作を追加します。 このサンプルでは、(遅延が発生して) ワークフローがアイドル状態になった直後にインスタンスがアンロードされます。  
  
5.  ワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティにメッセージを送信するプロキシを作成します。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  永続性データベースを設定します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
    2.  移動し、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4 です。X\\)。  
  
    3.  WorkflowManagementService.exe.config ファイルを編集し、<`database`> 要素内に次の接続文字列を追加します。  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  DurableDelay\CS ディレクトリに移動します。  
  
    5.  Setup.cmd を実行します。  
  
2.  実行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者特権を使用して、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]アイコンを選択して**管理者として実行**です。  
  
3.  Delay.sln ソリューション ファイルを開きます。  
  
4.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
5.  Ctrl キーを押しながら F5 キーを押してソリューションを実行します。  
  
#### <a name="to-uninstall-this-sample"></a>このサンプルをアンインストールするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
2.  DurableDelay\CS ディレクトリに移動します。  
  
3.  Cleanup.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`
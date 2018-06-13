---
title: XAMLX における永続的な遅延
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1b0e418e382c20350a61a36164265c1693925e11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516306"
---
# <a name="durable-delay-in-xamlx"></a>XAMLX における永続的な遅延
このサンプルでは、永続的な遅延を使用する方法を示します。これは、遅延の間、ワークフローを永続的なデバイスに永続化する遅延のことです。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>説明  
 このサンプル ワークフローには、遅延によって分割された 2 つのローカル ファイルへのメッセージが含まれています。 遅延が発生すると、ワークフローがアンロードされ、ワークフローはメモリに再読み込みされるまでワークフロー インスタンス ストアで 5 秒間待機します。  
  
 この .xamlx ファイルは、Visual Studio でホストされるワークフロー サービスです。 Visual Studio では、ワークフロー ホストに、ワークフロー サービスを使用する Cassini を使用します。  
  
 ワークフロー サービス ホストは、ワークフローをホストするだけでなく、読み込みとアンロードを行うことによってワークフロー インスタンスを管理します。 メッセージを送信するクライアントを設定すると、ワークフロー サービス ホストで Windows Workflow Foundation (WF) 定義のインスタンスを開始するには<xref:System.ServiceModel.Activities.Receive>ワークフローのアクティビティ。 この <xref:System.ServiceModel.Activities.Receive> は、<xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> プロパティが `true` に設定されているため、メッセージを受信した後にワークフローの新しいインスタンスを作成できます。  
  
 初期化中に、ワークフロー サービス ホストに対してインスタンスを永続化ストア (データベース) にアンロードするように指定する、インスタンスのアンロード動作が構成ファイルに追加されます。 このサンプルでは、(遅延が発生して) ワークフローがアイドル状態になった直後にインスタンスがアンロードされます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
2.  DurableDelayXamlx\CS フォルダーに移動します。  
  
3.  Setup.cmd を実行します。  
  
4.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者として実行します。  
  
5.  DurableDelayXamlx.sln ソリューション ファイルを開きます。  
  
6.  **ソリューション エクスプ ローラー**、ソリューションを右クリックし **プロパティ**です。  
  
7.  選択**マルチ スタートアップ プロジェクト**に両方のプロジェクトを設定および**開始**です。  
  
8.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
9. ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
#### <a name="to-uninstall-this-sample"></a>このサンプルをアンインストールするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
2.  DurableDelayXamlx\CS フォルダーに移動します。  
  
3.  Cleanup.cmd を実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`

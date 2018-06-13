---
title: トランザクション コンボイ スコープ
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: 4b053c15768a20ade4a469c9a40af797f49c268b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516566"
---
# <a name="transaction-convoy-scope"></a>トランザクション コンボイ スコープ
このサンプルでは、パラレルなコンボイ メッセージング アクティビティ パターンを <xref:System.ServiceModel.Activities.TransactedReceiveScope> と組み合わせて作成し、多数の操作をすべて同じトランザクションで任意の順序で行うことができるプロトコルをモデル化する方法を示します。 また、トランザクションがサーバーにフローされないためにクライアントで使用できるトランザクションがない場合に、<xref:System.ServiceModel.Activities.TransactedReceiveScope> で自動的に新しいトランザクションを作成する方法も示します。  
  
 このサンプルは、クライアントとサーバーを表す 2 つのワークフロー プロジェクトで構成されます。 クライアント プロジェクトでは、最初にメッセージを送信してサーバー ワークフローをブートストラップするワークフローを実行します。このワークフローで、相関関係が初期化され、残りのメッセージング アクティビティのトランザクション スコープが開始されます。 クライアントの <xref:System.Activities.Statements.Sequence> アクティビティには、<xref:System.ServiceModel.Activities.Send> と <xref:System.ServiceModel.Activities.ReceiveReply> の最初のペアと、3 つの分岐がある <xref:System.Activities.Statements.Parallel> アクティビティが含まれます。 各分岐で、一方向のメッセージがサーバーに送信されます。 <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> アクティビティの <xref:System.Activities.Statements.Parallel> プロパティは、3 つすべての分岐を完了するように `false` に設定されています。  
  
 サーバー ワークフローはクライアント ワークフローに似ていますが、メッセージング アクティビティが通信のサーバー側のものになり、すべての作業が同じトランザクションで実行されるように <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ内に格納されています。 サーバーで最初のメッセージを受信すると、トランザクションが作成されます。トランザクションはこのスコープのアンビエント トランザクションになり、<xref:System.ServiceModel.Activities.TransactedReceiveScope> 本体のスコープ内のあらゆるアクティビティがこのトランザクションにアクセスできます。 その後、すべての受信が並行して実行されます。 並行アクティビティの完了条件の定義に従って、すべての受信が 1 回だけ実行される必要があります。 暗黙的な永続化ポイントが <xref:System.ServiceModel.Activities.TransactedReceiveScope> 本体の末尾にあり、永続化操作も同じトランザクションで実行されます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ParallelConvoySample.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  どちらのプロジェクトも開始されるように設定されていることを確認します。  
  
    1.  **ソリューション エクスプ ローラー**、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。  
  
    2.  選択**マルチ スタートアップ プロジェクト**の両方のプロジェクトのアクションに設定されていることを確認および**開始**です。  
  
4.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     サーバーで "`Server is running`" と出力され、サーバーの準備ができたことが示されます。  
  
     クライアント コンソール ウィンドウで任意のキーを押してサンプルを開始します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`
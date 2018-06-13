---
title: サービス内での TransactionScope の入れ子化
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: 9c556df417548ab348d1dd5bc642928ae68d8878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518270"
---
# <a name="nesting-of-transactionscope-within-a-service"></a>サービス内での TransactionScope の入れ子化
このサンプルは、サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティ インスタンスを処理する方法を示す 2 つのシナリオで構成されます。 トランザクションでは、まず <xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してサーバー上でトランザクションを受信し、トランザクションの有効期間のスコープを設定します。 サービス内の最初のシナリオでは、2 つ目の <xref:System.Activities.Statements.TransactionScope> アクティビティを実行して、サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティを入れ子にする方法を示します。 2 番目のシナリオでは、入れ子になった <xref:System.Activities.Statements.TransactionScope> アクティビティ内でタイムアウトがどのように機能するかを示します。  
  
## <a name="client-application"></a>クライアント アプリケーション  
 クライアント アプリケーションは、<xref:System.Activities.Statements.TransactionScope> アクティビティの開始、分散トランザクション ID の出力、サーバーへのメッセージの送信、トランザクションのフロー、応答の受信、分散トランザクション ID の再出力、および完了処理を行うワークフローを実行します。 クライアント アプリケーションは、このワークフローをサービス シナリオごとに 1 回だけ実行します。  
  
## <a name="server-application"></a>サーバー アプリケーション  
 サーバー プロジェクトは、クライアントからのメッセージをリッスンするためのエンドポイントを作成する <xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされます。 ワークフローの中心は、クライアントからフローされたトランザクションを受信し、分散トランザクション ID を出力して、2 つ目の <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを実行する <xref:System.Activities.Statements.TransactionScope> です。 最初のシナリオでは、トランザクションは正常に完了します。 2 番目のシナリオでは、<xref:System.Activities.Statements.TransactionScope> アクティビティの本体は 5 秒の遅延で、トランザクションのタイムアウトは 2 秒に設定されています。 トランザクションがタイムアウトすると、トランザクションは中止されます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で TransactionServiceExample.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。  
  
3.  ビルドが成功した後、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。 ダイアログ ボックスから選択**マルチ スタートアップ プロジェクト**両方のプロジェクトのアクションを確認してください**開始**です。  
  
4.  F5 キーを押すか、選択**デバッグの開始**から、**デバッグ**メニュー。 または、ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`

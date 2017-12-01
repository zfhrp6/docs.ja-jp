---
title: "TransactedReceiveScope の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23117014b688f0b440da3cec8620023eaf212f71
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="use-of-transactedreceivescope"></a>TransactedReceiveScope の使用
このサンプルでは、クライアントからサーバーにトランザクションをフローする方法を示します。このために、<xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してフローされたトランザクションを含むメッセージを受信し、サーバー上でトランザクションの有効期間のスコープを設定します。 このサンプルは、クライアントとサーバーの役割を果たす 2 つのプロジェクトで構成されます。  
  
## <a name="client-application"></a>クライアント アプリケーション  
 クライアント アプリケーションは、分散トランザクション ID の出力、サーバーへのメッセージの送信、トランザクションのフロー、応答の受信、分散トランザクション ID の再出力、および完了処理を行うワークフローを実行します。 最初に出力される分散トランザクション ID は空の GUID です。これは、その時点ではトランザクションがまだローカルのみであるためです。  
  
## <a name="server-application"></a>サーバー アプリケーション  
 サーバー プロジェクトはクライアントに似ていますが、ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされます。これは、エンドポイントでクライアントからのメッセージをリッスンする必要があるためです。 ワークフローの中心は、クライアントからフローされたトランザクションの受信、送信されたメッセージの出力、分散トランザクション ID の出力、およびクライアントへの応答の送信を行う <xref:System.ServiceModel.Activities.TransactedReceiveScope> です。 分散トランザクション ID は空でない GUID になり、トランザクションに対応するアクティビティが <xref:System.ServiceModel.Activities.TransactedReceiveScope> の本体に追加された場合、そのアクティビティはフローされたランザクションで実行されます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で TransactedReceiveScope.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。  
  
3.  ビルドが成功した後、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。 ダイアログ ボックスで、次のように選択します。**マルチ スタートアップ プロジェクト**両方のプロジェクトのアクションを確認してください**開始**です。  
  
4.  F5 キーを押すか、選択**デバッグの開始**から、**デバッグ**メニュー。 または、ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。  
  
    > [!NOTE]
    >  クライアントを起動する前に、サーバーを起動しておく必要があります。 サービスをホストするコンソール ウィンドウの出力で、起動された時間が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`
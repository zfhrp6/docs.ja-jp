---
title: "TransactedReceiveScope の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# TransactedReceiveScope の使用
このサンプルでは、クライアントからサーバーにトランザクションをフローする方法を示します。このために、<xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してフローされたトランザクションを含むメッセージを受信し、サーバー上でトランザクションの有効期間のスコープを設定します。このサンプルは、クライアントとサーバーの役割を果たす 2 つのプロジェクトで構成されます。  
  
## クライアント アプリケーション  
 クライアント アプリケーションは、分散トランザクション ID の出力、サーバーへのメッセージの送信、トランザクションのフロー、応答の受信、分散トランザクション ID の再出力、および完了処理を行うワークフローを実行します。最初に出力される分散トランザクション ID は空の GUID です。これは、その時点ではトランザクションがまだローカルのみであるためです。  
  
## サーバー アプリケーション  
 サーバー プロジェクトはクライアントに似ていますが、ワークフローが <xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされます。これは、エンドポイントでクライアントからのメッセージをリッスンする必要があるためです。ワークフローの中心は、クライアントからフローされたトランザクションの受信、送信されたメッセージの出力、分散トランザクション ID の出力、およびクライアントへの応答の送信を行う <xref:System.ServiceModel.Activities.TransactedReceiveScope> です。分散トランザクション ID は空でない GUID になり、トランザクションに対応するアクティビティが <xref:System.ServiceModel.Activities.TransactedReceiveScope> の本体に追加された場合、そのアクティビティはフローされたランザクションで実行されます。  
  
#### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で TransactedReceiveScope.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、CTRL キーと SHIFT キーを押したまま B キーを押すか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
3.  ビルドが完了したら、ソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックします。ダイアログで、**\[マルチ スタートアップ プロジェクト\]** を選択し、両方のプロジェクトのアクションが **\[開始\]** になっていることを確認します。  
  
4.  F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。または、Ctrl キーを押しながら F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、デバッグ機能なしで実行します。  
  
    > [!NOTE]
    >  クライアントを起動する前に、サーバーを起動しておく必要があります。サービスをホストするコンソール ウィンドウの出力で、起動された時間が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`  
  
## 参照
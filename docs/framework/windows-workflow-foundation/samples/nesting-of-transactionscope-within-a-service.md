---
title: "サービス内での TransactionScope の入れ子化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# サービス内での TransactionScope の入れ子化
このサンプルは、サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティ インスタンスを処理する方法を示す 2 つのシナリオで構成されます。トランザクションでは、まず <xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してサーバー上でトランザクションを受信し、トランザクションの有効期間のスコープを設定します。サービス内の最初のシナリオでは、2 つ目の <xref:System.Activities.Statements.TransactionScope> アクティビティを実行して、サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティを入れ子にする方法を示します。2 番目のシナリオでは、入れ子になった <xref:System.Activities.Statements.TransactionScope> アクティビティ内でタイムアウトがどのように機能するかを示します。  
  
## クライアント アプリケーション  
 クライアント アプリケーションは、<xref:System.Activities.Statements.TransactionScope> アクティビティの開始、分散トランザクション ID の出力、サーバーへのメッセージの送信、トランザクションのフロー、応答の受信、分散トランザクション ID の再出力、および完了処理を行うワークフローを実行します。クライアント アプリケーションは、このワークフローをサービス シナリオごとに 1 回だけ実行します。  
  
## サーバー アプリケーション  
 サーバー プロジェクトは、クライアントからのメッセージをリッスンするためのエンドポイントを作成する <xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされます。ワークフローの中心は、クライアントからフローされたトランザクションを受信し、分散トランザクション ID を出力して、2 つ目の <xref:System.Activities.Statements.TransactionScope> アクティビティを実行する <xref:System.ServiceModel.Activities.TransactedReceiveScope> です。最初のシナリオでは、トランザクションは正常に完了します。2 番目のシナリオでは、<xref:System.Activities.Statements.TransactionScope> アクティビティの本体は 5 秒の遅延で、トランザクションのタイムアウトは 2 秒に設定されています。トランザクションがタイムアウトすると、トランザクションは中止されます。  
  
#### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で TransactionServiceExample.sln ソリューションを開きます。  
  
2.  ソリューションをビルドするには、CTRL キーと SHIFT キーを押したまま B キーを押すか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
3.  ビルドが完了したら、ソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックします。ダイアログ ボックスで、**\[マルチ スタートアップ プロジェクト\]** を選択し、両方のプロジェクトのアクションが **\[開始\]** になっていることを確認します。  
  
4.  F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。または、Ctrl キーを押しながら F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックして、デバッグ機能なしで実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
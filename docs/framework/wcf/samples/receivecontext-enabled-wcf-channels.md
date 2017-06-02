---
title: "ReceiveContext が有効な WCF チャネル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# ReceiveContext が有効な WCF チャネル
このサンプルでは、<xref:System.ServiceModel.Channels.ReceiveContext> を有効にした WCF チャネルの有用性を示します。  このサンプルでは、NetMSMQ チャネルを使用して 2 つの数値の積を見つけるサービスを実装します。  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> クラスを使用すると、メッセージの内容を検査した後でも、メッセージにアクセスするか、メッセージをキューに残してさらに処理するかをアプリケーションで指定できます。  このサンプルでは、クライアントがランダムな整数をトランザクション キューに送信します。  `ProductCalculator` サービスはメッセージを受信し、そのメッセージの内容 \(整数\) を検索して、積が計算できるかどうかを確認します。  サービス操作で積が計算されない場合、メッセージはキューに戻されます。このメッセージはキューをリッスンするサービスでもう一度受信できます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### このサンプルを使用するには  
  
1.  Microsoft Message Queuing \(MSMQ\) がインストールされていることを確認します。  
  
    1.  MSMQ を [!INCLUDE[lserver](../../../../includes/lserver-md.md)] にインストールするには  
  
        1.  **サーバー マネージャー**で **\[機能\]** をクリックします。  
  
        2.  **\[機能の概要\]** の右側のペインで、**\[機能の追加\]** をクリックします。  
  
        3.  表示されたウィンドウで **\[メッセージ キュー\]** を展開します。  
  
        4.  **\[メッセージ キュー サービス\]** を展開します。  
  
        5.  **\[ディレクトリ サービス統合\]** を \(ドメインに参加するコンピューターの場合\) クリックし、**\[HTTP サポート\]** をクリックします。  
  
        6.  **\[次へ\]** をクリックし、**\[インストール\]** をクリックします。  
  
    2.  MSMQ を [!INCLUDE[wv](../../../../includes/wv-md.md)] にインストールするには  
  
        1.  **コントロール パネル**を開きます。  
  
        2.  **\[プログラム\]** をクリックし、**\[プログラムと機能\]** の **\[Windows の機能の有効化または無効化\]** をクリックします。  
  
        3.  **\[Microsoft Message Queue \(MSMQ\) Server\]**、**\[Microsoft Message Queue \(MSMQ\) Server Core\]** の順に展開して、インストールする次のメッセージ キュー機能のチェック ボックスをオンにします。  
  
            -   \[メッセージ キュー サーバー\]  
  
            -   \[MSMQ Active Directory Domain Services Integration\] \(ドメインに参加するコンピューターの場合\)  
  
            -   \[MSMQ HTTP サポート\]  
  
        4.  **\[OK\]** をクリックします。  
  
        5.  コンピューターを再起動するかどうかを確認するメッセージが表示されたら、**\[OK\]** をクリックしてインストールを完了します。  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] がコンピューターにインストールされていることを確認します。  
  
3.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、ReceiveContextProductGenerator.sln ソリューション ファイルを開きます。  
  
4.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
5.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。
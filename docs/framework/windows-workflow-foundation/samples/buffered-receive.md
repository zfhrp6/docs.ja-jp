---
title: "バッファーされた受信機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# バッファーされた受信機能
このサンプルでは、[!INCLUDE[wf](../../../../includes/wf-md.md)] のバッファーされた受信機能を設定および構成する方法を示します。バッファーされた受信機能を使用すると、ワークフロー作成者は、メッセージが受信される順序を考慮することなくワークフローを作成できます。バッファーされた受信機能では、メッセージがローカルにバッファーされ、ワークフローで受信準備が整ったときにメッセージが配信されます。  
  
## 使用例  
 メッセージング アクティビティと共にバッファーされた受信機能を使用した、順番を無視したメッセージ処理。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## 説明  
 このサンプルでは、[!INCLUDE[wf1](../../../../includes/wf1-md.md)] を使用して [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスが実装されます。このサービスには <xref:System.ServiceModel.Activities.Receive> アクティビティのシーケンスがあります。このワークフローは、ローン承認のための 3 つの通知を受け取る単純なローン承認プロセスをモデル化しています。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント アプリケーションは、サービスで想定される順序とは逆の順序で 3 つの関連付けられた通知を送信します。サービスでバッファーされた受信機能が有効になっているので、順番を無視した各メッセージがサービスにバッファーされ、ワークフローで受信準備が整ったときに処理されます。  
  
 バッファーされた受信機能では、バインディングによる <xref:System.ServiceModel.Activities.ReceiveContent> のサポートが必要なので、サービスで <xref:System.ServiceModel.NetMsmqBinding> が使用されます。バインディングのための特別な構成は不要なので、既定の設定が使用されます。  
  
```  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
  
```  
  
 また、サービスでは、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> を使用してサービスのメタデータが公開されます。  
  
 同様に、<xref:System.ServiceModel.NetMsmqBinding> を使用してクライアント エンドポイントが構成されます。[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] の **\[サービス参照の追加\]** 機能を使用して、クライアント コードと構成が生成されます。App.config ファイルで生成されたクライアント エンドポイントを次の例に示します。  
  
```  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
  
```  
  
 このサンプルでは、次の Windows コンポーネントが有効になっている必要があります。  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] と互換性のある管理、IIS メタベースおよび IIS 6 構成との互換性  
  
3.  World Wide Web サービス、アプリケーション開発機能、および ASP.NET  
  
4.  Microsoft メッセージ キュー \(MSMQ\) サーバー  
  
#### サンプルをセットアップしてビルドするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトで、「`aspnet_regiis –I`」と入力して ASP.NET を登録し、Enter キーを押します。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者として実行します。  
  
3.  LoanService.sln を開きます。  
  
4.  LoanService プロジェクトの仮想ディレクトリを作成するかどうかを確認するメッセージが表示されたら、**\[はい\]** をクリックします。  
  
#### サービス キューを設定するには  
  
1.  F5 キーを押して LoanClient アプリケーションを実行し、キューを作成して Service1.xamlx で定義されたサービスをアクティブ化します。  
  
2.  コマンド プロンプトから Compmgmt.msc を実行して、**\[コンピューターの管理\]** コンソールを開きます。  
  
3.  **\[コンピューターの管理\]** コンソールで、**\[サービスとアプリケーション\]**、**\[メッセージ キュー\]**、**\[専用キュー\]** の順に展開します。  
  
4.  loanservice\/service1.xamlx キューを右クリックし、**\[プロパティ\]** をクリックします。  
  
5.  **\[セキュリティ\]** タブをクリックし、Everyone グループに **\[メッセージの受信\]**、**\[メッセージのピーク\]**、および **\[メッセージの送信\]** アクセス許可を追加します。  
  
6.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] マネージャーを開きます。  
  
7.  **\[サーバー\]**、**\[サイト\]**、**\[既定の Web サイト\]**、**\[private\]**、**\[LoanService\]** の順に参照し、**\[詳細オプション\]** をクリックします。  
  
8.  **\[有効なプロトコル\]** を **http**,**net.msmq** に変更します。  
  
#### サンプルを実行するには  
  
1.  http:\/\/localhost\/private\/loanservice\/service1.xamlx を参照し、サービスが実行されていることを確認します。  
  
2.  F5 キーを押して LoanClient アプリケーションを実行します。ワークフローが完了したら、メッセージ交換の結果を示す out.txt ファイルが C:\\Inbox に保存されます。  
  
#### クリーンアップするには  
  
1.  コマンド プロンプトから Compmgmt.msc を実行して、**\[コンピューターの管理\]** コンソールを開きます。  
  
2.  **\[サービスとアプリケーション\]** 、**\[メッセージ キュー\]**、**\[専用キュー\]** の順に展開します。  
  
3.  loanservice\/service1.xamlx キューを削除します。  
  
4.  C:\\Inbox ディレクトリを削除します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
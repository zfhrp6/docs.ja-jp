---
title: バッファーされた受信機能
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abec64433d10a23dca6186c6c9a553bbed12a017
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="buffered-receive"></a>バッファーされた受信機能
このサンプルを設定して、Windows Workflow Foundation (WF) でバッファーされた受信機能を構成する方法を示します。 バッファーされた受信機能を使用すると、ワークフロー作成者は、メッセージが受信される順序を考慮することなくワークフローを作成できます。 バッファーされた受信機能では、メッセージがローカルにバッファーされ、ワークフローで受信準備が整ったときにメッセージが配信されます。  
  
## <a name="demonstrates"></a>使用例  
 メッセージング アクティビティと共にバッファーされた受信機能を使用した、順番を無視したメッセージ処理。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>説明  
 このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サービスが実装されます。このサービスには <xref:System.ServiceModel.Activities.Receive> アクティビティのシーケンスがあります。 このワークフローは、ローン承認のための 3 つの通知を受け取る単純なローン承認プロセスをモデル化しています。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント アプリケーションは、サービスで想定される順序とは逆の順序で 3 つの関連付けられた通知を送信します。 サービスでバッファーされた受信機能が有効になっているので、順番を無視した各メッセージがサービスにバッファーされ、ワークフローで受信準備が整ったときに処理されます。  
  
 バッファーされた受信機能では、バインディングによる <xref:System.ServiceModel.Activities.ReceiveContent> のサポートが必要なので、サービスで <xref:System.ServiceModel.NetMsmqBinding> が使用されます。 バインディングのための特別な構成は不要なので、既定の設定が使用されます。  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 また、サービスでは、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> を使用してサービスのメタデータが公開されます。  
  
 同様に、<xref:System.ServiceModel.NetMsmqBinding> を使用してクライアント エンドポイントが構成されます。 クライアント コードと構成を使用して生成されて、**サービス参照の追加**Visual Studio の機能です。 App.config ファイルで生成されたクライアント エンドポイントを次の例に示します。  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 このサンプルでは、次の Windows コンポーネントが有効になっている必要があります。  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] と互換性のある管理、IIS メタベースおよび IIS 6 構成との互換性  
  
3.  World Wide Web サービス、アプリケーション開発機能、および ASP.NET  
  
4.  Microsoft メッセージ キュー (MSMQ) サーバー  
  
#### <a name="to-set-up-and-build-the-sample"></a>サンプルをセットアップしてビルドするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトで、「`aspnet_regiis –I`」と入力して ASP.NET を登録し、Enter キーを押します。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者として実行します。  
  
3.  LoanService.sln を開きます。  
  
4.  LoanService プロジェクトの仮想ディレクトリを作成したい場合は、選択を求められたときに**はい**です。  
  
#### <a name="to-set-up-the-service-queues"></a>サービス キューを設定するには  
  
1.  F5 キーを押して LoanClient アプリケーションを実行し、キューを作成して Service1.xamlx で定義されたサービスをアクティブ化します。  
  
2.  開く、**コンピューターの管理**コンソールで、コマンド プロンプトから Compmgmt.msc を実行します。  
  
3.  **コンピューターの管理**コンソールで、[**サービス**、**アプリケーション**、**メッセージ キュー**、**専用キュー]**.  
  
4.  Loanservice/service1.xamlx キューを右クリックし **プロパティ**です。  
  
5.  選択、**セキュリティ**タブをクリックし、追加**Everyone メッセージの受信**、**メッセージのピーク**と**メッセージの送信**アクセス許可。  
  
6.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] マネージャーを開きます。  
  
7.  参照**サーバー**、**サイト**、**既定の Web サイト**、**プライベート**、 **LoanService** を選択**高度なオプション**  
  
8.  変更、**有効なプロトコル**する**http**、 **net.msmq**です。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  参照http://localhost/private/loanservice/service1.xamlxをサービスが実行されていることを確認します。  
  
2.  F5 キーを押して LoanClient アプリケーションを実行します。 ワークフローが完了したら、メッセージ交換の結果を示す out.txt ファイルが C:\Inbox に保存されます。  
  
#### <a name="to-clean-up"></a>クリーンアップするには  
  
1.  開く、**コンピューターの管理**コンソールで、コマンド プロンプトから Compmgmt.msc を実行します。  
  
2.  展開**サービス**と**アプリケーション**、**メッセージ キュー**、**専用キュー**です。  
  
3.  loanservice/service1.xamlx キューを削除します。  
  
4.  C:\Inbox ディレクトリを削除します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`

---
title: "SOAP エンドポイントおよび HTTP エンドポイント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# SOAP エンドポイントおよび HTTP エンドポイント
このサンプルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web プログラミング モデルを使用して、RPC ベースのサービスを実装し、SOAP 形式 および "Plain Old XML" \(POX\) 形式でサービスを公開する方法を示します。  サービスの HTTP バインディングの詳細については、「[基本的な HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)」のサンプルを参照してください。  このサンプルでは、さまざまなバインドを使用して SOAP および HTTP で RPC ベースのサービスを公開する方法について詳しく示します。  
  
## 使用例  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用した SOAP および HTTP での RPC サービスの公開。  
  
## 説明  
 このサンプルは、2 つのコンポーネントで構成されています。1 つは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを含む Web アプリケーション プロジェクト \(Service\) で、もう 1 つは SOAP バインドと HTTP バインドを使用してサービス操作を呼び出すコンソール アプリケーション \(Client\) です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、入力として渡された文字列をエコーする、`GetData` と `PutData` の 2 つの操作を公開します。  サービス操作には、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用して注釈が付けられます。  これらの属性は、これらの操作の HTTP 投影を制御します。  また、サービス操作には、<xref:System.ServiceModel.OperationContractAttribute> を使用して注釈が付けられます。この属性では、サービス操作を SOAP バインディングで公開できます。  サービスの `PutData` メソッドは <xref:System.ServiceModel.Web.WebFaultException> をスローします。この例外は、HTTP では HTTP ステータス コードを使用して返送され、SOAP では SOAP エラーとして返送されます。  
  
 Web.config ファイルは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを次の 3 つのエンドポイントで設定します。  
  
-   SOAP ベースのクライアントからアクセスするためのサービス メタデータを公開する ~\/service.svc\/mex エンドポイント  
  
-   クライアントが HTTP バインディングを使用してサービスにアクセスできる ~\/service.svc\/http エンドポイント  
  
-   クライアントが HTTP バインディングで SOAP を使用してサービスにアクセスできる ~\/service.svc\/soap endpoint エンドポイント  
  
 HTTP エンドポイントは、`helpEnabled` が `true` に設定されている \<`webHttp`\> 標準エンドポイントで設定されます。  その結果、サービスは、HTTP ベースのクライアントがサービスにアクセスするために使用できる、XHTML ベースのヘルプ ページ \(~\/service.svc\/http\/help\) を公開します。  
  
 クライアント プロジェクトは、\(**\[サービス参照の追加\]** で生成された\) SOAP プロキシを使用したサービスのアクセスと、<xref:System.Net.WebClient> を使用したサービスのアクセスを示します。  
  
 サンプルは、1 つの Web ホスト サービスと 1 つのコンソール アプリケーションで構成されています。  コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### サンプルを実行するには  
  
1.  SOAP および HTTP エンドポイント サンプルのソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  まだ開いていない場合は、Ctrl キーを押しながら W キーと S キーを押して、**ソリューション エクスプローラー** ウィンドウを開きます。  
  
4.  **ソリューション エクスプローラー** ウィンドウで **Service** プロジェクトを右クリックして **\[デバッグ\]** コンテキスト メニュー オプションの上にカーソルを置き、**\[新しいインスタンスを開始\]** コンテキスト メニューを表示します。  **\[新しいインスタンスを開始\]** をクリックします。  これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5.  ソリューション エクスプローラー ウィンドウで Client プロジェクトを右クリックして **\[デバッグ\]** コンテキスト メニュー オプションの上にカーソルを置き、**\[新しいインスタンスを開始\]** コンテキスト メニューを表示します。  **\[新しいインスタンスを開始\]** をクリックします。  
  
6.  クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。  
  
7.  サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
8.  クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。  
  
10. Windows の通知領域で、ASP.NET 開発サーバーのアイコンを右クリックし、コンテキスト メニューの **\[停止\]** を選択します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」に移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
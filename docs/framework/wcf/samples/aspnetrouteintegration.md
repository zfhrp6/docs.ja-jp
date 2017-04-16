---
title: "AspNetRouteIntegration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# AspNetRouteIntegration
このサンプルでは、ASP.NET ルートを使用して [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST サービスをホストする方法を示します。「[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)」のサンプルでは、このシナリオの自己ホスト バージョンを示し、サービスの実装について詳しく説明しています。ここでは、ASP.NET 統合機能について集中的に説明します。ASP.NET ルーティング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「<xref:System.Web.Routing>」を参照してください。  
  
## サンプルの詳細  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでは、リソース指向の REST 方式で顧客のコレクションが公開されます。このサービスは、SOAP ベースの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様に、.svc ファイルを使用して ASP.NET でホストできます。ただし、多くの場合、これは HTTP シナリオには適していません。サービスの URL に .svc を含める必要があるためです。また、サービス ライブラリと共に .svc ファイルを配置することも必要です。これらの制限事項を回避するには、このサンプルで示すように、ASP.NET ルートを使用してサービスをホストします。  
  
 このサンプルでは、<xref:System.ServiceModel.Activation.ServiceRoute> を Global.asax ファイルに追加して ASP.NET でサービスをホストします。<xref:System.ServiceModel.Activation.ServiceRoute> は、サービスの型 \(この場合は "Service"\)、サービスに使用するサービス ホスト ファクトリの型 \(この場合は <xref:System.ServiceModel.Activation.WebServiceHostFactory>\)、およびサービスの HTTP ベース アドレス \(この場合は "~\/Customers"\) を指定します。  
  
 さらに、このサンプルには、<xref:System.Web.Routing.UrlRoutingModule> \(ASP.NET ルートを有効にする\) を追加してサービスの構成を行う Web.config が含まれています。具体的には、<xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> が `true` に設定されている既定の <xref:System.ServiceModel.Description.WebHttpEndpoint> を使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構成します。その結果、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャによって、自動的な HTML ベースのヘルプ ページが `http://localhost/Customers/help` に作成されます。このページでは、サービスに対する HTTP 要求の作成方法とサービスの HTTP 応答へのアクセス方法に関する情報 \(顧客の詳細を XML と JSON で表す方法の例など\) が提供されます。  
  
 顧客のコレクション \(一般的には、任意のリソース\) をこの方法で公開すると、クライアントは、URI と HTTP の `GET`、`PUT`、`DELETE`、および `POST` を使用して一貫した方法でサービスと対話することができます。  
  
 Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにアクセスする 1 つの方法にすぎません。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル ファクトリや <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。SDK 内の他のサンプル \(「[基本的な HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)」のサンプルや「[形式の自動選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)」のサンプルなど\) では、これらのクラスを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと通信する方法を示します。  
  
 このサンプルは、3 つのプロジェクトで構成されます。  
  
 Service  
 ASP.NET でホストされる WCF HTTP サービスを含む Web アプリケーション プロジェクト。  
  
 Client  
 サービスを呼び出すコンソール アプリケーション プロジェクト。  
  
 Common  
 クライアントとサービスによって使用される `Customer` 型を含む共有ライブラリ。クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、ASP.NET ルート統合サンプルのソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  まだ開いていない場合は、Ctrl キーを押しながら W キーと S キーを押して、**ソリューション エクスプローラー** ウィンドウを開きます。  
  
4.  **ソリューション エクスプローラー** ウィンドウで **Service** プロジェクトを右クリックして **\[デバッグ\]** コンテキスト メニュー オプションの上にカーソルを置き、**\[新しいインスタンスを開始\]** コンテキスト メニューを表示します。**\[新しいインスタンスを開始\]** をクリックします。これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5.  **ソリューション エクスプローラー** ウィンドウで **Client** プロジェクトを右クリックして **\[デバッグ\]** コンテキスト メニュー オプションの上にカーソルを置き、**\[新しいインスタンスを開始\]** コンテキスト メニューを表示します。**\[新しいインスタンスを開始\]** をクリックします。  
  
6.  クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
7.  クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
8.  サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。Windows の通知領域で、ASP.NET 開発サーバーのアイコンを右クリックし、コンテキスト メニューの **\[停止\]** を選択します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## 参照
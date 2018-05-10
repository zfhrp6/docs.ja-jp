---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 671857b0ace2e18f0dac7fd8033a20f3af889c8b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
このサンプルでは、ASP.NET ルートを使用する Windows Communication Foundation (WCF) の REST サービスをホストする方法を示します。 [基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプルはこのシナリオの自己ホスト型のバージョンを表示および深さのサービスの実装について説明します。 ここでは、ASP.NET 統合機能について集中的に説明します。 ASP.NET ルーティングの詳細については、次を参照してください。<xref:System.Web.Routing>です。  
  
## <a name="sample-details"></a>サンプルの詳細  
 WCF サービスは、リソース指向の REST 方式で顧客のコレクションを公開します。 SOAP ベースの WCF サービスと同じようには、.svc ファイルを使用して ASP.NET では、サービスをホストすることができます。 ただし、多くの場合、これは HTTP シナリオには適していません。サービスの URL に .svc を含める必要があるためです。 また、サービス ライブラリと共に .svc ファイルを配置することも必要です。 これらの制限事項を回避するには、このサンプルで示すように、ASP.NET ルートを使用してサービスをホストします。  
  
 このサンプルでは、<xref:System.ServiceModel.Activation.ServiceRoute> を Global.asax ファイルに追加して ASP.NET でサービスをホストします。 <xref:System.ServiceModel.Activation.ServiceRoute> は、サービスの型 (この場合は "Service")、サービスに使用するサービス ホスト ファクトリの型 (この場合は <xref:System.ServiceModel.Activation.WebServiceHostFactory>)、およびサービスの HTTP ベース アドレス (この場合は "~/Customers") を指定します。  
  
 さらに、このサンプルには、<xref:System.Web.Routing.UrlRoutingModule> (ASP.NET ルートを有効にする) を追加してサービスの構成を行う Web.config が含まれています。 構成が、既定値は、WCF サービスを構成する具体的には、<xref:System.ServiceModel.Description.WebHttpEndpoint>を持つ、<xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A>設定`true`です。 その結果に自動ベース HTML ヘルプ ページの作成、WCF インフラストラクチャ`http://localhost/Customers/help`サービスと、サービスの HTTP 応答のインスタンスにアクセスする方法を方法の例は要求の HTTP を作成する方法に関する情報を提供する顧客詳細については、XML と JSON で表されます。  
  
 顧客のコレクション (一般的には、任意のリソース) をこの方法で公開すると、クライアントは、URI と HTTP の `GET`、`PUT`、`DELETE`、および `POST` を使用して一貫した方法でサービスと対話することができます。  
  
 Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 WCF チャネル ファクトリと同様に他の .NET Framework クラスを使用して、サービスにアクセスすることも、<xref:System.Net.WebClient>です。 SDK 内の他のサンプル (など、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプルおよび[自動形式選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)サンプル) WCF サービスと通信するためにこれらのクラスを使用する方法を示します。  
  
 このサンプルは、3 つのプロジェクトで構成されます。  
  
 サービス  
 ASP.NET でホストされる WCF HTTP サービスを含む Web アプリケーション プロジェクト。  
  
 クライアント  
 サービスを呼び出すコンソール アプリケーション プロジェクト。  
  
 Common  
 クライアントとサービスによって使用される `Customer` 型を含む共有ライブラリ。 クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、ASP.NET ルート統合サンプルのソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  これがまだ開いていない場合は"ctrl キーを押しながら W キーと S キーを押して開くには、**ソリューション エクスプ ローラー**ウィンドウです。  
  
4.  **ソリューション エクスプ ローラー**ウィンドウ を右クリックし、**サービス**プロジェクトし、カーソルを置きます、**デバッグ**コンテキスト メニュー オプションように、**開始新しいインスタンス**コンテキスト メニューが表示され選択**新しいインスタンスを開始**です。  これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5.  **ソリューション エクスプ ローラー**ウィンドウ を右クリックし、**クライアント**プロジェクトし、カーソルを置きます、**デバッグ**コンテキスト メニュー オプションように、**新しい開始インスタンス**コンテキスト メニューが表示され選択**新しいインスタンスを開始**です。  
  
6.  クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。 サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
7.  クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
8.  サービスのデバッグを停止するには、Shift + F5 キーを押して、Windows 通知領域にある ASP.NET 開発サーバーのアイコンを右クリックし、選択**停止**コンテキスト メニュー。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>関連項目

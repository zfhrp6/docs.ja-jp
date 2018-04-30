---
title: AspNetRouteIntegration
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 93d248030c4b32bd7725cf9c6fbbb829a19f7845
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
このサンプルでは、ASP.NET ルートを使用して [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST サービスをホストする方法を示します。 [基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)サンプルはこのシナリオの自己ホスト型のバージョンを表示および深さのサービスの実装について説明します。 ここでは、ASP.NET 統合機能について集中的に説明します。 ASP.NET ルーティングの詳細については、次を参照してください。<xref:System.Web.Routing>です。  
  
## <a name="sample-details"></a>サンプルの詳細  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでは、リソース指向の REST 方式で顧客のコレクションが公開されます。 このサービスは、SOAP ベースの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと同様に、.svc ファイルを使用して ASP.NET でホストできます。 ただし、多くの場合、これは HTTP シナリオには適していません。サービスの URL に .svc を含める必要があるためです。 また、サービス ライブラリと共に .svc ファイルを配置することも必要です。 これらの制限事項を回避するには、このサンプルで示すように、ASP.NET ルートを使用してサービスをホストします。  
  
 このサンプルでは、<xref:System.ServiceModel.Activation.ServiceRoute> を Global.asax ファイルに追加して ASP.NET でサービスをホストします。 <xref:System.ServiceModel.Activation.ServiceRoute> は、サービスの型 (この場合は "Service")、サービスに使用するサービス ホスト ファクトリの型 (この場合は <xref:System.ServiceModel.Activation.WebServiceHostFactory>)、およびサービスの HTTP ベース アドレス (この場合は "~/Customers") を指定します。  
  
 さらに、このサンプルには、<xref:System.Web.Routing.UrlRoutingModule> (ASP.NET ルートを有効にする) を追加してサービスの構成を行う Web.config が含まれています。 具体的には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が <xref:System.ServiceModel.Description.WebHttpEndpoint> に設定されている既定の <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> を使用して、`true` サービスを構成します。 その結果、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャによって、自動的な HTML ベースのヘルプ ページが `http://localhost/Customers/help` に作成されます。このページでは、サービスに対する HTTP 要求の作成方法とサービスの HTTP 応答へのアクセス方法に関する情報 (顧客の詳細を XML と JSON で表す方法の例など) が提供されます。  
  
 顧客のコレクション (一般的には、任意のリソース) をこの方法で公開すると、クライアントは、URI と HTTP の `GET`、`PUT`、`DELETE`、および `POST` を使用して一貫した方法でサービスと対話することができます。  
  
 Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。 これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにアクセスする 1 つの方法にすぎません。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル ファクトリや <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。 SDK 内の他のサンプル (など、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプルおよび[自動形式選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)サンプル) との通信にこれらのクラスを使用する方法を示して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。  
  
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
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>関連項目

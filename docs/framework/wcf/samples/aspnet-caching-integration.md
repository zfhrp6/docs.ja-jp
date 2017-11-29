---
title: "ASP.NET キャッシュ統合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8830f1c19b7a91d6c22d3b5955624c7d8a86f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="aspnet-caching-integration"></a>ASP.NET キャッシュ統合
このサンプルでは、WCF WEB HTTP プログラミング モデルで ASP.NET 出力キャッシュを利用する方法を示します。 参照してください、[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)の自己ホスト型のバージョンの深さのサービスの実装について説明する、このシナリオのサンプルです。 ここでは、ASP.NET 出力キャッシュ統合機能について集中的に説明します。  
  
## <a name="demonstrates"></a>使用例  
 ASP.NET 出力キャッシュとの統合  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>説明  
 このサンプルでは、<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> サービスで ASP.NET 出力キャッシュを利用するために、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用します。 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用される属性で、特定の操作からの応答に適用する構成ファイル内のキャッシュ プロファイルの名前を指定します。  
  
 サンプル サービス プロジェクトの Service.cs ファイルの両方、`GetCustomer`と`GetCustomers`とマークされた操作、 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>、"CacheFor60Seconds"キャッシュ プロファイル名を提供します。 サービス プロジェクトの Web.config ファイルでキャッシュ プロファイル"CacheFor60Seconds"は下で提供、<`caching`> の要素 <`system.web`>。 このキャッシュ プロファイルでの値、`duration`属性は「60」で、このプロファイルに関連付けられた応答は 60 秒間に、ASP.NET 出力キャッシュにキャッシュされます。 また、このキャッシュ プロファイルの`varmByParam`属性の値が異なるため要求を"format"に設定されて、`format`クエリ文字列パラメーター、応答は別々 にキャッシュします。 最後に、キャッシュ プロファイルの`varyByHeader`Accept ヘッダー値が異なる要求の応答を個別にキャッシュされるため、属性が"Accept"に設定します。  
  
 Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル ファクトリや <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。 SDK 内の他のサンプル (など、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプルおよび[自動形式選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)サンプル) との通信にこれらのクラスを使用する方法を示す、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。  
  
## <a name="to-run-the-sample"></a>サンプルを実行するには  
 このサンプルは、3 つのプロジェクトで構成されます。  
  
-   **サービス**: ASP.NET でホストされる WCF HTTP サービスを含む Web アプリケーション プロジェクト。  
  
-   **クライアント**: サービスを呼び出すコンソール アプリケーション プロジェクト。  
  
-   **一般的な**: クライアントとサービスによって使用される Customer 型を含む共有ライブラリ。  
  
 クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  ASP.NET キャッシュ統合サンプルのソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  場合、**ソリューション エクスプ ローラー**ウィンドウが開いていない、ctrl キーを押しながら W キーを押しながら S キーを押します。  
  
4.  **ソリューション エクスプ ローラー**ウィンドウで、右クリックして、**サービス**プロジェクトし、選択**新しいインスタンスを開始**です。 これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5.  **ソリューション エクスプ ローラー**ウィンドウで、右クリックして、**クライアント**プロジェクトし、選択**新しいインスタンスを開始**です。  
  
6.  クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。  
  
7.  サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
8.  クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。  
  
10. Windows 通知領域にある ASP.NET 開発サーバーのアイコンを右クリックし、選択**停止**です。

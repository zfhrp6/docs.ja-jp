---
title: "ASP.NET キャッシュ統合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ASP.NET キャッシュ統合
このサンプルでは、WCF WEB HTTP プログラミング モデルで ASP.NET 出力キャッシュを利用する方法を示します。  このシナリオの自己ホスト バージョンについては、「[基本的なリソース サービス](../../../../docs/framework/wcf/samples/basic-resource-service.md)」のサンプルを参照してください。サービスの実装について詳しく説明されています。  ここでは、ASP.NET 出力キャッシュ統合機能について集中的に説明します。  
  
## 使用例  
 ASP.NET 出力キャッシュとの統合  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## 説明  
 このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスで ASP.NET 出力キャッシュを利用するために、<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> を使用します。  <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用される属性で、特定の操作からの応答に適用する構成ファイル内のキャッシュ プロファイルの名前を指定します。  
  
 このサンプルの Service プロジェクトの Service.cs ファイルでは、`GetCustomer` 操作と `GetCustomers` 操作がどちらも <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> でマークされ、キャッシュ プロファイル名として "CacheFor60Seconds" が指定されています。  キャッシュ プロファイル "CacheFor60Seconds" は、Service プロジェクトの Web.config ファイルで、\<`system.web`\> の \<`caching`\> 要素の下で定義されています。  このキャッシュ プロファイルの `duration` 属性の値は "60" であるため、このプロファイルに関連付けられた応答は、ASP.NET 出力キャッシュに 60 秒間キャッシュされます。  また、このキャッシュ プロファイルの `varmByParam` 属性が "format" に設定されているため、`format` クエリ文字列パラメーターの値が異なる要求の応答は別々にキャッシュされます。  さらに、キャッシュ プロファイルの `varyByHeader` 属性が "Accept" に設定されているため、Accept ヘッダーの値が異なる要求の応答は別々にキャッシュされます。  
  
 Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。  これは、WCF サービスにアクセスする 1 つの方法にすぎません。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル ファクトリや <xref:System.Net.WebClient> などの他の .NET Framework クラスを使用して、サービスにアクセスすることも可能です。  SDK 内の他のサンプル \(「[基本的な HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)」のサンプルや「[形式の自動選択](../../../../docs/framework/wcf/samples/automatic-format-selection.md)」のサンプルなど\) では、これらのクラスを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと通信する方法を示します。  
  
## サンプルを実行するには  
 このサンプルは、3 つのプロジェクトで構成されます。  
  
-   **Service**: ASP.NET でホストされる WCF HTTP サービスを含む Web アプリケーション プロジェクト。  
  
-   **Client**: サービスを呼び出すコンソール アプリケーション プロジェクト。  
  
-   **Common**: クライアントとサービスによって使用される Customer 型を含む共有ライブラリ。  
  
 クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。  
  
#### サンプルを実行するには  
  
1.  ASP.NET キャッシュ統合サンプルのソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  **ソリューション エクスプローラー** ウィンドウがまだ開いていない場合は、Ctrl キーを押しながら W キーと S キーを押します。  
  
4.  **ソリューション エクスプローラー** ウィンドウで、**Service** プロジェクトを右クリックし、**\[新しいインスタンスを開始\]** をクリックします。  これで、サービスをホストする ASP.NET 開発サーバーが起動します。  
  
5.  **ソリューション エクスプローラー** ウィンドウで、**Client** プロジェクトを右クリックし、**\[新しいインスタンスを開始\]** をクリックします。  
  
6.  クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。  ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。  
  
7.  サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。  
  
8.  クライアント コンソール アプリケーションを終了するには、任意のキーを押します。  
  
9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。  
  
10. Windows の通知領域で、ASP.NET 開発サーバーのアイコンを右クリックし、**\[停止\]** を選択します。
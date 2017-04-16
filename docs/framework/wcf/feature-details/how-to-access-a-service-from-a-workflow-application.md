---
title: "方法: ワークフロー アプリケーションからサービスにアクセスする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法: ワークフロー アプリケーションからサービスにアクセスする
このトピックでは、ワークフロー コンソール アプリケーションからワークフロー サービスを呼び出す方法について説明します。これを実行するには、「[方法: メッセージング アクティビティを使用してワークフロー サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)」を完了している必要があります。このトピックでは、ワークフロー アプリケーションからワークフロー サービスを呼び出す方法について説明していますが、同じ方法を使用して、どのような [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスでもワークフロー アプリケーションから呼び出すことができます。  
  
### ワークフロー コンソール アプリケーション プロジェクトの作成  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動します。  
  
2.  「[方法: メッセージング アクティビティを使用してワークフロー サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)」で作成した MyWFService プロジェクトを読み込みます。  
  
3.  **ソリューション エクスプローラー**で **MyWFService** ソリューションを右クリックし、**\[追加\]** をクリックして、**\[新しいプロジェクト\]** をクリックします。**\[インストールされたテンプレート\]** から **\[ワークフロー\]** を選択し、プロジェクトの種類の一覧から **\[ワークフロー コンソール アプリケーション\]** を選択します。次の図に示すように、プロジェクトに MyWFClient という名前を付け、既定の場所を使用します。  
  
     ![&#91;新しいプロジェクトの追加&#93; ダイアログ](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     **\[OK\]** をクリックして **\[新しいプロジェクトの追加\]** ダイアログ ボックスを閉じます。  
  
4.  プロジェクトが作成されると、Workflow1.xaml ファイルがデザイナーで開かれます。**\[ツールボックス\]** タブが開かれていない場合は、これをクリックして開き、プッシュピンをクリックしてツールボックス ウィンドウを開いたままにします。  
  
5.  Ctrl キーを押しながら F5 キーを押して、サービスを起動します。以前と同様に、ASP.NET 開発サーバーが起動され、Internet Explorer に WCF ヘルプ ページが表示されます。このページの URI は、次の手順で使用する必要があるため、確認しておいてください。  
  
     ![WCF ヘルプ ページと URI を表示している IE](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  **ソリューション エクスプローラー**で **MyWFClient** プロジェクトを右クリックし、**\[サービス参照の追加\]** をクリックします。**\[探索\]** ボタンをクリックして、サービスに使用できる現在のソリューションを検索します。\[サービス\] ボックスで、Service1.xamlx の横にある三角形をクリックします。Service1 の横にある三角形をクリックして、Service1 サービスによって実装されるコントラクトの一覧を表示します。**\[サービス\]** ボックスで、**\[Service1\]** ノードを展開します。次の図のように、**\[操作\]** ボックスに Echo 操作が表示されます。  
  
     ![&#91;サービス参照の追加&#93; ダイアログ](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")  
  
     既定の名前空間のままにし、**\[OK\]** をクリックして **\[サービス参照の追加\]** ダイアログ ボックスを閉じます。次のダイアログ ボックスが表示されます。  
  
     ![サービス参照の追加の通知ダイアログ](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     **\[OK\]** をクリックして、このダイアログ ボックスを閉じます。次に、Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。ツールボックスに **MyWFClient.ServiceReference1.Activities** という名前の新しい選択肢が追加されていることを確認します。この選択肢を展開して、次の図のように、追加されている Echo アクティビティを確認します。  
  
     ![ツールボックスのエコー アクティビティ](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  <xref:System.ServiceModel.Activities.Sequence> アクティビティをデザイナー画面にドラッグ アンド ドロップします。これは、ツールボックスの **\[制御フロー\]** セクションにあります。  
  
8.  <xref:System.ServiceModel.Activities.Sequence> アクティビティにフォーカスがある状態で、**\[変数\]** リンクをクリックして、`inString` という名前の文字列変数を追加します。この変数と `outString` という名前の文字列変数に、既定値である `“Hello, world”` を設定します。  
  
     ![変数の追加](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. **Echo** アクティビティを <xref:System.ServiceModel.Activities.Sequence> にドラッグ アンド ドロップします。次の図のように、プロパティ ウィンドウで、\_string 引数を `inString` 変数にバインドし、`out_string` 引数を outString 変数にバインドします。これにより、`inString` 変数の値を操作に渡し、戻り値を取得し、その戻り値を `outString` 変数に格納します。  
  
     ![変数への引数のバインド](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. サービス呼び出しによって返された文字列を表示するために、**Echo** アクティビティの下に **WriteLine** アクティビティをドラッグ アンド ドロップします。**WriteLine** アクティビティは、ツールボックスの **\[プリミティブ\]** ノードにあります。**WriteLine** アクティビティのテキスト ボックスに「`outString`」と入力し、**WriteLine** アクティビティの **Text** 引数を `outString` 変数にバインドします。この時点で、ワークフローは次の図のようになります。  
  
     ![完全なクライアント ワークフロー](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. MyWFService ソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックします。次の図のように、**\[マルチ スタートアップ プロジェクト\]** ボタンを選択し、各プロジェクトの **\[アクション\]** 列で **\[開始\]** を選択します。  
  
     ![スタートアップ プロジェクトのオプション](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")  
  
12. Ctrl キーを押しながら F5 キーを押し、サービスとクライアントの両方を起動します。ASP.NET 開発サーバーがサービスをホストし、Internet Explorer に WCF ヘルプ ページが表示され、コンソール ウィンドウでクライアント ワークフロー アプリケーションが起動して、サービスから返された文字列 \("Hello, world"\) が表示されます。  
  
## 参照  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [方法: メッセージング アクティビティを使用してワークフロー サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)   
 [Web プロジェクトでのワークフローからの WCF サービスの使用](http://go.microsoft.com/fwlink/?LinkId=207725)
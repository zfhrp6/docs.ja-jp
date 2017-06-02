---
title: "方法: メッセージング アクティビティを使用してワークフロー サービスを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法: メッセージング アクティビティを使用してワークフロー サービスを作成する
このトピックでは、メッセージング アクティビティを使用して単純なワークフロー サービスを作成する方法について説明します。  ここでは、メッセージング アクティビティだけで構成されるサービスのワークフロー サービスを作成する機構に重点を置きます。  実際のサービスでは、ワークフローに他の多くのアクティビティが含まれます。  このサービスは、文字列を取得して、それを呼び出し元に返す、Echo という 1 つの操作を実装します。  このトピックは、一連の 2 つのトピックの最初のものです。  次のトピック「[方法: ワークフロー アプリケーションからサービスにアクセスする](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)」では、このトピックで作成したサービスを呼び出すワークフロー アプリケーションの作成方法について説明します。  
  
### ワークフロー サービス プロジェクトを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューで **\[新規作成\]**、**\[プロジェクト\]** の順に選択して、**\[新しいプロジェクト\]** ダイアログ ボックスを表示します。  インストールされているテンプレートの一覧で **\[ワークフロー\]** を選択し、プロジェクトの種類の一覧で **\[WCF ワークフロー サービス アプリケーション\]** を選択します。  次の図に示すように、プロジェクトに `MyWFService` という名前を付け、既定の場所を使用します。  
  
     **\[OK\]** をクリックして **\[新しいプロジェクト\]** ダイアログ ボックスを閉じます。  
  
3.  プロジェクトが作成されると、次の図に示すように、Service1.xamlx ファイルがデザイナーで開かれます。  
  
     ![デザイナーに表示されている既定のワークフロー](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     "**シーケンシャル サービス**" というラベルの付いたアクティビティを右クリックし、**\[削除\]** をクリックします。  
  
### ワークフロー サービスを実装するには  
  
1.  画面左側の **\[ツールボックス\]** タブをクリックしてツールボックスを表示し、プッシュピンをクリックしてウィンドウを開いたままにします。  次の図に示すように、ツールボックスの **\[メッセージング\]** セクションを展開して、メッセージング アクティビティおよびメッセージング アクティビティ テンプレートを表示します。  
  
     ![メッセージング タブが展開されているツールボックス](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  **\[ReceiveAndSendReply\]** テンプレートをワークフロー デザイナーにドラッグ アンド ドロップします。  これにより、<xref:System.ServiceModel.Activities.Sequence> アクティビティが作成されます。次の図に示すように、**Receive** アクティビティの後に <xref:System.ServiceModel.Activities.SendReply> アクティビティがあります。  
  
     ![デザイナーに表示された ReceiveAndSendReply テンプレート](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     <xref:System.ServiceModel.Activities.SendReply> アクティビティの <xref:System.ServiceModel.Activities.SendReply.Request%2A> プロパティは `Receive` に設定されています。これは、<xref:System.ServiceModel.Activities.Receive> アクティビティが応答する <xref:System.ServiceModel.Activities.SendReply> アクティビティの名前です。  
  
3.  <xref:System.ServiceModel.Activities.Receive> アクティビティの `[OperationName]` というラベルの付いたボックスに「**Echo**」と入力します。  これにより、サービスが実装する操作の名前が定義されます。  
  
     ![操作名を指定する](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  <xref:System.ServiceModel.Activities.Receive> アクティビティを選択した状態で、プロパティ ウィンドウがまだ開いていない場合は、**\[表示\]** メニューの **\[プロパティ ウィンドウ\]** をクリックして開きます。  **\[プロパティ ウィンドウ\]** で、**\[CanCreateInstance\]** が表示されるまで下へスクロールし、次の図に示すように、チェックボックスをオンにします。  この設定によって、ワークフロー サービス ホストはメッセージが受信されると \(必要に応じて\) サービスの新しいインスタンスを作成できるようになります。  
  
     ![CanCreateInstance プロパティ](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  <xref:System.ServiceModel.Activities.Sequence> アクティビティを選択し、デザイナーの左下隅にある **\[変数\]** をクリックします。  これにより、変数エディターが開かれます。  **\[変数の作成\]** リンクをクリックして、操作に送られる文字列を格納する変数を追加します。  変数に `msg` という名前を付け、次の図に示すように、その **\[変数\]** の種類を文字列に設定します。  
  
     ![変数の追加](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     **\[変数\]** をもう一度クリックして、変数エディターを閉じます。  
  
6.  アクティビティの **\[コンテンツ\]** ボックスの <xref:System.ServiceModel.Activities.Receive> **\[定義..\]** リンクをクリックして、**\[コンテンツ定義\]** ダイアログ ボックスを表示します。  **\[パラメーター\]** オプション ボタンを選択し、**\[新しいパラメーターの追加\]** リンクをクリックし、`[名前]` ボックスに**「inMsg」**と入力し、**\[型\]** ボックスの **\[文字列\]** を選択し、`[割り当て先]` ボックスに「**msg**」と入力します。  
  
     ![パラメーター コンテンツの追加](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     これにより、Receive アクティビティが文字列パラメーターを受け取り、そのデータが `msg` 変数にバインドされるように指定されます。  **\[OK\]** をクリックして **\[コンテンツ定義\]** ダイアログ ボックスを閉じます。  
  
7.  **\[定義...\]** アクティビティの **\[コンテンツ\]** ボックスの <xref:System.ServiceModel.Activities.SendReply> リンクをクリックして、**\[コンテンツ定義\]** ダイアログ ボックスを表示します。  **\[パラメーター\]** オプション ボタンを選択し、**\[新しいパラメーターの追加\]** リンクをクリックして `[名前]` ボックスに**「msg」**と入力し、**\[型\]** ボックスの **\[文字列\]** を選択し、`[値]` ボックスに「**msg**」と入力します。  
  
     ![パラメーター コンテンツの追加](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     これにより、<xref:System.ServiceModel.Activities.SendReply> アクティビティがメッセージまたはメッセージ コントラクト型を送信し、そのデータが `msg` 変数にバインドされるように指定されます。  これは <xref:System.ServiceModel.Activities.SendReply> アクティビティであるため、`msg` のデータは、アクティビティがクライアントに送り返すメッセージの設定に使用されます。  **\[OK\]** をクリックして **\[コンテンツ定義\]** ダイアログ ボックスを閉じます。  
  
8.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックして、ソリューションを保存およびビルドします。  
  
## ワークフロー サービス プロジェクトの構成  
 ワークフロー サービスは完成しました。  ここでは、ホストと実行を容易にするように、ワークフロー サービス ソリューションを構成する方法について説明します。  このソリューションでは、ASP.NET 開発サーバーを使用してサービスをホストします。  
  
#### プロジェクトのスタートアップ オプションを設定するには  
  
1.  **ソリューション エクスプローラー**で **\[MyWFService\]** を右クリックし、**\[プロパティ\]** をクリックして **\[プロジェクトのプロパティ\]** ダイアログ ボックスを表示します。  
  
2.  **\[Web\]** タブを選択し、次の図に示すように、**\[開始動作\]** の **\[ページを指定する\]** を選択して、ボックスに「`Service1.xamlx`」と入力します。  
  
     ![プロジェクト プロパティ ダイアログ](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     これにより、ASP.NET 開発サーバーの Service1.xamlx で定義されたサービスがホストされます。  
  
3.  Ctrl キーを押しながら F5 キーを押して、サービスを起動します。  次の図に示すように、ASP.NET 開発サーバーのアイコンが、デスクトップの右下側に表示されます。  
  
     ![ASP.NET Developer Server のアイコン](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     また、Internet Explorer に、サービスの WCF サービス ヘルプ ページが表示されます。  
  
     ![WCF ヘルプ ページ](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  「[方法: ワークフロー アプリケーションからサービスにアクセスする](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)」トピックに進み、このサービスを呼び出すワークフロー クライアントを作成します。  
  
## 参照  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [ワークフロー サービスのホストの概要](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)   
 [メッセージング アクティビティ](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
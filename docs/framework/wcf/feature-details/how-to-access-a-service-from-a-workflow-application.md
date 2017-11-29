---
title: "方法: ワークフロー アプリケーションからサービスにアクセスする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d2d87c045fe81e3f5bf2cb490e47fb5fbd6bc7a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>方法: ワークフロー アプリケーションからサービスにアクセスする
このトピックでは、ワークフロー コンソール アプリケーションからワークフロー サービスを呼び出す方法について説明します。 完了に依存している、[する方法: メッセージング アクティビティでワークフロー サービスを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)トピックです。 このトピックでは、ワークフロー アプリケーションからワークフロー サービスを呼び出す方法について説明していますが、同じ方法を使用して、どのような [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスでもワークフロー アプリケーションから呼び出すことができます。  
  
### <a name="create-a-workflow-console-application-project"></a>ワークフロー コンソール アプリケーション プロジェクトの作成  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動します。  
  
2.  作成した MyWFService プロジェクトを読み込む、[する方法: メッセージング アクティビティでワークフロー サービスを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)トピックです。  
  
3.  右クリックして、 **MyWFService**でソリューション、**ソリューション エクスプ ローラー**選択**追加**、**新しいプロジェクト**です。 選択**ワークフロー**で、**インストールされたテンプレート**と**ワークフロー コンソール アプリケーション**プロジェクトの種類の一覧からです。 次の図に示すように、プロジェクトに MyWFClient という名前を付け、既定の場所を使用します。  
  
     ![新しいプロジェクト ダイアログ ボックスを追加](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     をクリックして、 **OK**を消去するボタン、**新しいプロジェクト ダイアログの追加**。  
  
4.  プロジェクトが作成されると、Workflow1.xaml ファイルがデザイナーで開かれます。 クリックして、**ツールボックス**タブを開き、[ツールボックス] ウィンドウを開いておき、プッシュピンをクリックして既にでない場合、ツールボックスを開きます。  
  
5.  Ctrl キーを押しながら F5 キーを押して、サービスを起動します。 以前と同様に、ASP.NET 開発サーバーが起動され、Internet Explorer に WCF ヘルプ ページが表示されます。 このページの URI は、次の手順で使用する必要があるため、確認しておいてください。  
  
     ![WCF ヘルプ ページと URI を表示する IE](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  右クリックして、 **MyWFClient**でプロジェクトを**ソリューション エクスプ ローラー**選択**サービス参照の追加**です。 クリックして、 **Discover**サービスの現在のソリューションを検索するボタンをクリックします。 [サービス] ボックスで、Service1.xamlx の横にある三角形をクリックします。 Service1 の横にある三角形をクリックして、Service1 サービスによって実装されるコントラクトの一覧を表示します。 展開、 **Service1**内のノード、 **Services**  ボックスの一覧です。 Echo 操作が表示されます、 **Operations**次の図に示すように一覧表示します。  
  
     ![サービス参照 ダイアログ ボックスを追加](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")  
  
     既定の名前空間を保持し、をクリックして**OK**を消去する、**サービス参照の追加**ダイアログ。 次のダイアログ ボックスが表示されます。  
  
     ![サービス参照の追加の通知ダイアログ](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     をクリックして**OK**ダイアログ ボックスを閉じます。 次に、Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。 新しいセクションが追加されたツールボックスの通知と呼ばれる**MyWFClient.ServiceReference1.Activities**です。 この選択肢を展開して、次の図のように、追加されている Echo アクティビティを確認します。  
  
     ![ツールボックスのアクティビティをエコー](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  ドラッグ アンド ドロップ、 <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`アクティビティをデザイナー画面にします。 下、**制御フロー**ツールボックスのセクションです。  
  
8.  <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` 、フォーカスのあるアクティビティをクリックして、**変数**リンクし、という名前の文字列変数を追加`inString`です。 変数の既定値を付けます`"Hello, world"`という名前の文字列変数だけでなく`outString`次の図に示すようにします。  
  
     ![変数を追加する](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. ドラッグ アンド ドロップ、**エコー**にアクティビティ、 <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`です。 プロパティ ウィンドウで次のようにバインドします。、`inMsg`への引数、`inString`変数および`outMsg`への引数、`outString`変数次の図に示すようにします。 これにより、`inString` 変数の値を操作に渡し、戻り値を取得し、その戻り値を `outString` 変数に格納します。  
  
     ![変数への引数のバインド](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. ドラッグ アンド ドロップ、 **WriteLine**アクティビティの下、**エコー**サービス呼び出しによって返される文字列を表示するアクティビティ。 **WriteLine**にアクティビティがある、**プリミティブ**ツールボックス内のノードです。 バインド、**テキスト**の引数、 **WriteLine**アクティビティを`outString`」と入力して変数`outString`のテキスト ボックスに、 **WriteLine**アクティビティ。 この時点で、ワークフローは次の図のようになります。  
  
     ![完全なクライアント ワークフロー](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. MyWFService ソリューションを右クリックし **スタートアップ プロジェクトを設定しています.**.選択、**マルチ スタートアップ プロジェクト**ラジオ ボタンを選択**開始**内の各プロジェクト、**アクション**列の次の図に示すようにします。  
  
     ![スタートアップ プロジェクトのオプション](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")  
  
12. Ctrl キーを押しながら F5 キーを押し、サービスとクライアントの両方を起動します。 ASP.NET 開発サーバー サービスをホストする、Internet Explorer に WCF ヘルプ ページが表示されます、およびクライアント ワークフロー アプリケーションは、コンソール ウィンドウで起動し、(「こんにちは, world」)、サービスから返される文字列が表示されます。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [方法: メッセージング アクティビティでワークフロー サービスを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Web プロジェクトでワークフローから WCF サービスの使用](http://go.microsoft.com/fwlink/?LinkId=207725)

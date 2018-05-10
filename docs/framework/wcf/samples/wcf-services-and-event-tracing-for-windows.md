---
title: WCF サービスと Event Tracing for Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF サービスと Event Tracing for Windows
このサンプルでイベント トレース for Windows (ETW) イベントを出力する Windows Communication Foundation (WCF) での分析トレースを使用する方法を示します。 分析トレースは、実稼働環境で WCF サービスのトラブルシューティングが可能で、WCF スタック キー_ポイントで出力されるイベントです。  
  
 WCF サービスの分析トレースのトレースは、使用可能に実稼働環境でのパフォーマンスに影響を最小限にします。 これらのトレースは、ETW セッションにイベントとして出力されます。  
  
 このサンプルでは、基本的な WCF サービスでイベントが出力されますサービスからイベント ビューアーを使用して表示するイベント ログに含まれます。 WCF サービスからのイベントをリッスンする専用の ETW セッションを開始することもできます。 サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EtwAnalyticTraceSample.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     Web ブラウザーで、をクリックして **[calculator.svc]** です。 サービスの WSDL ドキュメントの URI がブラウザーに表示されます。 その URI をコピーします。  
  
     既定では、サービスの開始ポート 1378 で要求をリッスンしている (http://localhost:1378/Calculator.svc)です。  
  
4.  WCF テスト クライアント (WcfTestClient.exe) を実行します。  
  
     WCF テスト クライアント (WcfTestClient.exe) にあります、 \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir > \Common7\IDE\ WcfTestClient.exe (既定[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]インストール ディレクトリは C:\Program files \microsoft Visual Studio 10.0)。  
  
5.  WCF テスト クライアント内でを選択して、サービスを追加**ファイル**、し**サービスの追加**です。  
  
     入力ボックスにエンドポイントのアドレスを追加します。 既定値は、http://localhost:1378/Calculator.svc です。  
  
6.  イベント ビューアー アプリケーションを開きます。  
  
     サービスを呼び出す前に、イベント ビューアーを起動し、WCF サービスから生成された追跡イベントのイベント ログがリッスンしていることを確認してください。  
  
7.  **開始**メニューの **管理ツール**、し**イベント ビューアー**です。  有効にする、**分析**と**デバッグ**ログ。  
  
8.  イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。 右クリック**アプリケーション サーバー-アプリケーション****ビュー**、し**分析およびデバッグ ログ**です。  
  
     いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。  
  
9. 有効にする、**分析**ログ。  
  
     イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**ログの有効化**です。  
  
#### <a name="to-test-the-service"></a>サービスをテストするには  
  
1.  WCF テスト クライアントに戻りをダブルクリックして`Divide`分母が 0 を指定する既定値のままとします。  
  
     分母が 0 の場合、サービスからエラーがスローされます。  
  
2.  サービスから出力されたイベントを確認します。  
  
     イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**更新**です。  
  
     WCF 分析トレースのイベントがイベント ビューアーに表示されます。 サービスからエラーがスローされたため、イベント ビューアーにエラー トレース イベントが表示されていることに注意してください。  
  
3.  手順 1. と 2. を繰り返します。ただし、今度は有効な入力値を指定します。 `N2` パラメーターの値は、0 以外であれば任意の数字でかまいません。  
  
     分析チャネルを更新して、WCF イベントにエラー イベントが含まれていないことを確認します。  
  
 このサンプルでは、WCF サービスから出力される分析トレース イベントを示します。  
  
#### <a name="to-cleanup-optional"></a>クリーンアップするには (省略可能)  
  
1.  イベント ビューアーを開きます。  
  
2.  移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**ログの無効化**です。  
  
3.  移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**ログの消去**です。  
  
4.  選択、**オフ**イベントをクリアするにはオプションです。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)

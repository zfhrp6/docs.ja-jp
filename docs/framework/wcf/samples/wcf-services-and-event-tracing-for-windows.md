---
title: "WCF サービスと Event Tracing for Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb8924cc04442e3b9eda5e251e6dcdc57f5660c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF サービスと Event Tracing for Windows
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の分析トレースを使用して、Event Tracing for Windows (ETW) でイベントを出力する方法を示します。 分析トレースは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] スタック内のキー ポイントで出力されるイベントです。これにより、運用環境での [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのトラブルシューティングが可能になります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの分析トレースは、有効にしてもパフォーマンスに最小限の影響しか及ぼさないため、運用環境で使用することができます。 これらのトレースは、ETW セッションにイベントとして出力されます。  
  
 このサンプルには、サービスのイベントをイベント ログに出力する基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが含まれています。イベント ログは、イベント ビューアーを使用して表示できます。 また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのイベントをリッスンする専用の ETW セッションを開始することもできます。 サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EtwAnalyticTraceSample.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     Web ブラウザーで、をクリックして**[calculator.svc]**です。 サービスの WSDL ドキュメントの URI がブラウザーに表示されます。 その URI をコピーします。  
  
     既定では、ポート 1378 (http://localhost:1378/Calculator.svc) で要求のリッスンが開始されます。  
  
4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント (WcfTestClient.exe) を実行します。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]にテスト用クライアント (WcfTestClient.exe) がある、 \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir > \Common7\IDE\ WcfTestClient.exe (既定[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]インストール ディレクトリは C:\Program files \microsoft Visual Studio 10.0)。  
  
5.  内で、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]テスト クライアントを選択して、サービスを追加**ファイル**、し**サービスの追加**です。  
  
     入力ボックスにエンドポイントのアドレスを追加します。 既定値は http://localhost:1378/Calculator.svc です。  
  
6.  イベント ビューアー アプリケーションを開きます。  
  
     サービスを呼び出す前に、イベント ビューアーを起動し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。  
  
7.  **開始**メニューの **管理ツール**、し**イベント ビューアー**です。  有効にする、**分析**と**デバッグ**ログ。  
  
8.  イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。 右クリック**アプリケーション サーバー-アプリケーション****ビュー**、し**分析およびデバッグ ログ**です。  
  
     いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。  
  
9. 有効にする、**分析**ログ。  
  
     イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**ログの有効化**です。  
  
#### <a name="to-test-the-service"></a>サービスをテストするには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントに戻り、[`Divide`] をダブルクリックします。既定値のまま、分母を 0 にしておきます。  
  
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
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)

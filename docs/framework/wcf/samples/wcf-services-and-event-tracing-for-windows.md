---
title: "WCF サービスと Event Tracing for Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# WCF サービスと Event Tracing for Windows
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の分析トレースを使用して、Event Tracing for Windows \(ETW\) でイベントを出力する方法を示します。  分析トレースは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] スタック内のキー ポイントで出力されるイベントです。これにより、運用環境での [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのトラブルシューティングが可能になります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの分析トレースは、有効にしてもパフォーマンスに最小限の影響しか及ぼさないため、運用環境で使用することができます。  これらのトレースは、ETW セッションにイベントとして出力されます。  
  
 このサンプルには、サービスのイベントをイベント ログに出力する基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが含まれています。イベント ログは、イベント ビューアーを使用して表示できます。  また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのイベントをリッスンする専用の ETW セッションを開始することもできます。  サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EtwAnalyticTraceSample.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     Web ブラウザーで、**\[Calculator.svc\]** をクリックします。  サービスの WSDL ドキュメントの URI がブラウザーに表示されます。  その URI をコピーします。  
  
     既定では、ポート 1378 \(http:\/\/localhost:1378\/Calculator.svc\) で要求のリッスンが開始されます。  
  
4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント \(WcfTestClient.exe\) を実行します。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント \(WcfTestClient.exe\) は \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] のインストール ディレクトリ\>\\Common7\\IDE\\WcfTestClient.exe にあります \([!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] の既定のインストール ディレクトリは C:\\Program Files\\Microsoft Visual Studio 10.0 です\)。  
  
5.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントで、**\[ファイル\]** メニューの **\[サービスの追加\]** をクリックしてサービスを追加します。  
  
     入力ボックスにエンドポイントのアドレスを追加します。  既定値は http:\/\/localhost:1378\/Calculator.svc です。  
  
6.  イベント ビューアー アプリケーションを開きます。  
  
     サービスを呼び出す前に、イベント ビューアーを起動し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。  
  
7.  **\[スタート\]** メニューから、**\[管理ツール\]**、**\[イベント ビューアー\]** の順に選択します。  **\[分析\]** ログと **\[デバッグ\]** ログを有効にします。  
  
8.  イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。  **\[アプリケーション サーバー \- アプリケーション\]** を右クリックし、**\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。  
  
     **\[分析およびデバッグ ログの表示\]** オプションがオンになっていることを確認します。  
  
9. **\[分析\]** ログを有効にします。  
  
     イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。  **\[分析\]** を右クリックし、**\[ログを有効にする\]** をクリックします。  
  
#### サービスをテストするには  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントに戻り、\[`Divide`\] をダブルクリックします。既定値のまま、分母を 0 にしておきます。  
  
     分母が 0 の場合、サービスからエラーがスローされます。  
  
2.  サービスから出力されたイベントを確認します。  
  
     イベント ビューアーに戻り、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。  **\[分析\]** を右クリックし、**\[更新\]** をクリックします。  
  
     WCF 分析トレースのイベントがイベント ビューアーに表示されます。  サービスからエラーがスローされたため、イベント ビューアーにエラー トレース イベントが表示されていることに注意してください。  
  
3.  手順 1. と 2. を繰り返します。ただし、今度は有効な入力値を指定します。  `N2` パラメーターの値は、0 以外であれば任意の数字でかまいません。  
  
     分析チャネルを更新して、WCF イベントにエラー イベントが含まれていないことを確認します。  
  
 このサンプルでは、WCF サービスから出力される分析トレース イベントを示します。  
  
#### クリーンアップするには \(省略可能\)  
  
1.  イベント ビューアーを開きます。  
  
2.  **\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。  **\[分析\]** を右クリックし、**\[ログの無効化\]** を選択します。  
  
3.  **\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。  **\[分析\]** を右クリックし、**\[ログのクリア\]** を選択します。  
  
4.  **\[クリア\]** をクリックしてイベントをクリアします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
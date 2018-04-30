---
title: WCF 分析トレース
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57e3ee18848031bce8ffbb54d26353fe36ee1def
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-analytic-tracing"></a>WCF 分析トレース
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] が [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] の ETW に書き込む分析トレースのストリームに独自のトレース イベントを追加する方法を示します。 分析トレースは、パフォーマンスを低下させずに簡単にサービスを確認できるようにするためのものです。 このサンプルでは、<xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API を使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと統合されるイベントを記述する方法を示します。  
  
 詳細については、 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> Api を参照してください<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>です。  
  
 Windows イベント トレーシングの詳細については、次を参照してください。[デバッグを向上させると、パフォーマンスのチューニングを ETW](http://go.microsoft.com/fwlink/?LinkId=166488)です。  
  
## <a name="disposing-eventprovider"></a>EventProvider の破棄  
 このサンプルでは、<xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> を実装した <xref:System.IDisposable?displayProperty=nameWithType> クラスを使用します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのトレースを実装する場合、サービスの有効期間に <xref:System.Diagnostics.Eventing.EventProvider> のリソースを使用することがあります。 そのため、読みやすくするためにも、このサンプルでは、ラップされた <xref:System.Diagnostics.Eventing.EventProvider> を破棄しません。 何かの理由で、サービスに対して別のトレースの要件を設定し、このリソースを破棄しなければならない場合は、アンマネージ リソースの破棄に関するベスト プラクティスに従ってこのサンプルを変更してください。 アンマネージ リソースを破棄に関する詳細については、次を参照してください。 [Dispose メソッドの実装](http://go.microsoft.com/fwlink/?LinkId=166436)です。  
  
## <a name="self-hosting-vs-web-hosting"></a>自己ホスト型と Web ホスト  
 Web ホスト サービスの場合は、WCF の分析トレースは、"hostreference"をトレースの出力は、サービスの識別に使用される、フィールドを提供します。 拡張可能なユーザー トレースをこのモデルに加えることができます。このサンプルで、そのためのベスト プラクティスを示します。 Web ホストの形式の参照時にパイプ '&#124;' 文字が実際には、その結果の表示文字列は、次のいずれかを指定できます。  
  
-   アプリケーションがルート以外にある場合  
  
     \<SiteName >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   アプリケーションがルートにある場合  
  
     \<SiteName >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 自己ホスト型サービスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]の分析トレースで"HostReference"フィールドは設定されません。 このサンプルの `WCFUserEventProvider` クラスは、自己ホスト型サービスで使用した場合も同じように動作します。  
  
## <a name="custom-event-details"></a>カスタム イベントの詳細  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の ETW イベント プロバイダー マニフェストには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの作成者がサービス コード内から生成できるように設計された 3 つのイベントが定義されています。 次の表に、その 3 つのイベントの概要を示します。  
  
|event|説明|イベント ID|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|このイベントは、問題以外の通知すべき処理がサービスで発生した場合に生成します。 たとえば、データベースの呼び出しに成功した後にイベントを生成します。|301|  
|UserDefinedWarningOccurred|このイベントは、後続の処理でエラーになる可能性がある問題が発生した場合に生成します。 たとえば、データベースの呼び出しが失敗したものの、冗長なデータ ストアを使用して回復できた場合に警告イベントを生成します。|302|  
|UserDefinedErrorOccurred|このイベントは、サービスが想定どおりに動作しなかった場合に生成します。 たとえば、データベースの呼び出しが失敗し、別の場所からもデータを取得できなかった場合にイベントを生成します。|303|  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、WCFAnalyticTracingExtensibility.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     Web ブラウザーで、をクリックして **[calculator.svc]** です。 サービスの WSDL ドキュメントの URI がブラウザーに表示されます。 その URI をコピーします。  
  
4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント (WcfTestClient.exe) を実行します。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]にテスト用クライアント (WcfTestClient.exe) がある、 \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir > \Common7\IDE\ WcfTestClient.exe (既定[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]インストール ディレクトリは C:\Program files \microsoft Visual Studio 10.0)。  
  
5.  内で、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]テスト クライアントを選択して、サービスを追加**ファイル**、し**サービスの追加**です。  
  
     入力ボックスにエンドポイントのアドレスを追加します。  
  
6.  をクリックして**OK**ダイアログ ボックスを閉じます。  
  
     下の左ペインで、ICalculator サービスが追加された**マイ サービス プロジェクト**です。  
  
7.  イベント ビューアー アプリケーションを開きます。  
  
     サービスを呼び出す前に、イベント ビューアーを起動し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。  
  
8.  **開始**メニューの **管理ツール**、し**イベント ビューアー**です。 有効にする、**分析**と**デバッグ**ログ。  
  
9. イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。 右クリック**アプリケーション サーバー-アプリケーション****ビュー**、し**分析およびデバッグ ログ**です。  
  
     いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。 有効にする、**分析**ログ。  
  
     イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**、し**分析**です。 右クリック**分析**選択**ログの有効化**です。  
  
10. WCF テスト クライアントを使用してサービスをテストします。  
  
    1.  WCF テスト クライアントでダブルクリック**Add()** ICalculator サービス ノードの下。  
  
         **Add()** メソッドが 2 つのパラメーターと共に右ペインに表示されます。  
  
    2.  最初のパラメーターに「2」と入力し、2 番目のパラメーターに「3」と入力します。  
  
    3.  をクリックして**Invoke**メソッドを呼び出します。  
  
11. 移動して、**イベント ビューアー**既に開いているウィンドウ。 移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。  
  
12. 右クリックし、**分析**ノード**更新**です。  
  
     右ペインにイベントが表示されます。  
  
13. ID が 303 のイベントを探してダブルクリックして開き、内容を確認します。  
  
     このイベントは、によって生成されますが、 `Add()` ICalculator サービスのメソッドと等しい、ペイロードは"2 + 3 = 5"です。  
  
#### <a name="to-clean-up-optional"></a>クリーンアップするには (省略可能)  
  
1.  開いている**イベント ビューアー**です。  
  
2.  移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**ログの無効化**です。  
  
3.  移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**、し**分析**です。 右クリック**分析**選択**ログの消去**です。  
  
4.  をクリックして**オフ**イベントをクリアします。  
  
## <a name="known-issue"></a>既知の問題  
 既知の問題がある、**イベント ビューアー** ETW イベントのデコードに失敗する可能性があります。 表示されているエラー メッセージが表示することがあります:"イベント ID の説明\<id > ソースから Microsoft Windows アプリケーション サーバー-アプリケーションが見つかりません。 このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが破損しています。 インストールするか、ローカル コンピューター上のコンポーネントを修復します。" このエラーが発生した場合は、選択**更新**から、**アクション**メニュー。 これにより、イベントが正常にデコードされます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)

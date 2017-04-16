---
title: "WCF 分析トレース | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# WCF 分析トレース
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] が [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] の ETW に書き込む分析トレースのストリームに独自のトレース イベントを追加する方法を示します。分析トレースは、パフォーマンスを低下させずに簡単にサービスを確認できるようにするためのものです。このサンプルでは、<xref:System.Diagnostics.Eventing?displayProperty=fullName> API を使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと統合されるイベントを記述する方法を示します。  
  
 <xref:System.Diagnostics.Eventing?displayProperty=fullName> API [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「<xref:System.Diagnostics.Eventing?displayProperty=fullName>」を参照してください。  
  
 Windows でのイベントのトレースの詳細については、「[ETW によりデバッグおよびパフォーマンス調整を改善する](http://go.microsoft.com/fwlink/?LinkId=166488)」を参照してください。  
  
## EventProvider の破棄  
 このサンプルでは、<xref:System.IDisposable?displayProperty=fullName> を実装した <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=fullName> クラスを使用します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのトレースを実装する場合、サービスの有効期間に <xref:System.Diagnostics.Eventing.EventProvider> のリソースを使用することがあります。そのため、読みやすくするためにも、このサンプルでは、ラップされた <xref:System.Diagnostics.Eventing.EventProvider> を破棄しません。何かの理由で、サービスに対して別のトレースの要件を設定し、このリソースを破棄しなければならない場合は、アンマネージ リソースの破棄に関するベスト プラクティスに従ってこのサンプルを変更してください。アンマネージ リソースの破棄[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Dispose メソッドの実装](http://go.microsoft.com/fwlink/?LinkId=166436)」を参照してください。  
  
## 自己ホスト型と Web ホスト型  
 Web ホスト型サービスの場合は、WCF の分析トレースで "HostReference" というフィールドが設定され、そのフィールドを使用してトレースの生成元のサービスを識別します。拡張可能なユーザー トレースをこのモデルに加えることができます。このサンプルで、そのためのベスト プラクティスを示します。結果の文字列にパイプ文字 '&#124;' が実際に表示さるときには、Web ホストの参照の形式は次のいずれかになります。  
  
-   アプリケーションがルート以外にある場合  
  
     \<サイト名\>\<アプリケーション仮想パス\>&#124;\<サービス仮想パス\>&#124;\<サービス名\>  
  
-   アプリケーションがルートにある場合  
  
     \<サイト名\>&#124;\<サービス仮想パス\>&#124;\<サービス名\>  
  
 自己ホスト型サービスの場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の分析トレースで "HostReference" フィールドが設定されません。このサンプルの `WCFUserEventProvider` クラスは、自己ホスト型サービスで使用した場合も同じように動作します。  
  
## カスタム イベントの詳細  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の ETW イベント プロバイダー マニフェストには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの作成者がサービス コード内から生成できるように設計された 3 つのイベントが定義されています。次の表に、その 3 つのイベントの概要を示します。  
  
|イベント|説明|イベント ID|  
|----------|--------|-------------|  
|UserDefinedInformationEventOccurred|このイベントは、問題以外の通知すべき処理がサービスで発生した場合に生成します。たとえば、データベースの呼び出しに成功した後にイベントを生成します。|301|  
|UserDefinedWarningOccurred|このイベントは、後続の処理でエラーになる可能性がある問題が発生した場合に生成します。たとえば、データベースの呼び出しが失敗したものの、冗長なデータ ストアを使用して回復できた場合に警告イベントを生成します。|302|  
|UserDefinedErrorOccurred|このイベントは、サービスが想定どおりに動作しなかった場合に生成します。たとえば、データベースの呼び出しが失敗し、別の場所からもデータを取得できなかった場合にイベントを生成します。|303|  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、WCFAnalyticTracingExtensibility.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     Web ブラウザーで、**\[Calculator.svc\]** をクリックします。サービスの WSDL ドキュメントの URI がブラウザーに表示されます。その URI をコピーします。  
  
4.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント \(WcfTestClient.exe\) を実行します。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント \(WcfTestClient.exe\) は \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] のインストール ディレクトリ\>\\Common7\\IDE\\WcfTestClient.exe にあります \([!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] の既定のインストール ディレクトリは C:\\Program Files\\Microsoft Visual Studio 10.0 です\)。  
  
5.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントで、**\[ファイル\]** メニューの **\[サービスの追加\]** をクリックしてサービスを追加します。  
  
     入力ボックスにエンドポイントのアドレスを追加します。  
  
6.  **\[OK\]** をクリックしてダイアログ ボックスを閉じます。  
  
     ICalculator サービスが、左ペインの **\[マイ サービス プロジェクト\]** の下に追加されます。  
  
7.  イベント ビューアー アプリケーションを開きます。  
  
     サービスを呼び出す前に、イベント ビューアーを起動し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。  
  
8.  **\[スタート\]** メニューから、**\[管理ツール\]**、**\[イベント ビューアー\]** の順に選択します。**\[分析\]** ログと **\[デバッグ\]** ログを有効にします。  
  
9. イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[アプリケーション サーバー \- アプリケーション\]** を右クリックし、**\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。  
  
     **\[分析およびデバッグ ログの表示\]** オプションがオンになっていることを確認します。**\[分析\]** ログを有効にします。  
  
     イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]**、**\[アプリケーション サーバー \- アプリケーション\]** の順に選択して **\[分析\]** に移動します。**\[分析\]** を右クリックし、**\[ログを有効にする\]** を選択します。  
  
10. WCF テスト クライアントを使用してサービスをテストします。  
  
    1.  WCF テスト クライアントで、ICalculator サービス ノードの下の **\[Add\(\)\]** をダブルクリックします。  
  
         **Add\(\)** メソッドが、2 つのパラメーターと共に右ペインに表示されます。  
  
    2.  最初のパラメーターに「2」と入力し、2 番目のパラメーターに「3」と入力します。  
  
    3.  **\[呼び出し\]** をクリックしてメソッドを呼び出します。  
  
11. 既に開いている **\[イベント ビューアー\]** ウィンドウに移動します。**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。  
  
12. **\[分析\]** ノードを右クリックし、**\[最新の情報に更新\]** をクリックします。  
  
     右ペインにイベントが表示されます。  
  
13. ID が 303 のイベントを探してダブルクリックして開き、内容を確認します。  
  
     このイベントは、ICalculator サービスの `Add()` メソッドによって生成されたもので、ペイロードは "2\+3\=5" になります。  
  
#### クリーンアップするには \(省略可能\)  
  
1.  **イベント ビューアー**を開きます。  
  
2.  **\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[分析\]** を右クリックし、**\[ログの無効化\]** を選択します。  
  
3.  **\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]**、**\[アプリケーション サーバー \- アプリケーション\]** の順に選択して **\[分析\]** に移動します。**\[分析\]** を右クリックし、**\[ログのクリア\]** を選択します。  
  
4.  **\[クリア\]** をクリックしてログをクリアします。  
  
## 既知の問題  
 **イベント ビューアー**の既知の問題により、ETW イベントをデコードできない場合があります。その場合、"ソース "Microsoft\-Windows\-Application Server\-Applications" からのイベント ID \<id\> の説明が見つかりません。このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが壊れています。ローカル コンピューターにコンポーネントをインストールするか、コンポーネントを修復してください。" というエラー メッセージが表示されます。このエラーが発生した場合は、**\[操作\]** メニューの **\[最新の情報に更新\]** をクリックしてください。これにより、イベントが正常にデコードされます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
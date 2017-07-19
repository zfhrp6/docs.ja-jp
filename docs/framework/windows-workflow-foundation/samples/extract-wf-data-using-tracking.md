---
title: "追跡を使用した WF データの抽出 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 追跡を使用した WF データの抽出
このサンプルでは、ワークフロー追跡を使用して、アクティビティからワークフロー変数と引数を抽出する方法を示します。また、追跡レコードへの注釈の追加、およびカスタム追跡レコード内のデータ ペイロードの抽出の例も示します。このサンプルでは、ワークフローからデータを抽出するために Event Tracing for Windows \(ETW\) 追跡参加要素を使用します。  
  
## サンプルの詳細  
 [!INCLUDE[wf](../../../../includes/wf-md.md)] には、ワークフロー インスタンスの実行を視覚的に示す追跡機能が用意されています。追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。このワークフロー追跡レコードと共に、ワークフロー インスタンス内のデータをワークフローから抽出することができます。追跡レコードから抽出できるデータの種類の詳細を以下に示します。  
  
1.  アクティビティ内のワークフロー変数とアクティビティの実行時の追跡レコード。  
  
     ワークフロー変数を抽出するには、抽出する変数をプロファイルで指定します。抽出する変数は、`ActivityStateQueries` でのみ指定できます。アクティビティからワークフロー変数を抽出するために使用する追跡プロファイルのコード例を次に示します。  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  アクティビティ引数とアクティビティ状態の追跡レコード。  
  
     引数は、アクティビティとのデータ フローの方法を定義します。抽出する引数は、<xref:System.Activities.Tracking.ActivityStateQuery> を使用して指定します。`Value` 引数を抽出する追跡プロファイルのコード例を次に示します。  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  注釈は、出力される追跡レコードに追加できるキーと値のペアです。  
  
     注釈は、追跡レコードのタグ付け機構として機能します。追跡プロファイルを通して追跡レコードに追加され、どの種類のワークフロー追跡クエリにも追加できます。追跡レコードに注釈を追加する方法を示す追跡プロファイルのコード例を次に示します。  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  カスタム追跡レコードは、ユーザー定義のアクティビティから出力されます。  
  
     カスタム追跡レコードは、対象のアクティビティ内で定義されたペイロード データを伝達できます。追跡プロファイルでカスタム追跡レコードを定期受信すると、追跡レコード内のペイロードを抽出することができます。カスタム追跡レコードを抽出するには、カスタムの <xref:System.Activities.Tracking.TrackingQuery> を使用します。カスタム追跡レコードをそのペイロードと共に抽出する追跡プロファイルのコード例を次に示します。  
  
    ```  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 このサンプルでは、Web.config で指定されたプロファイルを使用して、変数、引数、およびカスタム レコードを抽出し、注釈を追加する例を示しています。サンプルのワークフロー サービスでは、`<etwTracking>` 動作要素を追加して追跡を有効にしています。`ExtractWorkflowVariables` 追跡プロファイルの追跡を有効にするコード例を次に示します。  
  
```  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WFStockPriceApplication.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
     ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。  
  
4.  ブラウザーで、StockPriceService.xamlx をクリックします。  
  
5.  ブラウザーに、\[StockPriceService\] ページが表示され、ローカル サービスの WSDL アドレスが示されます。このアドレスをコピーします。  
  
     ローカル サービスの WSDL アドレスの例を次に示します。`http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  サービスを呼び出す前に、イベント ビューアーを起動し、ワークフロー サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。  
  
7.  **\[スタート\]** メニューから、**\[管理ツール\]**、**\[イベント ビューアー\]** の順に選択します。  
  
8.  イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]** の順に選択して **\[Microsoft\]** に移動します。**\[Microsoft\]** を右クリックし、**\[表示\]**、**\[分析およびデバッグ ログの表示\]** の順にクリックします。  
  
     **\[分析およびデバッグ ログの表示\]** オプションがオンになっていることを確認します。  
  
9. イベント ビューアーのツリー ビューで、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[分析\]** を右クリックし、**\[ログを有効にする\]** を選択します。  
  
10. [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアントを開きます。  
  
     WCF テスト クライアント \(WcfTestClient.exe\) は \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のインストール フォルダー\>\\Common7\\IDE\\ フォルダーにあります。  
  
     [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] の既定のインストール フォルダーは C:\\Program Files\\Microsoft Visual Studio 10.0 です。  
  
11. WCF テスト クライアントで、**\[ファイル\]** メニューの **\[サービスの追加\]** をクリックします。  
  
     前の手順でコピーしたローカル サービスの WSDL アドレスを入力ボックスに追加します。  
  
12. WCF テスト クライアントで、`GetStockPrice` をダブルクリックします。  
  
     `GetStockPrice` メソッドが開きます。この要求はパラメーターを 1 つ受け取ります。値 **Contoso** を使用します。  
  
13. **\[起動\]** をクリックします。  
  
14. イベント ビューアーに戻り、**\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[分析\]** を右クリックし、**\[更新\]** を選択します。ワークフロー イベントのイベント ID の範囲は 100 ～ 199 です。  
  
     イベントには、イベント ビューアーで表示できる注釈、変数、引数、およびカスタム追跡レコードが含まれます。  
  
## イベント ビューアーでのクリーンアップ  
 イベント ログの分析チャネルは、次の手順に従ってイベント ビューアーでクリーンアップできます。  
  
#### クリーンアップするには \(省略可能\)  
  
1.  イベント ビューアーを開きます。  
  
2.  **\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[分析\]** を右クリックし、**\[ログの無効化\]** を選択します。  
  
3.  **\[イベント ビューアー\]**、**\[アプリケーションとサービス ログ\]**、**\[Microsoft\]**、**\[Windows\]** の順に選択して **\[アプリケーション サーバー \- アプリケーション\]** に移動します。**\[分析\]** を右クリックし、**\[ログのクリア\]** を選択します。  
  
     **\[クリア\]** オプションを選択してイベントをクリアします。  
  
## 既知の問題  
  
> [!NOTE]
>  イベント ビューアーの既知の問題により、ETW イベントをデコードできない場合があります。その場合、次のようなエラー メッセージが表示されます。  
>   
>  `ソース "Microsoft-Windows-Application Server-Applications" からのイベント ID <id> の説明が見つかりません。このイベントを発生させるコンポーネントがローカル コンピューターにインストールされていないか、インストールが壊れています。ローカル コンピューターにコンポーネントをインストールするか、コンポーネントを修復してください。`  
>   
>  このエラーが発生した場合は、操作ウィンドウで **\[最新の情報に更新\]** をクリックしてください。これにより、イベントが正常にデコードされます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
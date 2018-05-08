---
title: 追跡を使用した WF データの抽出
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: 22b147521d4ce0c72fadfb7adc81e05f10ce52b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="extract-wf-data-using-tracking"></a>追跡を使用した WF データの抽出
このサンプルでは、ワークフロー追跡を使用して、アクティビティからワークフロー変数と引数を抽出する方法を示します。 また、追跡レコードへの注釈の追加、およびカスタム追跡レコード内のデータ ペイロードの抽出の例も示します。 このサンプルでは、ワークフローからデータを抽出するために Event Tracing for Windows (ETW) 追跡参加要素を使用します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 Windows Workflow Foundation (WF) は、ワークフロー インスタンスの実行を把握するための追跡を提供します。 追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。 このワークフロー追跡レコードと共に、ワークフロー インスタンス内のデータをワークフローから抽出することができます。 追跡レコードから抽出できるデータの種類の詳細を以下に示します。  
  
1.  アクティビティ内のワークフロー変数とアクティビティの実行時の追跡レコード。  
  
     ワークフロー変数を抽出するには、抽出する変数をプロファイルで指定します。 抽出する変数は、`ActivityStateQueries` でのみ指定できます。 アクティビティからワークフロー変数を抽出するために使用する追跡プロファイルのコード例を次に示します。  
  
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
  
     引数は、アクティビティとのデータ フローの方法を定義します。 抽出する引数は、<xref:System.Activities.Tracking.ActivityStateQuery> を使用して指定します。`Value` 引数を抽出する追跡プロファイルのコード例を次に示します。  
  
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
  
     注釈は、追跡レコードのタグ付け機構として機能します。 追跡プロファイルを通して追跡レコードに追加され、 どの種類のワークフロー追跡クエリにも追加できます。 追跡レコードに注釈を追加する方法を示す追跡プロファイルのコード例を次に示します。  
  
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
  
     カスタム追跡レコードは、対象のアクティビティ内で定義されたペイロード データを伝達できます。 追跡プロファイルでカスタム追跡レコードを定期受信すると、追跡レコード内のペイロードを抽出することができます。 カスタム追跡レコードを抽出するには、カスタムの <xref:System.Activities.Tracking.TrackingQuery> を使用します。 カスタム追跡レコードをそのペイロードと共に抽出する追跡プロファイルのコード例を次に示します。  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 このサンプルでは、Web.config で指定されたプロファイルを使用して、変数、引数、およびカスタム レコードを抽出し、注釈を追加する例を示しています。サンプルのワークフロー サービスでは、`<etwTracking>` 動作要素を追加して追跡を有効にしています。 `ExtractWorkflowVariables` 追跡プロファイルの追跡を有効にするコード例を次に示します。  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WFStockPriceApplication.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、F5 キーを押します。  
  
     ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。  
  
4.  ブラウザーで、StockPriceService.xamlx をクリックします。  
  
5.  ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。 このアドレスをコピーします。  
  
     ローカル サービスの WSDL アドレスの例を次に示します。 `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  サービスを呼び出す前に、イベント ビューアーを起動し、ワークフロー サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。  
  
7.  **開始**メニューの **管理ツール**し**イベント ビューアー**です。  
  
8.  イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、および**Microsoft**です。 右クリック**Microsoft**選択**ビュー**し**分析およびデバッグ ログ**です。  
  
     いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。  
  
9. イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**ログの有効化**です。  
  
10. [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアントを開きます。  
  
     WCF テスト クライアント (WcfTestClient.exe) にあります、 \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]インストール フォルダー > \Common7\IDE\ フォルダーです。  
  
     [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] の既定のインストール フォルダーは C:\Program Files\Microsoft Visual Studio 10.0 です。  
  
11. WCF テスト クライアントで、次のように選択します。**サービスの追加**から、**ファイル**メニュー。  
  
     前の手順でコピーしたローカル サービスの WSDL アドレスを入力ボックスに追加します。  
  
12. WCF テスト クライアントで、`GetStockPrice` をダブルクリックします。  
  
     `GetStockPrice` メソッドが開きます。 この要求はパラメーターを 1 つ受け取ります。 値を使用して**Contoso**です。  
  
13. をクリックして**呼び出す**です。  
  
14. イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**です。 右クリック**分析**選択**更新**です。 ワークフロー イベントのイベント ID の範囲は 100 ～ 199 です。  
  
     イベントには、イベント ビューアーで表示できる注釈、変数、引数、およびカスタム追跡レコードが含まれます。  
  
## <a name="cleaning-up-in-the-event-viewer"></a>イベント ビューアーでのクリーンアップ  
 イベント ログの分析チャネルは、次の手順に従ってイベント ビューアーでクリーンアップできます。  
  
#### <a name="to-clean-up-optional"></a>クリーンアップするには (省略可能)  
  
1.  イベント ビューアーを開きます。  
  
2.  移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。 右クリック**分析**選択**ログの無効化**です。  
  
3.  移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。 右クリック**分析**選択**ログの消去**です。  
  
     選択、**オフ**イベントをクリアするにはオプションです。  
  
## <a name="known-issue"></a>既知の問題  
  
> [!NOTE]
>  イベント ビューアーの既知の問題により、ETW イベントをデコードできない場合があります。 その場合、次のようなエラー メッセージが表示されます。  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  このエラーが発生した場合はクリックして**更新**[操作] ウィンドウ。 これにより、イベントが正常にデコードされます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)

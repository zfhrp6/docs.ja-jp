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
# <a name="extract-wf-data-using-tracking"></a><span data-ttu-id="885e4-102">追跡を使用した WF データの抽出</span><span class="sxs-lookup"><span data-stu-id="885e4-102">Extract WF Data using Tracking</span></span>
<span data-ttu-id="885e4-103">このサンプルでは、ワークフロー追跡を使用して、アクティビティからワークフロー変数と引数を抽出する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-103">This sample demonstrates how to use workflow tracking to extract workflow variables and arguments from activities.</span></span> <span data-ttu-id="885e4-104">また、追跡レコードへの注釈の追加、およびカスタム追跡レコード内のデータ ペイロードの抽出の例も示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-104">It also shows the addition of annotations to tracking records and the extraction of data payload within custom tracking records.</span></span> <span data-ttu-id="885e4-105">このサンプルでは、ワークフローからデータを抽出するために Event Tracing for Windows (ETW) 追跡参加要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="885e4-105">The sample uses the Event Tracing for Windows (ETW) tracking participant to extract data from the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="885e4-106">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="885e4-106">Sample Details</span></span>  
 <span data-ttu-id="885e4-107">Windows Workflow Foundation (WF) は、ワークフロー インスタンスの実行を把握するための追跡を提供します。</span><span class="sxs-lookup"><span data-stu-id="885e4-107">Windows Workflow Foundation (WF) provides tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="885e4-108">追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="885e4-108">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="885e4-109">このワークフロー追跡レコードと共に、ワークフロー インスタンス内のデータをワークフローから抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="885e4-109">Along with the workflow tracking records, data within the workflow instance can be extracted from the workflow.</span></span> <span data-ttu-id="885e4-110">追跡レコードから抽出できるデータの種類の詳細を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-110">The following list details the types of data that can be extracted from tracking records:</span></span>  
  
1.  <span data-ttu-id="885e4-111">アクティビティ内のワークフロー変数とアクティビティの実行時の追跡レコード。</span><span class="sxs-lookup"><span data-stu-id="885e4-111">Workflow variables within an activity and tracking records during activity execution.</span></span>  
  
     <span data-ttu-id="885e4-112">ワークフロー変数を抽出するには、抽出する変数をプロファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="885e4-112">To extract workflow variables, the variables to be extracted are specified in a profile.</span></span> <span data-ttu-id="885e4-113">抽出する変数は、`ActivityStateQueries` でのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="885e4-113">Variables to be extracted can only be specified with `ActivityStateQueries`.</span></span> <span data-ttu-id="885e4-114">アクティビティからワークフロー変数を抽出するために使用する追跡プロファイルのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-114">The following code example demonstrates a tracking profile used to extract the workflow variable from an activity.</span></span>  
  
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
  
2.  <span data-ttu-id="885e4-115">アクティビティ引数とアクティビティ状態の追跡レコード。</span><span class="sxs-lookup"><span data-stu-id="885e4-115">Activity arguments and activity state tracking records.</span></span>  
  
     <span data-ttu-id="885e4-116">引数は、アクティビティとのデータ フローの方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="885e4-116">Arguments define the way data flows in or out of an activity.</span></span> <span data-ttu-id="885e4-117">抽出する引数は、<xref:System.Activities.Tracking.ActivityStateQuery> を使用して指定します。`Value` 引数を抽出する追跡プロファイルのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-117">Arguments to be extracted are specified using an <xref:System.Activities.Tracking.ActivityStateQuery>.The following code example is a tracking profile that extracts the `Value` argument.</span></span>  
  
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
  
3.  <span data-ttu-id="885e4-118">注釈は、出力される追跡レコードに追加できるキーと値のペアです。</span><span class="sxs-lookup"><span data-stu-id="885e4-118">Annotations are key/value pairs that can be added to any tracking record that is emitted.</span></span>  
  
     <span data-ttu-id="885e4-119">注釈は、追跡レコードのタグ付け機構として機能します。</span><span class="sxs-lookup"><span data-stu-id="885e4-119">Annotations serve as a tagging mechanism for tracking records.</span></span> <span data-ttu-id="885e4-120">追跡プロファイルを通して追跡レコードに追加され、</span><span class="sxs-lookup"><span data-stu-id="885e4-120">Annotations are added to tracking records through a tracking profile.</span></span> <span data-ttu-id="885e4-121">どの種類のワークフロー追跡クエリにも追加できます。</span><span class="sxs-lookup"><span data-stu-id="885e4-121">Annotations can be added to any type of a workflow tracking query.</span></span> <span data-ttu-id="885e4-122">追跡レコードに注釈を追加する方法を示す追跡プロファイルのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-122">The following code example is a tracking profile that shows how an annotation can be added to a tracking record.</span></span>  
  
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
  
4.  <span data-ttu-id="885e4-123">カスタム追跡レコードは、ユーザー定義のアクティビティから出力されます。</span><span class="sxs-lookup"><span data-stu-id="885e4-123">Custom tracking records are emitted from user-defined activities.</span></span>  
  
     <span data-ttu-id="885e4-124">カスタム追跡レコードは、対象のアクティビティ内で定義されたペイロード データを伝達できます。</span><span class="sxs-lookup"><span data-stu-id="885e4-124">Custom tracking records can carry payload data defined within this activity.</span></span> <span data-ttu-id="885e4-125">追跡プロファイルでカスタム追跡レコードを定期受信すると、追跡レコード内のペイロードを抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="885e4-125">Subscribing for custom tracking records in a tracking profile allows the extraction of the payload within the tracking record.</span></span> <span data-ttu-id="885e4-126">カスタム追跡レコードを抽出するには、カスタムの <xref:System.Activities.Tracking.TrackingQuery> を使用します。</span><span class="sxs-lookup"><span data-stu-id="885e4-126">The custom tracking records can be extracted with custom a <xref:System.Activities.Tracking.TrackingQuery>.</span></span> <span data-ttu-id="885e4-127">カスタム追跡レコードをそのペイロードと共に抽出する追跡プロファイルのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-127">The following code example is a tracking profile that extracts a custom tracking record along with its payload.</span></span>  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 <span data-ttu-id="885e4-128">このサンプルでは、Web.config で指定されたプロファイルを使用して、変数、引数、およびカスタム レコードを抽出し、注釈を追加する例を示しています。サンプルのワークフロー サービスでは、`<etwTracking>` 動作要素を追加して追跡を有効にしています。</span><span class="sxs-lookup"><span data-stu-id="885e4-128">The sample demonstrates the extraction of a variables, arguments, custom records and adding annotations using a profile specified in a Web.config. Tracking is enabled on the sample workflow service by adding an `<etwTracking>` behavior element.</span></span> <span data-ttu-id="885e4-129">`ExtractWorkflowVariables` 追跡プロファイルの追跡を有効にするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-129">The following code example enables tracking for the `ExtractWorkflowVariables` tracking profile.</span></span>  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="885e4-130">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="885e4-130">To use this sample</span></span>  
  
1.  <span data-ttu-id="885e4-131">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WFStockPriceApplication.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="885e4-131">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="885e4-132">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="885e4-132">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="885e4-133">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="885e4-133">To run the solution, press F5.</span></span>  
  
     <span data-ttu-id="885e4-134">ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="885e4-134">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="885e4-135">ブラウザーで、StockPriceService.xamlx をクリックします。</span><span class="sxs-lookup"><span data-stu-id="885e4-135">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="885e4-136">ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。</span><span class="sxs-lookup"><span data-stu-id="885e4-136">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="885e4-137">このアドレスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="885e4-137">Copy this address.</span></span>  
  
     <span data-ttu-id="885e4-138">ローカル サービスの WSDL アドレスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="885e4-138">The following example shows a local service WSDL address.</span></span> `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  <span data-ttu-id="885e4-139">サービスを呼び出す前に、イベント ビューアーを起動し、ワークフロー サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="885e4-139">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>  
  
7.  <span data-ttu-id="885e4-140">**開始**メニューの **管理ツール**し**イベント ビューアー**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-140">From the **Start** menu, select **Administrative Tools** and then **Event Viewer**.</span></span>  
  
8.  <span data-ttu-id="885e4-141">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、および**Microsoft**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-141">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="885e4-142">右クリック**Microsoft**選択**ビュー**し**分析およびデバッグ ログ**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-142">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="885e4-143">いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。</span><span class="sxs-lookup"><span data-stu-id="885e4-143">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="885e4-144">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-144">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="885e4-145">右クリック**分析**選択**ログの有効化**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-145">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="885e4-146">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアントを開きます。</span><span class="sxs-lookup"><span data-stu-id="885e4-146">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], open the WCF test client.</span></span>  
  
     <span data-ttu-id="885e4-147">WCF テスト クライアント (WcfTestClient.exe) にあります、 \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]インストール フォルダー > \Common7\IDE\ フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="885e4-147">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder>\Common7\IDE\ folder.</span></span>  
  
     <span data-ttu-id="885e4-148">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] の既定のインストール フォルダーは C:\Program Files\Microsoft Visual Studio 10.0 です。</span><span class="sxs-lookup"><span data-stu-id="885e4-148">The default [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>  
  
11. <span data-ttu-id="885e4-149">WCF テスト クライアントで、次のように選択します。**サービスの追加**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="885e4-149">In WCF test client, select **Add Service** from the **File** menu.</span></span>  
  
     <span data-ttu-id="885e4-150">前の手順でコピーしたローカル サービスの WSDL アドレスを入力ボックスに追加します。</span><span class="sxs-lookup"><span data-stu-id="885e4-150">Add the local service WSDL address you copied earlier in the input box.</span></span>  
  
12. <span data-ttu-id="885e4-151">WCF テスト クライアントで、`GetStockPrice` をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="885e4-151">In WCF test client, double-click `GetStockPrice`.</span></span>  
  
     <span data-ttu-id="885e4-152">`GetStockPrice` メソッドが開きます。</span><span class="sxs-lookup"><span data-stu-id="885e4-152">This opens the `GetStockPrice` method.</span></span> <span data-ttu-id="885e4-153">この要求はパラメーターを 1 つ受け取ります。</span><span class="sxs-lookup"><span data-stu-id="885e4-153">The request accepts one parameter.</span></span> <span data-ttu-id="885e4-154">値を使用して**Contoso**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-154">Use the value **Contoso**.</span></span>  
  
13. <span data-ttu-id="885e4-155">をクリックして**呼び出す**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-155">Click **Invoke**.</span></span>  
  
14. <span data-ttu-id="885e4-156">イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、 **アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-156">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="885e4-157">右クリック**分析**選択**更新**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-157">Right-click **Analytic** and select **Refresh**.</span></span> <span data-ttu-id="885e4-158">ワークフロー イベントのイベント ID の範囲は 100 ～ 199 です。</span><span class="sxs-lookup"><span data-stu-id="885e4-158">The workflow events are in the event ID ranges 100-199.</span></span>  
  
     <span data-ttu-id="885e4-159">イベントには、イベント ビューアーで表示できる注釈、変数、引数、およびカスタム追跡レコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="885e4-159">The events contain the annotations, variables, arguments and custom tracking records that can be viewed in the event viewer.</span></span>  
  
## <a name="cleaning-up-in-the-event-viewer"></a><span data-ttu-id="885e4-160">イベント ビューアーでのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="885e4-160">Cleaning up in the Event Viewer</span></span>  
 <span data-ttu-id="885e4-161">イベント ログの分析チャネルは、次の手順に従ってイベント ビューアーでクリーンアップできます。</span><span class="sxs-lookup"><span data-stu-id="885e4-161">The analytic channel in the event log can be cleaned up in the Event Viewer by doing the following.</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="885e4-162">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="885e4-162">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="885e4-163">イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="885e4-163">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="885e4-164">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-164">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="885e4-165">右クリック**分析**選択**ログの無効化**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-165">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="885e4-166">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーションサーバー アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-166">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="885e4-167">右クリック**分析**選択**ログの消去**です。</span><span class="sxs-lookup"><span data-stu-id="885e4-167">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
     <span data-ttu-id="885e4-168">選択、**オフ**イベントをクリアするにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="885e4-168">Choose the **Clear** option to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="885e4-169">既知の問題</span><span class="sxs-lookup"><span data-stu-id="885e4-169">Known Issue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="885e4-170">イベント ビューアーの既知の問題により、ETW イベントをデコードできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="885e4-170">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="885e4-171">その場合、次のようなエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="885e4-171">You may see an error message that looks like the following.</span></span>  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  <span data-ttu-id="885e4-172">このエラーが発生した場合はクリックして**更新**[操作] ウィンドウ。</span><span class="sxs-lookup"><span data-stu-id="885e4-172">If you encounter this error, click **Refresh** in the actions pane.</span></span> <span data-ttu-id="885e4-173">これにより、イベントが正常にデコードされます。</span><span class="sxs-lookup"><span data-stu-id="885e4-173">The event should now decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="885e4-174">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="885e4-174">The samples may already be installed on your computer.</span></span> <span data-ttu-id="885e4-175">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="885e4-175">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="885e4-176">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="885e4-176">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="885e4-177">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="885e4-177">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a><span data-ttu-id="885e4-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="885e4-178">See Also</span></span>  
 [<span data-ttu-id="885e4-179">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="885e4-179">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

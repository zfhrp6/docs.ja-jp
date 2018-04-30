---
title: SQL 追跡
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4153ed905fc9c5c67ce1743fa76497f76b7398cc
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="sql-tracking"></a><span data-ttu-id="135bf-102">SQL 追跡</span><span class="sxs-lookup"><span data-stu-id="135bf-102">SQL Tracking</span></span>
<span data-ttu-id="135bf-103">このサンプルでは、カスタム SQL 追跡参加要素を作成し、追跡レコードを SQL データベースに書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="135bf-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="135bf-104">Windows Workflow Foundation (WF) ワークフローをワークフロー インスタンスの実行時に視覚的に追跡を提供します。</span><span class="sxs-lookup"><span data-stu-id="135bf-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="135bf-105">追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="135bf-106">ワークフロー追跡の詳細については、次を参照してください。[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)です。</span><span class="sxs-lookup"><span data-stu-id="135bf-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="135bf-107">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="135bf-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="135bf-108">SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="135bf-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="135bf-109">サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。</span><span class="sxs-lookup"><span data-stu-id="135bf-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="135bf-110">別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。</span><span class="sxs-lookup"><span data-stu-id="135bf-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>  
  
2.  <span data-ttu-id="135bf-111">Scripts ディレクトリ (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="135bf-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="135bf-112">これによって、TrackingSample という名前のデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-112">This creates a database called TrackingSample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="135bf-113">このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="135bf-114">別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。</span><span class="sxs-lookup"><span data-stu-id="135bf-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="135bf-115">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で SqlTrackingSample.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="135bf-115">Open SqlTrackingSample.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="135bf-116">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="135bf-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="135bf-117">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="135bf-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="135bf-118">ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="135bf-119">ブラウザーで、StockPriceService.xamlx をクリックします。</span><span class="sxs-lookup"><span data-stu-id="135bf-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="135bf-120">ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="135bf-121">このアドレスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="135bf-121">Copy this address.</span></span>  
  
     <span data-ttu-id="135bf-122">ローカル サービスの WSDL アドレスの例はhttp://localhost:65193/StockPriceService.xamlx?wsdlします。</span><span class="sxs-lookup"><span data-stu-id="135bf-122">An example of the local service WSDL address is http://localhost:65193/StockPriceService.xamlx?wsdl.</span></span>  
  
8.  <span data-ttu-id="135bf-123">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="135bf-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="135bf-124">このテスト クライアントは Microsoft Visual Studio 10.0\Common7\IDE ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="135bf-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="135bf-125">WCF テスト クライアントで、をクリックして、**ファイル**メニュー**サービスの追加**です。</span><span class="sxs-lookup"><span data-stu-id="135bf-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="135bf-126">テキスト ボックスにローカル サービスのアドレスを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="135bf-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="135bf-127">をクリックして**OK**ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="135bf-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="135bf-128">WCF テスト クライアントでダブルクリックして**GetStockPrice**です。</span><span class="sxs-lookup"><span data-stu-id="135bf-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="135bf-129">開き、`GetStockPrice`操作を 1 つのパラメーター値の型を受け取る`Contoso` をクリック**Invoke**です。</span><span class="sxs-lookup"><span data-stu-id="135bf-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="135bf-130">出力された追跡レコードが SQL データベースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="135bf-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="135bf-131">追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。</span><span class="sxs-lookup"><span data-stu-id="135bf-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="135bf-132">SQL Server Management Studio の詳細については、次を参照してください。 [SQL Server Management Studio の概要](http://go.microsoft.com/fwlink/?LinkId=165645)です。</span><span class="sxs-lookup"><span data-stu-id="135bf-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="135bf-133">SQL Server 2008 Management Studio Express をダウンロードできる[ここ](http://go.microsoft.com/fwlink/?LinkId=180520)です。</span><span class="sxs-lookup"><span data-stu-id="135bf-133">SQL Server 2008 Management Studio Express can be downloaded [here](http://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="135bf-134">テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="135bf-135">サンプルをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="135bf-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="135bf-136">サンプル ディレクトリ (\WF\Basic\Tracking\SqlTracking) で Trackingcleanup.cmd スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="135bf-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="135bf-137">Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。</span><span class="sxs-lookup"><span data-stu-id="135bf-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="135bf-138">別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。</span><span class="sxs-lookup"><span data-stu-id="135bf-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="135bf-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="135bf-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="135bf-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="135bf-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="135bf-141">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="135bf-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="135bf-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="135bf-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="135bf-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="135bf-143">See Also</span></span>  
 [<span data-ttu-id="135bf-144">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="135bf-144">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

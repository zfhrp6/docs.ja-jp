---
title: WCF サービスと Event Tracing for Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809834"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="f23a1-102">WCF サービスと Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="f23a1-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="f23a1-103">このサンプルでイベント トレース for Windows (ETW) イベントを出力する Windows Communication Foundation (WCF) での分析トレースを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="f23a1-104">分析トレースは、実稼働環境で WCF サービスのトラブルシューティングが可能で、WCF スタック キー_ポイントで出力されるイベントです。</span><span class="sxs-lookup"><span data-stu-id="f23a1-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>  
  
 <span data-ttu-id="f23a1-105">WCF サービスの分析トレースのトレースは、使用可能に実稼働環境でのパフォーマンスに影響を最小限にします。</span><span class="sxs-lookup"><span data-stu-id="f23a1-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="f23a1-106">これらのトレースは、ETW セッションにイベントとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="f23a1-107">このサンプルでは、基本的な WCF サービスでイベントが出力されますサービスからイベント ビューアーを使用して表示するイベント ログに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="f23a1-108">WCF サービスからのイベントをリッスンする専用の ETW セッションを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="f23a1-109">サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f23a1-110">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="f23a1-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="f23a1-111">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EtwAnalyticTraceSample.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f23a1-112">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f23a1-113">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="f23a1-114">Web ブラウザーで、をクリックして **[calculator.svc]** です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="f23a1-115">サービスの WSDL ドキュメントの URI がブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="f23a1-116">その URI をコピーします。</span><span class="sxs-lookup"><span data-stu-id="f23a1-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="f23a1-117">既定では、サービスの開始ポート 1378 で要求をリッスンしている (http://localhost:1378/Calculator.svc)です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="f23a1-118">WCF テスト クライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-118">Run the WCF test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="f23a1-119">WCF テスト クライアント (WcfTestClient.exe) にあります、 \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir > \Common7\IDE\ WcfTestClient.exe (既定[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]インストール ディレクトリは C:\Program files \microsoft Visual Studio 10.0)。</span><span class="sxs-lookup"><span data-stu-id="f23a1-119">The WCF test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="f23a1-120">WCF テスト クライアント内でを選択して、サービスを追加**ファイル**、し**サービスの追加**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-120">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="f23a1-121">入力ボックスにエンドポイントのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="f23a1-122">既定値は、http://localhost:1378/Calculator.svc です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="f23a1-123">イベント ビューアー アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="f23a1-124">サービスを呼び出す前に、イベント ビューアーを起動し、WCF サービスから生成された追跡イベントのイベント ログがリッスンしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f23a1-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>  
  
7.  <span data-ttu-id="f23a1-125">**開始**メニューの **管理ツール**、し**イベント ビューアー**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="f23a1-126">有効にする、**分析**と**デバッグ**ログ。</span><span class="sxs-lookup"><span data-stu-id="f23a1-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="f23a1-127">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="f23a1-128">右クリック**アプリケーション サーバー-アプリケーション****ビュー**、し**分析およびデバッグ ログ**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="f23a1-129">いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。</span><span class="sxs-lookup"><span data-stu-id="f23a1-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="f23a1-130">有効にする、**分析**ログ。</span><span class="sxs-lookup"><span data-stu-id="f23a1-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="f23a1-131">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="f23a1-132">右クリック**分析**選択**ログの有効化**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="f23a1-133">サービスをテストするには</span><span class="sxs-lookup"><span data-stu-id="f23a1-133">To test the service</span></span>  
  
1.  <span data-ttu-id="f23a1-134">WCF テスト クライアントに戻りをダブルクリックして`Divide`分母が 0 を指定する既定値のままとします。</span><span class="sxs-lookup"><span data-stu-id="f23a1-134">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="f23a1-135">分母が 0 の場合、サービスからエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="f23a1-136">サービスから出力されたイベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="f23a1-137">イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="f23a1-138">右クリック**分析**選択**更新**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="f23a1-139">WCF 分析トレースのイベントがイベント ビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="f23a1-140">サービスからエラーがスローされたため、イベント ビューアーにエラー トレース イベントが表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f23a1-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="f23a1-141">手順 1. と 2. を繰り返します。ただし、今度は有効な入力値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="f23a1-142">`N2` パラメーターの値は、0 以外であれば任意の数字でかまいません。</span><span class="sxs-lookup"><span data-stu-id="f23a1-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="f23a1-143">分析チャネルを更新して、WCF イベントにエラー イベントが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="f23a1-144">このサンプルでは、WCF サービスから出力される分析トレース イベントを示します。</span><span class="sxs-lookup"><span data-stu-id="f23a1-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="f23a1-145">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="f23a1-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="f23a1-146">イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="f23a1-147">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="f23a1-148">右クリック**分析**選択**ログの無効化**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="f23a1-149">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="f23a1-150">右クリック**分析**選択**ログの消去**です。</span><span class="sxs-lookup"><span data-stu-id="f23a1-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="f23a1-151">選択、**オフ**イベントをクリアするにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="f23a1-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f23a1-152">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f23a1-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f23a1-153">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f23a1-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f23a1-154">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="f23a1-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f23a1-155">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f23a1-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="f23a1-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="f23a1-156">See Also</span></span>  
 [<span data-ttu-id="f23a1-157">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="f23a1-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

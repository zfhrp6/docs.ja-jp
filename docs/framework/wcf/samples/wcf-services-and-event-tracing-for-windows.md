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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 809b48a27e5923db585d6125df0d2f55c96a4765
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="50867-102">WCF サービスと Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="50867-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="50867-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の分析トレースを使用して、Event Tracing for Windows (ETW) でイベントを出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="50867-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="50867-104">分析トレースは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] スタック内のキー ポイントで出力されるイベントです。これにより、運用環境での [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのトラブルシューティングが可能になります。</span><span class="sxs-lookup"><span data-stu-id="50867-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="50867-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの分析トレースは、有効にしてもパフォーマンスに最小限の影響しか及ぼさないため、運用環境で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="50867-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="50867-106">これらのトレースは、ETW セッションにイベントとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="50867-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="50867-107">このサンプルには、サービスのイベントをイベント ログに出力する基本的な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが含まれています。イベント ログは、イベント ビューアーを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="50867-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="50867-108">また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのイベントをリッスンする専用の ETW セッションを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="50867-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="50867-109">サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="50867-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="50867-110">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="50867-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="50867-111">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、EtwAnalyticTraceSample.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="50867-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="50867-112">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="50867-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="50867-113">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="50867-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="50867-114">Web ブラウザーで、をクリックして**[calculator.svc]**です。</span><span class="sxs-lookup"><span data-stu-id="50867-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="50867-115">サービスの WSDL ドキュメントの URI がブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="50867-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="50867-116">その URI をコピーします。</span><span class="sxs-lookup"><span data-stu-id="50867-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="50867-117">既定では、ポート 1378 (http://localhost:1378/Calculator.svc) で要求のリッスンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="50867-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="50867-118">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="50867-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="50867-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]にテスト用クライアント (WcfTestClient.exe) がある、 \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir > \Common7\IDE\ WcfTestClient.exe (既定[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]インストール ディレクトリは C:\Program files \microsoft Visual Studio 10.0)。</span><span class="sxs-lookup"><span data-stu-id="50867-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="50867-120">内で、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]テスト クライアントを選択して、サービスを追加**ファイル**、し**サービスの追加**です。</span><span class="sxs-lookup"><span data-stu-id="50867-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="50867-121">入力ボックスにエンドポイントのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="50867-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="50867-122">既定値は http://localhost:1378/Calculator.svc です。</span><span class="sxs-lookup"><span data-stu-id="50867-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="50867-123">イベント ビューアー アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="50867-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="50867-124">サービスを呼び出す前に、イベント ビューアーを起動し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから生成された追跡イベントをイベント ログでリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="50867-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="50867-125">**開始**メニューの **管理ツール**、し**イベント ビューアー**です。</span><span class="sxs-lookup"><span data-stu-id="50867-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="50867-126">有効にする、**分析**と**デバッグ**ログ。</span><span class="sxs-lookup"><span data-stu-id="50867-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="50867-127">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="50867-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="50867-128">右クリック**アプリケーション サーバー-アプリケーション****ビュー**、し**分析およびデバッグ ログ**です。</span><span class="sxs-lookup"><span data-stu-id="50867-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="50867-129">いることを確認、 **分析およびデバッグ ログ**オプションはオンにします。</span><span class="sxs-lookup"><span data-stu-id="50867-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="50867-130">有効にする、**分析**ログ。</span><span class="sxs-lookup"><span data-stu-id="50867-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="50867-131">イベント ビューアーのツリー ビューに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="50867-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="50867-132">右クリック**分析**選択**ログの有効化**です。</span><span class="sxs-lookup"><span data-stu-id="50867-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="50867-133">サービスをテストするには</span><span class="sxs-lookup"><span data-stu-id="50867-133">To test the service</span></span>  
  
1.  <span data-ttu-id="50867-134">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントに戻り、[`Divide`] をダブルクリックします。既定値のまま、分母を 0 にしておきます。</span><span class="sxs-lookup"><span data-stu-id="50867-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="50867-135">分母が 0 の場合、サービスからエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="50867-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="50867-136">サービスから出力されたイベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="50867-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="50867-137">イベント ビューアーに戻りに移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し、**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="50867-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="50867-138">右クリック**分析**選択**更新**です。</span><span class="sxs-lookup"><span data-stu-id="50867-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="50867-139">WCF 分析トレースのイベントがイベント ビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="50867-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="50867-140">サービスからエラーがスローされたため、イベント ビューアーにエラー トレース イベントが表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="50867-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="50867-141">手順 1. と 2. を繰り返します。ただし、今度は有効な入力値を指定します。</span><span class="sxs-lookup"><span data-stu-id="50867-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="50867-142">`N2` パラメーターの値は、0 以外であれば任意の数字でかまいません。</span><span class="sxs-lookup"><span data-stu-id="50867-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="50867-143">分析チャネルを更新して、WCF イベントにエラー イベントが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="50867-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="50867-144">このサンプルでは、WCF サービスから出力される分析トレース イベントを示します。</span><span class="sxs-lookup"><span data-stu-id="50867-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="50867-145">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="50867-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="50867-146">イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="50867-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="50867-147">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="50867-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="50867-148">右クリック**分析**選択**ログの無効化**です。</span><span class="sxs-lookup"><span data-stu-id="50867-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="50867-149">移動**イベント ビューアー**、 **Applications and Services Logs**、 **Microsoft**、 **Windows**、し**アプリケーション サーバー-アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="50867-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="50867-150">右クリック**分析**選択**ログの消去**です。</span><span class="sxs-lookup"><span data-stu-id="50867-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="50867-151">選択、**オフ**イベントをクリアするにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="50867-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50867-152">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="50867-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="50867-153">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="50867-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="50867-154">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="50867-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50867-155">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="50867-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="50867-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="50867-156">See Also</span></span>  
 [<span data-ttu-id="50867-157">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="50867-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

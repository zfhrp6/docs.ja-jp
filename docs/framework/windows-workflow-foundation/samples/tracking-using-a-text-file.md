---
title: テキスト ファイルを使用した追跡
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: aa59ab8304c68873c938f42fc585be883b234ecc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805799"
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="081d1-102">テキスト ファイルを使用した追跡</span><span class="sxs-lookup"><span data-stu-id="081d1-102">Tracking Using a Text File</span></span>
<span data-ttu-id="081d1-103">このサンプルでは、カスタム追跡参加要素を作成することで、Windows Workflow Foundation (WF) の追跡を拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="081d1-103">This sample demonstrates how to extend tracking in Windows Workflow Foundation (WF) by creating a custom tracking participant.</span></span> <span data-ttu-id="081d1-104">追跡参加要素は、出力された追跡レコードをランタイムから受け取る .NET Framework クラスです。</span><span class="sxs-lookup"><span data-stu-id="081d1-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="081d1-105">追跡参加要素を作成して、シナリオに必要な出力先に追跡イベントを転送することができます。</span><span class="sxs-lookup"><span data-stu-id="081d1-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="081d1-106">たとえば、ETW (Event Tracing for Windows) 追跡参加要素は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の一部として提供されています。</span><span class="sxs-lookup"><span data-stu-id="081d1-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="081d1-107">このサンプルの追跡参加要素は、レコードを XML 形式でテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="081d1-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="081d1-108">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="081d1-108">Sample details</span></span>  
 <span data-ttu-id="081d1-109">追跡参加要素の有用性と信頼性を最適化するには、いくつかの追加手順を完了して追跡参加要素をランタイムに適切に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="081d1-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="081d1-110">ベスト プラクティスに準拠する追跡参加要素を作成するためにこのサンプルで使用するクラスを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="081d1-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="081d1-111">クラス</span><span class="sxs-lookup"><span data-stu-id="081d1-111">Class</span></span>|<span data-ttu-id="081d1-112">説明</span><span class="sxs-lookup"><span data-stu-id="081d1-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="081d1-113"><xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を使用して、テキスト ファイルの追跡参加要素の構成に使用される構成セクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="081d1-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="081d1-114">これにより、ユーザーは、標準の .NET Framework 構成ファイルを使用してログ ファイルの出力先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="081d1-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="081d1-115">WCF での動作を拡張機能をランタイムに挿入できるようにします。</span><span class="sxs-lookup"><span data-stu-id="081d1-115">Behaviors in WCF allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="081d1-116">この動作によって、サービスの開始時に追跡参加要素がサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="081d1-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="081d1-117">実行時に追跡参加要素を受け取って XML としてログ ファイルに格納する追跡参加要素。</span><span class="sxs-lookup"><span data-stu-id="081d1-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="081d1-118">動作拡張要素の構成</span><span class="sxs-lookup"><span data-stu-id="081d1-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="081d1-119">.NET Framework 構成ファイルを使用して前に記述した動作拡張要素を利用するには、もう 1 つの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="081d1-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="081d1-120">拡張機能を使用する構成ファイルに次の構成を挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="081d1-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="081d1-121">動作拡張要素の構成の詳細な使用例については、サンプルの Web.config ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="081d1-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="081d1-122">カスタム追跡レコード</span><span class="sxs-lookup"><span data-stu-id="081d1-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="081d1-123">GetStockPrices.cs ファイルでは、<xref:System.Activities.CodeActivity> 内からカスタム追跡レコードを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="081d1-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="081d1-124">サンプルの実行時にこのレコードを調べてください。</span><span class="sxs-lookup"><span data-stu-id="081d1-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="081d1-125">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="081d1-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="081d1-126">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WFStockPriceApplication.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="081d1-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="081d1-127">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="081d1-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="081d1-128">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="081d1-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="081d1-129">ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="081d1-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="081d1-130">ブラウザーで、StockPriceService.xamlx をクリックします。</span><span class="sxs-lookup"><span data-stu-id="081d1-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="081d1-131">ブラウザーで、表示、 **StockPriceService**ページで、ローカル サービスの wsdl アドレスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="081d1-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="081d1-132">このアドレスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="081d1-132">Copy this address.</span></span>  
  
     <span data-ttu-id="081d1-133">ローカル サービスの wsdl アドレスの例はhttp://localhost:53797/StockPriceService.xamlx?wsdlします。</span><span class="sxs-lookup"><span data-stu-id="081d1-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="081d1-134">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] フォルダー (既定のインストール フォルダーは %SystemDrive%\Program Files\Microsoft Visual Studio 10.0) に移動します。</span><span class="sxs-lookup"><span data-stu-id="081d1-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="081d1-135">Common7\IDE\ サブフォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="081d1-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="081d1-136">WcfTestClient.exe ファイルをダブルクリックして、WCF テスト クライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="081d1-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="081d1-137">WCF テスト クライアントで、次のように選択します**サービスを追加しています...**</span><span class="sxs-lookup"><span data-stu-id="081d1-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="081d1-138">**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="081d1-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="081d1-139">コピーした URL をテキスト ボックスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="081d1-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="081d1-140">をクリックして**OK**ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="081d1-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="081d1-141">WCF テスト クライアントを使用してサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="081d1-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="081d1-142">WCF テスト クライアントでダブルクリック**GetStockPrice()** 下にある、 **IStockPriceService**ノード。</span><span class="sxs-lookup"><span data-stu-id="081d1-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="081d1-143">**GetStockPrice()** メソッドは、1 つのパラメーターと共に右ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="081d1-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="081d1-144">パラメーターの値として「Contoso」と入力します。</span><span class="sxs-lookup"><span data-stu-id="081d1-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="081d1-145">をクリックして**呼び出す**です。</span><span class="sxs-lookup"><span data-stu-id="081d1-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="081d1-146">アプリケーション データ ディレクトリにあるログ ファイル (%APPDATA%\trackingRecords.log) で追跡イベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="081d1-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="081d1-147">%Appdata% %SystemDrive%\Users に解決される環境変数である\\< ユーザー名\>\AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)]、 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]、または Windows Server 2008。</span><span class="sxs-lookup"><span data-stu-id="081d1-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="081d1-148">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="081d1-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="081d1-149">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="081d1-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="081d1-150">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="081d1-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="081d1-151">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="081d1-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="081d1-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="081d1-152">See Also</span></span>  
 [<span data-ttu-id="081d1-153">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="081d1-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

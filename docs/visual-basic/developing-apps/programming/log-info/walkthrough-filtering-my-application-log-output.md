---
title: My.Application.Log の出力のフィルター処理 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6c048578b320fedd2153aee7b466b1494551abe0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="4bf6f-102">チュートリアル: My.Application.Log の出力のフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bf6f-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="4bf6f-103">このチュートリアルでは、`My.Application.Log` オブジェクトの既定のログ フィルター処理を変更して、`Log` オブジェクトからリスナーに渡される情報や、リスナーによって記述される情報を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="4bf6f-104">構成情報はアプリケーションの構成ファイルに保存されるため、ロギングの動作はアプリケーションをビルドした後でも変更できます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="4bf6f-105">作業の開始</span><span class="sxs-lookup"><span data-stu-id="4bf6f-105">Getting Started</span></span>  
 <span data-ttu-id="4bf6f-106">`My.Application.Log` が書き込む各メッセージには、重大度レベルが関連付けられます。この情報は、ログ出力を制御するためにフィルター処理メカニズムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="4bf6f-107">このサンプル アプリケーションでは、`My.Application.Log` メソッドを使用して、重大度レベルの異なる複数のログ メッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="4bf6f-108">サンプル アプリケーションをビルドするには</span><span class="sxs-lookup"><span data-stu-id="4bf6f-108">To build the sample application</span></span>  
  
1.  <span data-ttu-id="4bf6f-109">新しい Visual Basic Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-109">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="4bf6f-110">Form1 に Button1 という名前のボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-110">Add a button named Button1 to Form1.</span></span>  
  
3.  <span data-ttu-id="4bf6f-111">Button1 の <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  <span data-ttu-id="4bf6f-112">デバッガーでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-112">Run the application in the debugger.</span></span>  
  
5.  <span data-ttu-id="4bf6f-113">**[Button1]** を押します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-113">Press **Button1**.</span></span>  
  
     <span data-ttu-id="4bf6f-114">アプリケーションは、アプリケーションのデバッグ出力とログ ファイルに次の情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-114">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  <span data-ttu-id="4bf6f-115">アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-115">Close the application.</span></span>  
  
     <span data-ttu-id="4bf6f-116">アプリケーションのデバッグ出力ウィンドウを表示する方法について詳しくは、「[出力ウィンドウ](/visualstudio/ide/reference/output-window)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="4bf6f-117">アプリケーションのログ ファイルの場所について詳しくは、「[チュートリアル: My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4bf6f-118">既定では、アプリケーションはアプリケーションの終了時にログ ファイルの出力をフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-118">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="4bf6f-119">上の例では、<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> メソッドの 2 回目の呼び出しと <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> メソッドの呼び出しでログが出力されます。`WriteEntry` メソッドの最初と最後の呼び出しでは出力されません。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="4bf6f-120">これは、`WriteEntry` と `WriteException` の重大度レベルが "Information" と "Error" であるためです。これらはどちらも、`My.Application.Log` オブジェクトの既定のログ フィルター処理で許可されます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="4bf6f-121">これに対し、重大度レベルが "Start" および "Stop" のイベントについては、ログ出力が生成されません。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="4bf6f-122">すべての My.Application.Log リスナーのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="4bf6f-122">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="4bf6f-123">`My.Application.Log` オブジェクトは、`DefaultSwitch` という名前の <xref:System.Diagnostics.SourceSwitch> を使用し、`WriteEntry` および `WriteException` メソッドからログ リスナーに渡すメッセージを制御します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="4bf6f-124">アプリケーションの構成ファイル内にある `DefaultSwitch` は、その値を <xref:System.Diagnostics.SourceLevels> 列挙値のいずれかに設定することで構成できます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="4bf6f-125">既定では、この値は "Information" です。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-125">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="4bf6f-126">次の表は、Log がリスナーにメッセージを書き込むために必要な重大度レベルを、`DefaultSwitch` の設定ごとに示したものです。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="4bf6f-127">DefaultSwitch の値</span><span class="sxs-lookup"><span data-stu-id="4bf6f-127">DefaultSwitch Value</span></span>|<span data-ttu-id="4bf6f-128">出力に必要なメッセージの重大度</span><span class="sxs-lookup"><span data-stu-id="4bf6f-128">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="4bf6f-129">`Critical` または `Error`</span><span class="sxs-lookup"><span data-stu-id="4bf6f-129">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="4bf6f-130">`Critical`、 `Error`、または `Warning`</span><span class="sxs-lookup"><span data-stu-id="4bf6f-130">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="4bf6f-131">`Critical`、`Error`、`Warning`、または `Information`</span><span class="sxs-lookup"><span data-stu-id="4bf6f-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="4bf6f-132">`Critical`、`Error`、`Warning`、`Information`、または `Verbose`</span><span class="sxs-lookup"><span data-stu-id="4bf6f-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="4bf6f-133">`Start`、`Stop`、`Suspend`、`Resume`、または `Transfer`</span><span class="sxs-lookup"><span data-stu-id="4bf6f-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="4bf6f-134">すべてのメッセージが許可されます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-134">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="4bf6f-135">すべてのメッセージがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-135">All messages are blocked.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4bf6f-136">`WriteEntry` メソッドと `WriteException` メソッドにはそれぞれ、重大度レベルを指定しないオーバー ロードがあります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="4bf6f-137">`WriteEntry` オーバー ロードの暗黙的な重大度レベルは "Information" で、`WriteException` オーバー ロードの暗黙的な重大度レベルは "Error" です。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="4bf6f-138">次の表は、前の例に示したログ出力について説明したものです。 既定の `DefaultSwitch` 設定 (Information) では、`WriteEntry` メソッドに対する 2 番目の呼び出しと、`WriteException` メソッドに対する呼び出しでのみ、ログ出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="4bf6f-139">アクティビティ トレース イベントだけを記録するには</span><span class="sxs-lookup"><span data-stu-id="4bf6f-139">To log only activity tracing events</span></span>  
  
1.  <span data-ttu-id="4bf6f-140">**ソリューション エクスプローラー**で app.config を右クリックし、**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="4bf6f-141">- または -</span><span class="sxs-lookup"><span data-stu-id="4bf6f-141">-or-</span></span>  
  
     <span data-ttu-id="4bf6f-142">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-142">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="4bf6f-143">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-143">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="4bf6f-144">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="4bf6f-145">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-145">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="4bf6f-146">最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションで、`<switches>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="4bf6f-147">スイッチのコレクションに `DefaultSwitch` を追加する要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="4bf6f-148">これは次のような要素です。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-148">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  <span data-ttu-id="4bf6f-149">`value` 属性の値を "ActivityTracing" に変更します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5.  <span data-ttu-id="4bf6f-150">app.config ファイルの内容は次の XML のようになります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-150">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  <span data-ttu-id="4bf6f-151">デバッガーでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-151">Run the application in the debugger.</span></span>  
  
7.  <span data-ttu-id="4bf6f-152">**[Button1]** を押します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-152">Press **Button1**.</span></span>  
  
     <span data-ttu-id="4bf6f-153">アプリケーションは、アプリケーションのデバッグ出力とログ ファイルに次の情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-153">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  <span data-ttu-id="4bf6f-154">アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-154">Close the application.</span></span>  
  
9. <span data-ttu-id="4bf6f-155">`value` 属性の値を "Information" に戻します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-155">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4bf6f-156">`DefaultSwitch` スイッチの設定では、`My.Application.Log` のみが制御されます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="4bf6f-157">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] の <xref:System.Diagnostics.Trace?displayProperty=nameWithType> クラスと <xref:System.Diagnostics.Debug?displayProperty=nameWithType> クラスの動作が変えられることはありません。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-157">It does not change how the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="4bf6f-158">My.Application.Log リスナーの個別のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="4bf6f-158">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="4bf6f-159">前の例では、すべての `My.Application.Log` 出力のフィルター処理を変更する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="4bf6f-160">この例では、個別のログ リスナーをフィルター処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="4bf6f-161">既定では、アプリケーションには、アプリケーションのデバッグ出力とログ ファイルに情報を書き込む 2 つのリスナーがあります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="4bf6f-162">構成ファイルは、`My.Application.Log` のスイッチのように、各リスナーにフィルターを適用することで、ログ リスナーの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="4bf6f-163">ログ リスナーは、メッセージの重大度がログの `DefaultSwitch` とログ リスナーのフィルターの両方によって許可された場合にのみ、メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="4bf6f-164">この例では、新しいデバッグ リスナーのフィルター処理を構成し、それを `Log` オブジェクトに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="4bf6f-165">デバッグ メッセージが新しいデバッグ リスナーから送られるようにするには、既定のデバッグ リスナーを `Log` オブジェクトから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="4bf6f-166">アクティビティ トレース イベントだけを記録するには</span><span class="sxs-lookup"><span data-stu-id="4bf6f-166">To log only activity-tracing events</span></span>  
  
1.  <span data-ttu-id="4bf6f-167">**ソリューション エクスプローラー**で app.config を右クリックし、**[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="4bf6f-168">- または -</span><span class="sxs-lookup"><span data-stu-id="4bf6f-168">-or-</span></span>  
  
     <span data-ttu-id="4bf6f-169">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-169">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="4bf6f-170">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-170">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="4bf6f-171">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="4bf6f-172">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-172">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="4bf6f-173">**ソリューション エクスプローラー**で app.config を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="4bf6f-174">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-174">Choose **Open**.</span></span>  
  
3.  <span data-ttu-id="4bf6f-175">`<sources>` セクション内にある、`name` 属性が "DefaultSource" の `<source>` セクションで、`<listeners>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="4bf6f-176">`<sources>` セクションは、最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4.  <span data-ttu-id="4bf6f-177">`<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-177">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  <span data-ttu-id="4bf6f-178">最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="4bf6f-179">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-179">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     <span data-ttu-id="4bf6f-180"><xref:System.Diagnostics.EventTypeFilter> フィルターは <xref:System.Diagnostics.SourceLevels> 列挙値の 1 つをその `initializeData` 属性として取ります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7.  <span data-ttu-id="4bf6f-181">app.config ファイルの内容は次の XML のようになります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-181">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  <span data-ttu-id="4bf6f-182">デバッガーでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-182">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="4bf6f-183">**[Button1]** を押します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-183">Press **Button1**.</span></span>  
  
     <span data-ttu-id="4bf6f-184">アプリケーションは、アプリケーションのログ ファイルに次の情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-184">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="4bf6f-185">フィルター処理の基準がより厳しくなったので、アプリケーションのデバッグ出力に書き込まれる情報は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="4bf6f-186">アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-186">Close the application.</span></span>  
  
 <span data-ttu-id="4bf6f-187">配置後にログの設定を変更する方法については、「[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4bf6f-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf6f-188">参照</span><span class="sxs-lookup"><span data-stu-id="4bf6f-188">See Also</span></span>  
 [<span data-ttu-id="4bf6f-189">チュートリアル : My.Application.Log による情報の書き込み先の確認</span><span class="sxs-lookup"><span data-stu-id="4bf6f-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="4bf6f-190">チュートリアル : My.Application.Log による情報の書き込み先の変更</span><span class="sxs-lookup"><span data-stu-id="4bf6f-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="4bf6f-191">チュートリアル : カスタム ログ リスナーの作成</span><span class="sxs-lookup"><span data-stu-id="4bf6f-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [<span data-ttu-id="4bf6f-192">方法: ログ メッセージを書き込む</span><span class="sxs-lookup"><span data-stu-id="4bf6f-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="4bf6f-193">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="4bf6f-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="4bf6f-194">アプリケーションからの情報のログ記録</span><span class="sxs-lookup"><span data-stu-id="4bf6f-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)

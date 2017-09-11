---
title: "My.Application.Log の出力のフィルター処理 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a19bd71f1346be292dcc7b143a0080ac1cf11ec0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="e73bf-102">チュートリアル: My.Application.Log の出力のフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e73bf-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>
<span data-ttu-id="e73bf-103">このチュートリアルでは、`My.Application.Log` オブジェクトの既定のログ フィルター処理を変更して、`Log` オブジェクトからリスナーに渡される情報や、リスナーによって記述される情報を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="e73bf-104">構成情報はアプリケーションの構成ファイルに保存されるため、ロギングの動作はアプリケーションをビルドした後でも変更できます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="e73bf-105">作業の開始</span><span class="sxs-lookup"><span data-stu-id="e73bf-105">Getting Started</span></span>  
 <span data-ttu-id="e73bf-106">`My.Application.Log` が書き込む各メッセージには、重大度レベルが関連付けられます。この情報は、ログ出力を制御するためにフィルター処理メカニズムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="e73bf-107">このサンプル アプリケーションでは、`My.Application.Log` メソッドを使用して、重大度レベルの異なる複数のログ メッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>  
  
#### <a name="to-build-the-sample-application"></a><span data-ttu-id="e73bf-108">サンプル アプリケーションをビルドするには</span><span class="sxs-lookup"><span data-stu-id="e73bf-108">To build the sample application</span></span>  
  
1.  <span data-ttu-id="e73bf-109">新しい [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows アプリケーション プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-109">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="e73bf-110">Form1 に Button1 という名前のボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-110">Add a button named Button1 to Form1.</span></span>  
  
3.  <span data-ttu-id="e73bf-111">Button1 の <xref:System.Windows.Forms.Control.Click> イベント ハンドラーで、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>  
  
     <span data-ttu-id="e73bf-112">[!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e73bf-112">[!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]</span></span>  
  
4.  <span data-ttu-id="e73bf-113">デバッガーでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-113">Run the application in the debugger.</span></span>  
  
5.  <span data-ttu-id="e73bf-114">**[Button1]** を押します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-114">Press **Button1**.</span></span>  
  
     <span data-ttu-id="e73bf-115">アプリケーションは、アプリケーションのデバッグ出力とログ ファイルに次の情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-115">The application writes the following information to the application's debug output and log file.</span></span>  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  <span data-ttu-id="e73bf-116">アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-116">Close the application.</span></span>  
  
     <span data-ttu-id="e73bf-117">アプリケーションのデバッグ出力ウィンドウを表示する方法について詳しくは、「[出力ウィンドウ](/visualstudio/ide/reference/output-window)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e73bf-117">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="e73bf-118">アプリケーションのログ ファイルの場所について詳しくは、「[チュートリアル: My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e73bf-118">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e73bf-119">既定では、アプリケーションはアプリケーションの終了時にログ ファイルの出力をフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-119">By default, the application flushes the log-file output when the application closes.</span></span>  
  
     <span data-ttu-id="e73bf-120">上の例では、<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> メソッドの 2 回目の呼び出しと <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> メソッドの呼び出しでログが出力されます。`WriteEntry` メソッドの最初と最後の呼び出しでは出力されません。</span><span class="sxs-lookup"><span data-stu-id="e73bf-120">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="e73bf-121">これは、`WriteEntry` と `WriteException` の重大度レベルが "Information" と "Error" であるためです。これらはどちらも、`My.Application.Log` オブジェクトの既定のログ フィルター処理で許可されます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-121">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="e73bf-122">これに対し、重大度レベルが "Start" および "Stop" のイベントについては、ログ出力が生成されません。</span><span class="sxs-lookup"><span data-stu-id="e73bf-122">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="e73bf-123">すべての My.Application.Log リスナーのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="e73bf-123">Filtering for All My.Application.Log Listeners</span></span>  
 <span data-ttu-id="e73bf-124">`My.Application.Log` オブジェクトは、`DefaultSwitch` という名前の <xref:System.Diagnostics.SourceSwitch> を使用し、`WriteEntry` および `WriteException` メソッドからログ リスナーに渡すメッセージを制御します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-124">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="e73bf-125">アプリケーションの構成ファイル内にある `DefaultSwitch` は、その値を <xref:System.Diagnostics.SourceLevels> 列挙値のいずれかに設定することで構成できます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-125">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="e73bf-126">既定では、この値は "Information" です。</span><span class="sxs-lookup"><span data-stu-id="e73bf-126">By default, its value is "Information".</span></span>  
  
 <span data-ttu-id="e73bf-127">次の表は、Log がリスナーにメッセージを書き込むために必要な重大度レベルを、`DefaultSwitch` の設定ごとに示したものです。</span><span class="sxs-lookup"><span data-stu-id="e73bf-127">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>  
  
|<span data-ttu-id="e73bf-128">DefaultSwitch の値</span><span class="sxs-lookup"><span data-stu-id="e73bf-128">DefaultSwitch Value</span></span>|<span data-ttu-id="e73bf-129">出力に必要なメッセージの重大度</span><span class="sxs-lookup"><span data-stu-id="e73bf-129">Message severity required for output</span></span>|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|<span data-ttu-id="e73bf-130">`Critical` または `Error`</span><span class="sxs-lookup"><span data-stu-id="e73bf-130">`Critical` or `Error`</span></span>|  
|`Warning`|<span data-ttu-id="e73bf-131">`Critical`、`Error`、または `Warning`</span><span class="sxs-lookup"><span data-stu-id="e73bf-131">`Critical`, `Error`, or `Warning`</span></span>|  
|`Information`|<span data-ttu-id="e73bf-132">`Critical`、`Error`、`Warning`、または `Information`</span><span class="sxs-lookup"><span data-stu-id="e73bf-132">`Critical`, `Error`, `Warning`, or `Information`</span></span>|  
|`Verbose`|<span data-ttu-id="e73bf-133">`Critical`、`Error`、`Warning`、`Information`、または `Verbose`</span><span class="sxs-lookup"><span data-stu-id="e73bf-133">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|  
|`ActivityTracing`|<span data-ttu-id="e73bf-134">`Start`、`Stop`、`Suspend`、`Resume`、または `Transfer`</span><span class="sxs-lookup"><span data-stu-id="e73bf-134">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|  
|`All`|<span data-ttu-id="e73bf-135">すべてのメッセージが許可されます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-135">All messages are allowed.</span></span>|  
|`Off`|<span data-ttu-id="e73bf-136">すべてのメッセージがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-136">All messages are blocked.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e73bf-137">`WriteEntry` メソッドと `WriteException` メソッドにはそれぞれ、重大度レベルを指定しないオーバー ロードがあります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-137">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="e73bf-138">`WriteEntry` オーバー ロードの暗黙的な重大度レベルは "Information" で、`WriteException` オーバー ロードの暗黙的な重大度レベルは "Error" です。</span><span class="sxs-lookup"><span data-stu-id="e73bf-138">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>  
  
 <span data-ttu-id="e73bf-139">次の表は、前の例に示したログ出力について説明したものです。 既定の `DefaultSwitch` 設定 (Information) では、`WriteEntry` メソッドに対する 2 番目の呼び出しと、`WriteException` メソッドに対する呼び出しでのみ、ログ出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-139">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="e73bf-140">アクティビティ トレース イベントだけを記録するには</span><span class="sxs-lookup"><span data-stu-id="e73bf-140">To log only activity tracing events</span></span>  
  
1.  <span data-ttu-id="e73bf-141">**ソリューション エクスプローラー**で app.config を右クリックし、**[開く]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-141">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>  
  
     <span data-ttu-id="e73bf-142">または</span><span class="sxs-lookup"><span data-stu-id="e73bf-142">-or-</span></span>  
  
     <span data-ttu-id="e73bf-143">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e73bf-143">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="e73bf-144">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-144">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="e73bf-145">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-145">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="e73bf-146">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-146">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="e73bf-147">最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションで、`<switches>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-147">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="e73bf-148">スイッチのコレクションに `DefaultSwitch` を追加する要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-148">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="e73bf-149">これは次のような要素です。</span><span class="sxs-lookup"><span data-stu-id="e73bf-149">It should look similar to this element:</span></span>  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  <span data-ttu-id="e73bf-150">`value` 属性の値を "ActivityTracing" に変更します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-150">Change the value of the `value` attribute to "ActivityTracing".</span></span>  
  
5.  <span data-ttu-id="e73bf-151">app.config ファイルの内容は次の XML のようになります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-151">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
6.  <span data-ttu-id="e73bf-152">デバッガーでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-152">Run the application in the debugger.</span></span>  
  
7.  <span data-ttu-id="e73bf-153">**[Button1]** を押します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-153">Press **Button1**.</span></span>  
  
     <span data-ttu-id="e73bf-154">アプリケーションは、アプリケーションのデバッグ出力とログ ファイルに次の情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-154">The application writes the following information to the application's debug output and log file:</span></span>  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  <span data-ttu-id="e73bf-155">アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-155">Close the application.</span></span>  
  
9. <span data-ttu-id="e73bf-156">`value` 属性の値を "Information" に戻します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-156">Change the value of the `value` attribute back to "Information".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e73bf-157">`DefaultSwitch` スイッチの設定では、`My.Application.Log` のみが制御されます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-157">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="e73bf-158">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] の <xref:System.Diagnostics.Trace?displayProperty=fullName> クラスと <xref:System.Diagnostics.Debug?displayProperty=fullName> クラスの動作が変えられることはありません。</span><span class="sxs-lookup"><span data-stu-id="e73bf-158">It does not change how the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=fullName> and <xref:System.Diagnostics.Debug?displayProperty=fullName> classes behave.</span></span>  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="e73bf-159">My.Application.Log リスナーの個別のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="e73bf-159">Individual Filtering For My.Application.Log Listeners</span></span>  
 <span data-ttu-id="e73bf-160">前の例では、すべての `My.Application.Log` 出力のフィルター処理を変更する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="e73bf-160">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="e73bf-161">この例では、個別のログ リスナーをフィルター処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-161">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="e73bf-162">既定では、アプリケーションには、アプリケーションのデバッグ出力とログ ファイルに情報を書き込む 2 つのリスナーがあります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-162">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>  
  
 <span data-ttu-id="e73bf-163">構成ファイルは、`My.Application.Log` のスイッチのように、各リスナーにフィルターを適用することで、ログ リスナーの動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-163">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="e73bf-164">ログ リスナーは、メッセージの重大度がログの `DefaultSwitch` とログ リスナーのフィルターの両方によって許可された場合にのみ、メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-164">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>  
  
 <span data-ttu-id="e73bf-165">この例では、新しいデバッグ リスナーのフィルター処理を構成し、それを `Log` オブジェクトに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-165">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="e73bf-166">デバッグ メッセージが新しいデバッグ リスナーから送られるようにするには、既定のデバッグ リスナーを `Log` オブジェクトから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-166">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>  
  
#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="e73bf-167">アクティビティ トレース イベントだけを記録するには</span><span class="sxs-lookup"><span data-stu-id="e73bf-167">To log only activity-tracing events</span></span>  
  
1.  <span data-ttu-id="e73bf-168">**ソリューション エクスプローラー**で app.config を右クリックし、**[開く]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-168">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="e73bf-169">または</span><span class="sxs-lookup"><span data-stu-id="e73bf-169">-or-</span></span>  
  
     <span data-ttu-id="e73bf-170">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e73bf-170">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="e73bf-171">**[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-171">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="e73bf-172">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-172">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="e73bf-173">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-173">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="e73bf-174">**ソリューション エクスプローラー**で app.config を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-174">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="e73bf-175">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e73bf-175">Choose **Open**.</span></span>  
  
3.  <span data-ttu-id="e73bf-176">`<sources>` セクション内にある、`name` 属性が "DefaultSource" の `<source>` セクションで、`<listeners>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-176">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="e73bf-177">`<sources>` セクションは、最上位の `<configuration>` セクション内の `<system.diagnostics>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-177">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
4.  <span data-ttu-id="e73bf-178">`<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-178">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  <span data-ttu-id="e73bf-179">最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-179">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="e73bf-180">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-180">Add this element to that `<sharedListeners>` section:</span></span>  
  
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
  
     <span data-ttu-id="e73bf-181"><xref:System.Diagnostics.EventTypeFilter> フィルターは <xref:System.Diagnostics.SourceLevels> 列挙値の 1 つをその `initializeData` 属性として取ります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-181">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>  
  
7.  <span data-ttu-id="e73bf-182">app.config ファイルの内容は次の XML のようになります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-182">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
8.  <span data-ttu-id="e73bf-183">デバッガーでアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-183">Run the application in the debugger.</span></span>  
  
9. <span data-ttu-id="e73bf-184">**[Button1]** を押します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-184">Press **Button1**.</span></span>  
  
     <span data-ttu-id="e73bf-185">アプリケーションは、アプリケーションのログ ファイルに次の情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e73bf-185">The application writes the following information to the application's log file:</span></span>  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     <span data-ttu-id="e73bf-186">フィルター処理の基準がより厳しくなったので、アプリケーションのデバッグ出力に書き込まれる情報は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="e73bf-186">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>  
  
     `Default Error   2   Error`  
  
10. <span data-ttu-id="e73bf-187">アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="e73bf-187">Close the application.</span></span>  
  
 <span data-ttu-id="e73bf-188">配置後にログの設定を変更する方法については、「[アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e73bf-188">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73bf-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="e73bf-189">See Also</span></span>  
 <span data-ttu-id="e73bf-190">[チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="e73bf-190">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 <span data-ttu-id="e73bf-191">[チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="e73bf-191">[Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span></span>  
 <span data-ttu-id="e73bf-192">[チュートリアル : カスタム ログ リスナーの作成](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md) </span><span class="sxs-lookup"><span data-stu-id="e73bf-192">[Walkthrough: Creating Custom Log Listeners](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md) </span></span>  
 <span data-ttu-id="e73bf-193">[方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="e73bf-193">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="e73bf-194">[トレース スイッチ](../../../../framework/debug-trace-profile/trace-switches.md) </span><span class="sxs-lookup"><span data-stu-id="e73bf-194">[Trace Switches](../../../../framework/debug-trace-profile/trace-switches.md) </span></span>  
 [<span data-ttu-id="e73bf-195">アプリケーションからの情報のログ記録</span><span class="sxs-lookup"><span data-stu-id="e73bf-195">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)


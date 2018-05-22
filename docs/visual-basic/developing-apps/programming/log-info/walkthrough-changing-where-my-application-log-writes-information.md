---
title: My.Application.Log による情報の書き込み先の変更 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: ab46f192f2e9549d0568737236742a366ce7b3a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="018be-102">チュートリアル: My.Application.Log による情報の書き込み先の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="018be-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="018be-103">`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="018be-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="018be-104">このチュートリアルでは、既定の設定をオーバーライドして、 `Log` オブジェクトによる書き込み先を他のログ リスナーに変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="018be-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="018be-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="018be-105">Prerequisites</span></span>  
 <span data-ttu-id="018be-106">`Log` オブジェクトは、複数のログ リスナーに情報を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="018be-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="018be-107">ログ リスナーの構成を変更する前に、現在の構成を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018be-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="018be-108">詳しくは、「[チュートリアル: My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="018be-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="018be-109">必要に応じて、「[方法 : イベント情報をテキスト ファイルに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)」または「[方法 : アプリケーション イベント ログに書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="018be-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="018be-110">リスナーを追加するには</span><span class="sxs-lookup"><span data-stu-id="018be-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="018be-111">**ソリューション エクスプローラー** で app.config を右クリックし、 **[開く]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="018be-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="018be-112">\- または</span><span class="sxs-lookup"><span data-stu-id="018be-112">\- or -</span></span>  
  
     <span data-ttu-id="018be-113">app.config ファイルがない場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="018be-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="018be-114">**[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="018be-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="018be-115">**[新しい項目の追加]** ダイアログ ボックスで、 **[アプリケーション構成ファイル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="018be-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="018be-116">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="018be-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="018be-117">`<listeners>` セクション内にある、 `<source>` 属性が "DefaultSource" の `name` セクションで、 `<sources>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="018be-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="018be-118">`<sources>` セクションは、最上位の `<system.diagnostics>` セクション内の `<configuration>` セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="018be-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="018be-119">その `<listeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="018be-119">Add these elements to that `<listeners>` section.</span></span>  
  
    ```xml  
    <!-- Uncomment to connect the application file log. -->  
    <!-- <add name="FileLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="EventLog" /> -->  
    <!-- Uncomment to connect the event log. -->  
    <!-- <add name="Delimited" /> -->  
    <!-- Uncomment to connect the XML log. -->  
    <!-- <add name="XmlWriter" /> -->  
    <!-- Uncomment to connect the console log. -->  
    <!-- <add name="Console" /> -->  
    ```  
  
4.  <span data-ttu-id="018be-120">`Log` のメッセージを受け取らせるログ リスナーをコメントから外します。</span><span class="sxs-lookup"><span data-stu-id="018be-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="018be-121">最上位の `<sharedListeners>` セクション内の `<system.diagnostics>` セクションで、 `<configuration>` セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="018be-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="018be-122">その `<sharedListeners>` セクションに次の要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="018be-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
    ```xml  
    <add name="FileLog"  
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
               Microsoft.VisualBasic, Version=8.0.0.0,   
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
         initializeData="FileLogWriter" />  
    <add name="EventLog"  
         type="System.Diagnostics.EventLogTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="sample application"/>  
    <add name="Delimited"   
         type="System.Diagnostics.DelimitedListTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleDelimitedFile.txt"  
         traceOutputOptions="DateTime" />  
    <add name="XmlWriter"  
         type="System.Diagnostics.XmlWriterTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="c:\temp\sampleLogFile.xml" />  
    <add name="Console"  
         type="System.Diagnostics.ConsoleTraceListener,   
               System, Version=2.0.0.0,   
               Culture=neutral, PublicKeyToken=b77a5c561934e089"  
         initializeData="true" />  
    ```  
  
7.  <span data-ttu-id="018be-123">app.config ファイルの内容は次の XML のようになります。</span><span class="sxs-lookup"><span data-stu-id="018be-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Uncomment to connect the application file log. -->  
              <!-- <add name="FileLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="EventLog" /> -->  
              <!-- Uncomment to connect the event log. -->  
              <!-- <add name="Delimited" /> -->  
              <!-- Uncomment to connect the XML log. -->  
              <!-- <add name="XmlWriter" /> -->  
              <!-- Uncomment to connect the console log. -->  
              <!-- <add name="Console" /> -->  
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
               initializeData="FileLogWriter" />  
          <add name="EventLog"  
               type="System.Diagnostics.EventLogTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="sample application"/>  
          <add name="Delimited"   
               type="System.Diagnostics.DelimitedListTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleDelimitedFile.txt"  
               traceOutputOptions="DateTime" />  
          <add name="XmlWriter"  
               type="System.Diagnostics.XmlWriterTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="c:\temp\sampleLogFile.xml" />  
          <add name="Console"  
               type="System.Diagnostics.ConsoleTraceListener,   
                     System, Version=2.0.0.0,   
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"  
               initializeData="true" />  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="018be-124">リスナーを再構成するには</span><span class="sxs-lookup"><span data-stu-id="018be-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="018be-125">`<add>` セクションで、リスナーの `<sharedListeners>` 要素を見つけます。</span><span class="sxs-lookup"><span data-stu-id="018be-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="018be-126">`type` 属性はリスナーの型の名前を表します。</span><span class="sxs-lookup"><span data-stu-id="018be-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="018be-127">この型は <xref:System.Diagnostics.TraceListener> クラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018be-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="018be-128">正しい型が確実に使用されるよう、型名には厳密な名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="018be-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="018be-129">詳細については、後述の「厳密な名前を指定された型を参照するには」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="018be-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="018be-130">使用できる型のいくつかを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="018be-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="018be-131"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> リスナー。ファイル ログに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="018be-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="018be-132"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> リスナー。`initializeData` パラメーターで指定された、コンピューターのイベント ログに情報を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="018be-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="018be-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> リスナーおよび <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> リスナー。`initializeData` パラメーターで指定されたファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="018be-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="018be-134"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> リスナー。コマンド ライン コンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="018be-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="018be-135">他の型のログ リスナーが情報を書き込む先については、その型のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="018be-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="018be-136">アプリケーションは、ログ リスナー オブジェクトを作成するときに、コンストラクターのパラメーターとして `initializeData` 属性を渡します。</span><span class="sxs-lookup"><span data-stu-id="018be-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="018be-137">`initializeData` 属性の意味はトレース リスナーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="018be-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="018be-138">ログ リスナーの作成後にアプリケーションはリスナーのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="018be-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="018be-139">これらのプロパティは、 `<add>` 要素の他の属性で定義されています。</span><span class="sxs-lookup"><span data-stu-id="018be-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="018be-140">特定のリスナーのプロパティの詳細については、そのリスナーの型のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="018be-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="018be-141">厳密な名前を指定された型を参照するには</span><span class="sxs-lookup"><span data-stu-id="018be-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="018be-142">ログ リスナーとして正しい型を確実に使用するために、完全修飾型名と厳密な名前のアセンブリ名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018be-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="018be-143">厳密な名前を指定された型の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="018be-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="018be-144">\<*型名*>, \<*アセンブリ名*>, \<*バージョン番号*>, \<*カルチャ*>, \<*厳密な名前*></span><span class="sxs-lookup"><span data-stu-id="018be-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="018be-145">次のコード例は、完全修飾された型の厳密な名前を確認する方法を示します。この例では "System.Diagnostics.FileLogTraceListener" です。</span><span class="sxs-lookup"><span data-stu-id="018be-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     <span data-ttu-id="018be-146">次に示すのが出力です。これを使用して、前述の「リスナーを追加するには」の手順で示した方法で、厳密な名前を指定された型を一意に参照できます。</span><span class="sxs-lookup"><span data-stu-id="018be-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="018be-147">参照</span><span class="sxs-lookup"><span data-stu-id="018be-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [<span data-ttu-id="018be-148">方法 : イベント情報をテキスト ファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="018be-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [<span data-ttu-id="018be-149">方法 : アプリケーション イベント ログに書き込む</span><span class="sxs-lookup"><span data-stu-id="018be-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)

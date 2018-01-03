---
title: "方法 : トレース リスナーを作成し初期化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ebc50e4075a5793c344cbc017eb60247c1c8774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="8b860-102">方法 : トレース リスナーを作成し初期化する</span><span class="sxs-lookup"><span data-stu-id="8b860-102">How to: Create and Initialize Trace Listeners</span></span>
<span data-ttu-id="8b860-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> クラスと <xref:System.Diagnostics.Trace?displayProperty=nameWithType> クラスは、メッセージの受け取りと処理を実行する、リスナーと呼ばれるオブジェクトにメッセージを送ります。</span><span class="sxs-lookup"><span data-stu-id="8b860-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="8b860-104">トレースまたはデバッグを有効にすると、こうしたリスナーの 1 つである <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType> が自動的に作成および初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8b860-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="8b860-105"><xref:System.Diagnostics.Trace> または <xref:System.Diagnostics.Debug> の出力を別のソースに送るには、別のトレース リスナーを作成して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b860-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>  
  
 <span data-ttu-id="8b860-106">作成するリスナーには、アプリケーションのニーズが反映されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b860-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="8b860-107">たとえば、すべてのトレース出力のテキスト レコードが必要である場合は、有効になったときにすべての出力を新しいテキスト ファイルに書き込む <xref:System.Diagnostics.TextWriterTraceListener> リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b860-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="8b860-108">一方、アプリケーションの実行時にのみ出力を表示する場合は、すべての出力をコンソール ウィンドウに送る <xref:System.Diagnostics.ConsoleTraceListener> リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="8b860-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="8b860-109"><xref:System.Diagnostics.EventLogTraceListener> は、トレース出力をイベント ログに転送することができます。</span><span class="sxs-lookup"><span data-stu-id="8b860-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="8b860-110">詳細については、「[トレース リスナー](../../../docs/framework/debug-trace-profile/trace-listeners.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b860-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>  
  
 <span data-ttu-id="8b860-111">トレース リスナーは、[アプリケーション構成ファイル](../../../docs/framework/configure-apps/index.md)またはコードで作成できます。</span><span class="sxs-lookup"><span data-stu-id="8b860-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="8b860-112">アプリケーション構成ファイルではコードを変更せずにトレース リスナーを追加、変更、または削除できるので、アプリケーション構成ファイルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8b860-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="8b860-113">構成ファイルを使用してトレース リスナーを作成して使用するには</span><span class="sxs-lookup"><span data-stu-id="8b860-113">To create and use a trace listener by using a configuration file</span></span>  
  
1.  <span data-ttu-id="8b860-114">アプリケーション構成ファイルでトレース リスナーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8b860-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="8b860-115">作成しているリスナーで他のオブジェクトが必要な場合は、必要なオブジェクトも宣言します。</span><span class="sxs-lookup"><span data-stu-id="8b860-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="8b860-116">テキスト ファイル `TextWriterOutput.log` への書き込みを実行する `myListener` というリスナーの作成方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8b860-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <trace autoflush="false" indentsize="4">  
          <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />  
            <remove name="Default" />  
          </listeners>  
        </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
2.  <span data-ttu-id="8b860-117">コードで <xref:System.Diagnostics.Trace> クラスを使用して、メッセージをトレース リスナーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="8b860-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>  
  
    ```vb  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="8b860-118">コードでトレース リスナーを作成して使用するには</span><span class="sxs-lookup"><span data-stu-id="8b860-118">To create and use a trace listener in code</span></span>  
  
-   <span data-ttu-id="8b860-119">トレース リスナーを <xref:System.Diagnostics.Trace.Listeners%2A> コレクションに追加し、トレース情報をリスナーに送ります。</span><span class="sxs-lookup"><span data-stu-id="8b860-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>  
  
    ```vb  
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
     - <span data-ttu-id="8b860-120">または</span><span class="sxs-lookup"><span data-stu-id="8b860-120">or -</span></span>  
  
-   <span data-ttu-id="8b860-121">リスナーがトレース出力を受け取らないようにするには、リスナーを <xref:System.Diagnostics.Trace.Listeners%2A> コレクションに追加しないようにします。</span><span class="sxs-lookup"><span data-stu-id="8b860-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="8b860-122">リスナー自体の出力メソッドを呼び出すことにより、<xref:System.Diagnostics.Trace.Listeners%2A> コレクションから独立したリスナーを通じて出力を生成できます。</span><span class="sxs-lookup"><span data-stu-id="8b860-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="8b860-123"><xref:System.Diagnostics.Trace.Listeners%2A> コレクションに属さないリスナーに行を書き込む方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8b860-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>  
  
    ```vb  
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")  
    myListener.WriteLine("Test message.")  
    ' You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush()  
    ```  
  
    ```csharp  
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");  
    myListener.WriteLine("Test message.");  
    // You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8b860-124">参照</span><span class="sxs-lookup"><span data-stu-id="8b860-124">See Also</span></span>  
 [<span data-ttu-id="8b860-125">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="8b860-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="8b860-126">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="8b860-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="8b860-127">方法 : アプリケーション コードにトレース ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="8b860-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="8b860-128">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="8b860-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

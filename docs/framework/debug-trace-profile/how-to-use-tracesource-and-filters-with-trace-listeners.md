---
title: "方法 : TraceSource とフィルターをトレース リスナーと共に使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b557a9f9f462df2d1afe6d6b61871e0e9f40174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="59492-102">方法 : TraceSource とフィルターをトレース リスナーと共に使用する</span><span class="sxs-lookup"><span data-stu-id="59492-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="59492-103">.NET Framework Version 2.0 の新機能の 1 つは、強化されたトレース システムです。</span><span class="sxs-lookup"><span data-stu-id="59492-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="59492-104">基本的な前提は変更されていません。トレース メッセージはスイッチ経由でリスナーに送信され、関連付けられている出力メディアに、データを報告します。</span><span class="sxs-lookup"><span data-stu-id="59492-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="59492-105">バージョン 2.0 の主な違いは、<xref:System.Diagnostics.TraceSource> クラスのインスタンスを介してトレースを開始できることです。</span><span class="sxs-lookup"><span data-stu-id="59492-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="59492-106"><xref:System.Diagnostics.TraceSource> は、拡張されたトレース システムとして機能することを目的としており、以前の <xref:System.Diagnostics.Trace> トレース クラスと <xref:System.Diagnostics.Debug> トレース クラスの静的メソッドの代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="59492-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="59492-107">使い慣れた <xref:System.Diagnostics.Trace> クラスと <xref:System.Diagnostics.Debug> クラスがまだ存在していますが、推奨される方法は、<xref:System.Diagnostics.TraceSource> クラスを使用したトレースです。</span><span class="sxs-lookup"><span data-stu-id="59492-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="59492-108">このトピックでは、アプリケーション構成ファイルと組み合わせた <xref:System.Diagnostics.TraceSource> の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59492-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="59492-109">可能であれば、推奨されませんが、構成ファイルを使用せずに <xref:System.Diagnostics.TraceSource> を使用してトレースすることもできます。</span><span class="sxs-lookup"><span data-stu-id="59492-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="59492-110">構成ファイルを使わずにトレースする方法の詳細については、「[How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)」(方法: トレース ソースを作成し初期化する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59492-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="59492-111">トレース ソースを作成して初期化するには</span><span class="sxs-lookup"><span data-stu-id="59492-111">To create and initialize your trace source</span></span>  
  
1.  <span data-ttu-id="59492-112">トレースをアプリケーションにインストルメント化する最初の手順では、トレース ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="59492-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="59492-113">各種のコンポーネントを含む大規模なプロジェクトでは、コンポーネントごとに個別のトレース ソースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="59492-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="59492-114">トレース ソース名にアプリケーション名を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="59492-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="59492-115">これにより、別のトレースを容易に別々に保管できます。</span><span class="sxs-lookup"><span data-stu-id="59492-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="59492-116">次のコードでは、新しいトレース ソース (`mySource)`) を作成し、イベントをトレースするメソッド (`Activity1`) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="59492-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="59492-117">トレース メッセージは、既定のトレース リスナーによって書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="59492-117">The trace messages are written by the default trace listener.</span></span>  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="59492-118">トレース リスナーとフィルターを作成し初期化するには</span><span class="sxs-lookup"><span data-stu-id="59492-118">To create and initialize trace listeners and filters</span></span>  
  
1.  <span data-ttu-id="59492-119">最初の手順で示すコードは、トレース リスナーまたはフィルターをプログラム的に識別しません。</span><span class="sxs-lookup"><span data-stu-id="59492-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="59492-120">このコードだけでは、トレース メッセージが既定のトレース リスナーに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="59492-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="59492-121">特定のトレース リスナーと関連付けられているフィルターを構成するには、アプリケーションの名前に対応する構成ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="59492-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="59492-122">このファイルで、リスナーの追加または削除、リスナーのプロパティとフィルターの設定、またはリスナーの削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="59492-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="59492-123">次の構成ファイルの例は、コンソール トレース リスナーと、前の手順で作成されたトレース ソースのテキスト ライター トレース リスナーを初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="59492-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="59492-124">この構成ファイルは、トレース リスナーを設定するだけでなく、両方のリスナーについてフィルターを作成し、トレース ソースのソース スイッチも作成します。</span><span class="sxs-lookup"><span data-stu-id="59492-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="59492-125">トレース リスナーを追加する 2 つの方法が示されています。1 つは、リスナーをトレース ソースに直接追加する方法で、もう 1 つは、リスナーを共有リスナー コレクションに追加したうえで、名前でリスナーをトレース ソースに追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="59492-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="59492-126">2 つのリスナーに対して識別されたフィルターは、異なるソース レベルで初期化されます。</span><span class="sxs-lookup"><span data-stu-id="59492-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="59492-127">この結果、一部のメッセージが 2 つのリスナーのいずれか一方のみによって書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="59492-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="59492-128">リスナーが、トレース メッセージを書き込むレベルを変更するには</span><span class="sxs-lookup"><span data-stu-id="59492-128">To change the level at which a listener writes a trace message</span></span>  
  
1.  <span data-ttu-id="59492-129">構成ファイルは、アプリケーションが初期化されるときにトレース ソースの設定を初期化します。</span><span class="sxs-lookup"><span data-stu-id="59492-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="59492-130">それらの設定を変更するには、構成ファイルを変更してアプリケーションを再起動するか、または <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってアプリケーションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59492-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59492-131">アプリケーションは、構成ファイルによって設定されたプロパティを動的に変更し、ユーザーによって指定された設定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="59492-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="59492-132">たとえば、現在の構成設定とは無関係に、警告メッセージが常にテキスト ファイルに送られるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="59492-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59492-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="59492-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="59492-134">方法: を作成し、トレース ソースの初期化</span><span class="sxs-lookup"><span data-stu-id="59492-134">How to: Create and Initialize Trace Sources</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [<span data-ttu-id="59492-135">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="59492-135">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)

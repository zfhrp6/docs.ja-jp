---
title: '方法: トレース ソースを作成し初期化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07c4d65e3fb6d61ae5d1b766c70cbb25d54bdc7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="7d9d2-102">方法: トレース ソースを作成し初期化する</span><span class="sxs-lookup"><span data-stu-id="7d9d2-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="7d9d2-103"><xref:System.Diagnostics.TraceSource> クラスをアプリケーションで使用すると、アプリケーションに関連付けることができるトレースを生成できます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="7d9d2-104"><xref:System.Diagnostics.TraceSource> は、イベントのトレース、データのトレース、および情報トレースの発行を簡単に実行できるトレース メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="7d9d2-105"><xref:System.Diagnostics.TraceSource> からのトレース出力は、構成ファイルを使用してもしなくても作成および初期化できます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="7d9d2-106">このトピックでは、この両方の手順について説明しています。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="7d9d2-107">ただし、実行時にトレース ソースによって作成されるトレースの再構成を容易にするために構成ファイルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="7d9d2-108">構成ファイルを使用してトレース ソースを作成し、初期化するには</span><span class="sxs-lookup"><span data-stu-id="7d9d2-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="7d9d2-109">Visual Studio コンソール アプリケーション プロジェクトを作成し、提供されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="7d9d2-110">このコードは、エラーや警告を記録し、コンソールと、構成ファイルのエントリによって作成された myListener ファイルにその一部をそれぞれ出力します。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  <span data-ttu-id="7d9d2-111">アプリケーション構成ファイルが存在しない場合は、アプリケーション構成ファイルをプロジェクトに追加して、手順 1. のコード例にある `TraceSourceApp` というトレース ソースを初期化します。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="7d9d2-112">既定の構成ファイルの内容を以下の設定に置き換えて、コンソール トレース リスナーと、手順 1. で作成されたトレース ソースのテキスト ライター トレース リスナーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
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
  
     <span data-ttu-id="7d9d2-113">この構成ファイルは、トレース リスナーを設定するだけでなく、両方のリスナーについてフィルターを作成し、トレース ソースのソース スイッチも作成します。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="7d9d2-114">トレース リスナーを追加する 2 つの方法が示されています。1 つは、リスナーをトレース ソースに直接追加する方法で、もう 1 つは、リスナーを共有リスナー コレクションに追加したうえで、名前でリスナーをトレース ソースに追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="7d9d2-115">2 つのリスナーに対して識別されたフィルターは、異なるソース レベルで初期化されます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="7d9d2-116">この結果、一部のメッセージが 2 つのリスナーのいずれか一方のみによって書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="7d9d2-117">構成ファイルは、アプリケーションが初期化されるときにトレース ソースの設定を初期化します。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="7d9d2-118">アプリケーションは、構成ファイルによって設定されたプロパティを動的に変更し、ユーザーによって指定された設定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="7d9d2-119">たとえば、現在の構成設定とは無関係に、警告メッセージが常にテキスト ファイルに送られるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="7d9d2-120">このプログラム例は、構成ファイルの設定値をオーバーライドして、警告メッセージがトレース リスナーに出力されるようにする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="7d9d2-121">アプリケーションの実行中に構成ファイルの設定値を変更しても、初期設定は変更されません。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="7d9d2-122">設定を変更するには、アプリケーションを再起動するか、または <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> メソッドを使用して、プログラムによってアプリケーションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="7d9d2-123">構成ファイルを使わずにトレース ソース、リスナー、およびフィルターを初期化するには</span><span class="sxs-lookup"><span data-stu-id="7d9d2-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="7d9d2-124">次のプログラム例を使用すると、構成ファイルを使わずにトレース ソース全体のトレースが有効になります。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="7d9d2-125">この方法はお勧めできませんが、構成ファイルに依存しないでトレース機能を確保する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7d9d2-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7d9d2-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d9d2-126">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="7d9d2-127">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="7d9d2-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

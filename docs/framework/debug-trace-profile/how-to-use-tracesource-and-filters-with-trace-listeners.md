---
title: "How to: Use TraceSource and Filters with Trace Listeners | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "initializing trace listeners"
  - "configuration files [.NET Framework], trace listeners"
  - "app.config files, trace listeners"
  - "levels of writing trace messages"
  - "trace listeners, TraceSource class"
  - "application configuration files, trace listeners"
  - "filters, trace listeners"
  - "TraceSource class, trace listeners"
  - "trace listeners, creating"
  - "trace listeners, filters"
  - "trace listeners, initializing"
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Use TraceSource and Filters with Trace Listeners
.NET Framework Version 2.0 の新機能の 1 つが拡張されたトレース システムです。  基本的な前提は変わっていません。つまり、トレース メッセージはスイッチを介してリスナーに送信され、リスナーは関連付けられている出力媒体にデータを報告します。  Version 2.0 の前バージョンとの大きな違いは、トレースが <xref:System.Diagnostics.TraceSource> クラスのインスタンスを使用して開始できるという点です。  <xref:System.Diagnostics.TraceSource> は拡張されたトレース システムとして機能するためのもので、以前の <xref:System.Diagnostics.Trace> トレース クラスと <xref:System.Diagnostics.Debug> トレース クラスの静的メソッドの代わりに使用できます。  前バージョンの <xref:System.Diagnostics.Trace> クラスと <xref:System.Diagnostics.Debug> クラスも引き続き使用できますが、トレースには <xref:System.Diagnostics.TraceSource> クラスを使用することをお勧めします。  
  
 ここでは、アプリケーション構成ファイルと合わせて <xref:System.Diagnostics.TraceSource> を使用する方法について説明します。トレースは、構成ファイルを使用せずに <xref:System.Diagnostics.TraceSource> のみを使用して実行することもできますが、お勧めできません。  構成ファイルを使用しないトレースについては、「[方法: トレース ソースを作成し初期化する](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)」を参照してください。  
  
### トレース ソースを作成および初期化するには  
  
1.  アプリケーションにトレース機能をインストルメントするには、最初にトレース ソースを作成します。  さまざまなコンポーネントを含む大型のプロジェクトでは、コンポーネントごとに別個のトレース ソースを作成できます。  トレース ソースの名前には、アプリケーション名を使用することをお勧めします。  これにより、個々のトレースを別々に維持することが容易になります。  次のコードでは、新しいトレース ソース \(`mySource`\) を作成し、イベントをトレースするメソッド \(`Activity1`\) を呼び出します。トレース メッセージは、既定のトレース リスナーによって書き込まれます。  
  
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
  
### トレース リスナーとフィルターを作成および初期化するには  
  
1.  最初のプロシージャのコードは、トレース リスナーとフィルターをプログラムによって識別しません。  このコードでは、単にトレース メッセージが既定のトレース リスナーに書き込まれるだけです。  特定のトレース リスナーとその関連フィルターを設定するには、アプリケーションの名前に対応する構成ファイルを編集します。  このファイルでは、リスナーを追加または削除したり、リスナーのプロパティとフィルターを設定したりできます。また、複数のリスナーを削除することもできます。  前のプロシージャで作成したトレース ソースに対するコンソール トレース リスナーとテキスト ライター トレース リスナーを初期化する方法を次の構成ファイルの例に示します。  この構成ファイルは、トレース リスナーを設定するだけでなく、両方のリスナーについてフィルターを作成し、トレース ソースのソース スイッチも作成します。  トレース リスナーを追加する 2 つの方法が示されています。1 つは、リスナーをトレース ソースに直接追加する方法で、もう 1 つは、リスナーを共有リスナー コレクションに追加したうえで、名前でリスナーをトレース ソースに追加する方法です。  2 つのリスナーに対して識別されたフィルターは、異なるソース レベルで初期化されます。  この結果、一部のメッセージが 2 つのリスナーのいずれか一方のみによって書き込まれます。  
  
    ```  
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
  
### リスナーがトレース メッセージを書き込むレベルを変更するには  
  
1.  構成ファイルは、アプリケーションが初期化されるときにトレース ソースの設定を初期化します。  この設定を変更するには、構成ファイルを変更し、アプリケーションを再起動するか、または <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=fullName> メソッドを使用して、プログラムによってアプリケーションを更新する必要があります。  アプリケーションは、構成ファイルによって設定されたプロパティを動的に変更し、ユーザーによって指定された設定値をオーバーライドできます。たとえば、現在の構成設定とは関係なく、警告メッセージが常にテキスト ファイルに送られるようにすることもできます。  
  
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
  
## 参照  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics.EventTypeFilter>   
 [方法: トレース ソースを作成し初期化する](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)   
 [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md)
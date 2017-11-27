---
title: "トレースとメッセージ ログの推奨設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6986c775db50ea5b763288f8f3b9bdcf1bf7e67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="686a8-102">トレースとメッセージ ログの推奨設定</span><span class="sxs-lookup"><span data-stu-id="686a8-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="686a8-103">このトピックでは、さまざまな動作環境における、推奨されるトレースとメッセージ ログの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="686a8-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="686a8-104">本運用環境での推奨される設定</span><span class="sxs-lookup"><span data-stu-id="686a8-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="686a8-105">本運用環境で WCF トレース ソースを使用する場合は、`switchValue` を Warning に設定します。</span><span class="sxs-lookup"><span data-stu-id="686a8-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="686a8-106">WCF `System.ServiceModel` トレース ソースを使用する場合は、`switchValue` 属性を `Warning` に設定し、`propagateActivity` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="686a8-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="686a8-107">ユーザー定義のトレース ソースを使用する場合は、`switchValue` 属性を `Warning, ActivityTracing` に設定します。</span><span class="sxs-lookup"><span data-stu-id="686a8-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="686a8-108">これを使用して手動で、[構成エディター ツール (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="686a8-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="686a8-109">前述のすべての場合において、パフォーマンスに影響しないと思われる場合は、`switchValue` 属性を `Information` に設定できます。これにより、相当な量のトレース データが生成されます。</span><span class="sxs-lookup"><span data-stu-id="686a8-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="686a8-110">次の例に、これらの推奨設定を示します。</span><span class="sxs-lookup"><span data-stu-id="686a8-110">The following example demonstrates these recommended settings.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="686a8-111">展開またはデバッグでの推奨される設定</span><span class="sxs-lookup"><span data-stu-id="686a8-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="686a8-112">展開またはデバッグ環境では、`Information` または `Verbose` を選択すると共に、ユーザー定義のトレース ソースまたは `ActivityTracing` トレース ソースの場合は `System.ServiceModel` を選択します。</span><span class="sxs-lookup"><span data-stu-id="686a8-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="686a8-113">また、デバッグ機能を向上させるには、トレース ソース (`System.ServiceModel.MessageLogging`) を構成に追加してメッセージ ログを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="686a8-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="686a8-114">`switchValue` 属性はこのトレース ソースに影響しません。</span><span class="sxs-lookup"><span data-stu-id="686a8-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="686a8-115">次の例に、`XmlWriterTraceListener` を利用した共有リスナーを使用する推奨設定を示します。</span><span class="sxs-lookup"><span data-stu-id="686a8-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="686a8-116">WMI を使用した設定変更</span><span class="sxs-lookup"><span data-stu-id="686a8-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="686a8-117">WMI を使用して実行時に構成設定を変更できます (前述の構成例のように構成の `wmiProviderEnabled` 属性を有効にします)。</span><span class="sxs-lookup"><span data-stu-id="686a8-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="686a8-118">たとえば、CIM Studio 内で WMI を使用し、実行時にトレース ソース レベルを Warning から Information に変更できます。</span><span class="sxs-lookup"><span data-stu-id="686a8-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="686a8-119">この方法でライブ デバッグを実行した場合のパフォーマンスへの負荷は非常に高くなる可能性があるので注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="686a8-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="686a8-120">詳細については、WMI を使用して、次を参照してください。、[診断の Windows Management Instrumentation を使用して](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="686a8-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="686a8-121">ASP.NET トレースでの相関イベントの有効化</span><span class="sxs-lookup"><span data-stu-id="686a8-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="686a8-122">ASP.NET イベントでは、ASP.NET イベントのトレースが有効になっていないと、相関 ID (ActivityID) が設定されません。</span><span class="sxs-lookup"><span data-stu-id="686a8-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="686a8-123">相関イベントを適切に表示するには ASP.NET イベントを有効にする必要があるコマンド コンソールで、次のコマンドを使用してトレースを呼び出すことができますに移動して**開始**、**実行**および種類**cmd**,</span><span class="sxs-lookup"><span data-stu-id="686a8-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="686a8-124">ASP.NET イベントのトレースを無効にするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="686a8-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="686a8-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="686a8-125">See Also</span></span>  
 [<span data-ttu-id="686a8-126">Windows Management Instrumentation を使用して、詳細な診断</span><span class="sxs-lookup"><span data-stu-id="686a8-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)

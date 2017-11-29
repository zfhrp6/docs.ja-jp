---
title: "トレースとメッセージ ログ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: "53"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a73c6e544b7aae003a525c29743d68db18a54515
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="177b8-102">トレースとメッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="177b8-102">Tracing and Message Logging</span></span>
<span data-ttu-id="177b8-103">このサンプルでは、トレースとメッセージ ログを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="177b8-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="177b8-104">結果のトレースとメッセージ ログを使用して表示、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="177b8-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="177b8-105">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="177b8-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="177b8-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177b8-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="177b8-107">トレース</span><span class="sxs-lookup"><span data-stu-id="177b8-107">Tracing</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="177b8-108"> では、<xref:System.Diagnostics> 名前空間で定義されたトレース機構が使用されます。</span><span class="sxs-lookup"><span data-stu-id="177b8-108"> uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="177b8-109">このトレース モデルのトレース データは、アプリケーションが実装するトレース ソースによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="177b8-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="177b8-110">各ソースは、名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="177b8-110">Each source is identified by a name.</span></span> <span data-ttu-id="177b8-111">トレース コンシューマでは、情報を取得するトレース ソースのトレース リスナが作成されます。</span><span class="sxs-lookup"><span data-stu-id="177b8-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="177b8-112">トレース データを受け取るには、トレース ソースのリスナを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="177b8-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="177b8-113">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこれを行うには、サービス モデルのトレース ソース `switchValue` を設定することにより、次のコードをサービスまたはクライアントのどちらかの構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="177b8-113">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="177b8-114">トレース ソースの詳細については、トレース ソースのセクションを参照してください、[トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="177b8-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="177b8-115">アクティビティのトレースと伝達</span><span class="sxs-lookup"><span data-stu-id="177b8-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="177b8-116">持つ`ActivityTracing`有効になっていると`propagateActivity`'éý'`true`で、`system.ServiceModel`トレース ソースに、クライアントとサービスの両方のエンドポイント (内のアクティビティ間 (アクティビティ) の処理の論理単位内のトレースの相関関係を提供します。アクティビティ転送を使用)、および複数のエンドポイント (アクティビティ ID の伝達) にわたるアクティビティ間です。</span><span class="sxs-lookup"><span data-stu-id="177b8-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="177b8-117">3 つの機構 (アクティビティ、転送、および伝達) により、サービス トレース ビューア ツールを使用してエラーの根本原因をより迅速に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="177b8-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="177b8-118">詳細については、次を参照してください。[相関トレースの表示とトラブルシューティング サービス トレース ビューアーを使用して](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)です。</span><span class="sxs-lookup"><span data-stu-id="177b8-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="177b8-119">ユーザー定義のアクティビティ トレースを作成することにより、サービス モデルによって提供されるトレースを拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="177b8-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="177b8-120">ユーザー定義のアクティビティ トレースによって、次の操作を可能にするトレース アクティビティを作成できます。</span><span class="sxs-lookup"><span data-stu-id="177b8-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="177b8-121">複数のトレースを作業の論理単位ごとにグループ化します。</span><span class="sxs-lookup"><span data-stu-id="177b8-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="177b8-122">転送や伝達を利用してアクティビティを相互に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="177b8-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="177b8-123">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トレースのパフォーマンスの負荷 (ログ ファイルによるディスク領域の負荷など) を軽減します。</span><span class="sxs-lookup"><span data-stu-id="177b8-123">Lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="177b8-124">ユーザー定義のアクティビティ トレースの詳細についてを参照してください、[トレースを拡張する](../../../../docs/framework/wcf/samples/extending-tracing.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="177b8-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="177b8-125">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="177b8-125">Message Logging</span></span>  
 <span data-ttu-id="177b8-126">メッセージ ログは、任意の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションのクライアントとサービスの両方で有効にできます。</span><span class="sxs-lookup"><span data-stu-id="177b8-126">Message logging can be enabled both on the client and service of any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="177b8-127">メッセージ ログを有効にするには、クライアントとサービスのどちらかに次のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="177b8-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="177b8-128">メッセージが記録されるときのトレースの種類は、そのメッセージがクライアントでトレースされるか、またはサーバーでトレースされるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="177b8-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="177b8-129">たとえば、クライアントに送信される "Add" メッセージは、クライアントでは "TransportWrite" カテゴリの下でトレースされるのに対し、サービスでは同じメッセージが "TransportRead" カテゴリの下でトレースされます。</span><span class="sxs-lookup"><span data-stu-id="177b8-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="177b8-130">クライアントの App.config ファイルまたはサービスの Web.config ファイルの <xref:System.Diagnostics> セクションに次のコードを追加して、トレース リスナを構成します。</span><span class="sxs-lookup"><span data-stu-id="177b8-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="177b8-131">メッセージは、構成ファイルで指定された対象ディレクトリ内に XML 形式で記録されます。</span><span class="sxs-lookup"><span data-stu-id="177b8-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="177b8-132">最初にログ ディレクトリが作成されていないと、トレース ファイルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="177b8-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="177b8-133">ディレクトリ C:\logs\ が存在することを確認するか、またはリスナの構成でログ記録用の代替ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="177b8-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="177b8-134">詳細については、このドキュメントの最後にある初期セットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="177b8-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="177b8-135">メッセージのログ記録の詳細については、次を参照してください。、[メッセージ ログの構成](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="177b8-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="177b8-136">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="177b8-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="177b8-137">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="177b8-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="177b8-138">トレースとメッセージ ログのサンプルを実行する前に、サービスによって .svclog ファイルが書き込まれるディレクトリ C:\logs\ を作成します。</span><span class="sxs-lookup"><span data-stu-id="177b8-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="177b8-139">このディレクトリ名は、トレースとメッセージがログ記録されるパスとして、構成ファイル内で定義されます。この名前は変更可能です。</span><span class="sxs-lookup"><span data-stu-id="177b8-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="177b8-140">ユーザー Network Service に、そのログ ディレクトリへの書き込みアクセスを与えます。</span><span class="sxs-lookup"><span data-stu-id="177b8-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="177b8-141">C#、C++、または Visual Basic .NET のバージョンのソリューションをビルドするの指示に従って、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="177b8-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="177b8-142">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="177b8-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="177b8-143">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="177b8-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="177b8-144">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="177b8-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="177b8-145">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="177b8-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="177b8-146">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="177b8-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="177b8-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="177b8-147">See Also</span></span>  
 [<span data-ttu-id="177b8-148">トレース</span><span class="sxs-lookup"><span data-stu-id="177b8-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="177b8-149">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="177b8-149">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)

---
title: "相関関係のトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea348811a1b2dbd19254f6979a5165c821aa31e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="ab897-102">相関関係のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ab897-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="ab897-103">相関関係は、ワークフロー サービス メッセージを互いに関連付けたり、正しいワークフロー インスタンスに関連付けたりするために使用されますが、正しく構成されていないと、メッセージが受信されず、アプリケーションが正しく機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="ab897-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="ab897-104">ここでは、相関関係のトラブルシューティングのいくつかの方法の概要と、相関関係を使用するときに発生する一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab897-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>  
  
## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="ab897-105">UnknownMessageReceived イベントの処理</span><span class="sxs-lookup"><span data-stu-id="ab897-105">Handle the UnknownMessageReceived Event</span></span>  
 <span data-ttu-id="ab897-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> イベントは、サービスで不明なメッセージ (既存のインスタンスに関連付けることができないメッセージなど) が受信されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="ab897-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="ab897-107">自己ホスト型サービスでは、このイベントをホスト アプリケーションで処理できます。</span><span class="sxs-lookup"><span data-stu-id="ab897-107">For self-hosted services, this event can be handled in the host application.</span></span>  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 <span data-ttu-id="ab897-108">Web ホスト サービスでこのイベントを処理するには、まず、<xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> の派生クラスを作成し、<xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A> をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ab897-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>  
  
```csharp  
class CustomFactory : WorkflowServiceHostFactory  
{  
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)  
    {  
        // Create the WorkflowServiceHost.  
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);  
  
        // Handle the UnknownMessageReceived event.  
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
        {  
            Console.WriteLine("Unknown Message Received:");  
            Console.WriteLine(e.Message);  
        };  
  
        return host;  
    }  
}  
```  
  
 <span data-ttu-id="ab897-109">次に、そのカスタムの <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> をサービスの `svc` ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="ab897-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 <span data-ttu-id="ab897-110">このハンドラーが呼び出されると、<xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> の <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> プロパティを使用して次のようなメッセージを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ab897-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>  
  
```Output  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
  </s:Header>  
  <s:Body>  
    <AddItem xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItem>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ab897-111"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> ハンドラーにディスパッチされたメッセージを調べることで、メッセージがワークフロー サービスのインスタンスに関連付けられなかった理由の手がかりを得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ab897-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="ab897-112">追跡によるワークフローの進行状況の監視</span><span class="sxs-lookup"><span data-stu-id="ab897-112">Use Tracking to Monitor the Progress of the Workflow</span></span>  
 <span data-ttu-id="ab897-113">追跡を使用すると、ワークフローの進行状況を監視できます。</span><span class="sxs-lookup"><span data-stu-id="ab897-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="ab897-114">既定では、ワークフローのライフサイクル イベント、アクティビティのライフサイクル イベント、エラー伝達、およびブックマーク再開に対して追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="ab897-115">そのほかに、カスタム アクティビティでカスタム追跡レコードを出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab897-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="ab897-116">相関関係のトラブルシューティングでは、アクティビティ追跡レコード、ブックマーク再開レコード、およびエラー伝達レコードが最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab897-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="ab897-117">アクティビティ追跡レコードを使用すると、ワークフローの現在の進行状況を確認したり、現在メッセージを待機しているメッセージング アクティビティを特定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab897-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="ab897-118">ブックマーク再開レコードを使用すると、ワークフローでメッセージが受信されたかどうかを確認できます。エラー伝達レコードは、ワークフローで発生したエラーの記録を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab897-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="ab897-119">追跡を有効にするには、<xref:System.Activities.Tracking.TrackingParticipant> の <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> で目的の <xref:System.ServiceModel.Activities.WorkflowServiceHost> を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab897-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="ab897-120">次の例で、 `ConsoleTrackingParticipant` (から、[カスタム追跡](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md)サンプル) が既定の追跡プロファイルを使用して構成されています。</span><span class="sxs-lookup"><span data-stu-id="ab897-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="ab897-121">ConsoleTrackingParticipant などの追跡参加要素は、コンソール ウィンドウを持つ自己ホスト型ワークフロー サービスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab897-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="ab897-122">Web ホスト サービスの永続的ストアに追跡情報をログに記録する追跡参加要素を使用するか、組み込みなど<xref:System.Activities.Tracking.EtwTrackingParticipant>、またはカスタムの追跡参加要素がログに記録する情報をファイルなど、 `TextWriterTrackingParticpant` から[テキスト ファイルを使用した追跡](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="ab897-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file, such as the `TextWriterTrackingParticpant` from the [Tracking Using a Text File](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ab897-123">追跡と追跡、Web でホストされるワークフロー サービスの構成を参照してください[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)、[ワークフローの追跡を構成する](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)、および[追跡 &#91;。WF のサンプル &#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="ab897-123"> tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
## <a name="use-wcf-tracing"></a><span data-ttu-id="ab897-124">WCF トレースの使用</span><span class="sxs-lookup"><span data-stu-id="ab897-124">Use WCF Tracing</span></span>  
 <span data-ttu-id="ab897-125">WCF トレースは、ワークフロー サービスのメッセージ フローのトレースを提供します。</span><span class="sxs-lookup"><span data-stu-id="ab897-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="ab897-126">このトレース情報は、相関関係 (特にコンテンツ ベースの相関関係) のトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab897-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="ab897-127">トレースを有効にするには、`system.diagnostics` ファイル (Web ホスト ワークフロー サービスの場合) または `web.config` ファイル (自己ホスト型ワークフロー サービスの場合) の `app.config` セクションで目的のトレース リスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="ab897-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="ab897-128">トレース ファイルにメッセージの内容を含めるには、`true` の `logEntireMessage` セクションの `messageLogging` 要素で `diagnostics` に対して `system.serviceModel` を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab897-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="ab897-129">次の例では、メッセージの内容を含むトレース情報を `service.svclog` という名前のファイルに書き込むように構成しています。</span><span class="sxs-lookup"><span data-stu-id="ab897-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
    </sources>  
  
    <sharedListeners>  
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging logEntireMessage="true" logMalformedMessages="false"  
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">  
      </messageLogging>  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ab897-130">含まれるトレース情報を表示する`service.svclog`、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab897-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="ab897-131">この方法を使用すると、渡されたメッセージの内容そのものを調べてコンテンツ ベースの相関関係の <xref:System.ServiceModel.CorrelationQuery> に一致するかどうかを確認できるため、コンテンツ ベースの相関関係のトラブルシューティングで特に便利です。</span><span class="sxs-lookup"><span data-stu-id="ab897-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ab897-132">WCF トレースを参照してください[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)、[トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)、および[、アプリケーションのトラブルシューティングを使用してトレース](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab897-132"> WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="ab897-133">コンテキスト交換の相関関係の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="ab897-133">Common Context Exchange Correlation Issues</span></span>  
 <span data-ttu-id="ab897-134">相関関係の中には、特定の種類のバインドが使用されていないと正しく機能しないものがあります。</span><span class="sxs-lookup"><span data-stu-id="ab897-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="ab897-135">たとえば、要求/応答の相関関係には <xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドが、コンテキスト交換の相関関係には <xref:System.ServiceModel.BasicHttpContextBinding> などのコンテキスト ベースのバインドが必要です。</span><span class="sxs-lookup"><span data-stu-id="ab897-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="ab897-136">双方向の操作はほとんどのバインドでサポートされているため、要求/応答の相関関係ではあまり問題になりませんが、コンテキスト ベースのバインドはわずかしかなく (<xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding>、<xref:System.ServiceModel.NetTcpContextBinding> など)、</span><span class="sxs-lookup"><span data-stu-id="ab897-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="ab897-137">それらのいずれかが使用されていないと、ワークフロー サービスへの最初の呼び出しは成功しますが、その後の呼び出しが次の <xref:System.ServiceModel.FaultException> で失敗します。</span><span class="sxs-lookup"><span data-stu-id="ab897-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 <span data-ttu-id="ab897-138">コンテキスト相関関係に使用されるコンテキスト情報は、双方向の操作が使用されている場合は <xref:System.ServiceModel.Activities.SendReply> から (コンテキスト相関関係を初期化する) <xref:System.ServiceModel.Activities.Receive> アクティビティに返され、操作が一方向の場合は呼び出し元によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="ab897-139">コンテキストが呼び出し元によって送信されず、ワークフロー サービスからも返されない場合は、後続の操作が呼び出されたときに上述の <xref:System.ServiceModel.FaultException> が返されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ab897-140">[コンテキスト交換](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab897-140"> [Context Exchange](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span></span>  
  
## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="ab897-141">要求/応答の相関関係の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="ab897-141">Common Request-Reply Correlation Issues</span></span>  
 <span data-ttu-id="ab897-142">要求-応答の相関関係を併用、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアを使用して、ワークフロー サービスでは、双方向の操作を実装する、 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペアを別の web サイトでの双方向の操作を呼び出すサービス。</span><span class="sxs-lookup"><span data-stu-id="ab897-142">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="ab897-143">WCF サービスの双方向の操作を呼び出す場合、このサービスには、従来の命令型のコード ベースの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを使用することも、ワークフロー サービスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab897-143">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="ab897-144">要求/応答の相関関係を使用するには、<xref:System.ServiceModel.BasicHttpBinding> などの双方向のバインドを使用する必要があります。操作が双方向である必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ab897-144">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>  
  
 <span data-ttu-id="ab897-145">ワークフロー サービスが双方向の操作を並行または重複<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>または<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>のペア、暗黙の関連付け処理で提供される管理<xref:System.ServiceModel.Activities.WorkflowServiceHost>、特に高負荷のシナリオでは十分でないと、メッセージのルーティングを正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ab897-145">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="ab897-146">この問題が発生しないようにするために、要求/応答の相関関係を使用する際には常に <xref:System.ServiceModel.Activities.CorrelationHandle> を明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ab897-146">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="ab897-147">使用する場合、 **SendAndReceiveReply**と**ReceiveAndSendReply** [メッセージング] セクションのテンプレート、**ツールボックス**ワークフロー デザイナーで、 <xref:System.ServiceModel.Activities.CorrelationHandle>既定では明示的に構成します。</span><span class="sxs-lookup"><span data-stu-id="ab897-147">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="ab897-148">コードを使用してワークフローを作成する場合は、ペアの最初のアクティビティの <xref:System.ServiceModel.Activities.CorrelationHandle> で <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab897-148">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="ab897-149">次の例では、<xref:System.ServiceModel.Activities.Receive> で <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> を明示的に指定して <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> アクティビティを構成しています。</span><span class="sxs-lookup"><span data-stu-id="ab897-149">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = ... // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="ab897-150">間で永続化は許可されていません、 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>ペアまたは<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>ペア。</span><span class="sxs-lookup"><span data-stu-id="ab897-150">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="ab897-151">両方のアクティビティが完了するまで存続する非永続化ゾーンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-151">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="ab897-152">遅延アクティビティなどのアクティビティがこの非永続化ゾーンにあって、ワークフローのアイドル状態を引き起こした場合、ホストでワークフローがアイドル状態になったときにワークフローを永続化するようにホストが構成されていても、ワークフローは永続化されません。</span><span class="sxs-lookup"><span data-stu-id="ab897-152">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="ab897-153">Persist アクティビティなどのアクティビティが非永続化ゾーンで明示的に永続化を試みた場合、致命的な例外がスローされ、ワークフローが中止されて、<xref:System.ServiceModel.FaultException> が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-153">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="ab897-154">次の致命的な例外メッセージが表示されます。"System.InvalidOperationException: 持続性のないブロックに Persist アクティビティを含めることはできません。"</span><span class="sxs-lookup"><span data-stu-id="ab897-154">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="ab897-155">この例外は呼び出し元に返されませんが、追跡が有効になっている場合は確認できます。</span><span class="sxs-lookup"><span data-stu-id="ab897-155">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="ab897-156">呼び出し元に返される <xref:System.ServiceModel.FaultException> のメッセージは、"WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' が完了しているため、操作を実行できませんでした" です。</span><span class="sxs-lookup"><span data-stu-id="ab897-156">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ab897-157">要求-応答の相関関係を参照してください[要求/応答](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab897-157"> request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>  
  
## <a name="common-content-correlation-issues"></a><span data-ttu-id="ab897-158">コンテンツ ベースの相関関係の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="ab897-158">Common Content Correlation Issues</span></span>  
 <span data-ttu-id="ab897-159">コンテンツ ベースの相関関係は、ワークフロー サービスが複数のメッセージを受信し、交換されるメッセージ内の一部のデータによって目的のインスタンスが識別される場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-159">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="ab897-160">コンテンツ ベースの相関関係では、顧客番号や注文 ID などのメッセージ内のデータを使用して、適切なワークフロー インスタンスにメッセージをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="ab897-160">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="ab897-161">ここでは、コンテンツ ベースの相関関係を使用するときに発生するいくつかの一般的な問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab897-161">This section describes several common issues that may occur when using content-based correlation.</span></span>  
  
### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="ab897-162">識別データが一意であることの確認</span><span class="sxs-lookup"><span data-stu-id="ab897-162">Ensure the Identifying Data Is Unique</span></span>  
 <span data-ttu-id="ab897-163">インスタンスの識別に使用されるデータは、相関関係キーにハッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ab897-163">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="ab897-164">相関関係による関連付けで使用するデータは必ず、一意にする必要があります。一意でない場合は、ハッシュされたキーで競合が発生し、誤った場所にメッセージがルーティングされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ab897-164">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="ab897-165">たとえば、顧客名だけに基づいた関連付けでは、同じ名前の顧客が複数存在する場合があるため、競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ab897-165">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="ab897-166">メッセージの関連付けに使用するデータの一部として、コロン (:) を使用することはできません。コロンは、メッセージ クエリのキーと値の区切り文字として既に使用されており、後でハッシュされる文字列に含まれるためです。</span><span class="sxs-lookup"><span data-stu-id="ab897-166">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="ab897-167">永続化を使用している場合は、現在の識別データが、以前に永続化されたインスタンスによって使用されていないかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab897-167">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="ab897-168">この問題は、永続化を一時的に無効にすることによって特定できます。</span><span class="sxs-lookup"><span data-stu-id="ab897-168">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="ab897-169">WCF トレースを使用すると、計算された相関関係キーを表示できるため、この種の問題のデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab897-169">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>  
  
### <a name="race-conditions"></a><span data-ttu-id="ab897-170">競合状態</span><span class="sxs-lookup"><span data-stu-id="ab897-170">Race Conditions</span></span>  
 <span data-ttu-id="ab897-171">サービスがメッセージを受信してから実際に相関関係が初期化されるまでにはわずかな時間差があり、その間は後続のメッセージが無視されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-171">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="ab897-172">ワークフロー サービスで、クライアントから一方向の操作で渡されるデータを使用してコンテンツ ベースの相関関係が初期化される場合に、呼び出し元が後続のメッセージをすぐに送信すると、この時間差の間それらのメッセージが無視されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-172">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="ab897-173">この問題を回避するには、双方向の操作を使用して相関関係を初期化するか、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab897-173">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>  
  
### <a name="correlation-query-issues"></a><span data-ttu-id="ab897-174">関連付けクエリについての問題</span><span class="sxs-lookup"><span data-stu-id="ab897-174">Correlation Query Issues</span></span>  
 <span data-ttu-id="ab897-175">関連付けクエリは、メッセージの関連付けに使用するメッセージ内のデータを指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-175">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="ab897-176">このデータは、XPath クエリを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="ab897-176">This data is specified by using an XPath query.</span></span> <span data-ttu-id="ab897-177">特に問題がないように見えるにもかかわらず、サービスへのメッセージがディスパッチされない場合は、トラブルシューティングの手法として、メッセージ データの値に一致するリテラル値を XPath クエリの代わりに指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ab897-177">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="ab897-178">リテラル値を指定するには `string` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab897-178">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="ab897-179">次の例では、<xref:System.ServiceModel.MessageQuerySet> に対して `11445` というリテラル値を使用するように `OrderId` が構成されています。XPath クエリはコメント アウトされています。</span><span class="sxs-lookup"><span data-stu-id="ab897-179">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>  
  
```csharp  
MessageQuerySet = new MessageQuerySet  
{  
    {  
        "OrderId",   
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")  
        new XPathMessageQuery("string('11445')")  
    }  
}  
```  
  
 <span data-ttu-id="ab897-180">関連付けデータが取得されないなど、XPath クエリが正しく構成されていない場合、次のメッセージと共にエラーが返されます。"関連付けクエリで空の結果セットが生成されました。</span><span class="sxs-lookup"><span data-stu-id="ab897-180">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="ab897-181">エンドポイントの関連付けクエリが正しく構成されていることを確認してください。"</span><span class="sxs-lookup"><span data-stu-id="ab897-181">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="ab897-182">前のセクションで説明したとおり、XPath クエリをリテラル値と置換すると、すばやくトラブルシューティングすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab897-182">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="ab897-183">XPath クエリ ビルダーを使用する場合に、この問題が発生することができます、 **関連付け初期化子**または**CorrelatesOn の定義**ダイアログ ボックスと、ワークフロー サービスは、メッセージ コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab897-183">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="ab897-184">次の例では、メッセージ コントラクト クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="ab897-184">In the following example, a message contract class is defined.</span></span>  
  
```csharp  
[MessageContract]  
public class AddItemMessage  
{  
    [MessageHeader]  
    public string CartId;  
  
    [MessageBodyMember]  
    public string Item;  
}  
```  
  
 <span data-ttu-id="ab897-185">このメッセージ コントラクトはワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-185">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="ab897-186">メッセージのヘッダーにある `CartId` は、メッセージを正しいインスタンスに関連付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-186">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="ab897-187">`CartId` を取得する XPath クエリがワークフロー デザイナーの関連付けダイアログを使用して作成される場合、次の正しくないクエリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab897-187">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 <span data-ttu-id="ab897-188"><xref:System.ServiceModel.Activities.Receive> アクティビティがデータのパラメーターを使用した場合、この XPath クエリは正しいですが、メッセージ コントラクトを使用しているため、誤りとなります。</span><span class="sxs-lookup"><span data-stu-id="ab897-188">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="ab897-189">次の XPath クエリがヘッダーから `CartId` を取得するために正しい XPath クエリです。</span><span class="sxs-lookup"><span data-stu-id="ab897-189">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>  
  
```  
sm:header()/tempuri:CartId  
```  
  
 <span data-ttu-id="ab897-190">これはメッセージの本文を調べて確認することができます。</span><span class="sxs-lookup"><span data-stu-id="ab897-190">This can be confirmed by examining the body of the message.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>  
  </s:Header>  
  <s:Body>  
    <AddItemMessage xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItemMessage>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ab897-191">次の例では、データを受信するために前のメッセージ コントラクトを使用する <xref:System.ServiceModel.Activities.Receive> 操作のために構成された `AddItem` アクティビティを示します。</span><span class="sxs-lookup"><span data-stu-id="ab897-191">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="ab897-192">XPath クエリは正しく構成されています。</span><span class="sxs-lookup"><span data-stu-id="ab897-192">The XPath query is correctly configured.</span></span>  
  
```xaml  
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">  
  <Receive.CorrelatesOn>  
    <XPathMessageQuery x:Key="key1">  
      <XPathMessageQuery.Namespaces>  
        <ssx:XPathMessageContextMarkup>  
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>  
        </ssx:XPathMessageContextMarkup>  
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>  
  </Receive.CorrelatesOn>  
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">  
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>  
  </ReceiveMessageContent>  
</Receive>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ab897-193">コンテンツ ベースの相関関係を参照してください[コンテンツ ベース](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)と[相関電卓](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="ab897-193"> content-based correlation, see [Content Based](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) and the [Correlated Calculator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) sample.</span></span>

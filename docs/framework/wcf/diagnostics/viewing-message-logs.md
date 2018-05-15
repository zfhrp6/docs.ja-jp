---
title: メッセージ ログを参照する
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 4fa205b52e3d19d2421d93297b5689422775f719
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="viewing-message-logs"></a><span data-ttu-id="b3fa4-102">メッセージ ログを参照する</span><span class="sxs-lookup"><span data-stu-id="b3fa4-102">Viewing Message Logs</span></span>
<span data-ttu-id="b3fa4-103">ここでは、メッセージ ログの表示方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="b3fa4-104">サービス トレース ビューアーでのメッセージ ログの表示</span><span class="sxs-lookup"><span data-stu-id="b3fa4-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="b3fa4-105">メッセージは、WCF によって処理されるように変換されます。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="b3fa4-106">そのため、ログ記録されたメッセージは、ログ記録された時点でのメッセージの内容を反映しているにすぎず、ネットワーク上での内容ではありません。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="b3fa4-107">メッセージ ログの出力はメッセージの転送形式とは関係がないため、メッセージ ログは常にデコードされたメッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="b3fa4-108">メッセージ ログが適切に設定されていれば、すべてのログ メッセージはプレーンテキストになります。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="b3fa4-109">たとえば、ログ メッセージの形式 (プレーンテキスト) は、バイナリ メッセージ エンコーダーの使用には影響されません。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="b3fa4-110">XmlWriterTraceListener の出力は、一連の XML フラグメントを含んだファイルです。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="b3fa4-111">このファイルは有効な XML ファイルではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="b3fa4-112">使用することをお勧め、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)メッセージのログ ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="b3fa4-113">このツールを使用する方法の詳細については、次を参照してください。[相関トレースの表示とトラブルシューティング サービス トレース ビューアーを使用して](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="b3fa4-114">サービス トレース ビューアー内でメッセージが表示、**メッセージ**タブです。操作エラーの原因となった、または操作エラーに関連するメッセージは、エラーの重大度に応じて、黄色 (警告レベル) または赤色 (エラー レベル) で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="b3fa4-115">メッセージをダブルクリックすると、要求の処理のコンテキストに従ってメッセージ トレースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3fa4-116">メッセージにヘッダーがない場合は、`<header/>` タグがログに記録されません。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="b3fa4-117">クライアント、中継、およびサービスによって記録されたメッセージの表示</span><span class="sxs-lookup"><span data-stu-id="b3fa4-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="b3fa4-118">環境には、クライアント、クライアントからメッセージが送信される中継、中継からさらにメッセージが転送されるサービスが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="b3fa4-119">すべての 3 つの場所でメッセージのログ記録が有効になっているし、で 3 つすべてのメッセージ ログを表示[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同時に、ログのメッセージ交換は正しく表示されません。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="b3fa4-120">これは、メッセージ ヘッダーの `CorrelationId` と `ActivityId` が、すべての送受信ペアで一意にならなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="b3fa4-121">この問題を解決するには、次のいずれかの方法に従います。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="b3fa4-122">2 つの 3 つのメッセージ ログの表示のみ、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)いつでもできます。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="b3fa4-123">内のすべての 3 つのログを表示する必要がある場合、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)新しいを作成して、リレー サービスを変更する、同時に<xref:System.ServiceModel.Channels.Message>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="b3fa4-124">このインスタンスは、受信メッセージの本文のコピーであり、また、`ActivityId` ヘッダーおよび `Action` ヘッダーを除くすべてのヘッダーのコピーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="b3fa4-125">これを実行する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-125">The following example code demonstrates how to do this.</span></span>  
  
```  
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="b3fa4-126">メッセージ ログ内容が不正確になる例外的なケース</span><span class="sxs-lookup"><span data-stu-id="b3fa4-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="b3fa4-127">次の条件では、ログ記録されたメッセージがネットワーク上にあるオクテット ストリームの正確な表現とはならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="b3fa4-128">BasicHttpBinding の場合、エンベロープ ヘッダーは /addressing/none 名前空間の受信メッセージについてログ記録されます。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="b3fa4-129">空白に不一致が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-129">Whitespaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="b3fa4-130">受信メッセージの場合、空の要素が異なる表現になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="b3fa4-131">たとえば、\<タグ >\</tag > の代わりに\<タグ/></span><span class="sxs-lookup"><span data-stu-id="b3fa4-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="b3fa4-132">既知の PII ログ記録が、既定または enableLoggingKnownPii="true" という明示的な設定で、無効になっている場合。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="b3fa4-133">UTF-8 へ変換するためのエンコードが有効な場合。</span><span class="sxs-lookup"><span data-stu-id="b3fa4-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fa4-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3fa4-134">See Also</span></span>  
 [<span data-ttu-id="b3fa4-135">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="b3fa4-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="b3fa4-136">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b3fa4-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="b3fa4-137">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="b3fa4-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)

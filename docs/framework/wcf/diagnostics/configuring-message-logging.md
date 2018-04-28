---
title: メッセージ ログの構成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63bdbc68851ace71b3afef30e274b9821ed1ad5f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="configuring-message-logging"></a><span data-ttu-id="9db3c-102">メッセージ ログの構成</span><span class="sxs-lookup"><span data-stu-id="9db3c-102">Configuring Message Logging</span></span>
<span data-ttu-id="9db3c-103">ここでは、さまざまなシナリオでのメッセージ ログの構成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-103">This topic describes how you can configure message logging for different scenarios.</span></span>  
  
## <a name="enabling-message-logging"></a><span data-ttu-id="9db3c-104">メッセージ ログの有効化</span><span class="sxs-lookup"><span data-stu-id="9db3c-104">Enabling Message Logging</span></span>  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="9db3c-105"> は、既定で、メッセージを記録しません。</span><span class="sxs-lookup"><span data-stu-id="9db3c-105"> does not log messages by default.</span></span> <span data-ttu-id="9db3c-106">メッセージ ログをアクティブにするには、トレース リスナーを `System.ServiceModel.MessageLogging` トレース ソースに追加し、構成ファイルで `<messagelogging>` 要素の属性を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-106">To activate message logging, you must add a trace listener to the `System.ServiceModel.MessageLogging` trace source and set attributes for the `<messagelogging>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="9db3c-107">次の例は、ログを有効にして追加オプションを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9db3c-107">The following example shows how to enable logging and specify additional options.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics>  
    <messageLogging   
         logEntireMessage="true"   
         logMalformedMessages="false"  
         logMessagesAtServiceLevel="true"   
         logMessagesAtTransportLevel="false"  
         maxMessagesToLog="3000"  
         maxSizeOfMessageToLog="2000"/>  
  </diagnostics>  
</system.serviceModel>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9db3c-108"> メッセージのログ記録の設定を参照してください[トレースとメッセージ ログの推奨設定](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-108"> message logging settings, see [Recommended Settings for Tracing and Message Logging](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="9db3c-109">`add` を使用して、使用するリスナーの名前と型を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-109">You can use `add` to specify the name and type of the listener you want to use.</span></span> <span data-ttu-id="9db3c-110">この例の構成では、リスナーに "messages" という名前を付け、使用する型として標準の .NET Framework トレース リスナー (`System.Diagnostics.XmlWriterTraceListener`) を追加しています。</span><span class="sxs-lookup"><span data-stu-id="9db3c-110">In the example configuration, the Listener is named "messages" and adds the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type to use.</span></span> <span data-ttu-id="9db3c-111">`System.Diagnostics.XmlWriterTraceListener` を使用する場合は、構成ファイルで出力ファイルの場所と名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-111">If you use `System.Diagnostics.XmlWriterTraceListener`, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="9db3c-112">指定するには、`initializeData` をログ ファイルの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-112">This is done by setting `initializeData` to the name of the log file.</span></span> <span data-ttu-id="9db3c-113">それ以外の場合、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-113">Otherwise, the system throws an exception.</span></span> <span data-ttu-id="9db3c-114">また、既定のファイルにログを出力するカスタム リスナーを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-114">You can also implement a custom listener that emits logs to a default file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9db3c-115">メッセージ ログはディスク領域にアクセスするため、ディスクに書き込む特定のサービスのメッセージ数を制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-115">Because message logging accesses disk space, you should limit the number of messages that are written to disk for a particular service.</span></span> <span data-ttu-id="9db3c-116">メッセージ数が上限に達すると、情報レベルでのトレースが生成され、すべてのメッセージ ログ処理が停止します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-116">When the message limit is reached, a trace at the Information level is produced and all message logging activities stop.</span></span>  
  
 <span data-ttu-id="9db3c-117">ログ レベルと追加オプションについては、「ログ レベルとオプション」のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-117">The logging level, as well as the additional options, are discussed in the Logging Level and Options section.</span></span>  
  
 <span data-ttu-id="9db3c-118">`switchValue` の `source` 属性は、トレースに対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-118">The `switchValue` attribute of a `source` is only valid for tracing.</span></span> <span data-ttu-id="9db3c-119">`switchValue` 属性を `System.ServiceModel.MessageLogging` トレース ソースに対して次のように指定しても無効です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-119">If you specify a `switchValue` attribute for the `System.ServiceModel.MessageLogging` trace source as follows, it has no effect.</span></span>  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 <span data-ttu-id="9db3c-120">トレース ソースを無効にする場合は、代わりに `logMessagesAtServiceLevel` 要素の `logMalformedMessages` 属性、`logMessagesAtTransportLevel` 属性、および `messageLogging` 属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-120">If you want to disable the trace source, you should use the `logMessagesAtServiceLevel`, `logMalformedMessages`, and `logMessagesAtTransportLevel` attributes of the `messageLogging` element instead.</span></span> <span data-ttu-id="9db3c-121">これらすべての属性を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-121">You should set all these attributes to `false`.</span></span> <span data-ttu-id="9db3c-122">この設定を行うには、構成エディター UI インターフェイスで前のコード例の構成ファイルを使用するか、または WMI を使用します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-122">This can be done by using the configuration file in the previous code example, through the Configuration Editor UI interface, or using WMI.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9db3c-123"> 構成エディター ツールを参照してください[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-123"> the Configuration Editor tool, see [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9db3c-124"> WMI を参照してください[診断の Windows Management Instrumentation を使用して](../../../../docs/framework/wcf/diagnostics/wmi/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-124"> WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
## <a name="logging-levels-and-options"></a><span data-ttu-id="9db3c-125">ログ レベルとオプション</span><span class="sxs-lookup"><span data-stu-id="9db3c-125">Logging Levels and Options</span></span>  
 <span data-ttu-id="9db3c-126">受信メッセージの場合は、メッセージが形成された直後、サービス レベルでメッセージがユーザー コードで処理される直前、および正しくないメッセージが検出されたときに、ログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-126">For incoming messages, logging happens immediately after the message is formed, immediately before the message gets to user code in the service level, and when malformed messages are detected.</span></span>  
  
 <span data-ttu-id="9db3c-127">送信メッセージの場合は、メッセージがユーザー コードから出力された直後およびメッセージがネットワークに出力される直前に、ログが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-127">For outgoing messages, logging happens immediately after the message leaves user code and immediately before the message goes on the wire.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="9db3c-128"> は、サービスとトランスポートの 2 種類のレベルでメッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-128"> logs messages at two different levels, service and transport.</span></span> <span data-ttu-id="9db3c-129">不正なメッセージも記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-129">Malformed messages are also logged.</span></span> <span data-ttu-id="9db3c-130">3 つのカテゴリは互いに独立しており、構成で個別に有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-130">The three categories are independent from each other and can be activated separately in configuration.</span></span>  
  
 <span data-ttu-id="9db3c-131">`logMessagesAtServiceLevel` 要素の `logMalformedMessages`、`logMessagesAtTransportLevel`、および `messageLogging` の各属性を設定することによって、ログ レベルを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-131">You can control the logging level by setting the `logMessagesAtServiceLevel`, `logMalformedMessages`, and `logMessagesAtTransportLevel` attributes of the `messageLogging` element.</span></span>  
  
### <a name="service-level"></a><span data-ttu-id="9db3c-132">サービス レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-132">Service Level</span></span>  
 <span data-ttu-id="9db3c-133">このレイヤーでは、ユーザー コードに入力 (受信時) される直前、またはユーザー コードから出力 (送信時) される直前のメッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-133">Messages logged at this layer are about to enter (on receiving) or leave (on sending) user code.</span></span> <span data-ttu-id="9db3c-134">フィルターを定義した場合は、そのフィルターと一致するメッセージだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-134">If filters have been defined, only messages that match the filters are logged.</span></span> <span data-ttu-id="9db3c-135">それ以外の場合は、サービス レベルのすべてのメッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-135">Otherwise, all messages at the service level are logged.</span></span> <span data-ttu-id="9db3c-136">このレベルでは、インフラストラクチャ メッセージ (トランザクション、ピア チャネル、およびセキュリティ) も記録されます。ただし、信頼できるメッセージング メッセージは記録されません。</span><span class="sxs-lookup"><span data-stu-id="9db3c-136">Infrastructure messages (transactions, peer channel, and security) are also logged at this level, except for Reliable Messaging messages.</span></span> <span data-ttu-id="9db3c-137">ストリーム メッセージの場合は、ヘッダーだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-137">On streamed messages, only the headers are logged.</span></span> <span data-ttu-id="9db3c-138">また、セキュリティで保護されたメッセージもこのレベルで復号化されて記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-138">In addition, secure messages are logged decrypted at this level.</span></span>  
  
### <a name="transport-level"></a><span data-ttu-id="9db3c-139">トランスポート レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-139">Transport Level</span></span>  
 <span data-ttu-id="9db3c-140">このレイヤーで記録されるメッセージは、ネットワーク上での転送に向けてエンコードできる状態になっているもの、および転送後にデコードできる状態になっているものです。</span><span class="sxs-lookup"><span data-stu-id="9db3c-140">Messages logged at this layer are ready to be encoded or decoded for or after transportation on the wire.</span></span> <span data-ttu-id="9db3c-141">フィルターを定義した場合は、そのフィルターと一致するメッセージだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-141">If filters have been defined, only messages that match the filters are logged.</span></span> <span data-ttu-id="9db3c-142">それ以外の場合は、トランスポート レイヤーのすべてのメッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-142">Otherwise, all messages at the transport layer are logged.</span></span> <span data-ttu-id="9db3c-143">このレイヤーでは、信頼できるメッセージング メッセージを含むすべてのインフラストラクチャ メッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-143">All infrastructure messages are logged at this layer, including reliable messaging messages.</span></span> <span data-ttu-id="9db3c-144">ストリーム メッセージの場合は、ヘッダーだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-144">On streamed messages, only the headers are logged.</span></span> <span data-ttu-id="9db3c-145">また、セキュリティで保護されたメッセージも、HTTPS などのセキュリティで保護されたトランスポートを使用している場合を除き、暗号化された状態でこのレベルで記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-145">In addition, secure messages are logged as encrypted at this level, except if a secure transport such as HTTPS is used.</span></span>  
  
### <a name="malformed-level"></a><span data-ttu-id="9db3c-146">不正レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-146">Malformed Level</span></span>  
 <span data-ttu-id="9db3c-147">不正なメッセージとは、処理の任意の段階で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] スタックによって拒否されたメッセージのことです。</span><span class="sxs-lookup"><span data-stu-id="9db3c-147">Malformed messages are messages that are rejected by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack at any stage of processing.</span></span> <span data-ttu-id="9db3c-148">正しくないメッセージは、そのままの状態で記録されます。暗号化されていれば、暗号化されたままで、適切でない XML も、そのままになります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-148">Malformed messages are logged as-is: encrypted if they are so, with non-proper XML, and so on.</span></span> <span data-ttu-id="9db3c-149">`maxSizeOfMessageToLog` は、CDATA として記録されるメッセージのサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-149">`maxSizeOfMessageToLog` defined the size of the message to be logged as CDATA.</span></span> <span data-ttu-id="9db3c-150">`maxSizeOfMessageToLog` の既定値は 256 K です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-150">By default, `maxSizeOfMessageToLog` is equal to 256K.</span></span> <span data-ttu-id="9db3c-151">この属性[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「他のオプション」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9db3c-151">[!INCLUDE[crabout](../../../../includes/crabout-md.md)] this attribute, see the Other Options section.</span></span>  
  
### <a name="other-options"></a><span data-ttu-id="9db3c-152">その他のオプション</span><span class="sxs-lookup"><span data-stu-id="9db3c-152">Other Options</span></span>  
 <span data-ttu-id="9db3c-153">ログ レベルに加えて、次のオプションを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-153">In addition to the logging levels, the user can specify the following options:</span></span>  
  
-   <span data-ttu-id="9db3c-154">全体メッセージの記録 (`logEntireMessage` 属性) : この値は、全体メッセージ (メッセージ ヘッダーと本文) を記録するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-154">Log Entire Message (`logEntireMessage` attribute): This value specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="9db3c-155">既定値は、`false` で、ヘッダーだけ記録することを意味します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-155">The default value is `false`, meaning that only the header is logged.</span></span> <span data-ttu-id="9db3c-156">この設定は、サービス メッセージ ログ レベルおよびトランスポート メッセージ ログ レベルに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-156">This setting affects service and transport message logging levels..</span></span>  
  
-   <span data-ttu-id="9db3c-157">記録するメッセージの最大数 (`maxMessagesToLog` 属性) : この値は、記録するメッセージの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-157">Max messages to log (`maxMessagesToLog` attribute): This value specifies the maximum number of messages to log.</span></span> <span data-ttu-id="9db3c-158">すべてのメッセージ (サービス メッセージ、トランスポート メッセージ、および不正メッセージ) が、このクォータに対してカウントされます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-158">All messages (service, transport, and malformed messages) are counted towards this quota.</span></span> <span data-ttu-id="9db3c-159">クォータに達すると、トレースが出力され、それ以上メッセージは記録されません。</span><span class="sxs-lookup"><span data-stu-id="9db3c-159">When the quota is reached, a trace is emitted and no additional message is logged.</span></span> <span data-ttu-id="9db3c-160">既定値は 10000 です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-160">The default value is 10000.</span></span>  
  
-   <span data-ttu-id="9db3c-161">記録するメッセージの最大サイズ (`maxSizeOfMessageToLog` 属性) : この値は、記録するメッセージの最大サイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-161">Max size of message to log (`maxSizeOfMessageToLog` attribute): This value specifies the maximum size of messages to log in bytes.</span></span> <span data-ttu-id="9db3c-162">サイズ制限を超えたメッセージは記録されず、そのメッセージに対して何の処理も実行されません。</span><span class="sxs-lookup"><span data-stu-id="9db3c-162">Messages that exceed the size limit are not logged, and no other activity is performed for that message.</span></span> <span data-ttu-id="9db3c-163">この設定は、すべてのトレース レベルに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-163">This setting affects all trace levels.</span></span> <span data-ttu-id="9db3c-164">ServiceModel トレースがオンの場合は、最初の記録ポイントで警告レベル トレース (ServiceModelSend\* または TransportReceive) が出力され、ユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-164">If ServiceModel tracing is on, a Warning level trace is emitted at the first logging point (ServiceModelSend\* or TransportReceive) to notify the user.</span></span> <span data-ttu-id="9db3c-165">サービス レベルとトランスポート レベルのメッセージの既定値は 256 K ですが、正しくないメッセージの既定値は 4 K です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-165">The default value for service level and transport level messages is 256K, while the default value for malformed messages is 4K.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="9db3c-166">`maxSizeOfMessageToLog` と照合するために計算されるメッセージ サイズは、シリアル化される前のメモリ上でのメッセージ サイズです。</span><span class="sxs-lookup"><span data-stu-id="9db3c-166">The message size that is computed to compare against `maxSizeOfMessageToLog` is the message size in memory before serialization.</span></span> <span data-ttu-id="9db3c-167">このサイズは、記録されるメッセージ文字列の実際の長さとは異なります。実際のサイズよりも大きい場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="9db3c-167">This size can differ from the actual length of the message string that is being logged, and in many occasions is bigger than the actual size.</span></span> <span data-ttu-id="9db3c-168">その結果、メッセージが記録されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-168">As a result, messages may not be logged.</span></span> <span data-ttu-id="9db3c-169">`maxSizeOfMessageToLog` 属性をメッセージの見積もりサイズよりも 10% 大きく設定することによって、この現象を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-169">You can account for this fact by specifying the `maxSizeOfMessageToLog` attribute to be 10% larger than the expected message size.</span></span> <span data-ttu-id="9db3c-170">また、不正メッセージを記録する場合は、メッセージ ログに使用する実際のディスク領域を、`maxSizeOfMessageToLog` で指定した値の最大 5 倍にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-170">In addition, if malformed messages are logged, the actual disk space utilized by the message logs can be up to 5 times the size of the value specified by `maxSizeOfMessageToLog`.</span></span>  
  
 <span data-ttu-id="9db3c-171">構成ファイルでトレース リスナーを定義していない場合は、ログ レベルの指定に関係なくログ出力は生成されません。</span><span class="sxs-lookup"><span data-stu-id="9db3c-171">If no trace listener is defined in the configuration file, no logging output is generated regardless of the specified logging level.</span></span>  
  
 <span data-ttu-id="9db3c-172">このセクションで説明されている属性などのメッセージ ログ オプションは、実行時に WMI (Windows Management Instrumentation) を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-172">Message logging options, such as the attributes described in this section, can be changed at runtime using Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="9db3c-173">アクセスすることによってこれ行う、 [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)ブール型プロパティを公開するインスタンス: `LogMessagesAtServiceLevel`、 `LogMessagesAtTransportLevel`、および`LogMalformedMessages`です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-173">This can be done by accessing the [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, and `LogMalformedMessages`.</span></span> <span data-ttu-id="9db3c-174">そのため、メッセージ ログ用のトレース リスナーを構成していても、これらのオプションを構成で `false` に設定している場合は、後でアプリケーションを実行しているときに `true` に変更できます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-174">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="9db3c-175">これで、メッセージ ログが実行時に有効になります。</span><span class="sxs-lookup"><span data-stu-id="9db3c-175">This effectively enables message logging at runtime.</span></span> <span data-ttu-id="9db3c-176">同様に、構成ファイルでメッセージ ログを有効にしている場合は、実行時に WMI を使用して無効にできます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-176">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span> <span data-ttu-id="9db3c-177">詳細については、次を参照してください。[診断の Windows Management Instrumentation を使用して](../../../../docs/framework/wcf/diagnostics/wmi/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-177">For more information, see [Using Windows Management Instrumentation for Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
 <span data-ttu-id="9db3c-178">メッセージ ログの `source` フィールドは、要求メッセージを送信または受信する際に要求/応答または一方向の要求については、サービス モデル レイヤーまたはトランスポート レイヤーで、または正しくないメッセージの場合に、メッセージを記録するコンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-178">The `source` field in a message log specifies in which context the message is logged: when sending/receiving a request message, for a request-reply or 1-way request, at service model or transport layer, or in the case of a malformed message.</span></span>  
  
 <span data-ttu-id="9db3c-179">正しくないメッセージは、の`source`と等しい`Malformed`です。</span><span class="sxs-lookup"><span data-stu-id="9db3c-179">For malformed messages, `source`  is equal to `Malformed`.</span></span> <span data-ttu-id="9db3c-180">それ以外の場合、source には、コンテキストに基づいて、以下の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-180">Otherwise, source has the following values based on the context.</span></span>  
  
 <span data-ttu-id="9db3c-181">要求/応答の場合</span><span class="sxs-lookup"><span data-stu-id="9db3c-181">For Request/Reply</span></span>  
  
||<span data-ttu-id="9db3c-182">Send Request</span><span class="sxs-lookup"><span data-stu-id="9db3c-182">Send Request</span></span>|<span data-ttu-id="9db3c-183">Receive Request</span><span class="sxs-lookup"><span data-stu-id="9db3c-183">Receive Request</span></span>|<span data-ttu-id="9db3c-184">Send Reply</span><span class="sxs-lookup"><span data-stu-id="9db3c-184">Send Reply</span></span>|<span data-ttu-id="9db3c-185">Receive Reply</span><span class="sxs-lookup"><span data-stu-id="9db3c-185">Receive Reply</span></span>|  
|-|------------------|---------------------|----------------|-------------------|  
|<span data-ttu-id="9db3c-186">Service Model layer</span><span class="sxs-lookup"><span data-stu-id="9db3c-186">Service Model layer</span></span>|<span data-ttu-id="9db3c-187">サービス</span><span class="sxs-lookup"><span data-stu-id="9db3c-187">Service</span></span><br /><br /> <span data-ttu-id="9db3c-188">レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-188">Level</span></span><br /><br /> <span data-ttu-id="9db3c-189">送信</span><span class="sxs-lookup"><span data-stu-id="9db3c-189">Send</span></span><br /><br /> <span data-ttu-id="9db3c-190">要求</span><span class="sxs-lookup"><span data-stu-id="9db3c-190">Request</span></span>|<span data-ttu-id="9db3c-191">サービス</span><span class="sxs-lookup"><span data-stu-id="9db3c-191">Service</span></span><br /><br /> <span data-ttu-id="9db3c-192">レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-192">Level</span></span><br /><br /> <span data-ttu-id="9db3c-193">Receive</span><span class="sxs-lookup"><span data-stu-id="9db3c-193">Receive</span></span><br /><br /> <span data-ttu-id="9db3c-194">要求</span><span class="sxs-lookup"><span data-stu-id="9db3c-194">Request</span></span>|<span data-ttu-id="9db3c-195">サービス</span><span class="sxs-lookup"><span data-stu-id="9db3c-195">Service</span></span><br /><br /> <span data-ttu-id="9db3c-196">レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-196">Level</span></span><br /><br /> <span data-ttu-id="9db3c-197">送信</span><span class="sxs-lookup"><span data-stu-id="9db3c-197">Send</span></span><br /><br /> <span data-ttu-id="9db3c-198">Reply</span><span class="sxs-lookup"><span data-stu-id="9db3c-198">Reply</span></span>|<span data-ttu-id="9db3c-199">サービス</span><span class="sxs-lookup"><span data-stu-id="9db3c-199">Service</span></span><br /><br /> <span data-ttu-id="9db3c-200">レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-200">Level</span></span><br /><br /> <span data-ttu-id="9db3c-201">Receive</span><span class="sxs-lookup"><span data-stu-id="9db3c-201">Receive</span></span><br /><br /> <span data-ttu-id="9db3c-202">Reply</span><span class="sxs-lookup"><span data-stu-id="9db3c-202">Reply</span></span>|  
|<span data-ttu-id="9db3c-203">Transport layer</span><span class="sxs-lookup"><span data-stu-id="9db3c-203">Transport layer</span></span>|<span data-ttu-id="9db3c-204">Transport</span><span class="sxs-lookup"><span data-stu-id="9db3c-204">Transport</span></span><br /><br /> <span data-ttu-id="9db3c-205">送信</span><span class="sxs-lookup"><span data-stu-id="9db3c-205">Send</span></span>|<span data-ttu-id="9db3c-206">Transport</span><span class="sxs-lookup"><span data-stu-id="9db3c-206">Transport</span></span><br /><br /> <span data-ttu-id="9db3c-207">Receive</span><span class="sxs-lookup"><span data-stu-id="9db3c-207">Receive</span></span>|<span data-ttu-id="9db3c-208">Transport</span><span class="sxs-lookup"><span data-stu-id="9db3c-208">Transport</span></span><br /><br /> <span data-ttu-id="9db3c-209">送信</span><span class="sxs-lookup"><span data-stu-id="9db3c-209">Send</span></span>|<span data-ttu-id="9db3c-210">Transport</span><span class="sxs-lookup"><span data-stu-id="9db3c-210">Transport</span></span><br /><br /> <span data-ttu-id="9db3c-211">Receive</span><span class="sxs-lookup"><span data-stu-id="9db3c-211">Receive</span></span>|  
  
 <span data-ttu-id="9db3c-212">一方向の要求の場合</span><span class="sxs-lookup"><span data-stu-id="9db3c-212">For One-way Request</span></span>  
  
||<span data-ttu-id="9db3c-213">Send Request</span><span class="sxs-lookup"><span data-stu-id="9db3c-213">Send Request</span></span>|<span data-ttu-id="9db3c-214">Receive Request</span><span class="sxs-lookup"><span data-stu-id="9db3c-214">Receive Request</span></span>|  
|-|------------------|---------------------|  
|<span data-ttu-id="9db3c-215">Service Model layer</span><span class="sxs-lookup"><span data-stu-id="9db3c-215">Service Model layer</span></span>|<span data-ttu-id="9db3c-216">サービス</span><span class="sxs-lookup"><span data-stu-id="9db3c-216">Service</span></span><br /><br /> <span data-ttu-id="9db3c-217">レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-217">Level</span></span><br /><br /> <span data-ttu-id="9db3c-218">送信</span><span class="sxs-lookup"><span data-stu-id="9db3c-218">Send</span></span><br /><br /> <span data-ttu-id="9db3c-219">データグラム</span><span class="sxs-lookup"><span data-stu-id="9db3c-219">Datagram</span></span>|<span data-ttu-id="9db3c-220">サービス</span><span class="sxs-lookup"><span data-stu-id="9db3c-220">Service</span></span><br /><br /> <span data-ttu-id="9db3c-221">レベル</span><span class="sxs-lookup"><span data-stu-id="9db3c-221">Level</span></span><br /><br /> <span data-ttu-id="9db3c-222">Receive</span><span class="sxs-lookup"><span data-stu-id="9db3c-222">Receive</span></span><br /><br /> <span data-ttu-id="9db3c-223">データグラム</span><span class="sxs-lookup"><span data-stu-id="9db3c-223">Datagram</span></span>|  
|<span data-ttu-id="9db3c-224">Transport layer</span><span class="sxs-lookup"><span data-stu-id="9db3c-224">Transport layer</span></span>|<span data-ttu-id="9db3c-225">Transport</span><span class="sxs-lookup"><span data-stu-id="9db3c-225">Transport</span></span><br /><br /> <span data-ttu-id="9db3c-226">送信</span><span class="sxs-lookup"><span data-stu-id="9db3c-226">Send</span></span>|<span data-ttu-id="9db3c-227">Transport</span><span class="sxs-lookup"><span data-stu-id="9db3c-227">Transport</span></span><br /><br /> <span data-ttu-id="9db3c-228">Receive</span><span class="sxs-lookup"><span data-stu-id="9db3c-228">Receive</span></span>|  
  
## <a name="message-filters"></a><span data-ttu-id="9db3c-229">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="9db3c-229">Message Filters</span></span>  
 <span data-ttu-id="9db3c-230">メッセージ フィルターは、`messageLogging` 構成セクションの `diagnostics` 構成要素で定義されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-230">Message filters are defined in the `messageLogging` configuration element of the `diagnostics` configuration section.</span></span> <span data-ttu-id="9db3c-231">これらは、サービス レベルとトランスポート レベルで適用されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-231">They are applied at the service and transport level.</span></span> <span data-ttu-id="9db3c-232">1 つ以上のフィルターを定義した場合は、少なくとも 1 つのフィルターと一致するメッセージだけが記録されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-232">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="9db3c-233">フィルターを定義しなかった場合は、すべてのメッセージが通過します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-233">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="9db3c-234">フィルターは、完全な XPath 構文をサポートし、構成ファイルでの出現順に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-234">Filters support the full XPath syntax and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="9db3c-235">フィルターが構文的に正しくない場合は、構成例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-235">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="9db3c-236">フィルターは、フィルターに一致するかどうかを確認できる、XPath DOM 内のノードの最大数を制限する `nodeQuota` 属性を使用することで、安全機能も提供します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-236">Filters also provide a safety feature using the `nodeQuota` attribute, which limits the maximum number of nodes in the XPath DOM that can be examined to match the filter.</span></span>  
  
 <span data-ttu-id="9db3c-237">次の例は、SOAP ヘッダー セクションがあるメッセージだけを記録するフィルターの設定方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9db3c-237">The following example shows how to configure a filter that records only messages that have a SOAP header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
    logMalformedMessages="true"   
    logMessagesAtServiceLevel="true"  
    logMessagesAtTransportLevel="true"  
    maxMessagesToLog="420">  
    <filters>  
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                 /soap:Envelope/soap:Header  
        </add>  
     </filters>  
</messageLogging>  
```  
  
 <span data-ttu-id="9db3c-238">フィルターは、メッセージの本文には適用できません。</span><span class="sxs-lookup"><span data-stu-id="9db3c-238">Filters cannot be applied to the body of a message.</span></span> <span data-ttu-id="9db3c-239">メッセージの本文を操作しようとするフィルターは、フィルターの一覧から削除されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-239">Filters that attempt to manipulate the body of a message are removed from the list of filters.</span></span> <span data-ttu-id="9db3c-240">その場合には、このことを示すイベントも出力されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-240">An event is also emitted that indicates this.</span></span> <span data-ttu-id="9db3c-241">たとえば、次のフィルターは、フィルター テーブルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-241">For example, the following filter would be removed from the filter table.</span></span>  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a><span data-ttu-id="9db3c-242">カスタム リスナーの構成</span><span class="sxs-lookup"><span data-stu-id="9db3c-242">Configuring a Custom Listener</span></span>  
 <span data-ttu-id="9db3c-243">追加オプションでカスタム リスナーを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-243">You can also configure a custom listener with additional options.</span></span> <span data-ttu-id="9db3c-244">カスタム リスナーは、記録を行う前に、アプリケーション固有の PII 要素をメッセージからフィルター処理するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9db3c-244">A custom listener can be useful in filtering application-specific PII elements from messages before logging.</span></span> <span data-ttu-id="9db3c-245">次の例は、カスタム リスナーの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="9db3c-245">The following example demonstrates a custom listener configuration.</span></span>  
  
```xml  
<system.diagnostics>  
   <sources>  
     <source name="System.ServiceModel.MessageLogging">  
           <listeners>  
             <add name="MyListener"   
                    type="YourCustomListener"  
                    initializeData="c:\logs\messages.svclog"  
                    maxDiskSpace="1000"/>  
           </listeners>  
     </source>  
   </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="9db3c-246">`type` 属性は、型のアセンブリ修飾名に設定する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9db3c-246">You should be aware that the `type` attribute should be set to a qualified assembly name of the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db3c-247">関連項目</span><span class="sxs-lookup"><span data-stu-id="9db3c-247">See Also</span></span>  
 [<span data-ttu-id="9db3c-248">\<メッセージ ログ ></span><span class="sxs-lookup"><span data-stu-id="9db3c-248">\<messageLogging></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [<span data-ttu-id="9db3c-249">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="9db3c-249">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [<span data-ttu-id="9db3c-250">トレースとメッセージ ログの推奨設定</span><span class="sxs-lookup"><span data-stu-id="9db3c-250">Recommended Settings for Tracing and Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)

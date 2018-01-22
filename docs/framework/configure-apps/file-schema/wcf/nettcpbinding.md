---
title: '&lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 057baf6d18cba61c0ceeb7d5152edcf082392310
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltnettcpbindinggt"></a><span data-ttu-id="8a1fc-102">&lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8a1fc-102">&lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="8a1fc-103">複数コンピューターの通信に適し、セキュリティで保護されて信頼できる最適化されたバインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="8a1fc-104">既定では、メッセージ セキュリティと認証用 Windows セキュリティ、メッセージ配信用 TCP、およびバイナリ メッセージ エンコーディングを持つランタイム通信スタックを生成します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="8a1fc-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8a1fc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="8a1fc-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8a1fc-106">\<bindings></span></span>  
<span data-ttu-id="8a1fc-107">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8a1fc-107">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a1fc-108">構文</span><span class="sxs-lookup"><span data-stu-id="8a1fc-108">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      maxBufferPoolSize="integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
      name="string"  
      openTimeout="TimeSpan"  
      portSharingEnabled="Boolean"  
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"   
      transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"   
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a1fc-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8a1fc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8a1fc-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a1fc-111">属性</span><span class="sxs-lookup"><span data-stu-id="8a1fc-111">Attributes</span></span>  
  
|<span data-ttu-id="8a1fc-112">属性</span><span class="sxs-lookup"><span data-stu-id="8a1fc-112">Attribute</span></span>|<span data-ttu-id="8a1fc-113">説明</span><span class="sxs-lookup"><span data-stu-id="8a1fc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a1fc-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="8a1fc-114">closeTimeout</span></span>|<span data-ttu-id="8a1fc-115">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="8a1fc-116">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8a1fc-117">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="8a1fc-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="8a1fc-118">hostnameComparisonMode</span></span>|<span data-ttu-id="8a1fc-119">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="8a1fc-120">この属性は `System.ServiceModel.HostnameComparisonMode` 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="8a1fc-121">既定値は `StrongWildcard` で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="8a1fc-122">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="8a1fc-122">listenBacklog</span></span>|<span data-ttu-id="8a1fc-123">リスナーで受け入れを待機するチャネルの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-123">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="8a1fc-124">この制限を超えた接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-124">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="8a1fc-125">`connectionTimeout` 属性は、クライアントが接続を待つ時間を制限します。この時間が経過すると接続の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-125">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="8a1fc-126">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-126">The default is 10.</span></span>|  
|<span data-ttu-id="8a1fc-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8a1fc-127">maxBufferPoolSize</span></span>|<span data-ttu-id="8a1fc-128">このバインディングに使用するバッファー プール サイズの上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-128">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="8a1fc-129">既定は 512 \* 1024 バイトです。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-129">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="8a1fc-130">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-130">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="8a1fc-131">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-131">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="8a1fc-132">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-132">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="8a1fc-133">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-133">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="8a1fc-134">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8a1fc-134">maxBufferSize</span></span>|<span data-ttu-id="8a1fc-135">メッセージをメモリに保存するのに使用するバッファーの最大サイズをバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-135">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="8a1fc-136">`transferMode` 属性が `Buffered` に等しい場合は、この属性が `maxReceivedMessageSize` 属性の値と等しくなっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-136">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="8a1fc-137">`transferMode` 属性が `Streamed` に等しい場合は、この属性が `maxReceivedMessageSize` 属性の値以下であり、またヘッダーのサイズ以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-137">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="8a1fc-138">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-138">The default is 65536.</span></span> <span data-ttu-id="8a1fc-139">詳細については、「<xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-139">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="8a1fc-140">maxConnections</span><span class="sxs-lookup"><span data-stu-id="8a1fc-140">maxConnections</span></span>|<span data-ttu-id="8a1fc-141">サービスが作成し受け付ける発信/着信接続数の上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-141">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="8a1fc-142">この属性により指定された別個の制限に対して、着信接続および発信接続がカウントされます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-142">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="8a1fc-143">制限を超える着信接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-143">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="8a1fc-144">制限を超える発信接続は、制限内に空きができるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-144">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="8a1fc-145">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-145">The default is 10.</span></span>|  
|<span data-ttu-id="8a1fc-146">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="8a1fc-146">maxReceivedMessageSize</span></span>|<span data-ttu-id="8a1fc-147">このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-147">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="8a1fc-148">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-148">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="8a1fc-149">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-149">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="8a1fc-150">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-150">The default is 65536.</span></span>|  
|<span data-ttu-id="8a1fc-151">name</span><span class="sxs-lookup"><span data-stu-id="8a1fc-151">name</span></span>|<span data-ttu-id="8a1fc-152">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-152">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="8a1fc-153">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-153">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="8a1fc-154">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="8a1fc-155">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="8a1fc-156">openTimeout</span><span class="sxs-lookup"><span data-stu-id="8a1fc-156">openTimeout</span></span>|<span data-ttu-id="8a1fc-157">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="8a1fc-158">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8a1fc-159">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-159">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="8a1fc-160">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="8a1fc-160">portSharingEnabled</span></span>|<span data-ttu-id="8a1fc-161">TCP ポート共有をこの接続で有効にするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-161">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="8a1fc-162">これが `false` の場合、各バインドは独自の排他ポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-162">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="8a1fc-163">クライアントには影響しないため、この設定はサービスのみに関連します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-163">This setting is relevant only to services, because clients are not affected.</span></span>|  
|<span data-ttu-id="8a1fc-164">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="8a1fc-164">receiveTimeout</span></span>|<span data-ttu-id="8a1fc-165">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="8a1fc-166">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8a1fc-167">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-167">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="8a1fc-168">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="8a1fc-168">sendTimeout</span></span>|<span data-ttu-id="8a1fc-169">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="8a1fc-170">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="8a1fc-171">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-171">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="8a1fc-172">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="8a1fc-172">transactionFlow</span></span>|<span data-ttu-id="8a1fc-173">バインディングが WS-Transactions のフローをサポートするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-173">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="8a1fc-174">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-174">The default is `false`.</span></span>|  
|<span data-ttu-id="8a1fc-175">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="8a1fc-175">transactionProtocol</span></span>|<span data-ttu-id="8a1fc-176">このバインディングで使用されるトランザクション プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-176">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="8a1fc-177">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-177">Valid values are</span></span><br /><br /> <span data-ttu-id="8a1fc-178">-   OleTransactions</span><span class="sxs-lookup"><span data-stu-id="8a1fc-178">-   OleTransactions</span></span><br /><span data-ttu-id="8a1fc-179">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="8a1fc-179">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="8a1fc-180">既定値は OleTransactions です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-180">The default is OleTransactions.</span></span> <span data-ttu-id="8a1fc-181">この属性は <xref:System.ServiceModel.TransactionProtocol> 型です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-181">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="8a1fc-182">transferMode</span><span class="sxs-lookup"><span data-stu-id="8a1fc-182">transferMode</span></span>|<span data-ttu-id="8a1fc-183">メッセージが要求や応答をバッファーするか、ストリーミングするかを指定する <xref:System.ServiceModel.TransferMode> 値です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-183">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a1fc-184">子要素</span><span class="sxs-lookup"><span data-stu-id="8a1fc-184">Child Elements</span></span>  
  
|<span data-ttu-id="8a1fc-185">要素</span><span class="sxs-lookup"><span data-stu-id="8a1fc-185">Element</span></span>|<span data-ttu-id="8a1fc-186">説明</span><span class="sxs-lookup"><span data-stu-id="8a1fc-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a1fc-187">\<security></span><span class="sxs-lookup"><span data-stu-id="8a1fc-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="8a1fc-188">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-188">Defines the security settings for the binding.</span></span> <span data-ttu-id="8a1fc-189">この要素は <xref:System.ServiceModel.Configuration.NetTcpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-189">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[<span data-ttu-id="8a1fc-190">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="8a1fc-190">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="8a1fc-191">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-191">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="8a1fc-192">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-192">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="8a1fc-193">reliableSession</span><span class="sxs-lookup"><span data-stu-id="8a1fc-193">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="8a1fc-194">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-194">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8a1fc-195">親要素</span><span class="sxs-lookup"><span data-stu-id="8a1fc-195">Parent Elements</span></span>  
  
|<span data-ttu-id="8a1fc-196">要素</span><span class="sxs-lookup"><span data-stu-id="8a1fc-196">Element</span></span>|<span data-ttu-id="8a1fc-197">説明</span><span class="sxs-lookup"><span data-stu-id="8a1fc-197">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a1fc-198">\<bindings></span><span class="sxs-lookup"><span data-stu-id="8a1fc-198">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="8a1fc-199">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-199">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a1fc-200">コメント</span><span class="sxs-lookup"><span data-stu-id="8a1fc-200">Remarks</span></span>  
 <span data-ttu-id="8a1fc-201">このバインディングは、既定ではランタイム通信スタックを生成し、トランスポート セキュリティ、メッセージ配信用 TCP、およびバイナリ メッセージ エンコーディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-201">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="8a1fc-202">このバインドは、イントラネット上の通信に適した [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] システム標準の選択肢です。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-202">This binding is an appropriate [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="8a1fc-203">`netTcpBinding` の既定の構成は、`wsHttpBinding` が提供する構成よりも高速ですが、これは [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 対 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 間の通信でのみ使用されることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-203">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]-to-[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] communication.</span></span> <span data-ttu-id="8a1fc-204">このセキュリティ動作は、省略可能な `securityMode` 属性を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-204">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="8a1fc-205">WS-ReliableMessaging を使用するかどうかは、省略可能な `reliableSessionEnabled` 属性を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-205">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="8a1fc-206">ただし、信頼できるメッセージングは、既定ではオフです。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-206">But reliable messaging is off by default.</span></span> <span data-ttu-id="8a1fc-207">`wsHttpBinding` や `basicHttpBinding` などの HTTP システム指定のバインディングは、既定では設定をオンにするように構成され、`netTcpBinding` バインディングは、既定では設定をオフにするように構成されているのが一般的であるため、たとえば、いずれかの WS-\* 仕様のサポートを得るには、サポートを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-207">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="8a1fc-208">これは、TCP の既定の構成の方が、HTTP バインディング用の既定の構成より、エンドポイント間でのメッセージ交換が高速になることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-208">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a1fc-209">例</span><span class="sxs-lookup"><span data-stu-id="8a1fc-209">Example</span></span>  
 <span data-ttu-id="8a1fc-210">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-210">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="8a1fc-211">バインディングの種類は、`binding` 要素の `<endpoint>` 属性に指定します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-211">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="8a1fc-212">netTcpBinding バインディングを構成してその設定の一部を変更する場合は、バインディング構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-212">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="8a1fc-213">エンドポイントは、`bindingConfiguration` 属性を使用してバインディング構成を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-213">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="8a1fc-214">次の例では、バインド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="8a1fc-214">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a1fc-215">参照</span><span class="sxs-lookup"><span data-stu-id="8a1fc-215">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
 [<span data-ttu-id="8a1fc-216">バインディング</span><span class="sxs-lookup"><span data-stu-id="8a1fc-216">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8a1fc-217">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="8a1fc-217">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8a1fc-218">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="8a1fc-218">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8a1fc-219">\<binding></span><span class="sxs-lookup"><span data-stu-id="8a1fc-219">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

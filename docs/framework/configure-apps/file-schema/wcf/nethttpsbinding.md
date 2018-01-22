---
title: '&lt;netHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 679ee79705ce7360087bc352f8049c8503cce52b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="686b9-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="686b9-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="686b9-103">HTTPS を介して通信できるエンド ポイントを構成および公開するために [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスが使用できるバインディングを表します。</span><span class="sxs-lookup"><span data-stu-id="686b9-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="686b9-104">双方向コントラクトで使用すると、Web ソケットが使用されます。それ以外の場合は、HTTPS が使用されます。</span><span class="sxs-lookup"><span data-stu-id="686b9-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="686b9-105">ルート要素</span><span class="sxs-lookup"><span data-stu-id="686b9-105">Root Element</span></span>  
<span data-ttu-id="686b9-106">次の要素</span><span class="sxs-lookup"><span data-stu-id="686b9-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686b9-107">構文</span><span class="sxs-lookup"><span data-stu-id="686b9-107">Syntax</span></span>  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan"   
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
           maxBufferPoolSize="Integer"  
           maxBufferSize="Integer"  
           maxReceivedMessageSize="Integer"  
           messageEncoding="Binary/Text/Mtom"  
           name="string"   
           openTimeout="TimeSpan"   
           proxyAddress="URI"  
           receiveTimeout="TimeSpan"  
           sendTimeout="TimeSpan"  
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="686b9-108">型</span><span class="sxs-lookup"><span data-stu-id="686b9-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="686b9-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="686b9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="686b9-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="686b9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="686b9-111">属性</span><span class="sxs-lookup"><span data-stu-id="686b9-111">Attributes</span></span>  
  
|<span data-ttu-id="686b9-112">属性</span><span class="sxs-lookup"><span data-stu-id="686b9-112">Attribute</span></span>|<span data-ttu-id="686b9-113">説明</span><span class="sxs-lookup"><span data-stu-id="686b9-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="686b9-114">クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="686b9-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="686b9-115">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="686b9-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="686b9-116">クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="686b9-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="686b9-117">この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="686b9-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="686b9-118">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="686b9-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="686b9-119">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="686b9-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="686b9-120">インターネット リソースは、ローカル アドレスを持つ場合ローカルです。</span><span class="sxs-lookup"><span data-stu-id="686b9-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="686b9-121">ローカル アドレスは、同じコンピューター、ローカル LAN、またはイントラネット上にあり、"http://webserver/"、"http://localhost/" などのピリオド (.) を含まない URI により構文的に識別されるアドレスです。</span><span class="sxs-lookup"><span data-stu-id="686b9-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="686b9-122">この属性の設定は、BasicHttpBinding で構成されたエンドポイントがローカル リソースへのアクセス時にプロキシ サーバーを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="686b9-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="686b9-123">この属性が `true` の場合、ローカル インターネット リソースへの要求はプロキシ サーバーを使用しません。</span><span class="sxs-lookup"><span data-stu-id="686b9-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="686b9-124">この属性を `true` に設定した場合で、同じコンピューター上のサービスと対話するクライアントがプロキシを経由するときは、(localhost ではなく) ホスト名を使用します。</span><span class="sxs-lookup"><span data-stu-id="686b9-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="686b9-125">この属性が `false` の場合、すべてのインターネット要求はプロキシ サーバー経由で行われます。</span><span class="sxs-lookup"><span data-stu-id="686b9-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="686b9-126">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="686b9-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="686b9-127">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="686b9-128">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="686b9-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="686b9-129">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="686b9-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="686b9-130">この属性は `HostnameComparisonMode` 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="686b9-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="686b9-131">既定値は `StrongWildcard` で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="686b9-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="686b9-132">チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる、最大メモリ量を指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="686b9-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="686b9-133">既定値は 524288 (0x80000) バイトです。</span><span class="sxs-lookup"><span data-stu-id="686b9-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="686b9-134">バッファー マネージャーは、バッファー プールを使用することで、バッファーの使用コストを最小化します。</span><span class="sxs-lookup"><span data-stu-id="686b9-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="686b9-135">バッファーは、チャネルから出てくるメッセージをサービスが処理するときに必要です。</span><span class="sxs-lookup"><span data-stu-id="686b9-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="686b9-136">メッセージの読み込み処理に十分なメモリがバッファー プールにない場合、バッファー マネージャーは、CLR ヒープから追加のメモリを割り当てる必要があります。これにより、ガベージ コレクションのオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="686b9-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="686b9-137">CLR ガベージ ヒープから多大な割り当てが行われることは、バッファー プール サイズが小さすぎること、およびこの属性で指定される制限を緩めて割り当てを増やすとパフォーマンスが向上する可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="686b9-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="686b9-138">このバインディングで構成されるエンドポイントのメッセージが処理されるときのメッセージを格納するバッファーの最大サイズを指定する整数値 (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="686b9-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="686b9-139">既定値は 65,536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="686b9-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="686b9-140">このバインディングで構成されるチャネルが受信可能なメッセージの最大メッセージ サイズ (ヘッダーを含む) をバイト単位で定義する正の整数。</span><span class="sxs-lookup"><span data-stu-id="686b9-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="686b9-141">受信側のメッセージが大きすぎると、送信側は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="686b9-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="686b9-142">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="686b9-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="686b9-143">既定値は 65,536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="686b9-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="686b9-144">SOAP メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="686b9-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="686b9-145">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="686b9-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="686b9-146">: テキストは、テキスト メッセージ エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="686b9-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="686b9-147">Mtom: は、メッセージ Transmission Organization Mechanism 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="686b9-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="686b9-148">既定値は Text です。</span><span class="sxs-lookup"><span data-stu-id="686b9-148">The default is Text.</span></span> <span data-ttu-id="686b9-149">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="686b9-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="686b9-150">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="686b9-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="686b9-151">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="686b9-152">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="686b9-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="686b9-153">また、この名前は、同じ種類のバインディング間で一意です。</span><span class="sxs-lookup"><span data-stu-id="686b9-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="686b9-154">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="686b9-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="686b9-155">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="686b9-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="686b9-156">バインディングの XML 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="686b9-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="686b9-157">既定値は "http://tempuri.org/Bindings" です。</span><span class="sxs-lookup"><span data-stu-id="686b9-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="686b9-158">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="686b9-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="686b9-159">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="686b9-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="686b9-160">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="686b9-161">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="686b9-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="686b9-162">HTTP プロキシのアドレスを格納する URI。</span><span class="sxs-lookup"><span data-stu-id="686b9-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="686b9-163">`useSystemWebProxy` が `true` に設定されている場合、この設定は `null` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="686b9-164">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="686b9-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="686b9-165">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="686b9-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="686b9-166">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="686b9-167">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="686b9-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="686b9-168">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="686b9-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="686b9-169">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="686b9-170">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="686b9-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="686b9-171">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="686b9-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="686b9-172">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="686b9-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="686b9-173">-BigEndianUnicode: Unicode BigEndian エンコーディングします。</span><span class="sxs-lookup"><span data-stu-id="686b9-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="686b9-174">Unicode: 16 ビット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="686b9-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="686b9-175">UTF8: 8 ビットのエンコーディング</span><span class="sxs-lookup"><span data-stu-id="686b9-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="686b9-176">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="686b9-176">The default is UTF8.</span></span> <span data-ttu-id="686b9-177">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="686b9-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="686b9-178">要求または応答に対してメッセージがバッファーされるか、ストリーム配信されるかを指定する有効な <xref:System.ServiceModel.TransferMode> 値。</span><span class="sxs-lookup"><span data-stu-id="686b9-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="686b9-179">使用できる場合にシステムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="686b9-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="686b9-180">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="686b9-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="686b9-181">子要素</span><span class="sxs-lookup"><span data-stu-id="686b9-181">Child Elements</span></span>  
  
|<span data-ttu-id="686b9-182">要素</span><span class="sxs-lookup"><span data-stu-id="686b9-182">Element</span></span>|<span data-ttu-id="686b9-183">説明</span><span class="sxs-lookup"><span data-stu-id="686b9-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="686b9-184">\<security></span><span class="sxs-lookup"><span data-stu-id="686b9-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="686b9-185">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="686b9-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="686b9-186">この要素は <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="686b9-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="686b9-187">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="686b9-187">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="686b9-188">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="686b9-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="686b9-189">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="686b9-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="686b9-190">親要素</span><span class="sxs-lookup"><span data-stu-id="686b9-190">Parent Elements</span></span>  
  
|<span data-ttu-id="686b9-191">要素</span><span class="sxs-lookup"><span data-stu-id="686b9-191">Element</span></span>|<span data-ttu-id="686b9-192">説明</span><span class="sxs-lookup"><span data-stu-id="686b9-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="686b9-193">\<bindings></span><span class="sxs-lookup"><span data-stu-id="686b9-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="686b9-194">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="686b9-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="686b9-195">コメント</span><span class="sxs-lookup"><span data-stu-id="686b9-195">Remarks</span></span>  
 <span data-ttu-id="686b9-196">NetHttpsBinding では、メッセージを送信するために、HTTPS をトランスポートとして使用します。</span><span class="sxs-lookup"><span data-stu-id="686b9-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="686b9-197">双方向コントラクトで使用すると、Web ソケットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="686b9-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="686b9-198">要求/応答コントラクト NetHttpsBinding と使用する場合、バイナリ エンコーダーとの BasicHttpsBinding のように動作します。</span><span class="sxs-lookup"><span data-stu-id="686b9-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="686b9-199">セキュリティは既定では、になっていますの mode 属性の設定を追加できます、 [\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)以外の値を子要素`None`です。</span><span class="sxs-lookup"><span data-stu-id="686b9-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="686b9-200">サービスは、"Text" メッセージ エンコードおよび UTF-8 テキスト エンコードを既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="686b9-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="686b9-201">例</span><span class="sxs-lookup"><span data-stu-id="686b9-201">Example</span></span>  
 <span data-ttu-id="686b9-202">第 1 世代と第 2 世代の Web サービスで HTTPS 通信と最大限の相互運用性を実現する、<xref:System.ServiceModel.NetHttpBinding> の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="686b9-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="686b9-203">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="686b9-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="686b9-204">バインディングの種類は、`binding` 要素の `<endpoint>` 属性を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="686b9-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="686b9-205">基本的なバインディングを構成してその設定の一部を変更する場合は、バインディング構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="686b9-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="686b9-206">エンドポイントは、`bindingConfiguration` 要素の `<endpoint>` 属性を使用して、名前でバインディング構成を参照する必要があります。次のサービスの構成コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="686b9-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard" 
               receiveTimeout="00:10:00" 
               sendTimeout="00:10:00" 
               openTimeout="00:10:00" 
               closeTimeout="00:10:00" 
               maxReceivedMessageSize="65536" 
               maxBufferSize="65536" 
               maxBufferPoolSize="524288" 
               transferMode="Buffered" 
               messageEncoding="Binary" 
               textEncoding="utf-8" 
               bypassProxyOnLocal="false" 
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="686b9-207">例</span><span class="sxs-lookup"><span data-stu-id="686b9-207">Example</span></span>  
 <span data-ttu-id="686b9-208">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="686b9-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="686b9-209">前の例の機能を実行するには、エンドポイント アドレスの bindingConfiguration とバインディングの名前を削除します。</span><span class="sxs-lookup"><span data-stu-id="686b9-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="686b9-210">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="686b9-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686b9-211">参照</span><span class="sxs-lookup"><span data-stu-id="686b9-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="686b9-212">バインディング</span><span class="sxs-lookup"><span data-stu-id="686b9-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="686b9-213">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="686b9-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="686b9-214">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="686b9-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="686b9-215">\<binding></span><span class="sxs-lookup"><span data-stu-id="686b9-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

---
title: '&lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44bc7a3ef40b08d7cee4e515e6628aef9987c0c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbasichttpbindinggt"></a><span data-ttu-id="82409-102">&lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="82409-102">&lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="82409-103">ASMX ベースの Web サービスとクライアント、および WS-I Basic Profile 1.1 に準拠するその他のサービスと通信できるエンドポイントを構成および公開するために [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスが使用できるバインディングを表します。</span><span class="sxs-lookup"><span data-stu-id="82409-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate with ASMX-based Web services and clients and other services that conform to the WS-I Basic Profile 1.1.</span></span>  
  
 <span data-ttu-id="82409-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="82409-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="82409-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="82409-105">\<bindings></span></span>  
<span data-ttu-id="82409-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="82409-106">\<basicHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82409-107">構文</span><span class="sxs-lookup"><span data-stu-id="82409-107">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
              name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82409-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="82409-108">Attributes and Elements</span></span>  
 <span data-ttu-id="82409-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="82409-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82409-110">属性</span><span class="sxs-lookup"><span data-stu-id="82409-110">Attributes</span></span>  
  
|<span data-ttu-id="82409-111">属性</span><span class="sxs-lookup"><span data-stu-id="82409-111">Attribute</span></span>|<span data-ttu-id="82409-112">説明</span><span class="sxs-lookup"><span data-stu-id="82409-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="82409-113">クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="82409-113">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="82409-114">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="82409-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="82409-115">クッキーを使用する ASMX Web サービスと対話する場合にこのプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="82409-115">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="82409-116">この方法で、サーバーから返されるクッキーを、それ以降のサービスに対するすべてのクライアント要求に自動的にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="82409-116">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="82409-117">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="82409-117">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="82409-118">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="82409-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="82409-119">インターネット リソースは、ローカル アドレスを持つ場合ローカルです。</span><span class="sxs-lookup"><span data-stu-id="82409-119">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="82409-120">ローカル アドレスは、同じコンピューター、ローカル LAN、またはイントラネット上にあり、"http://webserver/"、"http://localhost/" などのピリオド (.) を含まない URI により構文的に識別されるアドレスです。</span><span class="sxs-lookup"><span data-stu-id="82409-120">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="82409-121">この属性の設定は、BasicHttpBinding で構成されたエンドポイントがローカル リソースへのアクセス時にプロキシ サーバーを使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="82409-121">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="82409-122">この属性が `true` の場合、ローカル インターネット リソースへの要求はプロキシ サーバーを使用しません。</span><span class="sxs-lookup"><span data-stu-id="82409-122">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="82409-123">この属性を `true` に設定した場合で、同じコンピューター上のサービスと対話するクライアントがプロキシを経由するときは、(localhost ではなく) ホスト名を使用します。</span><span class="sxs-lookup"><span data-stu-id="82409-123">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="82409-124">この属性が `false` の場合、すべてのインターネット要求はプロキシ サーバー経由で行われます。</span><span class="sxs-lookup"><span data-stu-id="82409-124">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="82409-125">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="82409-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="82409-126">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="82409-127">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="82409-127">The default is 00:01:00.</span></span>|  
|`envelopeVersion`|<span data-ttu-id="82409-128">このバインディングによって処理されるメッセージに使用される SOAP のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="82409-128">Specifies the version of SOAP that is used for messages that are processed by this binding.</span></span> <span data-ttu-id="82409-129">有効値は、Soap11 のみです。</span><span class="sxs-lookup"><span data-stu-id="82409-129">The only valid value is Soap11.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="82409-130">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="82409-130">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="82409-131">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="82409-131">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="82409-132">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="82409-132">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="82409-133">チャネルからメッセージを受け取るメッセージ バッファーのマネージャーが使用するために割り当てられる、最大メモリ量を指定する整数値。</span><span class="sxs-lookup"><span data-stu-id="82409-133">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="82409-134">既定値は 524288 (0x80000) バイトです。</span><span class="sxs-lookup"><span data-stu-id="82409-134">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="82409-135">バッファー マネージャーは、バッファー プールを使用することで、バッファーの使用コストを最小化します。</span><span class="sxs-lookup"><span data-stu-id="82409-135">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="82409-136">バッファーは、チャネルから出てくるメッセージをサービスが処理するときに必要です。</span><span class="sxs-lookup"><span data-stu-id="82409-136">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="82409-137">メッセージの読み込み処理に十分なメモリがバッファー プールにない場合、バッファー マネージャーは、CLR ヒープから追加のメモリを割り当てる必要があります。これにより、ガベージ コレクションのオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="82409-137">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="82409-138">CLR ガベージ ヒープから多大な割り当てが行われることは、バッファー プール サイズが小さすぎること、およびこの属性で指定される制限を緩めて割り当てを増やすとパフォーマンスが向上する可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="82409-138">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="82409-139">このバインディングで構成されるエンドポイントのメッセージが処理されるときのメッセージを格納するバッファーの最大サイズを指定する整数値 (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="82409-139">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="82409-140">既定値は 65,536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="82409-140">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="82409-141">このバインディングで構成されるチャネルが受信可能なメッセージの最大メッセージ サイズ (ヘッダーを含む) をバイト単位で定義する正の整数。</span><span class="sxs-lookup"><span data-stu-id="82409-141">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="82409-142">受信側のメッセージが大きすぎると、送信側は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="82409-142">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="82409-143">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="82409-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="82409-144">既定値は 65,536 バイトです。</span><span class="sxs-lookup"><span data-stu-id="82409-144">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="82409-145">SOAP メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="82409-145">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="82409-146">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="82409-146">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="82409-147">: テキストは、テキスト メッセージ エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="82409-147">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="82409-148">Mtom: は、メッセージ Transmission Organization Mechanism 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="82409-148">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="82409-149">既定値は Text です。</span><span class="sxs-lookup"><span data-stu-id="82409-149">The default is Text.</span></span> <span data-ttu-id="82409-150">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="82409-150">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="82409-151">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="82409-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="82409-152">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="82409-153">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="82409-153">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="82409-154">また、この名前は、同じ種類のバインディング間で一意です。</span><span class="sxs-lookup"><span data-stu-id="82409-154">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="82409-155">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="82409-155">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="82409-156">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="82409-156">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="82409-157">バインディングの XML 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="82409-157">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="82409-158">既定値は "http://tempuri.org/Bindings" です。</span><span class="sxs-lookup"><span data-stu-id="82409-158">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="82409-159">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="82409-159">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="82409-160">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="82409-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="82409-161">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="82409-162">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="82409-162">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="82409-163">HTTP プロキシのアドレスを格納する URI。</span><span class="sxs-lookup"><span data-stu-id="82409-163">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="82409-164">`useSystemWebProxy` が `true` に設定されている場合、この設定は `null` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-164">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="82409-165">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="82409-165">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="82409-166">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="82409-166">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="82409-167">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-167">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="82409-168">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="82409-168">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="82409-169">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="82409-169">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="82409-170">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-170">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="82409-171">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="82409-171">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="82409-172">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="82409-172">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="82409-173">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="82409-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="82409-174">-BigEndianUnicode: Unicode BigEndian エンコーディングします。</span><span class="sxs-lookup"><span data-stu-id="82409-174">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="82409-175">Unicode: 16 ビット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="82409-175">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="82409-176">UTF8: 8 ビットのエンコーディング</span><span class="sxs-lookup"><span data-stu-id="82409-176">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="82409-177">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="82409-177">The default is UTF8.</span></span> <span data-ttu-id="82409-178">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="82409-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="82409-179">要求または応答に対してメッセージがバッファーされるか、ストリーム配信されるかを指定する有効な <xref:System.ServiceModel.TransferMode> 値。</span><span class="sxs-lookup"><span data-stu-id="82409-179">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="82409-180">使用できる場合にシステムの自動設定 HTTP プロキシを使用するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="82409-180">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="82409-181">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="82409-181">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82409-182">子要素</span><span class="sxs-lookup"><span data-stu-id="82409-182">Child Elements</span></span>  
  
|<span data-ttu-id="82409-183">要素</span><span class="sxs-lookup"><span data-stu-id="82409-183">Element</span></span>|<span data-ttu-id="82409-184">説明</span><span class="sxs-lookup"><span data-stu-id="82409-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82409-185">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="82409-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="82409-186">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="82409-186">Defines the security settings for the binding.</span></span> <span data-ttu-id="82409-187">この要素は <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="82409-187">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="82409-188">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="82409-188">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="82409-189">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="82409-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="82409-190">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="82409-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82409-191">親要素</span><span class="sxs-lookup"><span data-stu-id="82409-191">Parent Elements</span></span>  
  
|<span data-ttu-id="82409-192">要素</span><span class="sxs-lookup"><span data-stu-id="82409-192">Element</span></span>|<span data-ttu-id="82409-193">説明</span><span class="sxs-lookup"><span data-stu-id="82409-193">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82409-194">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="82409-194">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="82409-195">この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="82409-195">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82409-196">コメント</span><span class="sxs-lookup"><span data-stu-id="82409-196">Remarks</span></span>  
 <span data-ttu-id="82409-197">BasicHttpBinding では、SOAP 1.1 メッセージを送信するために、HTTP をトランスポートとして使用します。</span><span class="sxs-lookup"><span data-stu-id="82409-197">The BasicHttpBinding uses HTTP as the transport for sending SOAP 1.1 messages.</span></span> <span data-ttu-id="82409-198">サービスは、ASMX クライアントが消費するエンドポイントなど、WS-I BP 1.1 に準拠するエンドポイントを開示するためにこのバインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="82409-198">A service can use this binding to expose endpoints that conform to WS-I BP 1.1, such as those that ASMX clients consume.</span></span> <span data-ttu-id="82409-199">同様に、クライアントは BasicHttpBinding を使用して、ASMX Web サービスや BasicHttpBinding で構成されるサービスなどの WS-I BP 1.1 に準じるエンドポイントを公開するサービスと通信できます。</span><span class="sxs-lookup"><span data-stu-id="82409-199">Similarly, a client can use the BasicHttpBinding to communicate with services exposing endpoints that conform to WS-I BP 1.1, such as ASMX Web services or services configured with the BasicHttpBinding.</span></span>  
  
 <span data-ttu-id="82409-200">セキュリティは既定では、になっていますの mode 属性の設定を追加できます、 [\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)以外の値を子要素`None`です。</span><span class="sxs-lookup"><span data-stu-id="82409-200">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="82409-201">サービスは、"Text" メッセージ エンコードおよび UTF-8 テキスト エンコードを既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="82409-201">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82409-202">例</span><span class="sxs-lookup"><span data-stu-id="82409-202">Example</span></span>  
 <span data-ttu-id="82409-203">第 1 世代と第 2 世代の Web サービスで HTTP 通信と最大限の相互運用性を実現する、<xref:System.ServiceModel.BasicHttpBinding> の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="82409-203">The following example demonstrates the use of <xref:System.ServiceModel.BasicHttpBinding> that provides HTTP communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="82409-204">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="82409-204">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="82409-205">バインディングの種類は、`binding` 要素の `<endpoint>` 属性を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="82409-205">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="82409-206">基本的なバインディングを構成してその設定の一部を変更する場合は、バインディング構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82409-206">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="82409-207">エンドポイントは、`bindingConfiguration` 要素の `<endpoint>` 属性を使用して、名前でバインディング構成を参照する必要があります。次のサービスの構成コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="82409-207">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
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
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="82409-208">例</span><span class="sxs-lookup"><span data-stu-id="82409-208">Example</span></span>  
 <span data-ttu-id="82409-209">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="82409-209">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="82409-210">前の例の機能を実行するには、エンドポイント アドレスの bindingConfiguration とバインディングの名前を削除します。</span><span class="sxs-lookup"><span data-stu-id="82409-210">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
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
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="82409-211">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="82409-211">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82409-212">参照</span><span class="sxs-lookup"><span data-stu-id="82409-212">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="82409-213">バインディング</span><span class="sxs-lookup"><span data-stu-id="82409-213">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="82409-214">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="82409-214">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="82409-215">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="82409-215">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="82409-216">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="82409-216">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

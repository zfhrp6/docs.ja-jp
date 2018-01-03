---
title: '&lt;ws2007HttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a92ab5b85a65793473dcafbd67ac710912a476f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="81098-102">&lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="81098-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="81098-103"><xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession>、および <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> の各バインディング要素の適切なバージョンをサポートする相互運用可能なバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="81098-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="81098-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="81098-104">\<system.serviceModel></span></span>  
<span data-ttu-id="81098-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="81098-105">\<bindings></span></span>  
<span data-ttu-id="81098-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="81098-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81098-107">構文</span><span class="sxs-lookup"><span data-stu-id="81098-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81098-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="81098-108">Attributes and Elements</span></span>  
 <span data-ttu-id="81098-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="81098-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81098-110">属性</span><span class="sxs-lookup"><span data-stu-id="81098-110">Attributes</span></span>  
  
|<span data-ttu-id="81098-111">属性</span><span class="sxs-lookup"><span data-stu-id="81098-111">Attribute</span></span>|<span data-ttu-id="81098-112">説明</span><span class="sxs-lookup"><span data-stu-id="81098-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="81098-113">クライアントがクッキーを受け入れて、それらを今後の要求に反映させるかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="81098-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="81098-114">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="81098-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="81098-115">クッキーを使用する ASMX (ASP.NET Web サービス) と対話する場合に、このプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="81098-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="81098-116">これにより、サーバーから返されるクッキーが、このサービスに対するそれ以降のすべてのクライアント要求に自動的にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="81098-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="81098-117">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="81098-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="81098-118">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="81098-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="81098-119">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="81098-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="81098-120">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="81098-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81098-121">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="81098-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="81098-122">URI (Uniform Resource Identifier) の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="81098-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="81098-123">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="81098-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="81098-124">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="81098-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="81098-125">このバインドに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="81098-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="81098-126">既定値は 524,288 バイト (512 × 1,024) です。</span><span class="sxs-lookup"><span data-stu-id="81098-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="81098-127">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] の多くの部分でバッファーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="81098-127">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="81098-128">使用するたびに毎回バッファーを作成および破棄すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="81098-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="81098-129">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="81098-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="81098-130">これで、バッファーの作成と破棄によるオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="81098-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="81098-131">このバインディングで構成されたチャネルで受信可能な、ヘッダーを含む最大メッセージ サイズ (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="81098-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="81098-132">この制限を超える場合、メッセージの送信者は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="81098-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="81098-133">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="81098-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="81098-134">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="81098-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="81098-135">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="81098-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="81098-136">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="81098-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81098-137">-   `Text`: テキスト メッセージ エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="81098-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="81098-138">-   `Mtom`: メッセージ Transmission Organization Mechanism 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="81098-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="81098-139">既定値は、`Text` です。</span><span class="sxs-lookup"><span data-stu-id="81098-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="81098-140">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="81098-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="81098-141">バインドの構成名。</span><span class="sxs-lookup"><span data-stu-id="81098-141">The configuration name of the binding.</span></span> <span data-ttu-id="81098-142">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="81098-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="81098-143">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="81098-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="81098-144">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="81098-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="81098-145">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="81098-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="81098-146">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="81098-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81098-147">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="81098-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="81098-148">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="81098-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="81098-149">`useSystemWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="81098-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="81098-150">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="81098-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="81098-151">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="81098-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="81098-152">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="81098-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81098-153">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="81098-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="81098-154">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="81098-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="81098-155">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="81098-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="81098-156">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="81098-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="81098-157">バインディングでメッセージの発行に使用する文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="81098-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="81098-158">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="81098-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="81098-159">-   `UnicodeFffeTextEncoding`: Unicode ビッグ エンディアン エンコーディングします。</span><span class="sxs-lookup"><span data-stu-id="81098-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="81098-160">-   `Utf16TextEncoding`: 16 ビット エンコーディングします。</span><span class="sxs-lookup"><span data-stu-id="81098-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="81098-161">-   `Utf8TextEncoding`: 8 ビット エンコーディングします。</span><span class="sxs-lookup"><span data-stu-id="81098-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="81098-162">既定値は、`Utf8TextEncoding` です。</span><span class="sxs-lookup"><span data-stu-id="81098-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="81098-163">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="81098-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="81098-164">バインドが WS-Transactions のフローをサポートするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="81098-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="81098-165">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="81098-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="81098-166">システムの自動設定 HTTP プロキシを使用するかどうかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="81098-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="81098-167">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="81098-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81098-168">子要素</span><span class="sxs-lookup"><span data-stu-id="81098-168">Child Elements</span></span>  
  
|<span data-ttu-id="81098-169">要素</span><span class="sxs-lookup"><span data-stu-id="81098-169">Element</span></span>|<span data-ttu-id="81098-170">説明</span><span class="sxs-lookup"><span data-stu-id="81098-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81098-171">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="81098-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="81098-172">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="81098-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="81098-173">この要素は <xref:System.ServiceModel.Configuration.WSHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="81098-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="81098-174">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="81098-174">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="81098-175">このバインディングを使用して設定されるエンドポイントで処理できる、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="81098-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="81098-176">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="81098-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="81098-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="81098-177">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="81098-178">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="81098-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81098-179">親要素</span><span class="sxs-lookup"><span data-stu-id="81098-179">Parent Elements</span></span>  
  
|<span data-ttu-id="81098-180">要素</span><span class="sxs-lookup"><span data-stu-id="81098-180">Element</span></span>|<span data-ttu-id="81098-181">説明</span><span class="sxs-lookup"><span data-stu-id="81098-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81098-182">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="81098-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="81098-183">この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="81098-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81098-184">コメント</span><span class="sxs-lookup"><span data-stu-id="81098-184">Remarks</span></span>  
 <span data-ttu-id="81098-185">`WS2007HttpBinding` は、`WSHttpBinding` と同様のシステム標準のバインディングを追加しますが、ReliableSession、Security、および TransactionFlow の各プロトコルの OASIS (Organization for the Advancement of Structured Information Standards) 標準バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="81098-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="81098-186">このバインドを使用する場合、オブジェクト モデルも既定の設定も変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="81098-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81098-187">例</span><span class="sxs-lookup"><span data-stu-id="81098-187">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81098-188">参照</span><span class="sxs-lookup"><span data-stu-id="81098-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="81098-189">バインディング</span><span class="sxs-lookup"><span data-stu-id="81098-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="81098-190">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="81098-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="81098-191">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="81098-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="81098-192">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="81098-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

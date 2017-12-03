---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fce87326396d5e0f2a568fbd9b197b7a664f7e6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="b5492-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b5492-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="b5492-103">派生したセキュリティで保護された相互操作可能なバインディング[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)フェデレーション セキュリティをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b5492-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="b5492-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b5492-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b5492-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b5492-105">\<bindings></span></span>  
<span data-ttu-id="b5492-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b5492-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5492-107">構文</span><span class="sxs-lookup"><span data-stu-id="b5492-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5492-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b5492-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b5492-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b5492-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5492-110">属性</span><span class="sxs-lookup"><span data-stu-id="b5492-110">Attributes</span></span>  
  
|<span data-ttu-id="b5492-111">属性</span><span class="sxs-lookup"><span data-stu-id="b5492-111">Attribute</span></span>|<span data-ttu-id="b5492-112">説明</span><span class="sxs-lookup"><span data-stu-id="b5492-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="b5492-113">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="b5492-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b5492-114">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="b5492-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b5492-115">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="b5492-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b5492-116">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b5492-117">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b5492-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="b5492-118">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5492-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b5492-119">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5492-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b5492-120">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="b5492-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b5492-121">このバインドに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="b5492-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b5492-122">既定は 524,288 バイト (512 * 1024) です。</span><span class="sxs-lookup"><span data-stu-id="b5492-122">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="b5492-123">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] の多くの部分でバッファーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5492-123">Many parts of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] use buffers.</span></span> <span data-ttu-id="b5492-124">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="b5492-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="b5492-125">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="b5492-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="b5492-126">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="b5492-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b5492-127">チャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) が、このバインドを使用してバイト単位で設定されました。</span><span class="sxs-lookup"><span data-stu-id="b5492-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b5492-128">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="b5492-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="b5492-129">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b5492-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b5492-130">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="b5492-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b5492-131">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="b5492-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="b5492-132">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="b5492-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b5492-133">: テキストは、テキスト メッセージ エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b5492-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="b5492-134">Mtom: は、メッセージ Transmission Organization Mechanism 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="b5492-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b5492-135">既定値は Text です。</span><span class="sxs-lookup"><span data-stu-id="b5492-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="b5492-136">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="b5492-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b5492-137">バインドの構成名。</span><span class="sxs-lookup"><span data-stu-id="b5492-137">The configuration name of the binding.</span></span> <span data-ttu-id="b5492-138">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b5492-139">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b5492-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b5492-140">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5492-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b5492-141">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b5492-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b5492-142">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b5492-143">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b5492-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="b5492-144">プライバシーに関する声明の場所を示す URI。</span><span class="sxs-lookup"><span data-stu-id="b5492-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="b5492-145">現在のプライバシーに関する声明のバージョン。</span><span class="sxs-lookup"><span data-stu-id="b5492-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b5492-146">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="b5492-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="b5492-147">`useDefaultWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="b5492-148">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="b5492-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b5492-149">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b5492-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b5492-150">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b5492-151">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="b5492-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b5492-152">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="b5492-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b5492-153">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b5492-154">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="b5492-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b5492-155">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="b5492-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b5492-156">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="b5492-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b5492-157">-BigEndianUnicode: Unicode ビッグ エンディアン エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="b5492-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="b5492-158">Unicode: 16 ビット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="b5492-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b5492-159">-Utf 8: 8 ビット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="b5492-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b5492-160">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="b5492-160">The default is UTF8.</span></span> <span data-ttu-id="b5492-161">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="b5492-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="b5492-162">バインドが WS-Transactions のフローをサポートするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="b5492-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b5492-163">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="b5492-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b5492-164">システムの自動設定 HTTP プロキシを使用するかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="b5492-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="b5492-165">この属性が `null` の場合、プロキシ アドレスを `true` (つまり、設定しない) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="b5492-166">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="b5492-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5492-167">子要素</span><span class="sxs-lookup"><span data-stu-id="b5492-167">Child Elements</span></span>  
  
|<span data-ttu-id="b5492-168">要素</span><span class="sxs-lookup"><span data-stu-id="b5492-168">Element</span></span>|<span data-ttu-id="b5492-169">説明</span><span class="sxs-lookup"><span data-stu-id="b5492-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5492-170">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="b5492-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="b5492-171">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5492-171">Defines the security settings for the message.</span></span> <span data-ttu-id="b5492-172">この要素は <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="b5492-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="b5492-173">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="b5492-173">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b5492-174">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5492-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b5492-175">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="b5492-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="b5492-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="b5492-176">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="b5492-177">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b5492-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b5492-178">親要素</span><span class="sxs-lookup"><span data-stu-id="b5492-178">Parent Elements</span></span>  
  
|<span data-ttu-id="b5492-179">要素</span><span class="sxs-lookup"><span data-stu-id="b5492-179">Element</span></span>|<span data-ttu-id="b5492-180">説明</span><span class="sxs-lookup"><span data-stu-id="b5492-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5492-181">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b5492-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b5492-182">この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="b5492-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5492-183">コメント</span><span class="sxs-lookup"><span data-stu-id="b5492-183">Remarks</span></span>  
 <span data-ttu-id="b5492-184">フェデレーションは、複数の企業または信頼するドメインで認証と承認用の ID を共有する機能です。</span><span class="sxs-lookup"><span data-stu-id="b5492-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="b5492-185">フェデレーションは、WS-Trust プロトコルを使用して、ID 形式を、ある信頼するドメインから別の信頼するドメインにマップします。</span><span class="sxs-lookup"><span data-stu-id="b5492-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="b5492-186">フェデレーション HTTP バインドは、SOAP セキュリティと混合モード セキュリティをサポートしますが、トランスポート セキュリティの単独使用はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="b5492-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="b5492-187">このバインディングで構成されたサービスは、HTTP トランスポートを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5492-187">Services configured with this binding must use the HTTP transport.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="b5492-188">[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5492-188"> [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5492-189">例</span><span class="sxs-lookup"><span data-stu-id="b5492-189">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5492-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5492-190">See Also</span></span>  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [<span data-ttu-id="b5492-191">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b5492-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [<span data-ttu-id="b5492-192">バインディング</span><span class="sxs-lookup"><span data-stu-id="b5492-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b5492-193">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="b5492-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b5492-194">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="b5492-194">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b5492-195">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b5492-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

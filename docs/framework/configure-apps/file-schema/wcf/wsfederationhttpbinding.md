---
title: '&lt;wsFederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 694b904587795823ae2f730b8182f404eba93a58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltwsfederationhttpbindinggt"></a><span data-ttu-id="595ae-102">&lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="595ae-102">&lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="595ae-103">WS-Federation をサポートするバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="595ae-103">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="595ae-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="595ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="595ae-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="595ae-105">\<bindings></span></span>  
<span data-ttu-id="595ae-106">wsFederationBinding 要素</span><span class="sxs-lookup"><span data-stu-id="595ae-106">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595ae-107">構文</span><span class="sxs-lookup"><span data-stu-id="595ae-107">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>  
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
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="595ae-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="595ae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="595ae-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="595ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="595ae-110">属性</span><span class="sxs-lookup"><span data-stu-id="595ae-110">Attributes</span></span>  
  
|<span data-ttu-id="595ae-111">属性</span><span class="sxs-lookup"><span data-stu-id="595ae-111">Attribute</span></span>|<span data-ttu-id="595ae-112">説明</span><span class="sxs-lookup"><span data-stu-id="595ae-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="595ae-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="595ae-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="595ae-114">ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="595ae-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="595ae-115">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="595ae-115">The default is `false`.</span></span>|  
|<span data-ttu-id="595ae-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="595ae-116">closeTimeout</span></span>|<span data-ttu-id="595ae-117">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="595ae-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="595ae-118">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="595ae-119">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="595ae-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="595ae-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="595ae-120">hostnameComparisonMode</span></span>|<span data-ttu-id="595ae-121">URI の解析に使用する HTTP ホスト名比較モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="595ae-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="595ae-122">この属性は <xref:System.ServiceModel.HostNameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="595ae-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="595ae-123">既定値は <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。</span><span class="sxs-lookup"><span data-stu-id="595ae-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="595ae-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="595ae-124">maxBufferPoolSize</span></span>|<span data-ttu-id="595ae-125">このバインディングに使用するバッファー プール サイズの上限を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="595ae-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="595ae-126">既定は 524,288 バイト (512 * 1024) です。</span><span class="sxs-lookup"><span data-stu-id="595ae-126">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="595ae-127">Windows Communication Foundation (WCF) では、多くの部分でバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="595ae-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="595ae-128">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="595ae-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="595ae-129">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="595ae-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="595ae-130">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="595ae-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="595ae-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="595ae-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="595ae-132">このバインディングで構成されるチャネルで受信可能な最大メッセージ サイズ (ヘッダーを含む) をバイト単位で指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="595ae-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="595ae-133">この制限を超えるメッセージの送信者が、SOAP エラーを受信します。</span><span class="sxs-lookup"><span data-stu-id="595ae-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="595ae-134">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="595ae-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="595ae-135">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="595ae-135">The default is 65536.</span></span>|  
|<span data-ttu-id="595ae-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="595ae-136">messageEncoding</span></span>|<span data-ttu-id="595ae-137">メッセージのエンコードに使用されるエンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="595ae-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="595ae-138">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="595ae-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="595ae-139">: テキストは、テキスト メッセージ エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="595ae-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="595ae-140">Mtom: は、メッセージ Transmission Organization Mechanism 1.0 (MTOM) エンコーダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="595ae-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="595ae-141">既定値は Text です。</span><span class="sxs-lookup"><span data-stu-id="595ae-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="595ae-142">この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="595ae-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="595ae-143">name</span><span class="sxs-lookup"><span data-stu-id="595ae-143">name</span></span>|<span data-ttu-id="595ae-144">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="595ae-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="595ae-145">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="595ae-146">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="595ae-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="595ae-147">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="595ae-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="595ae-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="595ae-148">openTimeout</span></span>|<span data-ttu-id="595ae-149">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="595ae-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="595ae-150">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="595ae-151">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="595ae-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="595ae-152">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="595ae-152">privactyNoticeAt</span></span>|<span data-ttu-id="595ae-153">プライバシーに関する声明の場所を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="595ae-153">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="595ae-154">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="595ae-154">privactyNoticeVersion</span></span>|<span data-ttu-id="595ae-155">現在のプライバシーに関する声明のバージョンを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="595ae-155">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="595ae-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="595ae-156">proxyAddress</span></span>|<span data-ttu-id="595ae-157">HTTP プロキシのアドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="595ae-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="595ae-158">`useDefaultWebProxy` が `true` の場合、この設定を `null` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="595ae-159">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="595ae-159">The default is `null`.</span></span>|  
|<span data-ttu-id="595ae-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="595ae-160">receiveTimeout</span></span>|<span data-ttu-id="595ae-161">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="595ae-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="595ae-162">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="595ae-163">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="595ae-163">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="595ae-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="595ae-164">sendTimeout</span></span>|<span data-ttu-id="595ae-165">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="595ae-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="595ae-166">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="595ae-167">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="595ae-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="595ae-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="595ae-168">textEncoding</span></span>|<span data-ttu-id="595ae-169">バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。</span><span class="sxs-lookup"><span data-stu-id="595ae-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="595ae-170">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="595ae-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="595ae-171">-BigEndianUnicode: Unicode BigEndian エンコーディングします。</span><span class="sxs-lookup"><span data-stu-id="595ae-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="595ae-172">Unicode: 16 ビット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="595ae-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="595ae-173">UTF8: 8 ビットのエンコーディング</span><span class="sxs-lookup"><span data-stu-id="595ae-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="595ae-174">既定値は UTF8 です。</span><span class="sxs-lookup"><span data-stu-id="595ae-174">The default is UTF8.</span></span> <span data-ttu-id="595ae-175">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="595ae-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="595ae-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="595ae-176">transactionFlow</span></span>|<span data-ttu-id="595ae-177">バインディングが WS-Transactions のフローをサポートするかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="595ae-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="595ae-178">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="595ae-178">The default is `false`.</span></span>|  
|<span data-ttu-id="595ae-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="595ae-179">useDefaultWebProxy</span></span>|<span data-ttu-id="595ae-180">システムの自動設定 HTTP プロキシを使用するかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="595ae-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="595ae-181">この属性が `null` の場合、プロキシ アドレスを `true` (つまり、設定しない) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="595ae-182">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="595ae-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="595ae-183">子要素</span><span class="sxs-lookup"><span data-stu-id="595ae-183">Child Elements</span></span>  
  
|<span data-ttu-id="595ae-184">要素</span><span class="sxs-lookup"><span data-stu-id="595ae-184">Element</span></span>|<span data-ttu-id="595ae-185">説明</span><span class="sxs-lookup"><span data-stu-id="595ae-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="595ae-186">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="595ae-186">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="595ae-187">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="595ae-187">Defines the security settings for the message.</span></span> <span data-ttu-id="595ae-188">この要素は <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="595ae-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="595ae-189">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="595ae-189">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="595ae-190">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="595ae-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="595ae-191">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="595ae-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="595ae-192">reliableSession</span><span class="sxs-lookup"><span data-stu-id="595ae-192">reliableSession</span></span>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="595ae-193">チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="595ae-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="595ae-194">親要素</span><span class="sxs-lookup"><span data-stu-id="595ae-194">Parent Elements</span></span>  
  
|<span data-ttu-id="595ae-195">要素</span><span class="sxs-lookup"><span data-stu-id="595ae-195">Element</span></span>|<span data-ttu-id="595ae-196">説明</span><span class="sxs-lookup"><span data-stu-id="595ae-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="595ae-197">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="595ae-197">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="595ae-198">この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="595ae-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="595ae-199">コメント</span><span class="sxs-lookup"><span data-stu-id="595ae-199">Remarks</span></span>  
 <span data-ttu-id="595ae-200">フェデレーションは、複数のシステム間で認証と承認用の ID を共有する機能です。</span><span class="sxs-lookup"><span data-stu-id="595ae-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="595ae-201">これらの ID は、ユーザーまたはコンピューターを参照できます。</span><span class="sxs-lookup"><span data-stu-id="595ae-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="595ae-202">フェデレーション HTTP は、SOAP セキュリティと混合モード セキュリティをサポートしますが、トランスポート セキュリティの単独使用はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="595ae-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="595ae-203">このバインドは、WS-Federation プロトコルに対して [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="595ae-203">This binding provides [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] support for the WS-Federation protocol.</span></span> <span data-ttu-id="595ae-204">このバインディングで構成されたサービスは、HTTP トランスポートを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-204">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="595ae-205">バインドは、バインド要素のスタックで構成されます。</span><span class="sxs-lookup"><span data-stu-id="595ae-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="595ae-206">内の要素をバインディングのスタック</span><span class="sxs-lookup"><span data-stu-id="595ae-206">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="595ae-207">`wsFederationHttpBinding` のバインディング要素のスタックは、`wsHttpBinding` に含まれる</span><span class="sxs-lookup"><span data-stu-id="595ae-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="595ae-208">ときに[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)の既定値に設定されている<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>です。</span><span class="sxs-lookup"><span data-stu-id="595ae-208">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="595ae-209">`wsFederationHttpBinding`でメッセージのセキュリティ設定の詳細を制御[\<メッセージ >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="595ae-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="595ae-210">なお、 [\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)要素では、get アクセスのみ、バインディングを作成した後、バインディングによって使用されるセキュリティを変更ことはできません。</span><span class="sxs-lookup"><span data-stu-id="595ae-210">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="595ae-211">`wsFederationHttpBinding` は、プライバシーに関する声明の場所を示す URI の設定と取得を行う privactyNoticeAt 属性も提供します。</span><span class="sxs-lookup"><span data-stu-id="595ae-211">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="595ae-212">ポリシーをセキュリティで保護することが、フェデレーション シナリオでは特に重要です。</span><span class="sxs-lookup"><span data-stu-id="595ae-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="595ae-213">ポリシーを悪意のあるユーザーから保護するには、HTTPS などのセキュリティ形式の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="595ae-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="595ae-214">フェデレーション シナリオでこのバインディングを使用する場合は、発行済み (SAML) トークンの暗号化に使用するキー、トークンに入れるクレームの種類などの重要情報がサービス ポリシーに含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="595ae-215">これが改ざんされると、攻撃者は発行済みトークンのキーを発見してさらに改ざんを行ったり、情報を暴露したりなどの悪意ある行動を取る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="595ae-216">このような行為を防ぐには、(HTTPS などを使用して) ポリシーをセキュリティで保護し、サービスから安全に取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="595ae-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="595ae-217">このバインディングの詳細については、次を参照してください。[する方法: WSFederationHttpBinding を作成](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="595ae-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="595ae-218">例</span><span class="sxs-lookup"><span data-stu-id="595ae-218">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="saml"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</wsFederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="595ae-219">関連項目</span><span class="sxs-lookup"><span data-stu-id="595ae-219">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [<span data-ttu-id="595ae-220">方法: WSFederationHttpBinding を作成します。</span><span class="sxs-lookup"><span data-stu-id="595ae-220">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="595ae-221">バインディング</span><span class="sxs-lookup"><span data-stu-id="595ae-221">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="595ae-222">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="595ae-222">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="595ae-223">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="595ae-223">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="595ae-224">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="595ae-224">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)

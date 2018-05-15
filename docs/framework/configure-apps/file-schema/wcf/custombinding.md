---
title: '&lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 5d423a29430284c904bcfe8eb11ec470a62ecf57
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="dd439-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="dd439-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="dd439-103">ユーザーのメッセージ スタックを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="dd439-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dd439-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dd439-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="dd439-105">\<bindings></span></span>  
<span data-ttu-id="dd439-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="dd439-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd439-107">構文</span><span class="sxs-lookup"><span data-stu-id="dd439-107">Syntax</span></span>  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           authenticationMode="UserNameForAnonymous"  
           contextMode="Cookie"   
           defaultProtectionLevel="Sign"  
           enableKeyDerivation="false"  
           keyEntropyMode="ClientEntropy"   
                  messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"   
           securityVersion="WSSecurityXXX2005">  
           <localClientSettings cacheCookies="false"  
               detectReplays="false"  
               maxCookieCachingTime="00:07:24" />  
           <localServiceSettings replayCacheSize="9"  
               maxClockSkew="00:00:03"   
               replayWindow="00:07:22.2190000" />  
       </security>  
       <binaryMessageEncoding maxReadPoolSize="Integer"  
           maxWritePoolSize="Integer"  
           maxSessionSize="Integer" />  
       <httpsTransport manualAddressing="Boolean"  
           maxMessageSize="Integer"  
           authenticationScheme="Negotiate"   
           bypassProxyOnLocal="Boolean"  
           hostNameComparisonMode="Exact"   
           mapAddressingHeadersToHttpHeaders="Boolean"   
           proxyaddress="Uri"  
           realm="String"   
           requireClientCertificate="Boolean" />  
       <peerTransport manualAddressing="false"  
          maxMessageSize="20002"  
          listenIPAddress="202.10.1.9"   
          messageAuthentication="false"  
          peerNodeAuthenticationMode="None"  
          port="1000" />  
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd439-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dd439-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dd439-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd439-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd439-110">属性</span><span class="sxs-lookup"><span data-stu-id="dd439-110">Attributes</span></span>  
  
|<span data-ttu-id="dd439-111">属性</span><span class="sxs-lookup"><span data-stu-id="dd439-111">Attribute</span></span>|<span data-ttu-id="dd439-112">説明</span><span class="sxs-lookup"><span data-stu-id="dd439-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd439-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="dd439-113">closeTimeout</span></span>|<span data-ttu-id="dd439-114">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="dd439-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dd439-115">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd439-116">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="dd439-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dd439-117">name</span><span class="sxs-lookup"><span data-stu-id="dd439-117">name</span></span>|<span data-ttu-id="dd439-118">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="dd439-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dd439-119">この値は、カスタム バインディングの識別文字列として機能するユーザー定義文字列です。</span><span class="sxs-lookup"><span data-stu-id="dd439-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="dd439-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dd439-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dd439-121">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd439-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="dd439-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="dd439-122">openTimeout</span></span>|<span data-ttu-id="dd439-123">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="dd439-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dd439-124">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd439-125">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="dd439-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dd439-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="dd439-126">receiveTimeout</span></span>|<span data-ttu-id="dd439-127">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="dd439-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dd439-128">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd439-129">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="dd439-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dd439-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="dd439-130">sendTimeout</span></span>|<span data-ttu-id="dd439-131">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="dd439-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dd439-132">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd439-133">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="dd439-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd439-134">子要素</span><span class="sxs-lookup"><span data-stu-id="dd439-134">Child Elements</span></span>  
  
|<span data-ttu-id="dd439-135">要素</span><span class="sxs-lookup"><span data-stu-id="dd439-135">Element</span></span>|<span data-ttu-id="dd439-136">説明</span><span class="sxs-lookup"><span data-stu-id="dd439-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd439-137">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="dd439-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="dd439-138">カスタム バインドの双方向のメッセージングを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="dd439-139">たとえば HTTP のように、ネイティブでの二重通信を許可しないトランスポートで使用されます。</span><span class="sxs-lookup"><span data-stu-id="dd439-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="dd439-140">これとは対照的に、TCP では、二重通信がネイティブで許可されているので、クライアントにメッセージを返信するためにこのバインディング要素をサービスで使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dd439-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="dd439-141">クライアントは、サービスのアドレスを公開して、アクセスおよび接続の確立ができるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="dd439-142">このクライアント アドレスは、`ClientBaseAddress` 属性によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="dd439-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="dd439-143">この要素は <xref:System.ServiceModel.Configuration.CompositeDuplexElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="dd439-144">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="dd439-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="dd439-145">PNRP (Peer Name Resolution Protocol) ピア名リゾルバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="dd439-146">この要素は <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="dd439-147">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="dd439-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="dd439-148">WS-ReliableMessaging の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="dd439-149">この要素がカスタム バインディングに追加される場合、その結果となるチャネルにより、正確に 1 回の配信保証をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="dd439-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="dd439-150">この要素は <xref:System.ServiceModel.Configuration.ReliableSessionElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="dd439-151">\<security></span><span class="sxs-lookup"><span data-stu-id="dd439-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="dd439-152">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="dd439-153">この要素は <xref:System.ServiceModel.Configuration.SecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="dd439-154">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="dd439-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="dd439-155">SSL ストリーム バインディングのセキュリティ設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="dd439-156">この要素は <xref:System.ServiceModel.Configuration.SslStreamSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="dd439-157">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="dd439-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="dd439-158">バインディングがトランザクション フローをサポートし、プロトコルが `transactionProtocol` 属性によって使用される必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="dd439-159">この要素は <xref:System.ServiceModel.Configuration.TransactionFlowElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="dd439-160">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="dd439-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="dd439-161">カスタム バインドのストリーミング セキュリティのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd439-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="dd439-162">この要素は <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dd439-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd439-163">親要素</span><span class="sxs-lookup"><span data-stu-id="dd439-163">Parent Elements</span></span>  
  
|<span data-ttu-id="dd439-164">要素</span><span class="sxs-lookup"><span data-stu-id="dd439-164">Element</span></span>|<span data-ttu-id="dd439-165">説明</span><span class="sxs-lookup"><span data-stu-id="dd439-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd439-166">バインディング</span><span class="sxs-lookup"><span data-stu-id="dd439-166">bindings</span></span>|<span data-ttu-id="dd439-167">Windows Communication Foundation アプリケーションのすべてのバインディングを含みます。</span><span class="sxs-lookup"><span data-stu-id="dd439-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd439-168">コメント</span><span class="sxs-lookup"><span data-stu-id="dd439-168">Remarks</span></span>  
 <span data-ttu-id="dd439-169">カスタム バインドを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。</span><span class="sxs-lookup"><span data-stu-id="dd439-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="dd439-170">特定のエンティティの構成要素を追加した、特別にカスタマイズされたバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="dd439-171">たとえば、ユーザーは `httpsTransport` セクション、`reliableSession` セクション、および `security` セクションを組み合わせて、信頼できるセキュリティで保護された HTTPS ベースのバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="dd439-172">個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。</span><span class="sxs-lookup"><span data-stu-id="dd439-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="dd439-173">各要素は、スタック内の 1 つの要素を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="dd439-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="dd439-174">各カスタム バインディング内のトランスポート要素は 1 つだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="dd439-175">この要素がない場合、メッセージ スタックは不完全です。</span><span class="sxs-lookup"><span data-stu-id="dd439-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="dd439-176">要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。</span><span class="sxs-lookup"><span data-stu-id="dd439-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="dd439-177">スタック要素で推奨される順序を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dd439-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="dd439-178">トランザクション (省略可能)</span><span class="sxs-lookup"><span data-stu-id="dd439-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="dd439-179">リライアブル メッセージ機能 (省略可能)</span><span class="sxs-lookup"><span data-stu-id="dd439-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="dd439-180">セキュリティ (省略可能)</span><span class="sxs-lookup"><span data-stu-id="dd439-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="dd439-181">Transport</span><span class="sxs-lookup"><span data-stu-id="dd439-181">Transport</span></span>  
  
5.  <span data-ttu-id="dd439-182">エンコーダー (省略可能)</span><span class="sxs-lookup"><span data-stu-id="dd439-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="dd439-183">システムが提供するバインディングの中にサービスの要件を満たすものがない場合は、カスタム バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd439-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="dd439-184">たとえば、カスタム バインドを使用すると、サービス エンドポイントで新しいトランスポートや新しいエンコーダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="dd439-185">カスタム バインドは、特定の順序で "積み重ねられている" バインド要素のコレクションから <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> の 1 つを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="dd439-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="dd439-186">最上位にあるのは、トランザクションのフローを可能にするオプションの <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> です。</span><span class="sxs-lookup"><span data-stu-id="dd439-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="dd439-187">その次にあるのは、WS-ReliableMessaging 仕様で定義されているセッションおよび順序指定のメカニズムを提供するオプションの <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> です。</span><span class="sxs-lookup"><span data-stu-id="dd439-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="dd439-188">このセッションの概念は、SOAP およびトランスポート中継局を通過できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="dd439-189">その次にあるのは、承認、認証、保護、機密性などのセキュリティ機能を提供するオプションのセキュリティ バインド要素です。</span><span class="sxs-lookup"><span data-stu-id="dd439-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="dd439-190">次のセキュリティ バインド要素は、Windows Communication Foundation (WCF) によって用意されています。</span><span class="sxs-lookup"><span data-stu-id="dd439-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="dd439-191">その次にあるのは、バインド要素によって指定されるオプションのメッセージ パターンです。</span><span class="sxs-lookup"><span data-stu-id="dd439-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="dd439-192">その次にあるのは、オプションのトランスポート アップグレード/ヘルパー バインド要素です。</span><span class="sxs-lookup"><span data-stu-id="dd439-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="dd439-193">その次にあるのは、必須のメッセージ エンコード バインディング要素です。</span><span class="sxs-lookup"><span data-stu-id="dd439-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="dd439-194">独自のトランスポートを使用することも、以下のメッセージ エンコード バインドのいずれかを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="dd439-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="dd439-195">最下位には、必須のトランスポート要素があります。</span><span class="sxs-lookup"><span data-stu-id="dd439-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="dd439-196">独自のトランスポートを使用してまたはトランスポート バインド要素の Windows Communication Foundation (WCF) によって提供されるのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="dd439-197">各層のオプションの概要を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="dd439-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="dd439-198">レイヤー</span><span class="sxs-lookup"><span data-stu-id="dd439-198">Layer</span></span>|<span data-ttu-id="dd439-199">オプション</span><span class="sxs-lookup"><span data-stu-id="dd439-199">Options</span></span>|<span data-ttu-id="dd439-200">必須</span><span class="sxs-lookup"><span data-stu-id="dd439-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="dd439-201">トランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="dd439-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="dd439-202">Ｘ</span><span class="sxs-lookup"><span data-stu-id="dd439-202">No</span></span>|  
|<span data-ttu-id="dd439-203">信頼性</span><span class="sxs-lookup"><span data-stu-id="dd439-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="dd439-204">Ｘ</span><span class="sxs-lookup"><span data-stu-id="dd439-204">No</span></span>|  
|<span data-ttu-id="dd439-205">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="dd439-205">Security</span></span>|<span data-ttu-id="dd439-206">同期、非同期、トランスポート レベル</span><span class="sxs-lookup"><span data-stu-id="dd439-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="dd439-207">Ｘ</span><span class="sxs-lookup"><span data-stu-id="dd439-207">No</span></span>|  
|<span data-ttu-id="dd439-208">形状の変更</span><span class="sxs-lookup"><span data-stu-id="dd439-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="dd439-209">Ｘ</span><span class="sxs-lookup"><span data-stu-id="dd439-209">No</span></span>|  
|<span data-ttu-id="dd439-210">トランスポートのアップグレード</span><span class="sxs-lookup"><span data-stu-id="dd439-210">Transport Upgrades</span></span>|<span data-ttu-id="dd439-211">SSL ストリーム、Windows ストリーム、ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="dd439-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="dd439-212">Ｘ</span><span class="sxs-lookup"><span data-stu-id="dd439-212">No</span></span>|  
|<span data-ttu-id="dd439-213">エンコーディング</span><span class="sxs-lookup"><span data-stu-id="dd439-213">Encoding</span></span>|<span data-ttu-id="dd439-214">テキスト、バイナリ、MTOM、カスタム</span><span class="sxs-lookup"><span data-stu-id="dd439-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="dd439-215">はい</span><span class="sxs-lookup"><span data-stu-id="dd439-215">Yes</span></span>|  
|<span data-ttu-id="dd439-216">Transport</span><span class="sxs-lookup"><span data-stu-id="dd439-216">Transport</span></span>|<span data-ttu-id="dd439-217">TCP、名前付きパイプ、HTTP、HTTPS、MSMQ のフレーバー、カスタム</span><span class="sxs-lookup"><span data-stu-id="dd439-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="dd439-218">はい</span><span class="sxs-lookup"><span data-stu-id="dd439-218">Yes</span></span>|  
  
 <span data-ttu-id="dd439-219">さらに、独自のバインド要素を定義し、それを定義済みの層のいずれかの間に挿入できます。</span><span class="sxs-lookup"><span data-stu-id="dd439-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="dd439-220">カスタム バインドを変更するシステム提供のバインディングを使用する方法の詳細については、次を参照してください。[する方法: システム指定のバインディングをカスタマイズ](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd439-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="dd439-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd439-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="dd439-222">\<binding></span><span class="sxs-lookup"><span data-stu-id="dd439-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="dd439-223">バインディング</span><span class="sxs-lookup"><span data-stu-id="dd439-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dd439-224">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="dd439-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="dd439-225">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="dd439-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="dd439-226">customBinding 要素</span><span class="sxs-lookup"><span data-stu-id="dd439-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="dd439-227">バインディング</span><span class="sxs-lookup"><span data-stu-id="dd439-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dd439-228">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="dd439-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="dd439-229">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="dd439-229">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)

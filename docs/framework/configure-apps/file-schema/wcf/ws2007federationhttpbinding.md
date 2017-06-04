---
title: "&lt;ws2007FederationHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;ws2007FederationHttpBinding&gt;
[\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)から派生し、フェデレーション セキュリティをサポートする、セキュリティで保護された相互運用可能なバインディングです。  
  
## 構文  
  
```  
  
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
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`bypassProxyOnLocal`|ローカル アドレスでプロキシ サーバーをバイパスするかどうかを示す値。  既定値は、`false` です。|  
|`closeTimeout`|クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。  この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。  既定値は 00:01:00 です。|  
|`hostnameComparisonMode`|URI の解析に使用する HTTP ホスト名比較モードを指定します。  この属性は <xref:System.ServiceModel.HostnameComparisonMode> 型で、URI が一致したときにサービスへのアクセスにホスト名を使用するかどうかを指定します。  既定値は <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard> で、一致しているホスト名を無視します。|  
|`maxBufferPoolSize`|このバインドに使用するバッファー プールの最大サイズ。  既定は 524,288 バイト \(512 \* 1024\) です。  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] の多くの部分でバッファーが使用されます。  使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。  バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。  これで、バッファーの作成と破棄のオーバーヘッドを回避できます。|  
|`maxReceivedMessageSize`|チャネルで受信可能な最大メッセージ サイズ \(ヘッダーを含む\) が、このバインドを使用してバイト単位で設定されました。  この制限を超えるメッセージの送信者が、SOAP エラーを受信します。  メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。  既定値は 65536 です。|  
|`messageEncoding`|メッセージのエンコードに使用されるエンコーダーを定義します。  以下の値が有効です。<br /><br /> -   Text: テキスト メッセージのエンコーダーを使用します。<br />-   Mtom: Message Transmission Organization Mechanism 1.0 \(MTOM\) エンコーダーを使用します。<br /><br /> 既定値は Text です。<br /><br /> この属性は <xref:System.ServiceModel.WSMessageEncoding> 型です。|  
|`name`|バインドの構成名。  この値は、バインディングの ID として使用されるため、一意にする必要があります。  [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。  既定の構成、および名前のないバインディングと動作の詳細については、「[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。|  
|`openTimeout`|実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。  この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。  既定値は 00:01:00 です。|  
|`privactyNoticeAt`|プライバシーに関する声明の場所を示す URI。|  
|`privactyNoticeVersion`|現在のプライバシーに関する声明のバージョン。|  
|`proxyAddress`|HTTP プロキシのアドレスを指定する URI。  `useDefaultWebProxy` が `true` の場合、この設定を `null` にする必要があります。  既定値は、`null` です。|  
|`receiveTimeout`|受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。  この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。  既定値は 00:10:00 です。|  
|`sendTimeout`|送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。  この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。  既定値は 00:01:00 です。|  
|`textEncoding`|バインディングでメッセージの発行に使用される文字セット エンコーディングを設定します。  以下の値が有効です。<br /><br /> -   BigEndianUnicode: Unicode ビッグ エンディアン エンコーディング。<br />-   Unicode: 16 ビット エンコーディング。<br />-   UTF8: 8 ビット エンコーディング。<br /><br /> 既定値は UTF8 です。  この属性は <xref:System.Text.Encoding> 型です。|  
|`transactionFlow`|バインドが WS\-Transactions のフローをサポートするかどうかを指定する値。  既定値は、`false` です。|  
|`useDefaultWebProxy`|システムの自動設定 HTTP プロキシを使用するかどうかを示す値。  この属性が `true` の場合、プロキシ アドレスを `null` \(つまり、設定しない\) にする必要があります。  既定値は、`true` です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|メッセージのセキュリティ設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement> 型です。|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。  この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。|  
|[reliableSession](http://msdn.microsoft.com/ja-jp/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|チャネルのエンドポイント間に信頼できるセッションを確立するかどうかを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<bindings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。|  
  
## 解説  
 フェデレーションは、複数の企業または信頼するドメインで認証と承認用の ID を共有する機能です。  フェデレーションは、WS\-Trust プロトコルを使用して、ID 形式を、ある信頼するドメインから別の信頼するドメインにマップします。  フェデレーション HTTP バインドは、SOAP セキュリティと混合モード セキュリティをサポートしますが、トランスポート セキュリティの単独使用はサポートしません。  このバインディングで構成されたサービスは、HTTP トランスポートを使用する必要があります。  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
## 使用例  
  
```  
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
  
## 参照  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>   
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>   
 [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
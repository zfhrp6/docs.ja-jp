---
title: "&lt;customBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
caps.latest.revision: 24
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 24
---
# &lt;customBinding&gt; の &lt;security&gt;
カスタム バインディングのセキュリティ オプションを指定します。  
  
## 構文  
  
```  
  
<security   
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
      defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
      requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
      messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean"  
      securityHeaderLayout=  
              "Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean">  
   <issuedTokenParameters />  
   <localClientSettings />  
   <localServiceSettings />  
   <secureConversationBootstrap />  
</security>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|allowSerializedSigningTokenOnReply|省略可能です。  シリアル化されたトークンを応答で使用できる場合に指定するブール値。  既定値は `false` です。  二重バインドを使用する場合、この設定の既定値は `true` に設定され、行った設定はすべて無視されます。|  
|authenticationMode|省略可能です。  イニシエーターとレスポンダーの間で使用される認証モードを指定します。  すべての値については、以下を参照してください。<br /><br /> 既定値は、`sspiNegotiated` です。|  
|defaultAlgorithmSuite|省略可能です。  メッセージの暗号化とキー ラップ アルゴリズムを設定します。  アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。  これらのアルゴリズムは、Security Policy Language \(WS\-SecurityPolicy\) の仕様で指定されているアルゴリズムに対応付けられています。<br /><br /> 指定できる値を以下に示します。  既定値は `Basic256` です。<br /><br /> この属性は、既定とは異なるアルゴリズムのセットを選択する別のプラットフォームで操作するときに使用されます。  この設定を修正する場合、関連するアルゴリズムの強さと脆弱性に注意する必要があります。  この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。|  
|includeTimestamp|各メッセージにタイム スタンプが含まれるかどうかを指定するブール値です。  既定値は、`true` です。|  
|keyEntropyMode|メッセージをセキュリティで保護するキーを計算する方法を指定します。  キーは、クライアント キー マテリアルのみ、サービス キー マテリアルのみ、または両方の組み合わせに基づいて生成できます。  有効な値は、次のとおりです。<br /><br /> -   `ClientEntropy`: セッション キーは、クライアントから提供されるキー データに基づいています。<br />-   `ServerEntropy`: セッション キーは、サーバーから提供されるキー データに基づいています。<br />-   `CombinedEntropy`: セッション キーは、クライアントとサービスから提供されるキー データに基づいています。<br /><br /> 既定値は、`CombinedEntropy` です。<br /><br /> この属性は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> 型です。|  
|messageProtectionOrder|メッセージ レベルのセキュリティ アルゴリズムをメッセージに適用する順序を設定します。  以下の値が有効です。<br /><br /> -   `SignBeforeEncrypt`: 最初に署名してから暗号化します。<br />-   `SignBeforeEncryptAndEncryptSignature`: 最初に署名してから暗号化し、次に署名を暗号化します。<br />-   `EncryptBeforeSign`: 最初に暗号化してから署名します。<br /><br /> 既定値は、使用している WS\-Security のバージョンによって異なります。  WS\-Security 1.1 を使用する場合、既定値は `SignBeforeEncryptAndEncryptSignature` です。  WS\-Security 1.0 を使用する場合、既定値は `SignBeforeEncrypt` です。<br /><br /> この属性は <xref:System.ServiceModel.Security.MessageProtectionOrder> 型です。|  
|messageSecurityVersion|省略可能です。  使用される WS\-Security のバージョンを設定します。  以下の値が有効です。<br /><br /> -   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-   WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-   WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> 既定は、WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 であり、単純に `Default` として XML で表現できます。  この属性は <xref:System.ServiceModel.MessageSecurityVersion> 型です。|  
|requireDerivedKeys|キーを元の証明キーから派生できる場合に指定するブール値。  既定値は、`true` です。|  
|requireSecurityContextCancellation|省略可能です。  セキュリティ コンテキストが不要になったときにそれをキャンセルして終了する必要がある場合に指定するブール値。  既定値は、`true` です。|  
|requireSignatureConfirmation|省略可能です。  WS\-Security 署名確認を有効にするかどうかを指定するブール値です。  `true` に設定されている場合、メッセージ署名が応答側で確認されます。  カスタム バインディングが相互証明書に対して構成されているか、発行されたトークンを使用するように構成されている場合 \(WSS 1.1 バインド\)、この属性の既定値は `true` です。  それ以外の場合、既定値は `false` になります。<br /><br /> サービスが要求を完全に認識して応答していることを確認するために、署名確認を使用します。|  
|securityHeaderLayout|省略可能です。  セキュリティ ヘッダーでの要素の順序を指定します。  有効な値は、次のとおりです。<br /><br /> -   `Strict` : "使用前に宣言する" という一般的な方針に従って、項目がセキュリティ ヘッダーに追加されます。<br />-   `Lax`: WSS: SOAP メッセージ セキュリティに準じた任意の順序で、項目はセキュリティ ヘッダーに追加されます。<br />-   `LaxWithTimestampFirst`: WSS: SOAP メッセージ セキュリティに準じた任意の順序で、項目はセキュリティ ヘッダーに追加されます。ただし、セキュリティ ヘッダーの最初の要素は wsse:Timestamp 要素である必要があります。<br />-   `LaxWithTimestampLast`: WSS: SOAP メッセージ セキュリティに準じた任意の順序で、項目はセキュリティ ヘッダーに追加されます。ただし、セキュリティ ヘッダーの最後の要素は wsse:Timestamp 要素である必要があります。<br /><br /> 既定値は、`Strict` です。<br /><br /> この要素は <xref:System.ServiceModel.Channels.SecurityHeaderLayout> 型です。|  
  
## authenticationMode 属性  
  
|値|説明|  
|-------|--------|  
|String|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## defaultAlgorithm 属性  
  
|値|説明|  
|-------|--------|  
|Basic128|Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic192|Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic256|Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic256Rsa15|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|Basic192Rsa15|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|TripleDes|TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic128Rsa15|メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|TripleDesRsa15|TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|Basic128Sha256|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic192Sha256|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic256Sha256|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|TripleDesSha256|メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic128Sha256Rsa15|メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|Basic192Sha256Rsa15|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|Basic256Sha256Rsa15|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|TripleDesSha256Rsa15|メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|現在発行されているトークンを指定します。  この要素は <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement> 型です。|  
|[\<localClientSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|このバインディングのローカル クライアントのセキュリティ設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement> 型です。|  
|[\<localServiceSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|このバインディングのローカル サービスのセキュリティ設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement> 型です。|  
|[\<secureConversationBootstrap\>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## 解説  
 この要素の使い方[!INCLUDE[crabout](../../../../../includes/crabout-md.md)]、「[SecurityBindingElement 認証モード](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)」および「[方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)」を参照してください。  
  
## 使用例  
 次の例では、カスタム バインディングを使用してセキュリティを構成する方法を示します。  カスタム バインディングを使用して、セキュリティで保護されたトランスポートと共にメッセージ レベルのセキュリティを有効にする方法を示します。  これは、クライアントとサービス間でメッセージを転送する際にセキュリティで保護されたトランスポートが必要であると同時に、そのメッセージをメッセージ レベルでセキュリティ保護する必要がある場合に便利です。  この構成は、システム指定のバインディングではサポートされていません。  
  
 サービス構成では、TLS\/SSL プロトコルを使用して保護される TCP 通信、および Windows メッセージ セキュリティをサポートするカスタム バインディングが定義されます。  カスタム バインディングはサービス証明書を使用して、トランスポート レベルでサービスを認証し、クライアントとサービス間で転送中のメッセージを保護します。  これは [\<sslStreamSecurity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) バインディング要素によって実現されます。  サービスの証明書は、サービス動作を使用して構成されます。  
  
 さらに、カスタム バインディングは Windows 資格情報の種類 \(既定の資格情報の種類\) によるメッセージ セキュリティを使用します。  これは [security](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) バインディング要素によって実現されます。  Kerberos 認証機構が利用できる場合は、クライアントとサービスはどちらもメッセージ レベルのセキュリティを使用して認証されます。  Kerberos 認証機構が利用できない場合は、NTLM 認証が使用されます。  NTLM はサービスに対してクライアントを認証しますが、クライアントに対するサービスの認証は行いません。  [security](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) バインディング要素は `SecureConversation` authenticationType を使用するように構成されます。この結果、クライアントとサービスの両方でセキュリティ セッションが作成されます。  これは、サービスの双方向コントラクトを動作させるために必要です。  この例の実行の詳細については、「[カスタム バインディング セキュリティ](../../../../../docs/framework/wcf/samples/custom-binding-security.md)」を参照してください。  
  
```  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- use following base address -->  
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                    binding="customBinding"  
                    bindingConfiguration="Binding1"   
                    contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <sslStreamSecurity requireClientCertificate="false"/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.SecurityElement>   
 <xref:System.ServiceModel.Channels.SecurityBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [カスタム バインディング セキュリティ](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
---
title: "&lt;netTcpBinding&gt; の &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# &lt;netTcpBinding&gt; の &lt;transport&gt;
[\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) を使用して構成されたエンドポイントに対する、メッセージ レベルのセキュリティ要件の種類を定義します。  
  
## 構文  
  
```  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"  
             sslProtocols="Ssl3|Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|clientCredentialType|省略可能です。  トランスポート セキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。<br /><br /> -   既定値は `Windows` です。<br />-   この属性は <xref:System.ServiceModel.TcpClientCredentialType> 型です。|  
|protectionLevel|省略可能です。  TCP トランスポートのレベルでセキュリティを定義します。  メッセージに署名すると、転送中のメッセージが第三者によって改ざんされるリスクを軽減します。  暗号化により、転送中にデータレベルのプライバシーが提供されます。<br /><br /> 既定値は `EncryptAndSign` です。|  
|sslProtocols|どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。  既定値は Ssl3&#124;Tls&#124;Tls11&#124;Tls12 です。|  
|policyEnforcement|この列挙体は、<xref:System.Security.Authentication.ExtendedProtectionPolicy> を適用するタイミングを指定します。<br /><br /> 1.  Never – ポリシーが適用されることはありません \(拡張保護は無効になります\)。<br />2.  WhenSupported – ポリシーが適用されるのは、クライアントが拡張保護をサポートしている場合のみです。<br />3.  Always – ポリシーは常に適用されます。  拡張保護をサポートしていないクライアントは認証に失敗します。|  
  
## clientCredentialType 属性  
  
|値|説明|  
|-------|--------|  
|なし|クライアントは匿名です。  これには、サービスの証明書が必要です。|  
|Windows|SP ネゴシエーション \(Kerberos ネゴシエーション\) を使用して、クライアントの Windows 認証を指定します。|  
|証明書|クライアントは、証明書を使用して認証されます。  これは SSL ネゴシエーションを使用し、サービスの証明書が必要です。|  
  
## protectionLevel 属性  
  
|値|説明|  
|-------|--------|  
|なし|保護されません。|  
|Sign|メッセージは署名されます。|  
|EncryptAndSign|-   メッセージは暗号化および署名されます。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|[\<netTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) のセキュリティ機能を指定します。|  
  
## 解説  
 トランスポート セキュリティは、SOAP メッセージの整合性と機密性の保護、および相互認証に使用します。  このセキュリティ モードがバインディング上で選択された場合、チャネル スタックはセキュリティ トランスポートを使用して構成され、SOAP メッセージは Windows \(ネゴシエート\) や TCP 上の SSL などのトランスポート セキュリティを使用して保護されます。  
  
## 参照  
 <xref:System.ServiceModel.TcpTransportSecurity>   
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.NetTcpTransportSecurityElement>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
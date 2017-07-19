---
title: "&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# &lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素
[\<ws2007FederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) 要素のセキュリティ設定を定義します。  
  
## 構文  
  
```  
  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`mode`|省略可能です。  適用するセキュリティの種類を指定します。  既定値は `Message` です。  この属性は <xref:System.ServiceModel.WSFederationHttpSecurityMode> 型です。|  
  
## mode 属性  
  
|値|説明|  
|-------|--------|  
|なし|SOAP メッセージは、転送中はセキュリティで保護されません。|  
|メッセージ|SOAP メッセージ セキュリティを使用して、整合性、機密性、サーバー認証、およびクライアント認証を提供します。  既定では、本文は暗号化および署名されます。  サービスは、証明書を使用して構成する必要があります。  クライアント認証は、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。|  
|TransportWithMessageCredential|整合性、機密性、およびサーバー認証は、HTTPS によって提供されます。  サービスは、証明書を使用して構成する必要があります。  クライアント認証は、SOAP メッセージ セキュリティによって提供され、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|メッセージ レベル セキュリティの設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|[\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)のすべてのバインディング機能を定義します。|  
  
## 参照  
 <xref:System.ServiceModel.WSFederationHttpSecurity>   
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>   
 [方法 : WSFederationHttpBinding を作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [資格情報の種類の選択](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
---
title: "&lt;netHttpBinding&gt; の &lt;security | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;netHttpBinding&gt; の &lt;security
[\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)のセキュリティ機能を定義します。  
  
## 構文  
  
```  
  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|省略可能です。  使用されるセキュリティの種類を指定します。  既定値は、`None` です。  この属性は <xref:System.ServiceModel.NetHttpSecurityMode> 型です。|  
  
## mode 属性  
  
|値|説明|  
|-------|--------|  
|なし|-   メッセージは、転送中はセキュリティで保護されません。|  
|Transport|セキュリティは、HTTPS トランスポートを使用して提供されます。  SOAP メッセージは、HTTPS を使用したセキュリティで保護されます。  サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。  クライアントは、提供される ClientCredentialType を使用して認証されます。|  
|メッセージ|セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。  既定では、本文は暗号化および署名されます。  このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。  このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。|  
|TransportWithMessageCredential|整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。  クライアント認証は、SOAP メッセージ セキュリティで提供されます。  このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。|  
|TransportCredentialOnly|このモードは、メッセージの整合性と機密性を提供しません。  http ベースのクライアント認証を提供します。  このモードを使用するときは、十分に注意する必要があります。  トランスポート セキュリティが他の方法 \(IPSec など\) で提供され、クライアント認証だけが [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インフラストラクチャで提供されている環境で使用する必要があります。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|基本 HTTP サービスのトランスポート セキュリティ設定を定義します。  この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|基本 HTTP サービスのメッセージ セキュリティ設定を定義します。  この要素は、<xref:System.ServiceModel.NetHttpMessageSecurity> に対応しています。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|バインド|[\<basicHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)のバインディング要素です。|  
  
## 解説  
 既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。  この要素を使用すると、`netHttpBinding` 要素に追加のセキュリティ設定を構成できます。  
  
## 参照  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetHttpSecurityElement>   
 <xref:System.ServiceModel.NetHttpSecurity>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [資格情報の種類の選択](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
---
title: "&lt;netMsmqBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# &lt;netMsmqBinding&gt; の &lt;security&gt;
MSMQ バインディングのセキュリティ設定を定義します。  トランスポートまたは SOAP セキュリティが有効であるかどうか、および有効である場合は、どの認証モードと保護レベルを使用するかを指定します。  
  
## 構文  
  
```  
  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|整合性、機密性、および認証を制御するセキュリティの種類を指定します。  以下の値が有効です。<br /><br /> -   None: セキュリティは無効になります。<br />-   Transport: 保護と認証はトランスポートが提供します。  これは、2 つのキュー マネージャー間のメッセージ セキュリティに適用されます。  アプリケーションとキュー マネージャーとの間にセキュリティは提供されません。  既存の Msmq アプリケーションは、この種類のセキュリティ モードと機能的に等価です。<br />-   Message: エンドツーエンドのアプリケーション セキュリティを指定します。  トランスポート層で提供されるセキュリティありません。  これは、他の標準バインディングによって提供されたセキュリティと同様です。<br />-   Both: トランスポートと SOAP メッセージング レイヤーの両方でセキュリティを提供します。  同じ資格情報が、両方のレベルで要求されます。<br /><br /> 既定値は、Transport です。  この属性は <xref:System.ServiceModel.NetMsmqSecurityMode> 型です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|SOAP メッセージのセキュリティ設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> 型です。|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|MSMQ トランスポートのセキュリティ設定を定義します。  この要素は <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|バインド|[\<netMsmqBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) のバインディング要素です。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>   
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)   
 [WCF のキュー](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
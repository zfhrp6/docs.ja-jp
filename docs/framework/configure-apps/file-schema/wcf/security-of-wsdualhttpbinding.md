---
title: "&lt;wsDualHttpBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# &lt;wsDualHttpBinding&gt; の &lt;security&gt;
[\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)のセキュリティ機能を定義します。  
  
## 構文  
  
```  
  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|-   省略可能です。  適用するセキュリティの種類を指定します。  既定値は `Message` です。  この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。|  
  
## Mode 属性  
  
|値|説明|  
|-------|--------|  
|なし|セキュリティを無効にします。|  
|メッセージ|セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|メッセージ レベル セキュリティの設定を定義します。  この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|[\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)のすべてのバインディング機能を定義します。|  
  
## 解説  
 二重バインディングでは、クライアントの IP アドレスをサービスに公開します。  クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。  
  
## 参照  
 <xref:System.ServiceModel.WSDualHttpSecurity>   
 <xref:System.ServiceModel.WsDualHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WsDualHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.Configuration.WsDualHttpSecurityElement>   
 <xref:System.ServiceModel.BasicHttpSecurity>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
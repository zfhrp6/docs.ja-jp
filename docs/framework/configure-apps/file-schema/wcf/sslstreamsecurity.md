---
title: "&lt;sslStreamSecurity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# &lt;sslStreamSecurity&gt;
SSL ストリームを使用してチャネル セキュリティをサポートするカスタム バインド要素を表します。  
  
## 構文  
  
```  
  
<sslStreamSecurity requireClientCertificate="Boolean"  
      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|requireClientCertificate|クライアント証明書がこのバインディングに必要かどうかを指定するブール値。  既定値は、`false` です。|  
|sslProtocols|どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。  既定値は Ssl3&#124;Tls&#124;Tls11&#124;Tls12 です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
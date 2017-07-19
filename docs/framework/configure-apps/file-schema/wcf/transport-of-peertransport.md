---
title: "&lt;peerTransport&gt; の &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;peerTransport&gt; の &lt;transport&gt;
このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。  
  
## 構文  
  
```  
  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|credentialType|省略可能です。  ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。  この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。|  
  
## credentialType 属性  
  
|値|説明|  
|-------|--------|  
|証明書|ピア チャネル トランスポートの認証には X 509 証明書が必要です。|  
|\[Password\]|ピア チャネル トランスポートの認証には正しいパスワードが必要です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|ピア トランスポートのセキュリティ設定を定義します。|  
  
## 解説  
 この要素は、[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) の mode 属性が `Transport` または `TransportWithMessageCredential` に設定されている場合にのみ設定されます。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>   
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>   
 <xref:System.ServiceModel.PeerTransportSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [トランスポート セキュリティ](../../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
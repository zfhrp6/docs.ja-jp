---
title: "&lt;peerTransport&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;peerTransport&gt; の &lt;security&gt;
ピア チャネルに関連付けられたセキュリティ設定を格納します。使用される認証の種類とメッセージ トランスポートで使用されるセキュリティを含みます。  
  
## 構文  
  
```  
  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`mode`|適用するセキュリティの種類を指定します。  既定値は Message です。  この属性は <xref:System.ServiceModel.SecurityMode> 型です。|  
  
## mode 属性  
  
|値|説明|  
|-------|--------|  
|`None`|セキュリティを無効にします。|  
|`Transport`|セキュリティは、HTTPS を使用して確保されます。|  
|`Message`|SOAP セキュリティにより、認証、整合性、および機密性が実現します。|  
|`TransportWithMessageCredential`|HTTPS により、認証および機密性が実現します。  SOAP メッセージには、豊富な資格情報の種類が用意されています。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|カスタム バインディングのピア トランスポートを定義します。  この要素には、サービスと対話するときに使用される資格情報を指定する `clientCredentialType` 属性があります。  この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。<br /><br /> この要素は <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<peerTransport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|カスタム バインディングのピア トランスポートを定義します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>   
 <xref:System.ServiceModel.PeerSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [トランスポート セキュリティ](../../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
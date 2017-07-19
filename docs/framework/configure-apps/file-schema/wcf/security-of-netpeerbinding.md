---
title: "&lt;netPeerBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# &lt;netPeerBinding&gt; の &lt;security&gt;
[\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md) のセキュリティ設定を定義します。使用される認証の種類とメッセージ トランスポートで使用されるセキュリティを含みます。  
  
## 構文  
  
```  
  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|省略可能です。  このバインディングで構成されたピアが使用するセキュリティの種類を指定します。  既定値は `Message` です。  この属性は <xref:System.ServiceModel.SecurityMode> 型です。|  
  
## mode 属性  
  
|値|説明|  
|-------|--------|  
|メッセージ|SOAP セキュリティにより、認証、整合性、および機密性が実現します。|  
|なし|セキュリティを無効にします。|  
|Transport|セキュリティは、HTTPS を使用して確保されます。|  
|TransportWithMessageCredential|HTTPS により、認証および機密性が実現します。  SOAP メッセージには、豊富な資格情報の種類が用意されています。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|このバインディングで構成されたピアが送信するセキュリティで保護されたメッセージのトランスポートの型を定義します。  この要素は <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<binding\>](../../../../../docs/framework/misc/binding.md)|[\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)のすべてのバインディング機能を定義します。|  
  
## 解説  
 セキュリティは、メッセージ固有にすることも、トランスポート固有にすることもできます。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>   
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>   
 <xref:System.ServiceModel.PeerSecuritySettings>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [資格情報の種類の選択](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
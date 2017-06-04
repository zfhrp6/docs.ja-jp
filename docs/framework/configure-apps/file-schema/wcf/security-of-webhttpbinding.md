---
title: "&lt;webHttpBinding&gt; の &lt;security&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# &lt;webHttpBinding&gt; の &lt;security&gt;
[\<wsHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)で構成されるエンドポイントのセキュリティ要件を指定します。  
  
## 構文  
  
```  
  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|モード|トランスポート レベルのセキュリティをエンドポイントで使用するか、セキュリティを使用しないかを指定します。  既定値は、`None` です。  この属性は <xref:System.ServiceModel.WebHttpSecurityMode> 型です。|  
  
## Mode 属性  
  
|値|説明|  
|-------|--------|  
|なし|セキュリティを無効にします。|  
|Transport|セキュリティは、HTTPS を使用して確保されます。  サービスは、SSL 証明書を使用して構成する必要があります。  メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。  クライアント認証は、[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md) の `ClientCredentialType` 属性を使用して制御されます。|  
|TransportCredentialOnly|このモードは、メッセージの整合性と機密性を提供しません。  HTTP ベースのクライアント認証を提供します。  このモードを使用するときは、十分に注意する必要があります。  トランスポート セキュリティが他の方法 \(IPSec など\) で提供され、クライアント認証だけが [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インフラストラクチャで提供されている環境で使用する必要があります。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|トランスポートのセキュリティ設定を定義します。  この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<webHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|SOAP メッセージに代わって HTTP 要求に応答する [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web サービスのエンドポイントを構成するために使用するバインド要素。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>   
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>   
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>   
 <xref:System.ServiceModel.WebHttpSecurity>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [資格情報の種類の選択](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)   
 [WCF Web HTTP プログラミング モデル](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
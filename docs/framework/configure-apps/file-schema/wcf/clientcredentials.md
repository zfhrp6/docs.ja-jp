---
title: "&lt;clientCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;clientCredentials&gt;
サービスに対するクライアントの認証に使用される資格情報を指定します。  
  
## 構文  
  
```  
  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`supportInteractive`|実行時にクライアントの資格情報を選択する際に、対話型ユーザーを含めるかどうかを指定するブール値。  既定値は `true` です。|  
|`type`|この設定要素の種類を指定する文字列です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|サービスに対するクライアントの認証に使用される証明書を指定します。  この要素は <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> 型です。|  
|[\<httpDigest\>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|サービスに対するクライアントの認証に使用されるダイジェストを指定します。  この要素は <xref:System.ServiceModel.Configuration.HttpDigestClientElement> 型です。|  
|[\<issuedToken\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|セキュリティ トークン サービス \(STS\) に対するクライアントの認証に使用されるカスタム トークンの種類を指定します。  この要素は <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> 型です。|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|現在のピア資格情報を指定します。  この要素は <xref:System.ServiceModel.Configuration.PeerCredentialElement> 型です。|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|クライアントに対するサービスの認証に使用される証明書を指定し、証明書オプションを設定するための構造を提供します。  この証明書は、クライアントに対するサービスの帯域外に提供される必要があります。  この要素は <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> 型です。|  
|[\<windows\>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Windows 資格情報を指定します。  既定値は、現在のスレッドの資格情報です。  この要素は <xref:System.ServiceModel.Configuration.WindowsClientElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。|  
  
## 解説  
 クライアント資格情報は、相互認証が必要な場合にサービスに対するクライアントの認証に使用されます。  また、この構成セクションを使用して、クライアントがサービスの証明書によってサービスへのメッセージをセキュリティで保護する必要がある場合に使用するサービス証明書を指定することもできます。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)
---
title: "&lt;serviceCredentials&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;serviceCredentials&gt;
サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。  
  
## 構文  
  
```  
  
<serviceCredentials type="String">  
   <clientCertificate>  
   </clientCertificate>  
   <issuedTokenAuthentication>  
   </issuedTokenAuthentication>  
   <peer>  
   </peer>  
   <secureConversationAuthentication>  
   </secureConversationAuthentication>  
   <serviceCertificate>  
   </serviceCertificate>  
   <userNameAuthentication>  
   </userNameAuthentication>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</serviceCredentials>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`type`|この設定要素の種類を指定する文字列です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<clientCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|クライアント証明書を帯域外で使用できるときに使用される証明書を指定します。  この要素は、クライアント証明書の検証設定も指定します。  この要素は <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> 型です。|  
|[\<issuedTokenAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|このサービス用に現在発行されているトークンを指定します。  この要素は <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> 型です。|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|ピア ノードの現在の資格情報を指定します。  この要素は <xref:System.ServiceModel.Configuration.PeerCredentialElement> 型です。|  
|[\<secureConversationAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|セキュリティで保護されたメッセージ交換の現在の資格情報を指定します。  この要素は <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> 型です。|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|サービスが自身を識別するために使用する証明書を指定します。  この要素は <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> 型です。|  
|[\<userNameAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|ユーザー名とパスワードの検証の設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.UserNameServiceElement> 型です。|  
|[\<windowsAuthentication\>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|Windows 資格情報の検証の設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.WindowsServiceElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>   
 <xref:System.ServiceModel.Description.ServiceCredentials>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
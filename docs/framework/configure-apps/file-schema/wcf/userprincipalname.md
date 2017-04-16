---
title: "&lt;userPrincipalName&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;userPrincipalName&gt;
クライアントで認証するサービスのユーザー プリンシパル名 \(UPN\) を指定します。  
  
 UPN の設定の詳細については、「[サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
## 構文  
  
```  
  
<userPrincipalName value = "String" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|value|ユーザー アカウント名 \(ユーザー ログイン名と呼ばれることもある\) と、ユーザー アカウントの検索範囲のドメインを識別するドメイン名です。  これは、Windows ドメインにログオンするための標準的使用方法です。  形式は、someone@example.com です \(電子メールアドレスの場合\)。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<identity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|クライアントで認証するサービスの ID を指定します。|  
  
## 解説  
 この ID を持つエンドポイントに接続する、セキュリティで保護された [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアントは、エンドポイントの SSPI 認証を実行するときに UPN を使用します。  
  
## 使用例  
 次の構成コードは、クライアントで認証するサービスの UPN を指定します。  
  
```  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 <xref:System.ServiceModel.UpnEndpointIdentity>   
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [\<identity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
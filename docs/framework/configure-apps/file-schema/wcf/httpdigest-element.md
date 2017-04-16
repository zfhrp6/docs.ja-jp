---
title: "&lt;httpDigest&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;httpDigest&gt; 要素
サービスに対するクライアントの認証時に使用されるダイジェスト型の資格情報を指定します。  
  
## 構文  
  
```  
  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`impersonationLevel`|クライアントがサーバーと通信する偽装設定を設定します。  クライアントが選択する偽装モードは、サーバーでは適用されません。  以下の値が有効です。<br /><br /> -   Identification: サーバーはクライアントの ID および権限を取得できますが、クライアントを偽装することはできません。<br />-   Impersonation: サーバーは、ローカル システム上にあるクライアントのセキュリティ コンテキストを偽装できます。<br />-   Delegation: サーバーは、リモート システム上にあるクライアントのセキュリティ コンテキストを偽装できます。<br />-   Anonymous: サーバーは、クライアントを偽装したり、識別したりすることができません。<br />-   None: 偽装レベルが割り当てられていません。<br /><br /> 既定値は Identification です。  この属性は <xref:System.Security.Principal.TokenImpersonationLevel> 型です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## 解説  
 ダイジェストは、アルゴリズムと入力セットを使用して決定されるハッシュです。  認証する側と認証される側はアルゴリズムに同意し、入力として使用されるデータを交換します。  クライアントはハッシュを計算して、サービスに送信できます。  また、サービスもハッシュを計算して、値を比較します。  一致すると、クライアントが検証されます。  
  
 この機能は、Windows の Active Directory およびインターネット インフォメーション サービス \(IIS\) と共に有効にする必要があります。  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [IIS 6.0 のダイジェスト認証](http://go.microsoft.com/fwlink/?LinkId=88443)。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>   
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>   
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)   
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
---
title: "&lt;clientCredentials&gt; 要素の &lt;windows&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;clientCredentials&gt; 要素の &lt;windows&gt;
クライアントを表すために使用される Windows 資格情報の設定を指定します。  
  
## 構文  
  
```  
  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`allowedImpersonationLevel`|クライアントがサーバーと通信する偽装設定を設定します。  クライアントが選択する偽装モードは、サーバーでは適用されません。  以下の値が有効です。<br /><br /> -   Identification: サーバーはクライアントの ID および権限を取得できますが、クライアントを偽装することはできません。<br />-   Impersonation: サーバーは、ローカル システム上にあるクライアントのセキュリティ コンテキストを偽装できます。<br />-   Delegation: サーバーは、リモート システム上にあるクライアントのセキュリティ コンテキストを偽装できます。<br />-   Anonymous: サーバーは、クライアントを偽装したり、識別したりすることができません。<br />-   None: 偽装レベルが割り当てられていません。<br /><br /> 既定値は Identification です。  この属性は <xref:System.Security.Principal.TokenImpersonationLevel> 型です。|  
|`allowNtlm`|このプロパティを `true` に設定すると、Kerberos 認証を利用できない場合、NTLM 認証にダウングレードできます。<br /><br /> このプロパティを `false` に設定すると、NTLM が使用されている場合、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] はベスト エフォートで例外をスローします。  ただし、このプロパティを `false` に設定しても、ネットワーク経由で NTLM 資格情報が送信されなくなるとは限りません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>   
 <xref:System.ServiceModel.Security.WindowsClientCredential>   
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)   
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
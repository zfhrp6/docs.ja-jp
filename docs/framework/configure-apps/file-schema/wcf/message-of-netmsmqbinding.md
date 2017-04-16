---
title: "&lt;netMsmqBinding&gt; の &lt;message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;netMsmqBinding&gt; の &lt;message&gt;
この `netMsmqBinding` バインディングでの SOAP メッセージ セキュリティ設定を定義します。  
  
## 構文  
  
```  
  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|algorithmSuite|MSMQ トランスポートを介して送信されるメッセージにメッセージ ベースのセキュリティを実現するために使用されるメッセージの暗号化およびキー ラップ アルゴリズムを設定します。<br /><br /> 既定値は `Aes256` です。  この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。|  
|clientCredentialType|MSMQ トランスポートで送信されるメッセージに対してクライアント認証を実行するときに使用される資格情報の種類を指定します。  以下の値が有効です。<br /><br /> -   None: サービスが匿名クライアントと対話できるようになります。  サービスとクライアントはいずれも資格情報を要求しません。<br />-   Windows : Windows 資格情報の認証済みコンテキストの制御下での SOAP 交換を可能にします。  これは、常に Kerberos ベースの認証を実行します。<br />-   UserName: UserName 資格情報を使用してクライアントを認証するよう、サービスが要求できるようにします。  この場合の資格情報は、`clientCredentials` 動作を使用して指定する必要があります。 **Caution:**  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は、パスワード ダイジェストの送信、またはパスワードを使用したキーの派生、およびメッセージ セキュリティでのそのようなキーの使用をサポートしません。  したがって、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、UserName 資格情報を使用する場合に交換が強制的に保護されるようにします。  このモードは、サービス証明書が、`clientCredential` 動作および `serviceCertificate` を使用してクライアント側で指定されることを要求します。 <br /><br /> -   Certificate: 証明書を使用してクライアントを認証するようサービスが要求できるようにします。  この場合のクライアント資格情報は、`clientCredentials` 動作を使用して指定する必要があります。  この場合のサービス資格情報は、`serviceCertificate` を指定して `clientCredentials` 動作を使用することで、指定する必要があります。<br />-   CardSpace: サービスは、CardSpace を使用してクライアントを認証するよう要求します。  `serviceCertiifcate` は、`clientCredential` 動作で提供される必要があります。<br /><br /> 既定値は `Windows` です。  この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|バインディングのセキュリティ設定を定義します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>   
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>   
 <xref:System.ServiceModel.MessageSecurityOverMsmq>   
 [WCF のキュー](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
---
title: "&lt;netMsmqBinding&gt; の &lt;transport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;netMsmqBinding&gt; の &lt;transport&gt;
トランスポートのセキュリティ設定を定義します。  
  
## 構文  
  
```  
  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|msmqAuthenticationMode|MSMQ トランスポートによるメッセージの認証方法を指定します。  以下の値が有効です。<br /><br /> -   None: 認証は行われません。<br />-   WindowsDomain: 認証機構により Active Directory が使用され、メッセージに関連付けられたセキュリティ識別子の X.509 証明書が取得されます。  次に、これを使用してキューの ACL がチェックされ、ユーザーがキューへの書き込み権限を持っていることが確認されます。<br />-   Certificate: チャネルは、証明書ストアから証明書を取得します。<br /><br /> 既定値は、`WindowsDomain` です。<br /><br /> この属性が `None` に設定されている場合、`msmqProtectionLevel` 属性も `None` に設定する必要があります。  この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|msmqEncryptionAlgorithm|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。  以下の値が有効です。<br /><br /> -   RC4Stream<br />-   AES<br />-   既定値は `RC4Stream` です。  この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|msmqProtectionLevel|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。  暗号化を行うとメッセージの整合性が確保されますが、署名および暗号化を使用するとメッセージの整合性と否認防止の両方が確保されます。  つまり、メッセージは本当にその送信者から送信されていることになり、記載されている送信者が実際の送信者になります。  以下の値が有効です。<br /><br /> -   None: 保護されません。<br />-   Sign: メッセージは署名されます。<br />-   EncryptAndSign: メッセージは暗号化および署名されます。<br />-   既定値は、`Sign` です。|  
|msmqSecureHashAlgorithm|メッセージ ダイジェストの計算に使用されるハッシュ アルゴリズムを指定します。  以下の値が有効です。<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> 既定値は、`SHA1` です。  この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|キューに置かれているトランスポートのセキュリティ設定を定義します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>   
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>   
 <xref:System.ServiceModel.MsmqTransportSecurity>   
 [WCF のキュー](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
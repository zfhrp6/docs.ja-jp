---
title: '&lt;netMsmqBinding&gt; の &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e947667c414079f24398b401456efd56bf9922c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; の &lt;message&gt;
この `netMsmqBinding` バインディングでの SOAP メッセージ セキュリティ設定を定義します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<netMsmqBinding>  
\<binding>  
\<セキュリティ >  
\<message>  
  
## <a name="syntax"></a>構文  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|algorithmSuite|MSMQ トランスポートを介して送信されるメッセージにメッセージ ベースのセキュリティを実現するために使用されるメッセージの暗号化およびキー ラップ アルゴリズムを設定します。<br /><br /> 既定値は `Aes256` です。 この属性は <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。|  
|clientCredentialType|MSMQ トランスポートで送信されるメッセージに対してクライアント認証を実行するときに使用される資格情報の種類を指定します。 以下の値が有効です。<br /><br /> -なし: これにより、匿名クライアントとの対話をサービスします。 サービスとクライアントはいずれも資格情報を要求しません。<br />Windows 資格情報の認証されたコンテキスト下にある SOAP 交換これにより、Windows: です。 これは、常に Kerberos ベースの認証を実行します。<br />-ユーザー名。 これにより、サービスを必要とする UserName 資格情報を使用してクライアントを認証します。 ここでは資格情報を使用して指定する必要があります、`clientCredentials`動作**注意:** Windows Communication Foundation (WCF) が、パスワードを送信するには、ダイジェスト認証または派生キーのようなキーとパスワードを使用してをサポートしていませんメッセージ セキュリティ。 そのため、WCF は、UserName 資格情報を使用する場合に、交換が保護を適用します。 このモードは、サービス証明書が、`clientCredential` 動作および `serviceCertificate` を使用してクライアント側で指定されることを要求します。 <br /><br /> 証明書: これにより、サービスを必要とする証明書を使用してクライアントを認証します。 この場合のクライアント資格情報は、`clientCredentials` 動作を使用して指定する必要があります。 この場合のサービス資格情報は、`clientCredentials` を指定して `serviceCertificate` 動作を使用することで、指定する必要があります。<br />-CardSpace: これにより、サービスを必要とする、CardSpace を使用してクライアントを認証します。 `serviceCertiifcate` は、`clientCredential` 動作で提供される必要があります。<br /><br /> 既定値は `Windows` です。 この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|バインディングのセキュリティ設定を定義します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [WCF のキュー](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)

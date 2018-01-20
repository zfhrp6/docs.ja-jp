---
title: "&lt;netMsmqBinding&gt; の &lt;message&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a7fdb8c6df84a76450aabaa983275f563d342fa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; の &lt;message&gt;
この `netMsmqBinding` バインディングでの SOAP メッセージ セキュリティ設定を定義します。  
  
 \<system.ServiceModel>  
\<bindings>  
\<netMsmqBinding>  
\<binding>  
\<security>  
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
|clientCredentialType|MSMQ トランスポートで送信されるメッセージに対してクライアント認証を実行するときに使用される資格情報の種類を指定します。 以下の値が有効です。<br /><br /> -なし: これにより、匿名クライアントとの対話をサービスします。 サービスとクライアントはいずれも資格情報を要求しません。<br />Windows 資格情報の認証されたコンテキスト下にある SOAP 交換これにより、Windows: です。 これは、常に Kerberos ベースの認証を実行します。<br />-ユーザー名。 これにより、サービスを必要とする UserName 資格情報を使用してクライアントを認証します。 ここでは資格情報を使用して指定する必要があります、`clientCredentials`動作**注意:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]はパスワードを送信するには、ダイジェスト認証または派生キーのパスワードを使用して、メッセージ セキュリティのようなキーの使用をサポートしていません。 したがって、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、UserName 資格情報を使用する場合に交換が強制的に保護されるようにします。 このモードは、サービス証明書が、`clientCredential` 動作および `serviceCertificate` を使用してクライアント側で指定されることを要求します。 <br /><br /> 証明書: これにより、サービスを必要とする証明書を使用してクライアントを認証します。 この場合のクライアント資格情報は、`clientCredentials` 動作を使用して指定する必要があります。 この場合のサービス資格情報は、`clientCredentials` を指定して `serviceCertificate` 動作を使用することで、指定する必要があります。<br />-CardSpace: これにより、サービスを必要とする、CardSpace を使用してクライアントを認証します。 `serviceCertiifcate` は、`clientCredential` 動作で提供される必要があります。<br /><br /> 既定値は `Windows` です。 この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|バインディングのセキュリティ設定を定義します。|  
  
## <a name="see-also"></a>参照  
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

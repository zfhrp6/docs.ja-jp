---
title: "&lt;wsDualHttpBinding&gt; の &lt;message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;wsDualHttpBinding&gt; の &lt;message&gt;
[\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)のメッセージ レベルのセキュリティを定義します。  
  
## 構文  
  
```  
  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## 型  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|algorithmSuite|省略可能です。  メッセージの暗号化とキー ラップ アルゴリズムを設定します。  アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。  これらのアルゴリズムは、Security Policy Language \(WS\-SecurityPolicy\) の仕様で指定されているアルゴリズムに対応付けられています。<br /><br /> 有効値については、以下を参照してください。  既定値は `Basic256` です。|  
|clientCredentialType|省略可能です。  セキュリティ モード `Message` を使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。  有効値については、以下を参照してください。  既定値は、`Windows` です。<br /><br /> この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。|  
|negotiateServiceCredential|省略可能です。  サービス資格情報がクライアントの帯域外で提供されるか、ネゴシエーションのプロセスによってサービスからクライアントに取得されるかを指定するブール値。  そのようなネゴシエーションは、通常のメッセージ交換の準備です。<br /><br /> `clientCredentialType` 属性が None、Username、または Certificate の場合、この属性を `false` に設定すると、クライアントの帯域外でサービス証明書が使用可能になり、クライアントは [\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)のサービス動作でサービス証明書 \([\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) を使用\) を指定する必要があります。  このモードは、WS\-Trust および WS\-SecureConversation が実装された SOAP スタックと同時使用できます。<br /><br /> `ClientCredentialType` 属性が `Windows` に設定されている場合、この属性を `false` に設定すると Kerberos ベースの認証が指定されます。  これは、クライアントおよびサービスが同じ Kerberos ドメインの一部でなければならないことを意味します。  このモードは、Kerberos トークン プロファイル \(OASIS WSS TC で定義\) に加えて WS\-Trust および WS\-SecureConversation が実装された SOAP スタックと同時使用できます。  この属性が `true` の場合、SOAP メッセージを介して SPNego 交換をトンネル化する .NET SOAP ネゴシエーションが行われます。<br /><br /> 既定値は、`true` です。|  
  
## algorithmSuite 属性  
  
|値|説明|  
|-------|--------|  
|Basic128|Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic192|Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic256|Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic256Rsa15|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|Basic192Rsa15|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|TripleDes|TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic128Rsa15|メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|TripleDesRsa15|TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|Basic128Sha256|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic192Sha256|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic256Sha256|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|TripleDesSha256|メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa\-oaep\-mgf1p を使用します。|  
|Basic128Sha256Rsa15|メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|Basic192Sha256Rsa15|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|Basic256Sha256Rsa15|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|TripleDesSha256Rsa15|メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
  
## clientCredentialType 属性  
  
|値|説明|  
|-------|--------|  
|なし|サービスが匿名クライアントと対話できるようになります。  サービス側では、サービスがクライアントの資格情報を必要としないことを示しています。  クライアント側では、クライアントがクライアントの資格情報を提示しないことを示しています。|  
|Windows|SOAP 交換を、Windows 資格情報の認証されたコンテキストで行うことが可能になります。  `negotiateServiceCredential` 属性が `true` に設定されている場合、SSPI ネゴシエーションと Kerberos \(同時使用可能な標準\) のいずれかが実行されます。|  
|UserName|サービスが、UserName 資格情報を使用したクライアントの認証を要求できるようにします。  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、パスワード ダイジェストの送信、またはパスワードを使用したキーの派生、およびメッセージ セキュリティでのそのようなキーの使用をサポートしません。  そのため、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では UserName 資格情報を使用する場合は、トランスポートが強制的にセキュリティで保護されます。  この資格情報モードは、`negotiateServiceCredential` 属性に基づいて、同時実行可能な交換か、同時実行できないネゴシエーションのいずれかになります。|  
|証明書|証明書を使用したクライアントの認証を、サービスで要求することが可能になります。  メッセージのセキュリティ モードが使用されており、`negotiateServiceCredential` 属性が `false` に設定されている場合、クライアントをサービス証明書で準備する必要があります。|  
|IssuedToken|カスタム トークン \(通常はセキュリティ トークン サービスにより発行される\) を指定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|[\<wsDualHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)のセキュリティ機能を定義します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>   
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>   
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>   
 <xref:System.ServiceModel.MessageSecurityOverHttp>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<binding\>](../../../../../docs/framework/misc/binding.md)
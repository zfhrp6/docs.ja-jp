---
title: "&lt;messageSenderAuthentication&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;messageSenderAuthentication&gt; 要素
ピアツーピア メッセージ送信者の認証オプションを指定します。  
  
 ピア ツー ピア プログラミングの詳細については、「[ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)」を参照してください。  
  
## 構文  
  
```  
  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|customCertificateValidatorType|カスタム型の検証に使用される型およびアセンブリです。  `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。|  
|certifcateValidationMode|資格情報の検証に使用される 3 つのモードのいずれかを指定します。  `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。|  
|revocationMode|証明書失効リスト \(CRL\) のチェックに使用されるモードのいずれかです。|  
|trustedStoreLocation|2 つのシステム格納場所 \(`LocalMachine` または `CurrentUser`\) のいずれかです。  この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。  指定された格納場所の **\[信頼されたユーザー\]** ストアに対して検証が実行されます。|  
  
## customCertificateValidatorType 属性  
  
|値|説明|  
|-------|--------|  
|String|省略可能です。  タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。  少なくとも、名前空間とタイプ名が必要です。  省略可能な情報は、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンです。|  
  
## certificateValidationMode 属性  
  
|値|説明|  
|-------|--------|  
|列挙型|省略可能です。  `None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom` のいずれかの値にします。  既定値は、`ChainTrust` です。  既定値は、`ChainTrust` です。<br /><br /> 詳細については、「[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。|  
  
## revocationMode 属性  
  
|値|説明|  
|-------|--------|  
|列挙型|`NoCheck`、`Online`、`Offline` のいずれかの値にします。  既定値は、`Online` です。<br /><br /> 詳細については、「[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。|  
  
## trustedStoreLocation 属性  
  
|値|説明|  
|-------|--------|  
|列挙型|`LocalMachine` または `CurrentUser` のいずれかの値にします。  既定値は、`CurrentUser` です。  クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。  クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。  既定値は、`CurrentUser` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|ピア サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## 解説  
 メッセージ認証を選択した場合は、この要素を構成する必要があります。  出力チャネルでは、各メッセージは、[\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md) が提供する認証を使用して署名されます。  すべてのメッセージは、アプリケーションに配信される前に、この要素の `customCertificateValidatorType` 属性で指定した検証を使用してメッセージ資格情報がチェックされます。  検証は、資格情報を受け入れることも拒否することもできます。  
  
## 使用例  
 次のコードは、メッセージ送信者検証モードを `PeerOrChainTrust` に設定します。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## 参照  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/ja-jp/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/ja-jp/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [セキュリティによるピア チャネル アプリケーションの保護](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
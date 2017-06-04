---
title: "&lt;serviceCredentials&gt; の &lt;issuedTokenAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;serviceCredentials&gt; の &lt;issuedTokenAuthentication&gt;
サービス資格情報として発行されるカスタム トークンを指定します。  
  
## 構文  
  
```  
  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`allowedAudienceUris`|<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Tokens.SamlSecurityToken> セキュリティ トークンのターゲットとなる URI のセットを取得します。  この属性の使い方の詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>」を参照してください。|  
|`allowUntrustedRsaIssuers`|信頼できない RSA 証明書の発行者を許可するかどうかを指定するブール値。<br /><br /> 証明書は、信頼性を検証する証明機関 \(CA\) によって署名されます。  信頼できない発行者とは、証明書の署名が信頼できると指定されていない CA です。|  
|`audienceUriMode`|<xref:System.IdentityModel.Tokens.SamlSecurityToken> セキュリティ トークンの <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> を検証するかどうかを指定する値を取得します。  この値は、<xref:System.IdentityModel.Selectors.AudienceUriMode> 型です。  この属性の使い方の詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>」を参照してください。|  
|`certificateValidationMode`|証明書検証モードを設定します。  <xref:System.ServiceModel.Security.X509CertificateValidationMode> の有効な値のいずれかです。  `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。  既定値は、`ChainTrust` です。|  
|`customCertificateValidatorType`|省略可能な文字列。  カスタム型の検証に使用される型およびアセンブリです。  `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。|  
|`revocationMode`|失効状態の検証を行うかどうかに加え、検証をオンラインで実行するか、オフラインで実行するかを指定する失効モードを設定します。  この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。|  
|`samlSerializer`|サービス資格情報に使用される SamlSerializer の型を指定する省略可能な文字列属性。  既定値は空の文字列です。|  
|`trustedStoreLocation`|省略可能な列挙体です。  2 つのシステム格納場所 \(`LocalMachine` または `CurrentUser`\) のいずれかです。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|`knownCertificates`|サービス資格情報の信頼できる発行者を指定する <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 要素のコレクションを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。|  
  
## 解説  
 発行されるトークンのシナリオには、3 つの段階があります。  まず、サービスにアクセスしようとしているクライアントが*セキュリティ トークン サービス*に参照されます。  次に、セキュリティ トークン サービスがクライアントを認証し、その後、クライアントにトークン \(通常は、SAML \(Security Assertions Markup Language\) トークン\) を発行します。  最後に、クライアントがトークンを持ってサービスに戻ります。  サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。  トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。  
  
 この要素は、このようなセキュリティ トークン サービス証明書のリポジトリです。  証明書を追加するには、[\<knownCertificates\>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md) を使用します。  次の例に示すように、証明書ごとに [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) を挿入します。  
  
```  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 既定では、証明書はセキュリティ トークン サービスから取得する必要があります。  このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。  
  
 この構成要素の使用の詳細については、「[方法 : フェデレーション サービスで資格情報を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)」を参照してください。  
  
## 参照  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>   
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>   
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>   
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>   
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
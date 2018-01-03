---
title: '&lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85043317c42d60d9a56ceb1e5678ad3b8222df79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltknowncertificatesgt"></a>&lt;knownCertificates&gt;
セキュリティ トークン サービス (STS) から発行されるセキュリティ資格情報を認証するために提供される X.509 証明書のコレクションを表します。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
\<serviceBehaviors >  
\<動作 >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
\<knownCertificates >  
  
## <a name="syntax"></a>構文  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|コレクションに X.509 証明書を追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|サービス資格情報として発行されるトークンを指定します。|  
  
## <a name="remarks"></a>コメント  
 発行されるトークンのシナリオには、3 つの段階があります。 最初の段階で、サービスにアクセスしようとしているクライアントは呼びます、*トークン サービスをセキュリティで保護された*です。 次に、セキュリティ トークン サービスがクライアントを認証し、その後、クライアントにトークン (通常は、SAML (Security Assertions Markup Language) トークン) を発行します。 最後に、クライアントがトークンを持ってサービスに戻ります。 サービスはトークンを調べ、トークンを認証することでクライアントの認証を可能にするデータを確認します。 トークンを認証するには、セキュリティ トークン サービスで使用される証明書がサービスによって認識されている必要があります。  
  
 [ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)要素は、このようなセキュリティ トークン サービスの証明書のリポジトリ。 証明書を追加するには、使用、 [ \<knownCertificates > 要素](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)です。 挿入、 [\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)証明書ごとに、次の例で示すようにします。  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 既定では、証明書はセキュリティ トークン サービスから取得する必要があります。 このような "既知" の証明書により、正当なクライアントのみがサービスにアクセスできるようになります。  
  
 この構成要素の使用方法の詳細と同様に、フェデレーション サービスによって認証されるクライアントに必要な条件を確認するを参照してください。[する方法: フェデレーション サービスの資格情報の構成](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)です。 フェデレーション シナリオの詳細については、次を参照してください。[フェデレーションと発行されたトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)です。  
  
 例については、コレクションの構成を設定する方法を示しています、次を参照してください。 [\<追加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

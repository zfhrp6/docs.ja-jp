---
title: '&lt;clientCredentials&gt; 要素の &lt;clientCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: 805289a427747cd00b5fe37e489a8a6b2e0fb19b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltclientcertificategt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; 要素の &lt;clientCertificate&gt;
サービスに対するクライアントの認証に使用する X.509 証明書を定義します。  
  
 \<system.ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors>  
\<behavior>  
\<clientCredentials>  
\<clientCertificate >  
  
## <a name="syntax"></a>構文  
  
```xml  
<clientCertificate findValue="String"   
    storeLocation="LocalMachine/CurrentUser"  
    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`findValue`|X.509 証明書ストアで検索する値を含む文字列。 属性に格納されている型は、`X509FindType` 属性値の要件を満たす必要があります。 既定値は空の文字列です。|  
|`storeLocation`|クライアントがサービスに対して自身を認証するために使用する X.509 証明書の場所を指定します。 以下の値が有効です。<br /><br /> -LocalMachine: ローカル マシンに割り当てられている証明書ストア。<br />-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。<br /><br /> 既定は LocalMachine です。 この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。|  
|`storeName`|検索する X.509 証明書ストアの名前を指定します。 以下の値が有効です。<br /><br /> -AddressBook: 他のユーザーのストアの証明書します。<br />-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。<br />-証明書ストアを CertificateAuthority: 中間証明機関 (Ca)。<br />-Disallowed: 失効した証明書のストアの証明書します。<br />-My: 証明書しますストアの個人用証明書。<br />信頼されたルート証明機関 (Ca) のルート: 証明書ストア。<br />-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。<br />-TrustedPublisher: 直接信頼された発行者のストアの証明書します。<br /><br /> 既定値は My です。 この属性は <xref:System.Security.Cryptography.X509Certificates.StoreName> 型です。|  
|X509FindType|実行する X.509 検索の種類を定義します。 `findValue` 属性に格納されている型は、この属性の要件を満たす必要があります。 以下の値が有効です。<br /><br /> は、FindByThumbPrint<br />-   FindBySubjectName<br />-Findbysubjectdistinguishedname です。<br />-   FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> 既定値は FindBySubjectDistinguishedName です。 この属性は <xref:System.Security.Cryptography.X509Certificates.X509FindType> 型です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## <a name="remarks"></a>コメント  
 この構成要素は、この要素によるクライアントの認証に使用する証明書を指定します。 詳細については、次を参照してください。[する方法: クライアントの資格情報の値を指定](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [方法: クライアントの資格情報の値を指定する](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)  
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)

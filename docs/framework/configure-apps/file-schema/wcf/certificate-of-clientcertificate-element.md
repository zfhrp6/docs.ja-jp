---
title: '&lt;clientCertificate&gt; 要素の &lt;certificate&gt;'
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 07885f8f1a575ef5b6ccb8d5f91f38a561261183
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753392"
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a>&lt;clientCertificate&gt; 要素の &lt;certificate&gt;
メッセージの署名と暗号化に使用される X.509 証明書を指定します。  
  
 \<system.ServiceModel >  
\<ビヘイビアー >  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<clientCertificate >  
\<証明書 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`findValue`|X.509 証明書ストアで検索する値を含む文字列。 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。 既定値は空の文字列です。|  
|`storeLocation`|クライアントがサーバーの証明書の検証に使用する X.509 証明書ストアの場所を指定します。 以下の値が有効です。<br /><br /> -LocalMachine: ローカル マシンに割り当てられている証明書ストア。<br />-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。<br /><br /> 既定は LocalMachine です。|  
|`storeName`|開く X.509 証明書ストアの名前を指定します。 以下の値が有効です。<br /><br /> -AddressBook: 他のユーザーのストアの証明書します。<br />-AuthRoot: サードパーティ証明機関 (Ca) のストアの証明書します。<br />-証明書ストアを CertificationAuthority: 中間証明機関 (Ca) にします。<br />-Disallowed: 失効した証明書のストアの証明書します。<br />-My: 証明書しますストアの個人用証明書。<br />信頼されたルート証明機関 (Ca) のルート: 証明書ストア。<br />-TrustedPeople: 直接信頼されたユーザーやリソースのストアの証明書します。<br />-TrustedPublisher: 直接信頼された発行者のストアの証明書します。<br /><br /> 既定値は My です。|  
|`X509FindType`|実行する X.509 検索の種類を定義します。 以下の値が有効です。<br /><br /> は、FindByThumbPrint<br />-   FindBySubjectName<br />-Findbysubjectdistinguishedname です。<br />-   FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。<br /><br /> 既定値は FindBySubjectDistinguishedName です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>コメント  
 `<certificate>` 要素は、サービスがクライアントと安全に通信するために、サービスが前もってクライアントの証明書を持っている必要がある場合に使用します。 このような状況は、双方向通信パターンを使用する場合に生じます。 より一般的な要求/応答パターンでは、クライアントは自身の証明書を要求に含め、サービスはそれを使用してクライアントへの応答を暗号化し、署名します。 一方、双方向通信パターンでは、サービスにはクライアントからの要求が来ないので、クライアントの証明書をあらかじめ取得することで、クライアント宛のメッセージのセキュリティを保護する必要があります。 このため、クライアントの証明書を帯域外のネゴシエーションで取得し、この要素を使用して証明書を指定する必要があります。 双方向サービスの詳細については、次を参照してください。[する方法: 双方向コントラクトを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。  
  
## <a name="example"></a>例  
 次のコードは、`<authentication>` 要素の適切な X.509 証明書とカスタム検証タイプの検索方法を指定します。  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [方法 : カスタム証明書検証を使用するサービスを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)

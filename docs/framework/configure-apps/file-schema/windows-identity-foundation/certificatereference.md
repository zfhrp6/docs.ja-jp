---
title: "&lt;certificateReference&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;certificateReference&gt;
検索して、証明書ストアの X.509 証明書を検証するために使用する設定を指定します。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference   
        storeName=”AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher”  
        storeLocation=”CurrentUser||LocalMachine”  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|storeName|X.509 証明書ストアの名前。  既定値は「私」。  省略可能です。|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 、X.509 証明書ストアの場所を指定する値。  既定値は、"LocalMachine"です。  省略可能です。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType> 、実行する検索の種類を指定する値。  既定値は"FindBySubjectDistinguishedName"です。  省略可能です。|  
|findValue|X.509 証明書ストアで検索する値。  省略可能です。|  
|isChainIncluded|証明書チェーンを使用して検証を実行するかどうかを指定します。  既定値は"true;"です。 検証は、証明書チェーンを使用して実行されます。  省略可能です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|暗号化し、トークンを復号化するために使用する証明書を構成します。|  
  
## 解説  
 `<certificateReference>`要素を探し、証明書ストアの X.509 証明書を検証するために使用する設定を指定します。  子要素として指定されると、 `<serviceCertficate>`要素は、場所と検証の設定を暗号化し、トークンを復号化に使用される X.509 証明書の指定します。  `<certificateReference>`要素で表される、 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>クラス。
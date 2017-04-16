---
title: "&lt;certificate&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# &lt;certificate&gt; 要素
ピアツーピア クライアントのメッセージの署名と暗号化に使用する X.509 証明書を指定します。  
  
## 構文  
  
```  
  
<certificate findValue="String"   
  
storeLocation="LocalMachine/CurrentUser"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`findValue`|X.509 証明書ストアで検索する値を含む文字列。  属性に格納されている型は、指定された `x509FindType` の要件を満たす必要があります。  既定値は空の文字列です。|  
|`storeLocation`|クライアントがピアの証明書の検証に使用する X.509 証明書ストアの場所を指定します。  以下の値が有効です。<br /><br /> -   LocalMachine: ローカル マシンに割り当てられた証明書ストア。<br />-   CurrentUser: 現在のユーザーに割り当てられた証明書ストア。<br /><br /> 既定は LocalMachine です。|  
|`storeName`|開く X.509 証明書ストアの名前を指定します。  以下の値が有効です。<br /><br /> -   AddressBook: 他のユーザー用の証明書ストア。<br />-   AuthRoot: サードパーティ証明機関 \(CA\) の証明書ストア。<br />-   CertificateAuthority: 中間証明機関 \(CA\) の証明書ストア。<br />-   Disallowed: 失効した証明書の証明書ストア。<br />-   My: 個人用証明書の証明書ストア。<br />-   Root: 信頼されたルート証明機関 \(CA\) の証明書ストア。<br />-   TrustedPeople: 直接信頼されたユーザーやリソースの証明書ストア。<br />-   TrustedPublisher: 直接信頼された発行者の証明書ストア。<br /><br /> 既定値は My です。|  
|`X509FindType`|実行する X.509 検索の種類を定義します。  以下の値が有効です。<br /><br /> -   FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-   FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 属性に格納されている型は、指定された `X509FindType` の要件を満たす必要があります。<br /><br /> 既定値は FindBySubjectDistinguishedName です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|ピアツーピア クライアントの認証時に使用される資格情報を指定します。|  
  
## 解説  
 この構成要素には、ピア メッシュ内の近隣ノードを認証するときに使用される X509Certificate2 インスタンスが格納されます。  
  
 ピア ツー ピア プログラミングの詳細については、「[ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)」を参照してください。  
  
## 使用例  
 次のコードは、ピアツーピア シナリオで使用される証明書の検索方法を指定します。  
  
```  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>   
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>   
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>   
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/ja-jp/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/ja-jp/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [セキュリティによるピア チャネル アプリケーションの保護](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
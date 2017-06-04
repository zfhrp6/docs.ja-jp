---
title: "&lt;identity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# &lt;identity&gt;
ID 要素を使用すると、クライアント開発者は予想されるサービスの ID をデザイン時に指定できます。  クライアントとサービス間のハンドシェイク プロセスでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] インフラストラクチャが、予想されるサービスの ID とこの要素の値との一致を確実に行うので、認証が可能になります。  詳細については、「[サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」を参照してください。  
  
## 構文  
  
```  
  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|certificate|X.509 証明書の設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.CertificateElement> 型です。  この要素には、この証明書でエンコードされる値を指定する文字列の `encodedValue` 属性が含まれています。|  
|certificateReference|X.509 証明書検証の設定を指定します。  この要素は <xref:System.ServiceModel.Configuration.CertificateReferenceElement> 型です。|  
|dns|サービスの認証に使用される X.509 証明書の DNS を指定します。  この要素には、実際の ID を含む文字列の `value` 属性が含まれています。|  
|rsa|クライアントに対するサービスの認証に使用される X.509 証明書の RSA フィールドの値を指定します。  この要素には、実際の ID を含む文字列の `value` 属性が含まれています|  
|servicePrincipalName|サーバー プリンシパル名 \(SPN\) ID を指定します。これは、サービスのインスタンスを一意に識別するために、クライアントにより使用されるプリンシパル名です。  この要素には、実際のプリンシパル名が文字列で含まれている `value` 属性が含まれています。  この要素は <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> 型です。|  
|userPrincipalName|ユーザー プリンシパル名 \(UPN\) ID を指定します。これは、ネットワーク上のユーザーのログオン名の種類です。  ユーザー プリンシパル名では、Active Directory で使用されるユーザー オブジェクト名の後に、@ 記号が続き、通常はその後にドメイン名システムの親ドメインが続きます。  たとえば、Fabrikam.com ドメイン ツリーの Jeff のユーザー プリンシパル名は、[jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) となります。  この要素には、実際のプリンシパル名が文字列で含まれている `value` 属性が含まれています。  この要素は <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> 型です。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<custom\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|netPeerTcpBinding のカスタム ピア リゾルバーを指定します。|  
|[\<endpoint\>](http://msdn.microsoft.com/ja-jp/13aa23b7-2f08-4add-8dbf-a99f8127c017)|さまざまなタイプのエンドポイントを設定します。|  
|[\<issuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|フェデレーション サービスのセキュリティ トークン サービス \(STS\) を指定します。|  
|[\<issuerMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|フェデレーション サービスのセキュリティ トークン サービス \(STS\) のメタデータ エンドポイントを指定します。|  
|[\<issuedTokenParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|カスタム バインディングで発行済みトークンのパラメーターを定義します。|  
|[\<localIssuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|ローカル セキュリティ トークン サービス \(STS\) を指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.IdentityElement>   
 <xref:System.ServiceModel.EndpointAddress>   
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>   
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [エンドポイント : アドレス、バインディング、およびコントラクト](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
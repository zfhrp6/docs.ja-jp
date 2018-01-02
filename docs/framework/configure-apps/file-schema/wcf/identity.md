---
title: '&lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 819bb9dc9817050e45a39331361dd5489692f0b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltidentitygt"></a>&lt;identity&gt;
ID 要素を使用すると、クライアント開発者は予想されるサービスの ID をデザイン時に指定できます。 クライアントとサービス間のハンドシェイク プロセスでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] インフラストラクチャが、予想されるサービスの ID とこの要素の値との一致を確実に行うので、認証が可能になります。 詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。  
  
 \<システムです。ServiceModel >  
\<クライアント >  
\<エンドポイント >  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|certificate|X.509 証明書の設定を指定します。 この要素は <xref:System.ServiceModel.Configuration.CertificateElement> 型です。 この要素には、この証明書でエンコードされる値を指定する文字列の `encodedValue` 属性が含まれています。|  
|certificateReference|X.509 証明書検証の設定を指定します。 この要素は <xref:System.ServiceModel.Configuration.CertificateReferenceElement> 型です。|  
|dns|サービスの認証に使用される X.509 証明書の DNS を指定します。 この要素には、実際の ID を含む文字列の `value` 属性が含まれています。|  
|rsa|クライアントに対するサービスの認証に使用される X.509 証明書の RSA フィールドの値を指定します。 この要素には、実際の ID を含む文字列の `value` 属性が含まれています|  
|servicePrincipalName|サーバー プリンシパル名 (SPN) ID を指定します。これは、サービスのインスタンスを一意に識別するために、クライアントにより使用されるプリンシパル名です。 この要素には、実際のプリンシパル名が文字列で含まれている `value` 属性が含まれています。 この要素は <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> 型です。|  
|userPrincipalName|ユーザー プリンシパル名 (UPN) ID を指定します。これは、ネットワーク上のユーザーのログオン名の種類です。 ユーザー プリンシパル名では、Active Directory で使用されるユーザー オブジェクト名の後に、@ 記号が続き、通常はその後にドメイン名システムの親ドメインが続きます。 たとえば、Fabrikam.com ドメイン ツリーの Jeff のユーザー プリンシパル名を含めることが[ jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)です。この要素には、実際のプリンシパル名が文字列で含まれている `value` 属性が含まれています。 この要素は <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<カスタム >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|netPeerTcpBinding のカスタム ピア リゾルバーを指定します。|  
|[\<エンドポイント >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)|さまざまなタイプのエンドポイントを設定します。|  
|[\<発行者 >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|フェデレーション サービスのセキュリティ トークン サービス (STS) を指定します。|  
|[\<issuerMetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|フェデレーション サービスのセキュリティ トークン サービス (STS) のメタデータ エンドポイントを指定します。|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|カスタム バインドで発行済みトークンのパラメーターを定義します。|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|ローカル セキュリティ トークン サービス (STS) を指定します。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [エンドポイント : アドレス、バインディング、およびコントラクト](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

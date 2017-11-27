---
title: '&lt;issuerMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7e96c41348dea40806c2aca331d7f8ca9499a78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuermetadatagt"></a>&lt;issuerMetadata&gt;
\<system.serviceModel >  
\<バインド >  
\<wsFederationHttpBinding >  
\<バインド >  
\<セキュリティ >  
\<メッセージ >  
\<issuerMetadata >  
  
## <a name="syntax"></a>構文  
  
```xml  
<issuerMetadata address=String" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|address|必須の `string` 属性です。<br /><br /> エンドポイントのアドレスを指定します。 アドレスは、絶対 URI にする必要があります。 既定値は空の文字列です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ヘッダー >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|アドレス ヘッダーのコレクション。|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<メッセージ >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [カスタム バインドのセキュリティ機能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

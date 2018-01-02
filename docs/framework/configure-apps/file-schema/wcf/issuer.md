---
title: "&lt;発行者&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e034b3ed0813d621ed86c2c3e86bb901ab39e40b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt"></a>&lt;発行者&gt;
セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を指定します。  
  
 \<system.serviceModel >  
\<バインド >  
\<wsFederationHttpBinding >  
\<バインド >  
\<セキュリティ >  
\<メッセージ >  
\<発行者 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<issuer address="Uri" >  
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
</issuer>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|address|必須の文字列。 STS の URL です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ヘッダー >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|ビルダーが作成できるエンドポイントのアドレス ヘッダーのコレクション。|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|発行されたトークンを使用する場合、クライアントでサーバーの認証を有効にする設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<メッセージ >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|メッセージ レベルのセキュリティの設定を定義、 [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)要素。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [カスタム バインドを使用したセキュリティ機能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c7e5c28325326d838da851ff4add12f8ae612c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
セキュリティ トークンの取得に使用される、ローカル発行者のアドレスとバインディングを指定します。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
endpointBehaviors セクション  
\<動作 >  
\<clientCredentials >  
\<issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>構文  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|address|必須の文字列。 ローカル発行者の URI を指定します。|  
|バインド|省略可能な文字列。 システム指定のバインディングの 1 つ。 一覧については、次を参照してください。[システム指定のバインディング](../../../../../docs/framework/wcf/system-provided-bindings.md)です。|  
|bindingConfiguration|省略可能な文字列。 構成ファイル内に存在するバインド構成を指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|ローカル発行者の ID 情報を指定します。|  
|[\<ヘッダー >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|ローカル発行者を正しくアドレス指定するために必要なアドレス ヘッダーのコレクション。 `add` キーワードを使用して、このコレクションにヘッダーを追加できます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。|  
  
## <a name="remarks"></a>コメント  
 発行されたトークンをセキュリティ トークン サービス (STS) から取得する場合は、クライアント アプリケーションに、STS との通信に使用するアドレスとバインディングが構成されている必要があります。 <xref:System.ServiceModel.WSFederationHttpBinding> にセキュリティ トークン サービスの URL が設定されていない場合、またはフェデレーション バインディングの発行者アドレスが http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous か `null` である場合、クライアントの [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] チャネルは、`address` と `binding` で指定された値を使用して STS と通信し、発行されたトークンを取得します。 ローカル発行者を構成する方法については、次を参照してください。[する方法: ローカル発行者を構成する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)です。  
  
## <a name="example"></a>例  
 次の例は、`address` 要素の `binding`、`bindingConfiguration`、および `localIssuer` 属性を設定します。  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [方法 : ローカル発行者を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)  
 [方法 : フェデレーション クライアントを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)

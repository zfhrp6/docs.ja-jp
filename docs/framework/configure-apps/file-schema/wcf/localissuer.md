---
title: "&lt;localIssuer&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;localIssuer&gt;
セキュリティ トークンの取得に使用される、ローカル発行者のアドレスとバインディングを指定します。  
  
## 構文  
  
```  
  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|address|必須の文字列。  ローカル発行者の URI を指定します。|  
|バインド|省略可能な文字列。  システム指定のバインディングの 1 つ。  一覧については、「[システム標準のバインディング](../../../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。|  
|bindingConfiguration|省略可能な文字列。  構成ファイル内に存在するバインディング構成を指定します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<identity\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|ローカル発行者の ID 情報を指定します。|  
|[\<headers\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|ローカル発行者を正しくアドレス指定するために必要なアドレス ヘッダーのコレクション。  `add` キーワードを使用して、このコレクションにヘッダーを追加できます。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<issuedToken\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。|  
  
## 解説  
 発行されたトークンをセキュリティ トークン サービス \(STS\) から取得する場合は、クライアント アプリケーションに、STS との通信に使用するアドレスとバインディングが構成されている必要があります。  <xref:System.ServiceModel.WSFederationHttpBinding> にセキュリティ トークン サービスの URL が設定されていない場合、またはフェデレーション バインディングの発行者アドレスが http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous か `null` である場合、クライアントの [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] チャネルは、`address` と `binding` で指定された値を使用して STS と通信し、発行されたトークンを取得します。  ローカル発行者の構成の詳細については、「[方法 : ローカル発行者を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)」を参照してください。  
  
## 使用例  
 次の例は、`localIssuer` 要素の `address`、`binding`、および `bindingConfiguration` 属性を設定します。  
  
```  
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
  
## 参照  
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
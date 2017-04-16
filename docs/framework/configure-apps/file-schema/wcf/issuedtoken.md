---
title: "&lt;issuedToken&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;issuedToken&gt;
サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。  
  
## 構文  
  
```  
  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`cacheIssuedTokens`|トークンがキャッシュされるかどうかを指定する省略可能なブール属性。  既定値は、`true` です。|  
|`defaultKeyEntropyMode`|ハンドシェイク操作に使用されるランダム値 \(エントロピ\) を指定する省略可能な文字列属性。  値には、`ClientEntropy`、`ServerEntropy`、および `CombinedEntropy` があります。既定値は `CombinedEntropy` です。  この属性は <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> 型です。|  
|`issuedTokenRenewalThresholdPercentage`|トークンが更新されるまでに待機できる有効な期間 \(トークン発行者によって提供される\) のパーセンテージを指定する省略可能な整数属性。  値は 0 ～ 100 の範囲です。  既定値は 60 で、更新の実行までに待機できる期間の 60% を示します。|  
|`issuerChannelBehaviors`|発行者との通信時に使用するチャネル動作を指定する省略可能な属性。|  
|`localIssuerChannelBehaviors`|ローカル発行者との通信時に使用するチャネル動作を指定する省略可能な属性。|  
|`maxIssuedTokenCachingTime`|トークン発行者 \(STS\) が期間を指定しない場合に、発行済みトークンがキャッシュされる期間を指定する省略可能な Timespan 属性。  既定値は “10675199.02:48:05.4775807” です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<localIssuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|トークンのローカル発行者のアドレスと、エンドポイントとの通信に使用されるバインディングを指定します。|  
|[\<issuerChannelBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|ローカル発行者に接続するときに使用するエンドポイント動作を指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<clientCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## 解説  
 発行済みトークンは、フェデレーション シナリオでセキュリティ トークン サービス \(STS\) を使用して認証するときに使用されるカスタム資格情報の種類です。  既定ではトークンは、SAML トークンです。  詳細については、「[フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)」を参照してください。   および [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) を参照してください。  
  
 このセクションには、トークンのローカル発行者やセキュリティ トークン サービスで使用する動作の構成に使用する要素が含まれます。  ローカル発行者を使用するようにクライアントを構成する手順については、「[方法 : ローカル発行者を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>   
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>   
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>   
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)   
 [方法 : フェデレーション クライアントを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [方法 : ローカル発行者を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)   
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
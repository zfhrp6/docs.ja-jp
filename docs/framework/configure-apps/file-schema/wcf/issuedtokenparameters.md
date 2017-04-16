---
title: "&lt;issuedTokenParameters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;issuedTokenParameters&gt;
フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。  
  
## 構文  
  
```  
  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## 型  
 `Type`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|defaultMessageSecurityVersion|バインドでサポートする必要があるセキュリティ仕様 \(WS\-Security、WS\-Trust、WS\-Secure Conversation、および WS\-Security Policy\) のバージョンを指定します。  この値は、<xref:System.ServiceModel.MessageSecurityVersion> 型です。|  
|inclusionMode|トークン包含要件を指定します。  この属性は <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> 型です。|  
|keySize|トークン キー サイズを指定する整数。  既定値は 256 です。|  
|keyType|キーの型を指定する <xref:System.IdentityModel.Tokens.SecurityKeyType> の有効な値。  既定値は、`SymmetricKey` です。|  
|tokenType|トークンの種類を指定する文字列。  既定値は、"http:\/\/docs.oasis\-open.org\/wss\/oasis\-wss\-saml\-token\-profile\-1.1\#SAML" です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<additionalRequestParameters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|追加の要求パラメーターを指定する構成要素のコレクション。|  
|[\<claimTypeRequirements\>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|必須のクレームの種類のコレクションを指定します。<br /><br /> フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。  たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。  このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。|  
|[\<issuer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|現在のトークンを発行するエンドポイントを指定する構成要素。|  
|[\<issuerMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|トークン発行者のメタデータのエンドポイント アドレスを指定する構成要素。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<secureConversationBootstrap\>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。|  
|[\<security\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|カスタム バインディングのセキュリティ オプションを指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>   
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>   
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [バインディング](../../../../../docs/framework/wcf/bindings.md)   
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [カスタム バインディング セキュリティ](../../../../../docs/framework/wcf/samples/custom-binding-security.md)   
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)   
 [カスタム バインディングを使用したセキュリティ機能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)   
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
---
title: "&lt;claimTypeRequirements&gt; 要素の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3234cd45-1478-468e-8b19-5c50815c4786
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;claimTypeRequirements&gt; 要素の &lt;add&gt;
フェデレーション資格情報に表示されると予想される必須のクレームおよび省略可能なクレームの種類を指定します。  たとえば、サービスは、クレームの種類の特定のセットを処理する必要がある受信資格情報について要件を記述します。  
  
## 構文  
  
```  
  
<claimTypeRequirements>  
      <add claimType="URI"  
        isOptional="Boolean" />  
</claimTypeRequirements>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|claimType|クレームの種類を定義する URI。  たとえば、Web サイトから製品を購入するために、ユーザーは、十分な与信限度額を備えた有効なクレジット カードを示す必要があります。  クレームの種類として、クレジット カードの URI があります。|  
|isOptional|これが省略可能なクレームかどうかを指定するブール値。  これが必須のクレームの場合は、この属性を `false` に設定します。<br /><br /> サービスが必須でない情報を求めるときにこの属性を使用できます。  たとえば、ユーザーに氏名と住所の入力を要求し、電話番号は省略可能にする場合などです。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<claimTypeRequirements\>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|必須のクレームの種類のコレクションを指定します。  各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。<br /><br /> フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。  たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。  このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。|  
  
## 解説  
 フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。  たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。  この要件はセキュリティ ポリシー内に明記されます。  クライアントがフェデレーション サービスの資格情報 \(CardSpace など\) を要求する場合、クライアントは要件をトークン要求 \(RequestSecurityToken\) に設定します。これにより、フェデレーション サービスは、要件どおりの資格情報を発行できます。  
  
## 使用例  
 次の構成では、2 つのクレームの種類の要件をセキュリティ バインディングに追加しています。  
  
```  
<bindings>  
    <wsFederationHttpBinding>  
      <binding name="myFederatedBinding">  
        <security mode="Message">  
          <message issuedTokenType="urn:oasis:names:tc:SAML:1.0:assertion">  
            <claimTypeRequirements>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/EmailAddress"/>  
              <add claimType=  
"http://schemas.microsoft.com/ws/2005/05/identity/claims/UserName"    
optional="true" />  
            </claims>  
          </message>  
        </security>  
      </binding>  
    </wsFederationHttpBinding>  
</bindings>  
```  
  
## 参照  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>   
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>   
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>   
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>   
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
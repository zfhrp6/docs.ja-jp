---
title: "クレームとトークン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クレーム [WCF], トークン"
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# クレームとトークン
ここでは、サポートされている既定のトークンから [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] によって作成されるさまざまなクレームの種類について説明します。  
  
 クライアント資格情報のクレームは、<xref:System.IdentityModel.Claims.ClaimSet> クラスと <xref:System.IdentityModel.Claims.Claim> クラスを使用して確認できます。  `ClaimSet` には、`Claim` オブジェクトのコレクションが格納されます。  各 `Claim` には、次の重要なメンバーがあります。  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> プロパティは、作成されるクレームの種類を指定する URI \(Uniform Resource Identifier\) を返します。  たとえば、クレームの種類が証明書の拇印の場合、その URI は http:schemas.microsoft.com\/ws\/20005\/05\/identity\/claims\/thumprint です。  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティは、クレームの権限を指定する URI を返します。  定義済みの権限は、<xref:System.IdentityModel.Claims.Rights> クラスにあります \(<xref:System.IdentityModel.Claims.Rights.Identity%2A>、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>\)。  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> プロパティは、クレームに関連付けられているリソースを返します。  
  
 各 <xref:System.IdentityModel.Claims.ClaimSet> には、<xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> プロパティがあり、それぞれ `Issuer` の <xref:System.IdentityModel.Claims.ClaimSet> を表します。  
  
## Windows アカウント  
 クライアント資格情報が Windows ユーザー アカウントにマップされる場合、<xref:System.IdentityModel.Claims.ClaimSet> は次の値を格納します。  
  
-   `Issuer` は、<xref:System.IdentityModel.Claims.ClaimSet> クラスの静的 Windows プロパティによって返される値です。  
  
-   コレクションには次のクレームがあります。  
  
    -   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 値がセキュリティ識別子 \(SID\)、<xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティ値が `Identity` で、<xref:System.IdentityModel.Claims.Claim.Resource%2A> が実際の SID 値を返す <xref:System.IdentityModel.Claims.Claim>。  SID は、ドメイン コントローラーによって各ユーザーに発行される一意の値です。  SID は、Windows セキュリティとの対話でユーザーを識別するために使用されます。  
  
    -   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 値 が SID、<xref:System.IdentityModel.Claims.Claim.Right%2A> が `PossessProperty` で、<xref:System.IdentityModel.Claims.Claim.Resource%2A> が SID 値の <xref:System.IdentityModel.Claims.Claim>。  
  
    -   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> が <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> が `PossessProperty` で、<xref:System.IdentityModel.Claims.Claim.Resource%2A> がユーザー名 \(たとえば、"MYMACHINE\\Bob"\) を含んだ文字列である <xref:System.IdentityModel.Claims.Claim>。  
  
    -   ユーザーが属するさまざまなグループの <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> が指定された追加の SID クレーム。  
  
## 証明書  
 クライアント資格情報が証明書の場合、<xref:System.IdentityModel.Claims.ClaimSet> は次の値を格納します。  
  
-   自己発行証明書の場合、`Issuer` は <xref:System.IdentityModel.Claims.ClaimSet> です。  <xref:System.IdentityModel.Claims.ClaimSet> は、<xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> に設定された <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>、`Identity` に設定された <xref:System.IdentityModel.Claims.Claim.Right%2A>、および証明書の拇印を含んだ <xref:System.Byte> 配列である <xref:System.IdentityModel.Claims.Claim.Resource%2A> 値を返します。  
  
-   証明機関によって発行された証明書の場合、発行者は、証明機関の証明書を表す `ClaimSet` です。  
  
-   コレクションの `Claims` には次のものが含まれます。  
  
    -   `ClaimType` が Thumbprint、`Right` が PossessProperty で、`Resource` が証明書の拇印を含んだバイト配列である `Claim`。  
  
    -   証明書のさまざまなプロパティを表す X500DistinguishedName、Dns、Name、Upn、Rsa などの複数の種類の追加の PossessProperty クレーム。  Rsa クレームのリソースは、証明書に関連付けられた公開キーです。**メモ** クライアント資格情報の種類が、サービスによって Windows アカウントにマップされる証明書の場合、2 つの `ClaimSet` オブジェクトが生成されます。  最初のオブジェクトには、Windows アカウントに関するすべてのクレームが入り、2 番目のオブジェクトには、証明書に関するすべてのクレームが入ります。  
  
## ユーザー名\/パスワード  
 クライアント資格情報が、Windows アカウントにマップされないユーザー名とパスワード \(または同等のもの\) の場合、`ClaimSet` は、`ClaimSet` クラスの静的 <xref:System.IdentityModel.Claims.ClaimSet.System%2A> プロパティによって発行されます。  `ClaimSet` は、リソースがクライアントによって提供されるユーザー名である <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> 型の `Identity` クレームを格納します。  対応するクレームには、`PossessProperty` の`Right` があります。  
  
## RSA キー  
 証明書に関連付けられていない RSA キーが使用される場合、`ClaimSet` は、自己発行され、リソースが RSA キーである <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> 型の `Identity` クレームを格納します。  対応するクレームには、`PossessProperty` の `Right` があります。  
  
## SAML  
 クライアントが SAML \(Security Assertions Markup Language\) トークンを使用して認証する場合、`ClaimSet` は、SAML トークンを署名したエンティティ \(通常は、SAML トークンを発行したセキュリティ トークン サービス \(STS\) の証明書\) によって発行されます。  `ClaimSet` は、SAML トークンに含まれているとおりのさまざまなクレームを格納します。  SAML トークンが、名前が `null` 以外の `SamlSubject` を含んでいる場合、型が <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> で、リソース型が <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> の `Identity` クレームが作成されます。  
  
## Identity クレームと ServiceSecurityContext.IsAnonymous  
 クライアント資格情報から生成された `ClaimSet` オブジェクトが、`Right` が `Identity` のクレームを格納していない場合、<xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> プロパティは `true` を返します。  このようなクレームが 1 つ以上ある場合、`IsAnonymous` プロパティは `false` を返します。  
  
## 参照  
 <xref:System.IdentityModel.Claims.ClaimSet>   
 <xref:System.IdentityModel.Claims.Claim>   
 <xref:System.IdentityModel.Claims.Rights>   
 <xref:System.IdentityModel.Claims.ClaimTypes>   
 [ID モデルを使用したクレームと承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
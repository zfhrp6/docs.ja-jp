---
title: "方法 : WSFederationHttpBinding を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フェデレーション"
  - "WCF, フェデレーション"
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 方法 : WSFederationHttpBinding を作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、<xref:System.ServiceModel.WSFederationHttpBinding> クラス \(構成の [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)\) が、フェデレーション サービスを公開するための機構を提供します。  これはクライアントに対して認証を要求するサービスであって、認証にはセキュリティ トークン サービスが発行するセキュリティ トークンが必要となります。  このトピックでは、必要な処理をコード中に埋め込む形、あるいは構成ファイルに必要な記述を加える形で、<xref:System.ServiceModel.WSFederationHttpBinding> の設定をする手順を説明します。  バインディングを作成すると、エンドポイントを設定してこのバインディングを使用できるようになります。  
  
 基本的な手順の概略を以下に示します。  
  
1.  セキュリティ モードを選択します。  <xref:System.ServiceModel.WSFederationHttpBinding> には、メッセージ レベルでエンドツーエンドのセキュリティを提供する `Message` を指定できます。複数のホップや `TransportWithMessageCredential` にまたがる通信であってもこれは有効です。クライアントとサービスが HTTPS 上で直接接続できる場合に、特に性能を発揮します。  
  
    > [!NOTE]
    >  <xref:System.ServiceModel.WSFederationHttpBinding> には、セキュリティ モードとして `None` を指定することもできます。  このモードは安全性が低く、デバッグ目的での使用のみを目的としています。  セキュリティ モードが `None` の <xref:System.ServiceModel.WSFederationHttpBinding> を使用してサービス エンドポイントを配置した場合、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) によって生成される <xref:System.ServiceModel.WsHttpBinding> のセキュリティ モードも `None` になります。  
  
     `WSFederationHttpBinding` の場合、システムに組み込まれている他のバインディングとは違って、クライアント資格情報の種類を選択する必要はありません。  これは、常に、発行されたトークンを資格情報として使うからです。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は指定された発行者からトークンを取得し、これをサービスに提示することによりクライアント認証を行います。  
  
2.  フェデレーション クライアントの場合、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> プロパティの値として、セキュリティ トークン サービスの URL を指定します。  <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> としてバインディングを指定し、セキュリティ トークン サービスとの通信に使用します。  
  
3.  省略可能です。  <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> プロパティの値として、トークンの種類の URI \(Uniform Resource Identifier\) を指定します。  フェデレーション サービスについては、提示されれば受理できるトークンの種類を指定します。  フェデレーション クライアントについては、セキュリティ トークン サービスに要求するトークンの種類を指定します。  
  
     トークンの種類を指定しなければ、クライアント側ではその URI なしで WS\-Trust のセキュリティ トークン要求 \(RTS\) を生成します。また、サービス側では、クライアントが既定で SAML \(Security Assertions Markup Language\) 1.1 のトークンを提示して認証するものと想定します。  
  
     SAML 1.1 トークンの URI は "http:\/\/docs.oasis\-open.org\/wss\/oasis\-wss\-saml\-token\-profile\-1.1\#SAMLV1.1" です。  
  
4.  省略可能です。  フェデレーション サービスの場合、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> プロパティの値として、セキュリティ トークン サービスのメタデータ URL を指定します。  メタデータ エンドポイントは、サービスがメタデータを公開するよう設定されている場合に、クライアントが適切なバインディング\/エンドポイントのペアを選択するために必要です。  メタデータの公開[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)」を参照してください。  
  
 他に設定できるプロパティとしては、発行されたトークンの証明キーとして使用するキーの種類、クライアント\/サーバー間で使用するアルゴリズム スイート、サービス資格情報をネゴシエートするか明示的に指定するか、トークンに入っていればそれに応じてサービス側で処理できるクレームの種類、クライアントがセキュリティ トークン サービスに送信する要求に追加しなければならない他の XML 要素などがあります。  
  
> [!NOTE]
>  `NegotiateServiceCredential` プロパティが意味をなすのは、`SecurityMode` の設定値が `Message` である場合に限ります。  `SecurityMode` の設定値が `TransportWithMessageCredential` であれば、`NegotiateServiceCredential` プロパティは無視されます。  
  
### 必要な処理をコード中に埋め込む形で WSFederationHttpBinding を設定するには  
  
1.  <xref:System.ServiceModel.WSFederationHttpBinding> のインスタンスを作成します。  
  
2.  必要に応じて、<xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.WSFederationHttpSecurityMode> または <xref:System.ServiceModel.WSFederationHttpSecurityMode> に設定します。  <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> 以外のアルゴリズム スイートが必要であれば、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> プロパティに、列挙体 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> のいずれかの値を設定します。  
  
3.  <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティに適切な値を設定します。  
  
4.  必要に応じて、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> プロパティに <xref:System.IdentityModel.Tokens.SecurityKeyType> の `SymmetricKey` または `AsymmetricKey` を設定します。  
  
5.  <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> プロパティに適切な値を設定します。  値を設定しない場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって既定値 "http:\/\/docs.oasis\-open.org\/wss\/oasis\-wss\-saml\-token\-profile\-1.1\#SAMLV1.1" に設定されます。これは SAML 1.1 トークンを表します。  
  
6.  クライアント側ではローカル発行者が指定されていなければ必須。サービス側では省略可能。  セキュリティ トークン サービスのアドレスと ID 情報が設定された <xref:System.ServiceModel.EndpointAddress> を作成し、この <xref:System.ServiceModel.EndpointAddress> インスタンスを <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> プロパティに代入します。  
  
7.  クライアント側ではローカル発行者が指定されていなければ必須。サービス側では不要。  `SecurityTokenService` の <xref:System.ServiceModel.Channels.Binding> を作成し、この <xref:System.ServiceModel.Channels.Binding> インスタンスを <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> プロパティに代入します。  
  
8.  クライアント側では不要。サービス側では省略可能。  セキュリティ トークン サービスのメタデータ用の <xref:System.ServiceModel.EndpointAddress> インスタンスを作成し、`IssuerMetadataAddress` プロパティに代入します。  
  
9. クライアント側、サービス側とも省略可能。  必要な数の <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> インスタンスを生成し、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> プロパティで返されたコレクションに追加します。  
  
10. クライアント側、サービス側とも省略可能。  必要な数の <xref:System.Xml.XmlElement> インスタンスを生成し、<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> プロパティで返されたコレクションに追加します。  
  
### 構成ファイルに必要な記述を加える形でフェデレーション エンドポイントを作成するには  
  
1.  [\<bindings\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素の子要素として [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 要素をアプリケーション構成ファイルに作成します。  
  
2.  [\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 要素の子要素として [\<binding\>](../../../../docs/framework/misc/binding.md) 要素を 作成し、`name` 属性に適切な値を設定します。  
  
3.  [\<binding\>](../../../../docs/framework/misc/binding.md) 要素の子要素として `<security>` 要素を作成します。  
  
4.  必要に応じて、`<security>` 要素の `mode` 属性値に `Message` または `TransportWithMessageCredential` を設定します。  
  
5.  `<security>` 要素の子要素として `<message>` 要素を作成します。  
  
6.  省略可能です。  `<message>` 要素の `algorithmSuite` 属性に適切な値を設定します。  既定値は、`Basic256` です。  
  
7.  省略可能です。  非対称証明キーが必要ならば、`<message>` 要素の `issuedKeyType` 属性を `AsymmetricKey` に設定します。  既定値は、`SymmetricKey` です。  
  
8.  省略可能です。  `<message>` 要素の `issuedTokenType` 属性を設定します。  
  
9. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では省略可能。  `<message>` 要素の子要素として `<issuer>` 要素を作成します。  
  
10. `<issuer>` 要素に `address` 属性を設定し、セキュリティ トークン サービスがトークン要求を受け付けるアドレスを指定します。  
  
11. 省略可能です。  `<identity>` 子要素を追加し、セキュリティ トークン サービスの識別子を指定します。  
  
12. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
13. クライアント側ではローカル発行者が指定されていなければ必須。サービス側では不要。  バインディング セクション内に、セキュリティ トークン サービスとの通信に使用可能な [\<binding\>](../../../../docs/framework/misc/binding.md) 要素を作成します。  バインディングの作成方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 構成でサービス バインディングを指定する](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)」を参照してください。  
  
14. `<issuer>` 要素の `binding` 属性および `bindingConfiguration` 属性に設定して、前の手順で作成したバインディングを指定します。  
  
15. クライアント側では不要。サービス側では省略可能。  \<`message`\> 要素の子要素として `<issuerMetadata>` 要素を作成します。  次に、`<issuerMetadata>` 要素の `address` 属性に、セキュリティ トークン サービスがメタデータを公開するアドレスを指定します。  オプションで、`<identity>` 子要素を追加し、セキュリティ トークン サービスの識別子を指定します。  
  
16. クライアント側、サービス側とも省略可能。  `<message>` 要素の子要素として `<claimTypeRequirements>` 要素を追加します。  サービスが依存する必須または省略可能なクレームを指定します。それには、[\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) 要素を `<claimTypeRequirements>` 要素に追加し、`claimType` 属性でクレームの種類を指定します。  さらに、`isOptional` 属性に、クレームが必須か省略可能かを設定します。  
  
## 使用例  
 強制的に `WSFederationHttpBinding` を設定するコード例を以下に示します。  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
 <!-- TODO: review snippet reference [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  -->  
  
## 参照  
 [フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)   
 [フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)   
 [方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
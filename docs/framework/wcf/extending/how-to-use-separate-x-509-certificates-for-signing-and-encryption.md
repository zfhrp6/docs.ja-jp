---
title: "方法 : 署名および暗号化に個別の X.509 証明書を使用する | Microsoft Docs"
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
  - "ClientCredentials クラス"
  - "ClientCredentialsSecurityTokenManager クラス"
  - "WCF, 拡張機能"
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法 : 署名および暗号化に個別の X.509 証明書を使用する
ここでは、クライアントとサービスの両方においてメッセージの署名と暗号化とで別の証明書を使用するように [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を構成する方法を示します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では複数のクライアント証明書またはサービス証明書を設定する API が提供されていないため、署名と暗号化で別の証明書を使用できるようにするには、カスタム クライアント資格情報またはカスタム サービス資格情報 \(あるいはその両方\) を作成する必要があります。さらに、複数の証明書の情報を利用し、指定されたキーの使用方法やメッセージの方向について適切なセキュリティ トークン プロバイダーを作成するために、セキュリティ トークン マネージャーを用意する必要があります。  
  
 使用される主要なクラス、そのクラスの継承元のクラス \(上向きの矢印で表示\)、および特定のメソッドおよびプロパティの戻り値の型を次の図に示します。  
  
-   `MyClientCredentials` は、<xref:System.ServiceModel.Description.ClientCredentials> のカスタム実装です。  
  
    -   図に示されたすべてのプロパティは、すべて <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> のインスタンスを返します。  
  
    -   メソッド <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> は、`MyClientCredentialsSecurityTokenManager` のインスタンスを返します。  
  
-   `MyClientCredentialsSecurityTokenManager` は、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> のカスタム実装です。  
  
    -   メソッド <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> は、<xref:System.IdentityModel.Selectors.X509SecurityTokenProvider> のインスタンスを返します。  
  
 ![クライアント資格情報がどのように使用されるのかを示す図](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd\-a59f\-4571\-b36f\-7e6b2f0d610f")  
  
 カスタム資格情報[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。  
  
 また、カスタム ID 検証機能を作成し、カスタム バインディングのセキュリティ バインド要素にリンクする必要があります。さらに、既定の資格情報の代わりにカスタム資格情報を使用する必要があります。  
  
 カスタム バインディングに関連したクラス、およびカスタム ID 検証機能のリンク方法を次の図に示します。関連するバインド要素はいくつかありますが、そのすべてが <xref:System.ServiceModel.Channels.BindingElement> から継承されています。<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> には、<xref:System.ServiceModel.Channels.LocalClientSecuritySettings> プロパティがあります。このプロパティは、`MyIdentityVerifier` のカスタマイズの元となる <xref:System.ServiceModel.Security.IdentityVerifier> のインスタンスを返します。  
  
 ![カスタム バインディング要素を示す図](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2\-0bb4\-4921\-9bf4\-20d4d82c3da5")  
  
 カスタム ID 検証機能[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : カスタム クライアント ID 検証機能を作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)」を参照してください。  
  
### 署名と暗号化に別個の証明書を使用するには  
  
1.  <xref:System.ServiceModel.Description.ClientCredentials> クラスを継承する新しいクライアント資格情報クラスを定義します。複数の証明書を指定できるようにする、`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate`、および `ServiceEncryptingCertificate` の 4 つの新しいプロパティを実装します。また、<xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> メソッドをオーバーライドして、次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスのインスタンスを返すように設定します。  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承する新しいクライアント セキュリティ トークン マネージャーを定義します。適切なセキュリティ トークン プロバイダーを作成するために、<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> メソッドをオーバーライドします。メッセージの方向とキーの使用方法は、`requirement` パラメーター \(<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>\) で提供されます。  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  <xref:System.ServiceModel.Description.ServiceCredentials> クラスを継承する新しいサービス資格情報クラスを定義します。複数の証明書を指定できるようにする、`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate`、および `ServiceEncryptingCertificate` の 4 つの新しいプロパティを実装します。また、<xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> メソッドをオーバーライドして、次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスのインスタンスを返すように設定します。  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> クラスを継承する新しいサービス セキュリティ トークン マネージャーを定義します。渡されたメッセージの方向とキーの使用方法について適切なセキュリティ トークン プロバイダーを作成するために、<xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> メソッドをオーバーライドします。  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### クライアントで複数の証明書を使用するには  
  
1.  カスタム バインディングの作成セキュリティ バインド要素は、要求と応答について異なるセキュリティ トークン プロバイダーが存在することを可能にする二重モードで動作する必要があります。これを行うには、二重モード対応のトランスポートを使用するか、次のコードで示すように <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> を使用します。次のステップで定義するカスタマイズ済みの <xref:System.ServiceModel.Security.IdentityVerifier> をセキュリティ バインド要素にリンクします。既定のクライアント資格情報を、事前に作成したカスタマイズ済みのクライアント資格情報に置き換えます。  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  カスタム <xref:System.ServiceModel.Security.IdentityVerifier> を定義します。要求の暗号化と応答への署名で異なる証明書が使用されるため、サービスには複数の ID があります。  
  
    > [!NOTE]
    >  次のサンプルで用意されたカスタム ID 検証方法では、デモンストレーション用であるため、エンドポイント ID 検査がまったく行われません。これは製品版のコードでは、お勧めしません。  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### サービスで複数の証明書を使用するには  
  
1.  カスタム バインディングの作成セキュリティ バインド要素は、要求と応答について異なるセキュリティ トークン プロバイダーが存在することを可能にする二重モードで動作する必要があります。クライアントの場合と同様に、二重モード対応のトランスポートを使用するか、次のコードで示すように <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> を使用します。既定のサービス資格情報を、事前に作成したカスタマイズ済みのサービス資格情報に置き換えます。  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## 参照  
 <xref:System.ServiceModel.Description.ClientCredentials>   
 <xref:System.ServiceModel.Description.ServiceCredentials>   
 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>   
 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>   
 <xref:System.ServiceModel.Security.IdentityVerifier>   
 [チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
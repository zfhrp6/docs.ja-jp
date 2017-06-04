---
title: "方法 : カスタム セキュリティ トークン プロバイダーを作成する | Microsoft Docs"
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
  - "セキュリティ [WCF], 資格情報の提供"
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# 方法 : カスタム セキュリティ トークン プロバイダーを作成する
ここでは、カスタム セキュリティ トークン プロバイダーを持つ新しいトークンの種類を作成する方法と、そのプロバイダーをカスタム セキュリティ トークン マネージャーと統合する方法について説明します。  
  
> [!NOTE]
>  <xref:System.IdentityModel.Tokens> 名前空間にあるシステム指定のトークンがユーザーの要件に一致しない場合、カスタム トークン プロバイダーを作成します。  
  
 セキュリティ トークン プロバイダーは、クライアントまたはサービスの資格情報に基づいてセキュリティ トークンの表現を作成します。  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] セキュリティでカスタム セキュリティ トークン プロバイダーを使用するには、カスタム資格情報とセキュリティ トークン マネージャーの実装を作成する必要があります。  
  
 カスタム資格情報とセキュリティ トークン マネージャーの詳細については、「[チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。  
  
 資格情報、セキュリティ トークン マネージャー、およびプロバイダー クラスと認証システム クラスの詳細については、「[Security Architecture](http://msdn.microsoft.com/ja-jp/16593476-d36a-408d-808c-ae6fd483e28f)」を参照してください。  
  
### カスタム セキュリティ トークン プロバイダーを作成するには  
  
1.  <xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスから派生する新しいクラスを定義します。  
  
2.  <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> メソッドを実装します。  このメソッドは、セキュリティ トークンのインスタンスを作成して返す役割を担います。  `MySecurityTokenProvider` という名前のクラスを作成し、<xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> メソッドをオーバーライドして <xref:System.IdentityModel.Tokens.X509SecurityToken> クラスのインスタンスを返す例を次に示します。  クラス コンストラクターには <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> クラスのインスタンスが必要です。  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### カスタム セキュリティ トークン マネージャーにカスタム セキュリティ トークン プロバイダーを統合するには  
  
1.  <xref:System.IdentityModel.Selectors.SecurityTokenManager> クラスから派生する新しいクラスを定義します。  以下の例は、<xref:System.IdentityModel.Selectors.SecurityTokenManager> クラスから派生した <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスから派生したクラスです。  
  
2.  まだオーバーライドされていない場合は、<xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> メソッドをオーバーライドします。  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> メソッドは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティ フレームワークによりメソッドに渡される <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> パラメーターに適した <xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスのインスタンスを返す役割を担います。  メソッドが適切なセキュリティ トークン パラメーターで呼び出された場合に、カスタム セキュリティ トークン プロバイダーの実装 \(以前の手順で作成済み\) を返すようにメソッドを変更します。  セキュリティ トークン マネージャーの詳細については、「[チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)」を参照してください。  
  
3.  <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> パラメーターに基づいてカスタム セキュリティ トークン プロバイダーを返すカスタム ロジックをメソッドに追加します。  トークンの要件が満たされた場合に、カスタム セキュリティ トークン プロバイダーを返す例を次に示します。  要件には、X.509 セキュリティ トークンとメッセージの方向 \(メッセージ出力にトークンが使用される\) が含まれます。  他のすべての場合で、コードは基本クラスを呼び出し、他のセキュリティ トークンの要件に合わせてシステム指定の動作を維持します。  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## 使用例  
 完全な <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 実装と対応する <xref:System.IdentityModel.Selectors.SecurityTokenManager> 実装を次に示します。  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## 参照  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>   
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>   
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>   
 <xref:System.IdentityModel.Tokens.X509SecurityToken>   
 [チュートリアル: カスタム クライアントおよびサービスの資格情報を作成する](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)   
 [方法 : カスタム セキュリティ トークン認証システムを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)   
 [Security Architecture](http://msdn.microsoft.com/ja-jp/16593476-d36a-408d-808c-ae6fd483e28f)
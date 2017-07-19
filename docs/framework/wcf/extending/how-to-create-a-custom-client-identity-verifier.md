---
title: "方法 : カスタム クライアント ID 検証機能を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 方法 : カスタム クライアント ID 検証機能を作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の *ID* 機能を使用すると、クライアントで、予想されるサービスの ID を事前に指定できます。  サーバーがクライアントに対して自身を認証するたびに、ID がこの予想 ID と照合されます  \(ID とその機能の詳細については、「[サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」を参照してください\)。  
  
 必要に応じて、カスタム ID 検証機能を使用して検証をカスタマイズできます。  たとえば、追加のサービス ID 検証チェックを実行できます。  この例では、カスタム ID 検証機能で、サーバーから戻された X.509 証明書の追加のクレームをチェックします。  サンプル アプリケーションについては、「[サービス ID サンプル](../../../../docs/framework/wcf/samples/service-identity-sample.md)」を参照してください。  
  
### EndpointIdentity クラスを拡張するには  
  
1.  <xref:System.ServiceModel.EndpointIdentity> クラスから派生する新しいクラスを定義します。  拡張子 `OrgEndpointIdentity` に名前を付ける例を次に示します。  
  
2.  拡張 <xref:System.ServiceModel.Security.IdentityVerifier> クラスで使用するプライベート メンバーとプロパティを追加し、サービスによって返されたセキュリティ トークンのクレームに対して ID チェックを実行します。  この例では、`OrganizationClaim` プロパティを定義します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### IdentityVerifier クラスを拡張するには  
  
1.  <xref:System.ServiceModel.Security.IdentityVerifier> から派生する新しいクラスを定義します。  拡張子 `CustomIdentityVerifier` に名前を付ける例を次に示します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> メソッドをオーバーライドします。  このメソッドは、ID チェックが成功したか失敗したかを判定します。  
  
3.  `CheckAccess` メソッドには 2 つのパラメーターがあります。  1 つ目は <xref:System.ServiceModel.EndpointIdentity> クラスのインスタンスです。  2 つ目は <xref:System.IdentityModel.Policy.AuthorizationContext> クラスのインスタンスです。  
  
     メソッド実装では、<xref:System.IdentityModel.Policy.AuthorizationContext> クラスの <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> プロパティから返されたクレームのコレクションを検査し、必要に応じて認証チェックを実行します。  この例では、まず種類が "識別名" のクレームをすべて検索し、次にその名前と <xref:System.ServiceModel.EndpointIdentity> の拡張 \(`OrgEndpointIdentity`\) とを比較します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### TryGetIdentity メソッドを実装するには  
  
1.  <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> メソッドを実装します。このメソッドは、クライアントが <xref:System.ServiceModel.EndpointIdentity> クラスのインスタンスを返すことができるかどうかを判定します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャは、まず `TryGetIdentity` メソッドの実装を呼び出して、メッセージからサービスの ID を取得します。  次に、インフラストラクチャは、返された `EndpointIdentity` と <xref:System.IdentityModel.Policy.AuthorizationContext> を使用して `CheckAccess` 実装を呼び出します。  
  
2.  `TryGetIdentity` メソッドに次のコードを追加します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### カスタム バインディングを実装してカスタム ID 検証機能を設定するには  
  
1.  <xref:System.ServiceModel.Channels.Binding> オブジェクトを返すメソッドを作成します。  この例は、まず <xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードを <xref:System.ServiceModel.SecurityMode>、<xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> を <xref:System.ServiceModel.MessageCredentialType> に設定します。  
  
2.  <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> メソッドを使用して <xref:System.ServiceModel.Channels.BindingElementCollection> を作成します。  
  
3.  コレクションから <xref:System.ServiceModel.Channels.SecurityBindingElement> を返し、それを <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 変数にキャストします。  
  
4.  <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> クラスの <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> プロパティを、以前作成した `CustomIdentityVerifier` クラスの新しいインスタンスに設定します。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  返されたカスタム バインディングを使用してクライアントのインスタンスとクラスを作成します。  これにより、クライアントは、次のコードに示すようにサービスのカスタム ID 検証チェックを実行できるようになります。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## 使用例  
 <xref:System.ServiceModel.Security.IdentityVerifier> クラスの完全な実装方法の例を次に示します。  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## 使用例  
 <xref:System.ServiceModel.EndpointIdentity> クラスの完全な実装方法の例を次に示します。  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## 参照  
 <xref:System.ServiceModel.ServiceAuthorizationManager>   
 <xref:System.ServiceModel.EndpointIdentity>   
 <xref:System.ServiceModel.Security.IdentityVerifier>   
 [サービス ID サンプル](../../../../docs/framework/wcf/samples/service-identity-sample.md)   
 [承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)   
 [承認ポリシー](../../../../docs/framework/wcf/samples/authorization-policy.md)
---
title: "方法 : ローカル発行者を設定する | Microsoft Docs"
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
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法 : ローカル発行者を設定する
ここでは、発行済みトークンに対してローカル発行者を使用するようにクライアントを構成する方法を説明します。  
  
 クライアントがフェデレーション サービスと通信する場合、クライアントが自分をフェデレーション サービスに対して認証するときに使用するトークンの発行元となるセキュリティ トークン サービスのアドレスが、サービスによって指定されることがよくあります。特定の状況では、クライアントが*ローカル発行者*を使用するように構成されることがあります。  
  
 フェデレーション バインディングの発行者アドレスが http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous または `null` である場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] はローカル発行者を使用します。そのような場合は、ローカルの発行者およびバインディングのアドレスと共に <xref:System.ServiceModel.Description.ClientCredentials> を構成し、その発行者との通信に使用する必要があります。  
  
> [!NOTE]
>  `ClientCredentials` クラスの <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> プロパティが `true` に設定されており、ローカル発行者アドレスが指定されておらず、[\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)または他のフェデレーション バインディングで指定される発行者アドレスが http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self、http:\/\/schemas.microsoft.com\/2005\/12\/ServiceModel\/Addressing\/Anonymous、または `null` である場合、Windows の [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 発行者が使用されます。  
  
### コードでローカル発行者を構成するには  
  
1.  <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 型の変数を作成します。  
  
2.  `ClientCredentials` クラスの <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> プロパティから返されるインスタンスに変数を設定します。このインスタンスは、\(<xref:System.ServiceModel.ClientBase%601> から継承された\) クライアントの <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> プロパティ、または <xref:System.ServiceModel.ChannelFactory> の <xref:System.ServiceModel.ChannelFactory.Credentials%2A> プロパティから次のように返されます。  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> プロパティを <xref:System.ServiceModel.EndpointAddress> の新規インスタンスに設定します。このとき、次のようにコンストラクターに対する引数としてローカル発行者のアドレスを使用します。  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     あるいは、次のように新規の <xref:System.Uri> インスタンスをコンストラクターへの引数として作成します。  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     次に示すように、`addressHeaders` パラメーターは <xref:System.ServiceModel.Channels.AddressHeader> インスタンスの配列です。  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> プロパティを使用して、ローカル発行者のバインディングを次のように設定します。  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  省略可能。ローカル発行者に対して構成したエンドポイントの動作を <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> プロパティから返されるコレクションに追加することにより、この動作を次のように追加します。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### 構成でローカル発行者を構成するには  
  
1.  その要素自体がエンドポイント動作の [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 要素の子要素である [\<issuedToken\>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) 要素の子として、[\<localIssuer\>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) 要素を作成します。  
  
2.  `address` 属性を、トークン要求を受け入れるローカル発行者のアドレスに設定します。  
  
3.  `binding` および `bindingConfiguration` 属性を、ローカル発行者のエンドポイントと通信するときに使用する適切なバインディングを参照する値に設定します。  
  
4.  省略可能。\<`localIssuer`\> 要素の子要素として [\<identity\>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) 要素を設定し、ローカル発行者の ID 情報を指定します。  
  
5.  省略可能。\<`localIssuer`\> 要素の子要素として [\<headers\>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) 要素を設定し、ローカル発行者を正しくアドレス指定するために必要な追加ヘッダーを指定します。  
  
## .NET Framework セキュリティ  
 特定のバインディングに対して発行者アドレスとバインディングが指定されている場合、ローカル発行者はこのバインディングを使用するエンドポイントには使用されません。ローカル発行者を常に使用する必要があるクライアントには、このようなバインディングが使用されることがないこと、または発行者アドレスが `null` となるようにクライアントによってバインディングが変更されることが保証されている必要があります。  
  
## 参照  
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [方法 : フェデレーション クライアントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
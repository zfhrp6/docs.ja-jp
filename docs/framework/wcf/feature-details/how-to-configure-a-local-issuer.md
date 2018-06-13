---
title: '方法 : ローカル発行者を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 2b227398af3ea0dfd7cd866f1110ccc1737553c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495094"
---
# <a name="how-to-configure-a-local-issuer"></a>方法 : ローカル発行者を設定する
ここでは、発行済みトークンに対してローカル発行者を使用するようにクライアントを構成する方法を説明します。  
  
 クライアントがフェデレーション サービスと通信する場合、クライアントが自分をフェデレーション サービスに対して認証するときに使用するトークンの発行元となるセキュリティ トークン サービスのアドレスが、サービスによって指定されることがよくあります。 特定の状況で使用するクライアントを構成することがあります、*ローカル発行者*です。  
  
 Windows Communication Foundation (WCF) フェデレーション バインディングの発行者アドレスがある場合はローカル発行者を使用してhttp://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymousまたは`null`です。 そのような場合は、ローカルの発行者およびバインディングのアドレスと共に <xref:System.ServiceModel.Description.ClientCredentials> を構成し、その発行者との通信に使用する必要があります。  
  
> [!NOTE]
>  場合、<xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A>のプロパティ、`ClientCredentials`クラスに設定されている`true`、ローカル発行者のアドレスが指定されていない、および発行者のアドレスを指定して、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)またはその他のフェデレーション バインディングはhttp://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self、 http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous、または`null`、Windows では、[!INCLUDE[infocard](../../../../includes/infocard-md.md)]発行者を使用します。  
  
### <a name="to-configure-the-local-issuer-in-code"></a>コードでローカル発行者を構成するには  
  
1.  <xref:System.ServiceModel.Security.IssuedTokenClientCredential> 型の変数を作成します。  
  
2.  <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> クラスの `ClientCredentials` プロパティから返されるインスタンスに変数を設定します。 このインスタンスは、(<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> から継承された) クライアントの <xref:System.ServiceModel.ClientBase%601> プロパティ、または <xref:System.ServiceModel.ChannelFactory.Credentials%2A> の <xref:System.ServiceModel.ChannelFactory> プロパティから次のように返されます。  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> プロパティを <xref:System.ServiceModel.EndpointAddress> の新規インスタンスに設定します。このとき、次のようにコンストラクターに対する引数としてローカル発行者のアドレスを使用します。  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     あるいは、次のように新規の <xref:System.Uri> インスタンスをコンストラクターへの引数として作成します。  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders`パラメーターは配列の<xref:System.ServiceModel.Channels.AddressHeader>インスタンスを示すようにします。  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  使用して、ローカル発行者のバインディングの設定、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>プロパティです。  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  任意。 ローカル発行者に対して構成したエンドポイントの動作を <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> プロパティから返されるコレクションに追加することにより、この動作を次のように追加します。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>構成でローカル発行者を構成するには  
  
1.  作成、 [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)の子要素として、 [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)はそれ自体の子要素、 [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)エンドポイントの動作の要素。  
  
2.  `address` 属性を、トークン要求を受け入れるローカル発行者のアドレスに設定します。  
  
3.  `binding` および `bindingConfiguration` 属性を、ローカル発行者のエンドポイントと通信するときに使用する適切なバインディングを参照する値に設定します。  
  
4.  任意。 設定、 [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)の子要素として、<`localIssuer`> 要素し、ローカル発行者の id 情報を指定します。  
  
5.  任意。 設定、 [\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)の子要素として、<`localIssuer`> 要素と、ローカル発行者を正しく対処するために必要な追加のヘッダーを指定します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 特定のバインディングに対して発行者アドレスとバインディングが指定されている場合、ローカル発行者はこのバインディングを使用するエンドポイントには使用されません。 ローカル発行者を常に使用する必要があるクライアントには、このようなバインディングが使用されることがないこと、または発行者アドレスが `null` となるようにクライアントによってバインディングが変更されることが保証されている必要があります。  
  
## <a name="see-also"></a>関連項目  
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [方法 : フェデレーション クライアントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [方法 : WSFederationHttpBinding を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)

---
title: "方法 : ローカル発行者を設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90edf0735d890e0abc1560de5a7f523ee2faa7c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="3d74e-102">方法 : ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="3d74e-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="3d74e-103">ここでは、発行済みトークンに対してローカル発行者を使用するようにクライアントを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="3d74e-104">クライアントがフェデレーション サービスと通信する場合、クライアントが自分をフェデレーション サービスに対して認証するときに使用するトークンの発行元となるセキュリティ トークン サービスのアドレスが、サービスによって指定されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="3d74e-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="3d74e-105">特定の状況で使用するクライアントを構成することがあります、*ローカル発行者*です。</span><span class="sxs-lookup"><span data-stu-id="3d74e-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 <span data-ttu-id="3d74e-106">フェデレーション バインディングの発行者アドレスが http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous または [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] である場合、`null` はローカル発行者を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-106">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses a local issuer in cases where the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`.</span></span> <span data-ttu-id="3d74e-107">そのような場合は、ローカルの発行者およびバインディングのアドレスと共に <xref:System.ServiceModel.Description.ClientCredentials> を構成し、その発行者との通信に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d74e-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d74e-108">場合、<xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A>のプロパティ、`ClientCredentials`クラスに設定されている`true`、ローカル発行者のアドレスが指定されていない、および発行者のアドレスを指定して、 [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)またはその他のフェデレーション バインディングは http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self、http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous、またはが`null`、Windows、[!INCLUDE[infocard](../../../../includes/infocard-md.md)]発行者を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, or is `null`, then the Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="3d74e-109">コードでローカル発行者を構成するには</span><span class="sxs-lookup"><span data-stu-id="3d74e-109">To configure the local issuer in code</span></span>  
  
1.  <span data-ttu-id="3d74e-110"><xref:System.ServiceModel.Security.IssuedTokenClientCredential> 型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>  
  
2.  <span data-ttu-id="3d74e-111"><xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> クラスの `ClientCredentials` プロパティから返されるインスタンスに変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="3d74e-112">このインスタンスは、(<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> から継承された) クライアントの <xref:System.ServiceModel.ClientBase%601> プロパティ、または <xref:System.ServiceModel.ChannelFactory.Credentials%2A> の <xref:System.ServiceModel.ChannelFactory> プロパティから次のように返されます。</span><span class="sxs-lookup"><span data-stu-id="3d74e-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <span data-ttu-id="3d74e-113"><xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> プロパティを <xref:System.ServiceModel.EndpointAddress> の新規インスタンスに設定します。このとき、次のようにコンストラクターに対する引数としてローカル発行者のアドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="3d74e-114">あるいは、次のように新規の <xref:System.Uri> インスタンスをコンストラクターへの引数として作成します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="3d74e-115">`addressHeaders`パラメーターは配列の<xref:System.ServiceModel.Channels.AddressHeader>インスタンスを示すようにします。</span><span class="sxs-lookup"><span data-stu-id="3d74e-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <span data-ttu-id="3d74e-116">使用して、ローカル発行者のバインディングの設定、<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3d74e-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  <span data-ttu-id="3d74e-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3d74e-117">Optional.</span></span> <span data-ttu-id="3d74e-118">ローカル発行者に対して構成したエンドポイントの動作を <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> プロパティから返されるコレクションに追加することにより、この動作を次のように追加します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="3d74e-119">構成でローカル発行者を構成するには</span><span class="sxs-lookup"><span data-stu-id="3d74e-119">To configure the local issuer in configuration</span></span>  
  
1.  <span data-ttu-id="3d74e-120">作成、 [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)の子要素として、 [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)はそれ自体の子要素、 [ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)エンドポイントの動作の要素。</span><span class="sxs-lookup"><span data-stu-id="3d74e-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2.  <span data-ttu-id="3d74e-121">`address` 属性を、トークン要求を受け入れるローカル発行者のアドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3.  <span data-ttu-id="3d74e-122">`binding` および `bindingConfiguration` 属性を、ローカル発行者のエンドポイントと通信するときに使用する適切なバインディングを参照する値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4.  <span data-ttu-id="3d74e-123">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3d74e-123">Optional.</span></span> <span data-ttu-id="3d74e-124">設定、 [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)の子要素として、<`localIssuer`> 要素し、ローカル発行者の id 情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5.  <span data-ttu-id="3d74e-125">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3d74e-125">Optional.</span></span> <span data-ttu-id="3d74e-126">設定、 [\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)の子要素として、<`localIssuer`> 要素と、ローカル発行者を正しく対処するために必要な追加のヘッダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3d74e-127">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3d74e-127">.NET Framework Security</span></span>  
 <span data-ttu-id="3d74e-128">特定のバインディングに対して発行者アドレスとバインディングが指定されている場合、ローカル発行者はこのバインディングを使用するエンドポイントには使用されません。</span><span class="sxs-lookup"><span data-stu-id="3d74e-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="3d74e-129">ローカル発行者を常に使用する必要があるクライアントには、このようなバインディングが使用されることがないこと、または発行者アドレスが `null` となるようにクライアントによってバインディングが変更されることが保証されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d74e-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d74e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d74e-130">See Also</span></span>  
 [<span data-ttu-id="3d74e-131">方法: フェデレーション サービスの資格情報を構成します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="3d74e-132">方法: フェデレーション クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="3d74e-133">方法: WSFederationHttpBinding を作成します。</span><span class="sxs-lookup"><span data-stu-id="3d74e-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)

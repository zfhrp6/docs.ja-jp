---
title: "方法 : WCF クライアントで WSE 3.0 サービスにアクセスする"
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
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49ff6378bcd35ab2d4e2adf3783a1c4e73025d3a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a><span data-ttu-id="b101e-102">方法 : WCF クライアントで WSE 3.0 サービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="b101e-102">How to: Access a WSE 3.0 Service with a WCF Client</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="b101e-103"> クライアントが WS-Addressing 仕様の 2004 年 8 月版を使用するように構成されている場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントは Microsoft .NET サービスの Web サービス拡張 (WSE: Web Services Enhancements) 3.0 とネットワーク レベルの互換性があります。</span><span class="sxs-lookup"><span data-stu-id="b101e-103"> clients are wire-level compatible with Web Services Enhancements (WSE) 3.0 for Microsoft .NET services when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span> <span data-ttu-id="b101e-104">ただし、WSE 3.0 サービス プロトコルをサポートしない、メタデータ交換 (MEX)、これを使用する場合、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を作成する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント クラスをセキュリティの設定は適用されません生成された[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント。</span><span class="sxs-lookup"><span data-stu-id="b101e-104">However, WSE 3.0 services do not support the metadata exchange (MEX) protocol, so when you use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class, the security settings are not applied to the generated [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="b101e-105">そのため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの生成後に、WSE 3.0 サービスで必要なセキュリティ設定を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b101e-105">Therefore, you must specify the security settings that the WSE 3.0 service requires after the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is generated.</span></span>  
  
 <span data-ttu-id="b101e-106">カスタム バインディングを使用してこれらのセキュリティ設定を適用することにより、WSE 3.0 サービスの要件、および WSE 3.0 サービスと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントとの相互運用性の要件を考慮に入れることができます。</span><span class="sxs-lookup"><span data-stu-id="b101e-106">You can apply these security settings by using a custom binding to take into account the WSE 3.0 service's requirements and the interoperable requirements between a WSE 3.0 service and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="b101e-107">これらの相互運用性要件には、前述の 2004 年 8 月版 WS-Addressing 仕様の使用と、WSE 3.0 の既定のメッセージ保護が <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> であることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b101e-107">These interoperability requirements include the aforementioned use of the August 2004 WS-Addressing specification and the  WSE 3.0default message protection of <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span> <span data-ttu-id="b101e-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の既定のメッセージ保護は、<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。</span><span class="sxs-lookup"><span data-stu-id="b101e-108">The default message protection for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="b101e-109">このトピックでは、WSE 3.0 サービスと相互運用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディングの作成方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="b101e-109">This topic details how to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding that interoperates with a WSE 3.0 service.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b101e-110"> には、このバインディングが組み込まれたサンプルも用意されています。</span><span class="sxs-lookup"><span data-stu-id="b101e-110"> also provides a sample that incorporates this binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b101e-111">このサンプルを参照してください[ASMX Web サービスとの相互運用](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b101e-111"> this sample, see [Interoperating with ASMX Web Services](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md).</span></span>  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a><span data-ttu-id="b101e-112">WCF クライアントで WSE 3.0 サービスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="b101e-112">To access a WSE 3.0 Web service with a WCF client</span></span>  
  
1.  <span data-ttu-id="b101e-113">実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を作成する、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 Web サービスのクライアントです。</span><span class="sxs-lookup"><span data-stu-id="b101e-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="b101e-114">WSE 3.0 Web サービスに対して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b101e-114">For a WSE 3.0 Web service, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is created.</span></span> <span data-ttu-id="b101e-115">WSE 3.0 は MEX プロトコルをサポートしていないため、このツールを使用して Web サービスのセキュリティ要件を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="b101e-115">Because WSE 3.0 does not support the MEX protocol, you cannot use the tool to retrieve the security requirements for the Web service.</span></span> <span data-ttu-id="b101e-116">アプリケーション開発者は、クライアントのセキュリティ設定を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b101e-116">The application developer must add the security settings for the client.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b101e-117">作成する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを参照してください、[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="b101e-117"> creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="b101e-118">WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b101e-118">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="b101e-119">次のクラスの一部である、 [WSE との相互運用](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)サンプル。</span><span class="sxs-lookup"><span data-stu-id="b101e-119">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample:</span></span>  
  
    1.  <span data-ttu-id="b101e-120"><xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b101e-120">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="b101e-121">`WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b101e-121">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="b101e-122">WSE サービスで使用する WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定を指定するプロパティを、このクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="b101e-122">Add properties to the class that specify the WSE turnkey assertion used by the WSE service, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span> <span data-ttu-id="b101e-123">WSE 3.0 では、設定不要アサーションはクライアントまたは Web サービスのセキュリティ要件を指定します。これらのセキュリティ要件は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のバインディングの認証モードに似ています。</span><span class="sxs-lookup"><span data-stu-id="b101e-123">In WSE 3.0, a turnkey assertion specifies the security requirements for a client or Web service—similar to the authentication mode of a binding in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
         <span data-ttu-id="b101e-124">WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定をそれぞれ指定する、`SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext`、および `MessageProtectionOrder` の各プロパティを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b101e-124">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="b101e-125"><xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b101e-125">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="b101e-126">`SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b101e-126">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="b101e-127">クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b101e-127">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="b101e-128">WSE 3.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の設定不要なセキュリティ アサーションで定義されているように、メッセージの保護と認証を使用しなければならない `AnonymousForCertificate` クライアントを指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b101e-128">The following code example specifies that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="b101e-129">また、セキュリティで保護されたセッションと派生キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="b101e-129">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b101e-130">例</span><span class="sxs-lookup"><span data-stu-id="b101e-130">Example</span></span>  
 <span data-ttu-id="b101e-131">WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b101e-131">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="b101e-132">この `WseHttpBinding` という名前のカスタムのバインディングは、WSSecurityAnonymous WSE 3.0 QuickStart のサンプルと通信する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのバインディング プロパティの指定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b101e-132">That custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that communicates with the WSSecurityAnonymous WSE 3.0 QuickStart sample.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="b101e-133">参照</span><span class="sxs-lookup"><span data-stu-id="b101e-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="b101e-134">WSE との相互運用</span><span class="sxs-lookup"><span data-stu-id="b101e-134">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)

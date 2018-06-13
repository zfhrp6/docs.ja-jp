---
title: '方法 : WCF クライアントと WSE3.0 サービスを相互運用するために構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: e30403f9c97f31e93c22a9658ffb74d4d02a49ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490644"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="4f6c7-102">方法 : WCF クライアントと WSE3.0 サービスを相互運用するために構成する</span><span class="sxs-lookup"><span data-stu-id="4f6c7-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="4f6c7-103">Windows Communication Foundation (WCF) クライアントは、WCF クライアントが Ws-addressing 仕様の 2004 年 8 月版を使用して構成されている場合に、Microsoft .NET (WSE) サービスの Web サービス拡張 3.0 とネットワーク レベルで互換性がします。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="4f6c7-104">WSE 3.0 Web サービスと相互運用するように WCF クライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="4f6c7-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1.  <span data-ttu-id="4f6c7-105">実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSE 3.0 Web サービスの WCF クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="4f6c7-106">WSE Web サービス、WCF クライアント クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="4f6c7-107">WCF クライアントを作成する方法については、次を参照してください。、[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-107">For details about creating a WCF client, see the [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="4f6c7-108">WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="4f6c7-109">次のクラスの一部である、 [WSE との相互運用](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-109">The following class is part of the [Interoperating with WSE](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41) sample.</span></span>  
  
    1.  <span data-ttu-id="4f6c7-110"><xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="4f6c7-111">`WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  <span data-ttu-id="4f6c7-112">WSE の設定不要アサーションを指定するクラスに、派生キーが必要か、セキュリティで保護されたセッションが使用されるか、署名の確認が必要かどうかの指定、およびメッセージ保護設定などのプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="4f6c7-113">次のコード例で定義`SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder`WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうかおよびメッセージ保護設定を指定するプロパティそれぞれします。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-113">The following code example defines `SecurityAssertion,``RequireDerivedKeys, EstablishSecurityContext, MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  <span data-ttu-id="4f6c7-114"><xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-114">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="4f6c7-115">`SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-115">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  <span data-ttu-id="4f6c7-116">クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-116">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="4f6c7-117">次のコード例を WCF クライアント必要があります使用するように指定メッセージの保護と認証、WSE 3.0 で定義されている`AnonymousForCertificate`設定不要のセキュリティ アサーションです。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-117">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="4f6c7-118">また、セキュリティで保護されたセッションと派生キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-118">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="4f6c7-119">例</span><span class="sxs-lookup"><span data-stu-id="4f6c7-119">Example</span></span>  
 <span data-ttu-id="4f6c7-120">WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-120">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="4f6c7-121">カスタムのバインディングは、名前は`WseHttpBinding`、WCF クライアントのバインディング プロパティを指定を使用して、します。</span><span class="sxs-lookup"><span data-stu-id="4f6c7-121">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  
  
  
[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="4f6c7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f6c7-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 [<span data-ttu-id="4f6c7-123">WSE との相互運用</span><span class="sxs-lookup"><span data-stu-id="4f6c7-123">Interoperating with WSE</span></span>](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)

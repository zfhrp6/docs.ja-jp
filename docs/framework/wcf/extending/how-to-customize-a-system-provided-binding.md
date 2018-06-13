---
title: '方法 : システム指定のバインディングをカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 04b81689d7d625d519a0a9fc8b1fa6df3df16ada
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803673"
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="811c0-102">方法 : システム指定のバインディングをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="811c0-102">How to: Customize a System-Provided Binding</span></span>
<span data-ttu-id="811c0-103">Windows Communication Foundation (WCF) には、すべてのプロパティでは、基になるバインド要素のプロパティの一部を構成することのいくつかのシステム指定のバインディングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="811c0-103">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="811c0-104">ここでは、バインド要素のプロパティを設定してカスタム バインドを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="811c0-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="811c0-105">直接作成し、システム指定のバインディングを使用せずにバインディング要素を構成する方法の詳細については、次を参照してください。[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="811c0-105">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
 <span data-ttu-id="811c0-106">作成して、カスタム バインディングの拡張の詳細については、次を参照してください。[バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="811c0-106">For more information about creating and extending custom bindings, see [Extending Bindings](../../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
 <span data-ttu-id="811c0-107">WCF でのすべてのバインディングで構成されて*バインド要素*です。</span><span class="sxs-lookup"><span data-stu-id="811c0-107">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="811c0-108">各バインド要素は <xref:System.ServiceModel.Channels.BindingElement> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="811c0-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="811c0-109"><xref:System.ServiceModel.BasicHttpBinding> などのシステム指定のバインディングでは、独自のバインド要素が作成され構成されます。</span><span class="sxs-lookup"><span data-stu-id="811c0-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="811c0-110">ここでは、バインディングに直接公開されないこのバインド要素 (具体的には <xref:System.ServiceModel.BasicHttpBinding> クラス) のプロパティにアクセスして変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="811c0-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="811c0-111">個別のバインド要素は <xref:System.ServiceModel.Channels.BindingElementCollection> クラスで表されるコレクションに格納し、トランザクション フロー、信頼できるセッション、セキュリティ、複合二重、一方向、ストリーム セキュリティ、メッセージ エンコーディング、トランスポートの順に追加します。</span><span class="sxs-lookup"><span data-stu-id="811c0-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="811c0-112">どのバインディングでも、これらすべてのバインド要素が必要になるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="811c0-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="811c0-113">ユーザー定義のバインド要素も、このバインド要素のコレクションに表示されますが、前述の順序で表示される必要があります。</span><span class="sxs-lookup"><span data-stu-id="811c0-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="811c0-114">たとえば、ユーザー定義のトランスポートは、バインド要素コレクションの最後の要素となる必要があります。</span><span class="sxs-lookup"><span data-stu-id="811c0-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="811c0-115"><xref:System.ServiceModel.BasicHttpBinding> クラスには、次の 3 つのバインド要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="811c0-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1.  <span data-ttu-id="811c0-116">オプションのセキュリティ バインド要素。HTTP トランスポートで使用される <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> クラス (メッセージ レベル セキュリティ)、またはトランスポート層がセキュリティを提供する場合 (HTTPS トランスポート) に使用される <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="811c0-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2.  <span data-ttu-id="811c0-117">必須のメッセージ エンコーダー バインド要素。<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> または <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="811c0-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3.  <span data-ttu-id="811c0-118">必須のトランスポート バインド要素。<xref:System.ServiceModel.Channels.HttpTransportBindingElement> または <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="811c0-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="811c0-119">この例で バインドのインスタンスを作成、生成お、*カスタム バインド*、そこから、カスタム バインディング内のバインド要素を確認し、設定、HTTP バインド要素が見つかったときにその`KeepAliveEnabled`プロパティを`false`.</span><span class="sxs-lookup"><span data-stu-id="811c0-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="811c0-120">`KeepAliveEnabled` プロパティは、`BasicHttpBinding` に直接公開されていないので、カスタム バインディングを作成し、バインド要素まで移動して、このプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="811c0-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="811c0-121">システム標準のバインディングを変更するには</span><span class="sxs-lookup"><span data-stu-id="811c0-121">To modify a system-provided binding</span></span>  
  
1.  <span data-ttu-id="811c0-122"><xref:System.ServiceModel.BasicHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードをメッセージ レベルに設定します。</span><span class="sxs-lookup"><span data-stu-id="811c0-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  <span data-ttu-id="811c0-123">バインディングからカスタム バインディングを作成し、そのカスタム バインディングのプロパティの 1 つから <xref:System.ServiceModel.Channels.BindingElementCollection> クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="811c0-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <span data-ttu-id="811c0-124"><xref:System.ServiceModel.Channels.BindingElementCollection> クラスをループして <xref:System.ServiceModel.Channels.HttpTransportBindingElement> クラスが見つかったら、その <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="811c0-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="811c0-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="811c0-125">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="811c0-126">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="811c0-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)

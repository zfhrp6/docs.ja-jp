---
title: "方法 : サービスのメッセージを検査および変更する"
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
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64d9ccf97533be6be0da5d1e23763e8174aead3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="9684a-102">方法 : サービスのメッセージを検査および変更する</span><span class="sxs-lookup"><span data-stu-id="9684a-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="9684a-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を実装し、それをサービス ランタイムに挿入することで、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> クライアントの送受信メッセージを検査または変更できます。</span><span class="sxs-lookup"><span data-stu-id="9684a-103">You can inspect or modify the incoming or outgoing messages across a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="9684a-104">詳細については、次を参照してください。[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)です。</span><span class="sxs-lookup"><span data-stu-id="9684a-104">For more information, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span> <span data-ttu-id="9684a-105">サービスの同等の機能は、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="9684a-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="9684a-106">メッセージを検査または変更するには</span><span class="sxs-lookup"><span data-stu-id="9684a-106">To inspect or modify messages</span></span>  
  
1.  <span data-ttu-id="9684a-107"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="9684a-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="9684a-108">サービス メッセージ インスペクターを容易に挿入したいスコープに応じて、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="9684a-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3.  <span data-ttu-id="9684a-109"><xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> で <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9684a-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9684a-110">詳細については、「[を構成して、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="9684a-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9684a-111">例</span><span class="sxs-lookup"><span data-stu-id="9684a-111">Example</span></span>  
 <span data-ttu-id="9684a-112">下のコード例では、次の項目を順番に示しています。</span><span class="sxs-lookup"><span data-stu-id="9684a-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="9684a-113">サービス インスペクターの実装</span><span class="sxs-lookup"><span data-stu-id="9684a-113">A service inspector implementation.</span></span>  
  
-   <span data-ttu-id="9684a-114">インスペクターを挿入するサービス動作</span><span class="sxs-lookup"><span data-stu-id="9684a-114">A service behavior that inserts the inspector.</span></span>  
  
-   <span data-ttu-id="9684a-115">サービス アプリケーションに動作を読み込んで実行する構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9684a-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9684a-116">参照</span><span class="sxs-lookup"><span data-stu-id="9684a-116">See Also</span></span>  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>  
 [<span data-ttu-id="9684a-117">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="9684a-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

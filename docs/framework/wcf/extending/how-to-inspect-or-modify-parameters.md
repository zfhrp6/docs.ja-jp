---
title: '方法 : パラメーターを検査または変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 1b825ff795f4db9d570420b187b8fedd041ddd3d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="05b2b-102">方法 : パラメーターを検査または変更する</span><span class="sxs-lookup"><span data-stu-id="05b2b-102">How to: Inspect or Modify Parameters</span></span>
<span data-ttu-id="05b2b-103">検査または実装することによって、Windows Communication Foundation (WCF) クライアント オブジェクトまたは WCF サービスの単一操作による受信または送信メッセージを変更することができます、<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>インターフェイスと、クライアントまたはサービス ランタイムに挿入します。</span><span class="sxs-lookup"><span data-stu-id="05b2b-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="05b2b-104">通常、操作の動作は、1 回の操作に対してパラメーター インスペクターを追加するために使用します。他の動作は、広い範囲でランタイムへの簡単なアクセスを提供するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="05b2b-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="05b2b-105">詳細については、次を参照してください。[を拡張するクライアント](../../../../docs/framework/wcf/extending/extending-clients.md)と[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)です。</span><span class="sxs-lookup"><span data-stu-id="05b2b-105">For more information, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md) and [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="05b2b-106">パラメーターの検査と変更</span><span class="sxs-lookup"><span data-stu-id="05b2b-106">Inspecting or Modifying Parameters</span></span>  
  
1.  <span data-ttu-id="05b2b-107"><xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="05b2b-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2.  <span data-ttu-id="05b2b-108">要求されるスコープに応じて <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> を実装し、パラメーター インスペクターを <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="05b2b-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3.  <span data-ttu-id="05b2b-109"><xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> に対して <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> メソッドまたは <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> メソッドを呼び出す前に、動作を挿入します。</span><span class="sxs-lookup"><span data-stu-id="05b2b-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="05b2b-110">詳細については、「[を構成して、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="05b2b-110">For details, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b2b-111">例</span><span class="sxs-lookup"><span data-stu-id="05b2b-111">Example</span></span>  
 <span data-ttu-id="05b2b-112">下のコード例では、次の項目を順番に示しています。</span><span class="sxs-lookup"><span data-stu-id="05b2b-112">The following code examples show, in order:</span></span>  
  
-   <span data-ttu-id="05b2b-113">パラメーター インスペクターの実装</span><span class="sxs-lookup"><span data-stu-id="05b2b-113">A parameter inspector implementation.</span></span>  
  
-   <span data-ttu-id="05b2b-114"><xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>、および <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> を使用してパラメーター インスペクターを挿入する動作実装</span><span class="sxs-lookup"><span data-stu-id="05b2b-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="05b2b-115">クライアント上にパラメーター インスペクターを挿入するために、クライアント アプリケーションでエンドポイント動作を読み込み、実行する構成ファイル</span><span class="sxs-lookup"><span data-stu-id="05b2b-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="05b2b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="05b2b-116">See Also</span></span>  
 [<span data-ttu-id="05b2b-117">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="05b2b-117">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

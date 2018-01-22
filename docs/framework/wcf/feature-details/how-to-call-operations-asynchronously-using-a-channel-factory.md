---
title: "方法 : チャネル ファクトリを使用して、非同期的に操作を呼び出す"
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
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 216c0d529a15004ea9f7d6f087aeee4bf4f10e56
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="5ca13-102">方法 : チャネル ファクトリを使用して、非同期的に操作を呼び出す</span><span class="sxs-lookup"><span data-stu-id="5ca13-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="5ca13-103">ここでは、<xref:System.ServiceModel.ChannelFactory%601> ベースのクライアント アプリケーションを使用する場合に、クライアントからサービス操作に非同期にアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="5ca13-104">サービスを呼び出すために <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> オブジェクトを使用する場合は、イベント ドリブンの非同期呼び出しモデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ca13-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="5ca13-105">詳細については、次を参照してください。[する方法: サービスの操作を非同期に呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ca13-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="5ca13-106">イベント ベースの非同期呼び出しモデルについての詳細については、次を参照してください[イベント ベースの非同期パターンを使用したマルチ スレッド プログラミング](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)。)。</span><span class="sxs-lookup"><span data-stu-id="5ca13-106">For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span></span>  
  
 <span data-ttu-id="5ca13-107">このトピックのサービスは、`ICalculator` インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="5ca13-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="5ca13-108">クライアントはこのインターフェイスにある操作を非同期に呼び出すことができます。これはたとえば `Add` という操作を `BeginAdd` と `EndAdd` の 2 つのメソッドに分割できることを意味します。前者によって呼び出しを開始し、後者によって操作の完了時に結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="5ca13-109">例については、サービスに非同期的に操作を実装する方法を示す、次を参照してください。[する方法: 非同期サービス操作を実装する](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ca13-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="5ca13-110">同期および非同期の操作に関する詳細については、「[同期と非同期の操作](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ca13-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="5ca13-111">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="5ca13-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="5ca13-112">WCF サービス操作を非同期に呼び出すには</span><span class="sxs-lookup"><span data-stu-id="5ca13-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="5ca13-113">実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールを`/async`オプションを次のコマンドに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="5ca13-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="5ca13-114">これにより、操作の非同期クライアント版のサービス コントラクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5ca13-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="5ca13-115">次のサンプル コードに示すように、非同期操作の完了時に呼び出されるコールバック関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="5ca13-116">サービス操作に非同期にアクセスするには、次のサンプル コードに示すように、クライアントを作成して `Begin[Operation]` (たとえば `BeginAdd`) を呼び出し、コールバック関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="5ca13-117">コールバック関数が実行されると、クライアントは `End<operation>` (`EndAdd` など) を呼び出して結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ca13-118">例</span><span class="sxs-lookup"><span data-stu-id="5ca13-118">Example</span></span>  
 <span data-ttu-id="5ca13-119">上記の手順で使用したクライアント コードで使用するサービスは、次のコードに示すように `ICalculator` インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="5ca13-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="5ca13-120">コントラクトの `Add` 操作と `Subtract` 操作は、上記のクライアントの手順がクライアントで非同期に呼び出される場合でも、サービス側では [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のランタイムにより同期して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5ca13-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="5ca13-121">`Multiply` 操作と `Divide` 操作は、クライアントで同期して呼び出される場合でも、サービス側ではサービスを非同期に呼び出すように使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ca13-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="5ca13-122">この例では、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="5ca13-123">このプロパティ設定は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 非同期パターンの実装と共に、ランタイムに対して、操作を非同期で呼び出すよう指示します。</span><span class="sxs-lookup"><span data-stu-id="5ca13-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5ca13-124">参照</span><span class="sxs-lookup"><span data-stu-id="5ca13-124">See Also</span></span>  
 [<span data-ttu-id="5ca13-125">サービス コントラクト: 非同期のサンプル</span><span class="sxs-lookup"><span data-stu-id="5ca13-125">Service Contract: Asynchronous Sample</span></span>](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)

---
title: "方法 : WCF サービス操作を非同期に呼び出す"
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
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f8f1419deb60b1f68e47c26c0edd5523a9d23768
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="ebaac-102">方法 : WCF サービス操作を非同期に呼び出す</span><span class="sxs-lookup"><span data-stu-id="ebaac-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="ebaac-103">ここでは、クライアントからサービス操作に非同期にアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebaac-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="ebaac-104">このトピックのサービスは、`ICalculator` インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="ebaac-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="ebaac-105">クライアントは、イベント ドリブンの非同期呼び出しモデルを使用して、このインターフェイスで操作を非同期に呼び出すことができます </span><span class="sxs-lookup"><span data-stu-id="ebaac-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="ebaac-106">(イベント ベースの非同期呼び出しモデルについての詳細については、次を参照してください。[イベント ベースの非同期パターンを使用したマルチ スレッド プログラミング](http://go.microsoft.com/fwlink/?LinkId=248184))。</span><span class="sxs-lookup"><span data-stu-id="ebaac-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="ebaac-107">例については、サービスに非同期的に操作を実装する方法を示す、次を参照してください。[する方法: 非同期サービス操作を実装する](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="ebaac-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="ebaac-108">同期および非同期の操作の詳細については、次を参照してください。[同期と非同期の操作](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="ebaac-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebaac-109"><xref:System.ServiceModel.ChannelFactory%601> を使用している場合、イベント ドリブンの非同期呼び出しモデルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ebaac-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="ebaac-110">使用して非同期呼び出しを行う方法について、<xref:System.ServiceModel.ChannelFactory%601>を参照してください[する方法: 呼び出し操作に非同期的を使用して、チャネル ファクトリ](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)です。</span><span class="sxs-lookup"><span data-stu-id="ebaac-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ebaac-111">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ebaac-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="ebaac-112">WCF サービス操作を非同期に呼び出すには</span><span class="sxs-lookup"><span data-stu-id="ebaac-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="ebaac-113">実行、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)両方を持つツール、`/async`と`/tcv:Version35`次のコマンドに示すように、このコマンド オプションを一緒にします。</span><span class="sxs-lookup"><span data-stu-id="ebaac-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="ebaac-114">これにより、同期操作と標準のデリゲート ベースの非同期操作だけでなく、以下を含む [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスも生成されます。</span><span class="sxs-lookup"><span data-stu-id="ebaac-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class that contains:</span></span>  
  
    -   <span data-ttu-id="ebaac-115">2 つ <`operationName` > `Async` -イベント ベースの非同期呼び出し方法で使用するための操作です。</span><span class="sxs-lookup"><span data-stu-id="ebaac-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="ebaac-116">例:</span><span class="sxs-lookup"><span data-stu-id="ebaac-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="ebaac-117">フォームの操作が完了しましたイベント <`operationName` > `Completed` -イベント ベースの非同期呼び出し方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="ebaac-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="ebaac-118">例:</span><span class="sxs-lookup"><span data-stu-id="ebaac-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <span data-ttu-id="ebaac-119"><xref:System.EventArgs?displayProperty=nameWithType>各操作の種類 (形式の <`operationName`>`CompletedEventArgs`) - イベント ベースの非同期呼び出し方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="ebaac-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="ebaac-120">例:</span><span class="sxs-lookup"><span data-stu-id="ebaac-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="ebaac-121">次のサンプル コードに示すように、呼び出し元アプリケーションで、非同期操作の完了時に呼び出されるコールバック メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="ebaac-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="ebaac-122">操作を呼び出す前に、新しいジェネリックを使用して<xref:System.EventHandler%601?displayProperty=nameWithType>型の <`operationName` > `EventArgs` (前の手順で作成された) ハンドラー メソッドを追加する、<`operationName` > `Completed`イベント。</span><span class="sxs-lookup"><span data-stu-id="ebaac-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="ebaac-123">まず、<`operationName` > `Async`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ebaac-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="ebaac-124">例:</span><span class="sxs-lookup"><span data-stu-id="ebaac-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ebaac-125">例</span><span class="sxs-lookup"><span data-stu-id="ebaac-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebaac-126">イベント ベースの非同期モデルのデザイン ガイドラインには、複数の値を返す場合に、1 つの値を `Result` プロパティとして返し、残りの値を <xref:System.EventArgs> オブジェクトのプロパティとして返すことが記載されています。</span><span class="sxs-lookup"><span data-stu-id="ebaac-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ebaac-127">この 1 つの結果として、クライアントがイベント ベースの非同期コマンド オプションを使用してメタデータをインポートし、操作から複数の値が返される場合、既定の <xref:System.EventArgs> オブジェクトが 1 つの値を `Result` プロパティとして返し、残りの値は <xref:System.EventArgs> オブジェクトのプロパティになります。メッセージ オブジェクトを `Result` プロパティとして受け取り、返された値をそのオブジェクトのプロパティとして取得する場合は、`/messageContract` コマンド オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ebaac-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="ebaac-128">これにより、`Result` オブジェクトの <xref:System.EventArgs> プロパティとして応答メッセージを返すシグネチャが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ebaac-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ebaac-129">すべての内部戻り値は、応答メッセージ オブジェクトのプロパティになります。</span><span class="sxs-lookup"><span data-stu-id="ebaac-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ebaac-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebaac-130">See Also</span></span>  
 [<span data-ttu-id="ebaac-131">方法: 非同期サービス操作を実装する</span><span class="sxs-lookup"><span data-stu-id="ebaac-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)

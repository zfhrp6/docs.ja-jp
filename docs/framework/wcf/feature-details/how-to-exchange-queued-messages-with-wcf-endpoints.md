---
title: "方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b52fe96bc88f09b807640dedcc54a8468dc26e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="b1f9f-102">方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="b1f9f-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="b1f9f-103">キューを使用すると、通信中にサービスを使用できない場合でも、クライアントと [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス間で信頼できるメッセージングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-103">Queues ensure that reliable messaging can occur between a client and a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="b1f9f-104">以下の手順は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装時に、標準のキューに置かれたバインディングを使用してクライアントとサービス間で永続的な通信を確保する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="b1f9f-105">ここでは、<xref:System.ServiceModel.NetMsmqBinding> を使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス間でキューによる通信を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="b1f9f-106">WCF サービスでキューを使用するには</span><span class="sxs-lookup"><span data-stu-id="b1f9f-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="b1f9f-107"><xref:System.ServiceModel.ServiceContractAttribute> でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="b1f9f-108">サービス コントラクトの一部であるインターフェイスの動作を <xref:System.ServiceModel.OperationContractAttribute> でマークし、メソッドに対して応答が返されないため、一方向と指定します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="b1f9f-109">サービス コントラクトおよびその操作の定義の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="b1f9f-110">サービス コントラクトがユーザー定義型を渡す場合は、その型のデータ コントラクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="b1f9f-111">次のコードは、2 つのデータ コントラクト (`PurchaseOrder` および `PurchaseOrderLineItem`) を示します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="b1f9f-112">これらの 2 つの型は、サービスに送信されるデータを定義します </span><span class="sxs-lookup"><span data-stu-id="b1f9f-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="b1f9f-113">(このデータ コントラクトを定義するクラスによって多数のメソッドが定義されることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="b1f9f-114">これらのメソッドは、データ コントラクトの一部とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="b1f9f-115">`DataMember` 属性で宣言されているメンバーだけがデータ コントラクトに含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="b1f9f-116">インターフェイスで定義したサービス コントラクトのメソッドをクラスに実装します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="b1f9f-117"><xref:System.ServiceModel.OperationBehaviorAttribute> メソッド上の `SubmitPurchaseOrder` に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="b1f9f-118">これは、トランザクション内でこの操作を呼び出す必要があること、およびメソッドが完了したときにトランザクションが自動的に完了することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="b1f9f-119"><xref:System.Messaging> を使用してトランザクション キューを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="b1f9f-120">代わりに、MSMQ (Microsoft Message Queuing) Microsoft 管理コンソール (MMC: Microsoft Management Console) を使用してキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="b1f9f-121">その場合は、トランザクション キューを作成してください。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="b1f9f-122">サービス アドレスを指定し、標準の <xref:System.ServiceModel.Description.ServiceEndpoint> バインディングを使用する <xref:System.ServiceModel.NetMsmqBinding> を構成で定義します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b1f9f-123">使用して[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]構成を参照してください[Windows Communication Foundation アプリケーションを構成する](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)です。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-123"> using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="b1f9f-124">`OrderProcessing` を使用して、キューからメッセージを読み取って処理する <xref:System.ServiceModel.ServiceHost> サービスのホストを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="b1f9f-125">サービス ホストを開いてサービスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-125">Open the service host to make the service available.</span></span> <span data-ttu-id="b1f9f-126">任意のキーを押してサービスを終了するようユーザーに伝えるメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="b1f9f-127">`ReadLine` を呼び出して、キーが押されるまで待機してサービスを終了します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="b1f9f-128">キューに置かれたサービスのクライアントを作成するには</span><span class="sxs-lookup"><span data-stu-id="b1f9f-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="b1f9f-129">次の例は、ホスト アプリケーションを実行し、Svcutil.exe ツールを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="b1f9f-130">次の例に示すように、アドレスを指定し、標準の <xref:System.ServiceModel.Description.ServiceEndpoint> バインディングを使用する <xref:System.ServiceModel.NetMsmqBinding> を構成で定義します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="b1f9f-131">次の例に示すように、トランザクション キューに書き込むトランザクション スコープを作成し、`SubmitPurchaseOrder` 操作を呼び出して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b1f9f-132">例</span><span class="sxs-lookup"><span data-stu-id="b1f9f-132">Example</span></span>  
 <span data-ttu-id="b1f9f-133">次の例は、この例に含まれるサービス コード、ホスト アプリケーション、App.config ファイル、およびクライアント コードを示します。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="b1f9f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1f9f-134">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [<span data-ttu-id="b1f9f-135">トランザクション MSMQ バインディング</span><span class="sxs-lookup"><span data-stu-id="b1f9f-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [<span data-ttu-id="b1f9f-136">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="b1f9f-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="b1f9f-137">方法: WCF エンドポイントでメッセージを交換して、メッセージ キュー アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b1f9f-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="b1f9f-138">メッセージ キューへの Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b1f9f-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="b1f9f-139">メッセージ キュー (MSMQ) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b1f9f-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="b1f9f-140">メッセージ キュー統合バインディングのサンプル</span><span class="sxs-lookup"><span data-stu-id="b1f9f-140">Message Queuing Integration Binding Samples</span></span>](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [<span data-ttu-id="b1f9f-141">Windows Communication foundation キュー メッセージ</span><span class="sxs-lookup"><span data-stu-id="b1f9f-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="b1f9f-142">メッセージ キューを介したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b1f9f-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)

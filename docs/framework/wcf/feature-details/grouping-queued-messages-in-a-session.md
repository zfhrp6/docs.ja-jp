---
title: "セッションでキューに置かれたメッセージのグループ化"
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
helpviewer_keywords: queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aba045456d61b5ad687f1030dca3c26b083cdb58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="25e0d-102">セッションでキューに置かれたメッセージのグループ化</span><span class="sxs-lookup"><span data-stu-id="25e0d-102">Grouping Queued Messages in a Session</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="25e0d-103"> には、単一の受信側アプリケーションで処理できるよう、一連の関連メッセージをグループ化するセッションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="25e0d-103"> provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="25e0d-104">セッションに含まれるメッセージは、同じトランザクションに含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="25e0d-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="25e0d-105">すべてのメッセージが同じトランザクションに含まれるため、1 つのメッセージの処理が失敗すると、セッション全体がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="25e0d-106">各セッションは、配信不能キューや有害キューに関してよく似た動作をします。</span><span class="sxs-lookup"><span data-stu-id="25e0d-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="25e0d-107">キューに置かれたバインディングに設定される有効期間 (TTL: Time To Live) プロパティがセッションに構成されている場合は、セッション全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="25e0d-108">したがって、TTL が切れる前にセッション内の一部のメッセージが送信された場合は、セッション全体が配信不能キューに配置されます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="25e0d-109">同様に、アプリケーション キューからアプリケーションにセッション内のメッセージを送信できなかった場合は、セッション全体が有害キューに配置されます (有害キューを使用できる場合)。</span><span class="sxs-lookup"><span data-stu-id="25e0d-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="25e0d-110">メッセージのグループ化の例</span><span class="sxs-lookup"><span data-stu-id="25e0d-110">Message Grouping Example</span></span>  
 <span data-ttu-id="25e0d-111">メッセージのグループ化が役立つ 1 つの例は、注文処理アプリケーションを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスとして実装する場合です。</span><span class="sxs-lookup"><span data-stu-id="25e0d-111">One example where grouping messages is helpful is when implementing an order-processing application as a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="25e0d-112">たとえば、クライアントがこのアプリケーションに多数の項目を含む注文を送信するとします。</span><span class="sxs-lookup"><span data-stu-id="25e0d-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="25e0d-113">このクライアントは、項目ごとにサービスを呼び出すため、個別のメッセージが送信されることになります。</span><span class="sxs-lookup"><span data-stu-id="25e0d-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="25e0d-114">このため、最初の項目はサーバー A で受信され、2 番目の項目はサーバー B で受信される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="25e0d-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="25e0d-115">項目が追加されるたびに、この項目を処理するサーバーは適切な注文を見つけて項目を追加する必要があるため、効率が非常に悪くなります。</span><span class="sxs-lookup"><span data-stu-id="25e0d-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="25e0d-116">すべての要求を 1 台のサーバーのみで処理する場合でも、現在処理中のすべての注文をこのサーバーによって常に把握し、新しい項目がどの注文に属するものなのかを判別する必要があるため、同様の非効率が生じます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="25e0d-117">単一の注文に属するすべての要求をグループ化すると、このようなアプリケーションの実装は大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="25e0d-118">1 つの注文に属するすべての項目が 1 セッションとしてクライアント アプリケーションから送信されるため、サービスは注文を処理するときにセッション全体を 1 回で処理できます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="25e0d-119">手順</span><span class="sxs-lookup"><span data-stu-id="25e0d-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="25e0d-120">セッションを使用するようにサービス コントラクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="25e0d-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="25e0d-121">セッションを必要とするサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="25e0d-122">これを実行するには、<xref:System.ServiceModel.OperationContractAttribute> 属性に次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="25e0d-123">これらのメソッドは何も返さないため、コントラクト内の操作を一方向としてマークします。</span><span class="sxs-lookup"><span data-stu-id="25e0d-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="25e0d-124">これを実行するには、<xref:System.ServiceModel.OperationContractAttribute> 属性に次の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="25e0d-125">サービス コントラクトを実装し、`InstanceContextMode` に `PerSession` を指定します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="25e0d-126">これにより、セッションごとに 1 回だけサービスがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="25e0d-127">各サービス操作には、トランザクションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="25e0d-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="25e0d-128">これを指定するには <xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="25e0d-129">トランザクションを完了する操作では、`TransactionAutoComplete` を `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25e0d-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="25e0d-130">システム指定の `NetMsmqBinding` バインディングを使用するエンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="25e0d-131"><xref:System.Messaging> を使用してトランザクション キューを作成します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="25e0d-132">代わりに、MSMQ (メッセージ キュー) または MMC を使用してキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="25e0d-133">この場合、トランザクション キューを作成します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="25e0d-134"><xref:System.ServiceModel.ServiceHost> を使用して、サービスのサービス ホストを作成します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="25e0d-135">サービス ホストを開いてサービスを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="25e0d-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="25e0d-136">サービス ホストを閉じます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="25e0d-137">クライアントを設定するには</span><span class="sxs-lookup"><span data-stu-id="25e0d-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="25e0d-138">トランザクションのスコープを作成してトランザクション キューに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="25e0d-139">作成、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールです。</span><span class="sxs-lookup"><span data-stu-id="25e0d-139">Create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="25e0d-140">注文を行います。</span><span class="sxs-lookup"><span data-stu-id="25e0d-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="25e0d-141">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを閉じます。</span><span class="sxs-lookup"><span data-stu-id="25e0d-141">Close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25e0d-142">例</span><span class="sxs-lookup"><span data-stu-id="25e0d-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="25e0d-143">説明</span><span class="sxs-lookup"><span data-stu-id="25e0d-143">Description</span></span>  
 <span data-ttu-id="25e0d-144">次の例では、`IProcessOrder` サービス、およびこのサービスを使用するクライアントのコードを示します。</span><span class="sxs-lookup"><span data-stu-id="25e0d-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="25e0d-145">このコードは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が、キューに置かれたセッションを使用して動作をグループ化するしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="25e0d-145">It shows how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="25e0d-146">サービスのコード</span><span class="sxs-lookup"><span data-stu-id="25e0d-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="25e0d-147">クライアントのコード</span><span class="sxs-lookup"><span data-stu-id="25e0d-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="25e0d-148">参照</span><span class="sxs-lookup"><span data-stu-id="25e0d-148">See Also</span></span>  
 [<span data-ttu-id="25e0d-149">セッションとキュー</span><span class="sxs-lookup"><span data-stu-id="25e0d-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [<span data-ttu-id="25e0d-150">キューの概要</span><span class="sxs-lookup"><span data-stu-id="25e0d-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)

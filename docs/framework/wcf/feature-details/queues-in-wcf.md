---
title: "Windows Communication Foundation のキュー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfc78d355db4bd8c9d43541545e6fac35086b39
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="queues-in-windows-communication-foundation"></a><span data-ttu-id="6e4ef-102">Windows Communication Foundation のキュー</span><span class="sxs-lookup"><span data-stu-id="6e4ef-102">Queues in Windows Communication Foundation</span></span>
<span data-ttu-id="6e4ef-103">このセクションの各トピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でのキューのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-103">The topics in this section discuss [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for queues.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6e4ef-104"> では、Microsoft Message Queuing (以前の MSMQ) をトランスポートとして利用することによってキューをサポートしており、次のシナリオを実現できます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-104"> provides support for queuing by leveraging Microsoft Message Queuing (previously known as MSMQ) as a transport and enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="6e4ef-105">疎結合アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-105">Loosely coupled applications.</span></span> <span data-ttu-id="6e4ef-106">送信元アプリケーションは、受信側アプリケーションでメッセージ処理の用意ができているかどうかを確認せずにキューにメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-106">Sending applications can send messages to queues without needing to know whether the receiving application is available to process the message.</span></span> <span data-ttu-id="6e4ef-107">キューにより処理の独立性が提供されるため、送信元アプリケーションは、受信側アプリケーションのメッセージ処理速度とは関係なく、キューにメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-107">The queue provides processing independence that allows a sending application to send messages to the queue at a rate that does not depend on how fast the receiving applications can process the messages.</span></span> <span data-ttu-id="6e4ef-108">キューに対するメッセージの送信がメッセージ処理と密接に結び付けられていない場合は、システムの全体的な可用性が向上します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-108">Overall system availability increases when sending messages to a queue is not tightly coupled to message processing.</span></span>  
  
-   <span data-ttu-id="6e4ef-109">エラーの分離。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-109">Failure isolation.</span></span> <span data-ttu-id="6e4ef-110">キューにメッセージを送受信するアプリケーションは、互いに影響を与えずにエラーを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-110">Applications sending or receiving messages to a queue can fail without affecting each other.</span></span> <span data-ttu-id="6e4ef-111">たとえば、受信側のアプリケーションでエラーが発生しても、送信側のアプリケーションではメッセージをキューに送信し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-111">If, for example, the receiving application fails, the sending application can continue to send messages to the queue.</span></span> <span data-ttu-id="6e4ef-112">受信側は、エラーからの復帰後、キューにあるメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-112">When the receiver is up again, it can process the messages from the queue.</span></span> <span data-ttu-id="6e4ef-113">エラーの分離により、システムの全体的な信頼性と可用性が向上します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-113">Failure isolation increases the overall system reliability and availability.</span></span>  
  
-   <span data-ttu-id="6e4ef-114">負荷の平準化。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-114">Load leveling.</span></span> <span data-ttu-id="6e4ef-115">送信元アプリケーションから送信するメッセージが多すぎるために、受信側アプリケーションの処理が間に合わなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-115">Sending applications can overwhelm receiving applications with messages.</span></span> <span data-ttu-id="6e4ef-116">キューによってこの送信側と受信側のメッセージの不均衡が調整されるため、受信側の処理が間に合わなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-116">Queues can manage mismatched message production and consumption rates so that a receiver is not overwhelmed.</span></span>  
  
-   <span data-ttu-id="6e4ef-117">操作の切断。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-117">Disconnected operations.</span></span> <span data-ttu-id="6e4ef-118">モバイル デバイスのように遅延の大きなネットワーク、または可用性に制限のあるネットワークを介して通信を行う場合に、送信、受信、および処理の各操作を切断できます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-118">Sending, receiving, and processing operations can become disconnected when communicating over high-latency networks or limited-availability networks, such as in the case of mobile devices.</span></span> <span data-ttu-id="6e4ef-119">エンドポイントが切断された場合も、キューによってこれらの操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-119">Queues allow these operations to continue, even when the endpoints are disconnected.</span></span> <span data-ttu-id="6e4ef-120">接続が再度確立されると、メッセージはキューから受信側アプリケーションに転送されます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-120">When the connection is reestablished, the queue forwards messages to the receiving application.</span></span>  
  
 <span data-ttu-id="6e4ef-121">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションでキューの機能を使用する場合は、標準バインディングのいずれかを使用できます。また、標準バインディングでは要件が満たされない場合には、カスタム バインディングを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-121">To use the queues feature in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, you can use one of the standard bindings, or you can create a custom binding if one of the standard bindings does not satisfy your requirements.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6e4ef-122">関連する標準バインドと、1 つを選択する方法を参照してください。[する方法: WCF エンドポイントとメッセージ キュー アプリケーションとメッセージを交換](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-122"> relevant standard bindings and how to choose one, see [How to: Exchange Messages with WCF Endpoints and Message Queuing Applications](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6e4ef-123">カスタム バインディングを作成するを参照してください[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-123"> creating custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e4ef-124">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6e4ef-124">In This Section</span></span>  
 [<span data-ttu-id="6e4ef-125">キューの概要</span><span class="sxs-lookup"><span data-stu-id="6e4ef-125">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 <span data-ttu-id="6e4ef-126">メッセージ キュー概念について概要を示します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-126">An overview of message queuing concepts.</span></span>  
  
 [<span data-ttu-id="6e4ef-127">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="6e4ef-127">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 <span data-ttu-id="6e4ef-128">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によるキューのサポートの概要です。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-128">An overview of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queue support.</span></span>  
  
 [<span data-ttu-id="6e4ef-129">方法 : WCF エンドポイントを使用してキューに置かれたメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="6e4ef-129">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 <span data-ttu-id="6e4ef-130"><xref:System.ServiceModel.NetMsmqBinding> クラスを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス間で通信を行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-130">Explains how to use the <xref:System.ServiceModel.NetMsmqBinding> class to communicate between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="6e4ef-131">方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="6e4ef-131">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 <span data-ttu-id="6e4ef-132"><xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションとメッセージ キュー アプリケーション間で通信を行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-132">Explains how to use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> to communicate between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Message Queuing applications.</span></span>  
  
 [<span data-ttu-id="6e4ef-133">セッションでキューに置かれたメッセージのグループ化</span><span class="sxs-lookup"><span data-stu-id="6e4ef-133">Grouping Queued Messages in a Session</span></span>](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 <span data-ttu-id="6e4ef-134">単一の受信側アプリケーションが関連メッセージを迅速に処理できるように、キューでメッセージをグループ化する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-134">Explains how to group messages in a queue to facilitate correlated message processing by a single receiving application.</span></span>  
  
 [<span data-ttu-id="6e4ef-135">トランザクションに含まれるメッセージのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="6e4ef-135">Batching Messages in a Transaction</span></span>](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 <span data-ttu-id="6e4ef-136">トランザクションでメッセージをバッチ処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-136">Explains how to batch messages in a transaction.</span></span>  
  
 [<span data-ttu-id="6e4ef-137">配信不能キューを使用したメッセージ転送エラー処理</span><span class="sxs-lookup"><span data-stu-id="6e4ef-137">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 <span data-ttu-id="6e4ef-138">配信不能キューを使用してメッセージの転送エラーと配信エラーを処理する方法、および配信不能キューのメッセージを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-138">Explains how to handle message transfer and delivery failures using dead letter queues and how to process messages from the dead letter queue.</span></span>  
  
 [<span data-ttu-id="6e4ef-139">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="6e4ef-139">Poison Message Handling</span></span>](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 <span data-ttu-id="6e4ef-140">有害メッセージ (受信側アプリケーションへの配信試行の回数が最大値を超えたメッセージ) の処理方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-140">Explains how to handle poison messages (messages that have exceeded the maximum number of delivery attempts to the receiving application).</span></span>  
  
 [<span data-ttu-id="6e4ef-141">Windows Vista、Windows Server 2003、および Windows XP におけるキュー機能の相違点</span><span class="sxs-lookup"><span data-stu-id="6e4ef-141">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 <span data-ttu-id="6e4ef-142">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、[!INCLUDE[wv](../../../../includes/wv-md.md)]、および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] における [!INCLUDE[wxp](../../../../includes/wxp-md.md)] キュー機能の相違についてまとめています。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-142">Summarizes the differences in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queues feature between [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
 [<span data-ttu-id="6e4ef-143">トランスポート セキュリティを使用したメッセージのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6e4ef-143">Securing Messages Using Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 <span data-ttu-id="6e4ef-144">トランスポート セキュリティを使用して、キューに置かれたメッセージを保護する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-144">Describes how to use transport security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="6e4ef-145">メッセージ セキュリティを使用したメッセージのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6e4ef-145">Securing Messages Using Message Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 <span data-ttu-id="6e4ef-146">メッセージ セキュリティを使用して、キューに置かれたメッセージを保護する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-146">Describes how to use message security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="6e4ef-147">キューに置かれたメッセージングのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6e4ef-147">Troubleshooting Queued Messaging</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 <span data-ttu-id="6e4ef-148">一般的なキューの問題をトラブルシューティングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-148">Explains how to troubleshoot common queuing problems.</span></span>  
  
 [<span data-ttu-id="6e4ef-149">キューに置かれた通信のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6e4ef-149">Best Practices for Queued Communication</span></span>](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 <span data-ttu-id="6e4ef-150">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキューを使用した通信のベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6e4ef-150">Explains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queued communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4ef-151">参照</span><span class="sxs-lookup"><span data-stu-id="6e4ef-151">See Also</span></span>  
 [<span data-ttu-id="6e4ef-152">メッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="6e4ef-152">Message Queuing</span></span>](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)

---
title: "方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する"
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
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d09b8e662b2876fa5d5c5246ea7e7a4998cde9ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="6c710-102">方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="6c710-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="6c710-103">既存の MSMQ アプリケーションを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションと統合できます。それには、メッセージ キュー (MSMQ) 統合バインディングを使用して MSMQ メッセージを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージとの間で相互に変換できます。</span><span class="sxs-lookup"><span data-stu-id="6c710-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="6c710-104">これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントから MSMQ の受信側アプリケーションを呼び出したり、MSMQ の送信元アプリケーションから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを呼び出したりできます。</span><span class="sxs-lookup"><span data-stu-id="6c710-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="6c710-105">ここでは、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を使用して、(1) System.Messaging を使用して記述された MSMQ アプリケーション サービスと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの間および (2) MSMQ アプリケーション クライアントと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの間で、キュー通信を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c710-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="6c710-106">MSMQ 受信側のアプリケーションを呼び出す方法を説明する完全なサンプルについては、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントを参照してください、[メッセージ キューへの Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="6c710-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="6c710-107">呼び出す方法を示す完全なサンプルについては、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ クライアントからサービスを参照してください、[メッセージ キューが Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="6c710-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="6c710-108">MSMQ クライアントからのメッセージを受信する WCF サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="6c710-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="6c710-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのサービス コントラクトを定義するインターフェイスを、次のコード例に示すように定義します。このサービスは、MSMQ の送信元アプリケーションからキューに置かれたメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="6c710-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="6c710-110">次のコード例に示すように、定義したインターフェイスを実装し、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をクラスに適用します。</span><span class="sxs-lookup"><span data-stu-id="6c710-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="6c710-111"><xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を指定する構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6c710-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="6c710-112">構成されたバインディングを使用する <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6c710-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="6c710-113">MSMQ の受信側アプリケーションにメッセージを送信する WCF クライアントを作成するには</span><span class="sxs-lookup"><span data-stu-id="6c710-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="6c710-114">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのサービス コントラクトを定義するインターフェイスを、次のコード例に示すように定義します。このクライアントは、キューに置かれたメッセージを MSMQ の受信側に送信します。</span><span class="sxs-lookup"><span data-stu-id="6c710-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="6c710-115">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントが MSMQ の受信側を呼び出すために使用するクライアント クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="6c710-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="6c710-116">MsmqIntegrationBinding バインディングの使用を指定する構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="6c710-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="6c710-117">クライアント クラスのインスタンスを作成し、メッセージ受信サービスによって定義されたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6c710-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6c710-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c710-118">See Also</span></span>  
 [<span data-ttu-id="6c710-119">キューの概要</span><span class="sxs-lookup"><span data-stu-id="6c710-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="6c710-120">方法: Exchange の WCF エンドポイントとメッセージのキュー</span><span class="sxs-lookup"><span data-stu-id="6c710-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="6c710-121">メッセージ キューへの Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6c710-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="6c710-122">メッセージ キュー (MSMQ) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="6c710-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="6c710-123">Windows Communication foundation キュー メッセージ</span><span class="sxs-lookup"><span data-stu-id="6c710-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="6c710-124">メッセージ キューを介したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6c710-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)

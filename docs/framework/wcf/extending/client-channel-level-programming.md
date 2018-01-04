---
title: "クライアントのチャネル レベルのプログラミング"
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
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c3d9bc1819045c8261f003cbab52dd71c4da408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="e55bd-102">クライアントのチャネル レベルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="e55bd-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="e55bd-103">ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クラスとこれに関連するオブジェクト モデルを使用せずに、<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> クライアント アプリケーションを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-103">This topic describes how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="e55bd-104">メッセージの送信</span><span class="sxs-lookup"><span data-stu-id="e55bd-104">Sending Messages</span></span>  
 <span data-ttu-id="e55bd-105">メッセージを送信し、応答を受信して処理できるようにするには、次の手順に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e55bd-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1.  <span data-ttu-id="e55bd-106">バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-106">Create a binding.</span></span>  
  
2.  <span data-ttu-id="e55bd-107">チャネル ファクトリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e55bd-107">Build a channel factory.</span></span>  
  
3.  <span data-ttu-id="e55bd-108">チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-108">Create a channel.</span></span>  
  
4.  <span data-ttu-id="e55bd-109">要求を送信し、応答を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e55bd-109">Send a request and read the reply.</span></span>  
  
5.  <span data-ttu-id="e55bd-110">すべてのチャネル オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e55bd-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="e55bd-111">バインディングの作成</span><span class="sxs-lookup"><span data-stu-id="e55bd-111">Creating a Binding</span></span>  
 <span data-ttu-id="e55bd-112">受信側の場合と同様に (を参照してください[サービス チャネル レベルのプログラミング](../../../../docs/framework/wcf/extending/service-channel-level-programming.md))、メッセージの開始を送信するバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="e55bd-113">この例では、新しい <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> を作成し、その要素コレクションに <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> を追加します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="e55bd-114">ChannelFactory のビルド</span><span class="sxs-lookup"><span data-stu-id="e55bd-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="e55bd-115"><xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType> を作成する代わりに、今回はバインディングで型パラメーターを <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> にして <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> を呼び出すことで、<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType> を作成します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e55bd-116">チャネル リスナーは受信メッセージを待機する側で使用されますが、チャネル ファクトリはチャネルを作成するために通信を開始する側で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e55bd-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="e55bd-117">チャネル リスナーと同様に、チャネル ファクトリも使用する前に開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="e55bd-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="e55bd-118">チャネルの作成</span><span class="sxs-lookup"><span data-stu-id="e55bd-118">Creating a Channel</span></span>  
 <span data-ttu-id="e55bd-119">次に <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> を呼び出して、<xref:System.ServiceModel.Channels.IRequestChannel> を作成します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="e55bd-120">この呼び出しには、新しく作成するチャネルを使用して通信を行う対象となるエンドポイントのアドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="e55bd-121">チャネルを作成したら、このチャネルで Open を呼び出して通信できる状態にします。</span><span class="sxs-lookup"><span data-stu-id="e55bd-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="e55bd-122">この Open の呼び出しにより、トランスポートの性質に応じて、目的のエンドポイントとの接続が開始されることもあれば、ネットワーク上では何も起こらないこともあります。</span><span class="sxs-lookup"><span data-stu-id="e55bd-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="e55bd-123">要求の送信と応答の読み取り</span><span class="sxs-lookup"><span data-stu-id="e55bd-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="e55bd-124">チャネルが開かれると、メッセージを作成して、チャネルの Request メソッドを使用して要求を送信し、応答が返ってくるのを待機できます。</span><span class="sxs-lookup"><span data-stu-id="e55bd-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="e55bd-125">Request メソッドが終了すると、応答メッセージを取得して読み取り、エンドポイントの応答内容を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e55bd-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="e55bd-126">オブジェクトの終了</span><span class="sxs-lookup"><span data-stu-id="e55bd-126">Closing Objects</span></span>  
 <span data-ttu-id="e55bd-127">リソースのリークを避けるには、通信に使用したオブジェクトが不要になったら、これを終了します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="e55bd-128">次のコード例に、メッセージを送信して応答を読み取るためにチャネル ファクトリを使用する基本的なクライアントを示します。</span><span class="sxs-lookup"><span data-stu-id="e55bd-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]

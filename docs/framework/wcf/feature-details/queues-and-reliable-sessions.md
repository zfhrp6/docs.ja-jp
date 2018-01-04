---
title: "キューと信頼できるセッション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9a78bab9f7c4af23cf01c44e1d22a41a87a96f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="queues-and-reliable-sessions"></a><span data-ttu-id="661aa-102">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="661aa-102">Queues and Reliable Sessions</span></span>
<span data-ttu-id="661aa-103">キューおよび信頼できるセッションは、信頼できるメッセージングを実装する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能です。</span><span class="sxs-lookup"><span data-stu-id="661aa-103">Queues and reliable sessions are the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features that implement reliable messaging.</span></span> <span data-ttu-id="661aa-104">このセクションの各トピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージング機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="661aa-104">The topics contained in this section discuss the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reliable messaging features.</span></span>  
  
 <span data-ttu-id="661aa-105">信頼できるメッセージングとは、信頼できるメッセージング送信元 (送信元と呼ぶ) から信頼できるメッセージング送信先 (送信先と呼ぶ) にメッセージを確実に転送することを指します。</span><span class="sxs-lookup"><span data-stu-id="661aa-105">Reliable messaging is how a reliable messaging source (called the source) transfers messages reliably to a reliable messaging destination (called the destination).</span></span>  
  
 <span data-ttu-id="661aa-106">信頼できるメッセージングの主要な側面は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="661aa-106">Reliable messaging has the following key aspects:</span></span>  
  
-   <span data-ttu-id="661aa-107">メッセージ転送エラーまたはトランスポート エラーに関係なく、送信元から送信先に送られるメッセージの転送が保証されること。</span><span class="sxs-lookup"><span data-stu-id="661aa-107">Transfer assurances for messages sent from a source to a destination regardless of message transfer failure or transport failures.</span></span>  
  
-   <span data-ttu-id="661aa-108">送信元と送信先を互いに分離することにより、送信元または送信先が利用できない場合でも、送信元と送信先でのそれぞれ独立したエラーと回復が可能になると共に、信頼できるメッセージの転送と配信が実現されること。</span><span class="sxs-lookup"><span data-stu-id="661aa-108">Separation of the source and the destination from each other, which provides independent failure and recovery of the source and the destination as well as reliable transfer and delivery of messages even though the source or destination is unavailable.</span></span>  
  
 <span data-ttu-id="661aa-109">信頼できるメッセージングを実現すると、待ち時間が長くなることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="661aa-109">Reliable messaging frequently comes at the cost of high latency.</span></span> <span data-ttu-id="661aa-110">待ち時間とは、メッセージが送信元から送信先に到達するまでにかかる時間です。</span><span class="sxs-lookup"><span data-stu-id="661aa-110">Latency is the time it takes for the message to reach the destination from the source.</span></span> <span data-ttu-id="661aa-111">そこで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、信頼できるメッセージングとして、次の 2 種類を提供します。</span><span class="sxs-lookup"><span data-stu-id="661aa-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], therefore, provides the following types of reliable messaging:</span></span>  
  
-   <span data-ttu-id="661aa-112">[信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)、どのプランに、コストの遅延が大きいことがなく信頼できる転送</span><span class="sxs-lookup"><span data-stu-id="661aa-112">[Reliable Sessions](../../../../docs/framework/wcf/feature-details/reliable-sessions.md), which offer reliable transfer without the cost of high latency</span></span>  
  
-   <span data-ttu-id="661aa-113">[WCF のキュー](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)、信頼できる転送と、ソースとターゲット間の分離の両方を提供します。</span><span class="sxs-lookup"><span data-stu-id="661aa-113">[Queues in WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md), which offer both reliable transfers and separation between the source and the destination.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="661aa-114">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="661aa-114">Reliable Sessions</span></span>  
 <span data-ttu-id="661aa-115">信頼できるセッションでは、メッセージング (送信元および送信先) エンドポイントを分離する中継局の数や種類に関係なく、WS-ReliableMessaging プロトコルを使用して、送信元から送信先へのエンドツーエンドの信頼できるメッセージ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="661aa-115">Reliable sessions provide end-to-end reliable transfer of messages between a source and a destination using the WS-ReliableMessaging protocol regardless of the number or type of intermediaries that separate the messaging (source and destination) endpoints.</span></span> <span data-ttu-id="661aa-116">これには SOAP を使用しないトランスポート手段 (HTTP プロキシなど)、またはエンドポイント間でメッセージをやりとりする場合に必要となる SOAP を使用する手段 (SOAP ベースのルーターやブリッジなど) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="661aa-116">This includes any transport intermediaries that do not use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="661aa-117">信頼できるセッションでは、メモリ内転送ウィンドウを使用して、トランスポート エラーが発生した場合に SOAP メッセージ レベル エラーをマスクし、接続を再確立します。</span><span class="sxs-lookup"><span data-stu-id="661aa-117">Reliable sessions use an in-memory transfer window to mask SOAP message-level failures and re-establish connections in the case of transport failures.</span></span>  
  
 <span data-ttu-id="661aa-118">信頼できるセッションは、待ち時間の短い、信頼できるメッセージ転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="661aa-118">Reliable sessions provide low-latency reliable message transfers.</span></span> <span data-ttu-id="661aa-119">これらは、TCP が IP ブリッジ経由のパケットで実現するものと同等の転送を、プロキシや中継局経由の SOAP メッセージで実現します。</span><span class="sxs-lookup"><span data-stu-id="661aa-119">They provide for SOAP messages over any proxies or intermediaries, equivalent to what TCP provides for packets over IP bridges.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="661aa-120">信頼できるセッションを参照してください[信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)です。</span><span class="sxs-lookup"><span data-stu-id="661aa-120"> reliable sessions, see [Reliable Sessions](../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
### <a name="queues"></a><span data-ttu-id="661aa-121">キュー</span><span class="sxs-lookup"><span data-stu-id="661aa-121">Queues</span></span>  
 <span data-ttu-id="661aa-122">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキューでは、待ち時間は長くなりますが、信頼できるメッセージの転送と共に送信元および送信先の分離が実現されます。</span><span class="sxs-lookup"><span data-stu-id="661aa-122">Queues in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provide both reliable transfers of messages and separation between sources and destinations at the cost of high latency.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="661aa-123"> のキュー通信は、Microsoft Message Queuing (MSMQ) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="661aa-123"> queued communication is built on top of Message Queuing (also known as MSMQ).</span></span>  
  
 <span data-ttu-id="661aa-124">MSMQ は Windows にオプションとして付属し、NT サービスの 1 つとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="661aa-124">MSMQ is shipped as an option with Windows that runs as an NT service.</span></span> <span data-ttu-id="661aa-125">MSMQ サービスは、送信元の代わりに転送キューで転送用のメッセージを取得し、ターゲット キューに配信します。</span><span class="sxs-lookup"><span data-stu-id="661aa-125">It captures messages for transmission in a transmission queue on behalf of the source and delivers it to a target queue.</span></span> <span data-ttu-id="661aa-126">ターゲット キューは、送信先の代わりにメッセージを受け取り、後で送信先がメッセージを要求したときに配信します。</span><span class="sxs-lookup"><span data-stu-id="661aa-126">The target queue accepts messages on behalf of the destination for later delivery whenever the destination requests for messages.</span></span> <span data-ttu-id="661aa-127">MSMQ キュー マネージャーは信頼できるメッセージ転送プロトコルを実装して、送信中にメッセージが失われないようにします。</span><span class="sxs-lookup"><span data-stu-id="661aa-127">The MSMQ queue managers implement a reliable message-transfer protocol so that messages are not lost in transmission.</span></span> <span data-ttu-id="661aa-128">このプロトコルは、ネイティブまたは SOAP リライアブル メッセージ プロトコル (SRMP) などの SOAP ベースのプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="661aa-128">The protocol can be native or SOAP-based, such as Soap Reliable Messaging Protocol (SRMP).</span></span>  
  
 <span data-ttu-id="661aa-129">キュー間でのメッセージの信頼できる転送に加え、送信元と送信先の分離により、疎結合されたアプリケーションで信頼できる通信を実現できます。</span><span class="sxs-lookup"><span data-stu-id="661aa-129">The separation, coupled with reliable message transfers between queues, enables applications that are loosely coupled to communicate reliably.</span></span> <span data-ttu-id="661aa-130">信頼できるセッションとは異なり、送信元と送信先が同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="661aa-130">Unlike reliable sessions, the source and destination do not have to be running at the same time.</span></span> <span data-ttu-id="661aa-131">このため、送信元によるメッセージの生成レートと送信先によるメッセージの消費レートが一致しないときに、キューを実質的に負荷平準化機構として使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="661aa-131">This implicitly enables scenarios where queues are, in effect, used as a load-leveling mechanism when there is a mismatch between the rate of message production by the source and the rate of the message consumption by the destination.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="661aa-132">キューを参照してください[WCF のキュー](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="661aa-132"> queues, see [Queues in WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661aa-133">参照</span><span class="sxs-lookup"><span data-stu-id="661aa-133">See Also</span></span>  
 [<span data-ttu-id="661aa-134">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="661aa-134">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="661aa-135">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="661aa-135">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="661aa-136">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="661aa-136">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [<span data-ttu-id="661aa-137">信頼できるセッションの概要</span><span class="sxs-lookup"><span data-stu-id="661aa-137">Reliable Sessions Overview</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)

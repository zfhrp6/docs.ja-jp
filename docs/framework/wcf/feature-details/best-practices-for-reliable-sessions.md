---
title: "信頼できるセッションのベスト プラクティス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea7266cb89a233146217d8cadd85839360351f71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-for-reliable-sessions"></a><span data-ttu-id="40822-102">信頼できるセッションのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="40822-102">Best Practices for Reliable Sessions</span></span>

<span data-ttu-id="40822-103">このトピックでは、信頼できるセッションのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="40822-103">This topic discusses best practices for reliable sessions.</span></span>

## <a name="setting-maxtransferwindowsize"></a><span data-ttu-id="40822-104">MaxTransferWindowSize の設定</span><span class="sxs-lookup"><span data-stu-id="40822-104">Setting MaxTransferWindowSize</span></span>

<span data-ttu-id="40822-105">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の信頼できるセッションでは、転送ウィンドウを使用して、クライアント側およびサービス側のメッセージを保持しています。</span><span class="sxs-lookup"><span data-stu-id="40822-105">Reliable sessions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] use a transfer window to hold messages on the client and service.</span></span> <span data-ttu-id="40822-106"><xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> プロパティは、この転送ウィンドウに保持できるメッセージの最大数を表します。</span><span class="sxs-lookup"><span data-stu-id="40822-106">The configurable property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indicates how many messages the transfer window can hold.</span></span>

<span data-ttu-id="40822-107">送信者は、このことを示します。 受信確認の待機中に転送ウィンドウが保持できるメッセージの数受信側、サービス用にバッファーにメッセージの数を示します。</span><span class="sxs-lookup"><span data-stu-id="40822-107">On the sender, this indicates how many messages the transfer window can hold while waiting for acknowledgements; on the receiver, it indicates how many messages to buffer for the service.</span></span>

<span data-ttu-id="40822-108">ネットワークの効率性と、サービスの容量の最適な適切なサイズの選択に影響します。</span><span class="sxs-lookup"><span data-stu-id="40822-108">Choosing the right size impacts the efficiency of the network and the optimal capacity of the service.</span></span> <span data-ttu-id="40822-109">次のセクションでは、このプロパティと値の影響の値を選択する際の考慮事項を詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="40822-109">The following sections detail what to consider when choosing a value for this property and the impact of the value.</span></span>

<span data-ttu-id="40822-110">既定の転送ウィンドウ サイズは、8 つのメッセージです。</span><span class="sxs-lookup"><span data-stu-id="40822-110">The default transfer window size is eight messages.</span></span>

### <a name="efficient-use-of-the-network"></a><span data-ttu-id="40822-111">ネットワークの効率的な使用</span><span class="sxs-lookup"><span data-stu-id="40822-111">Efficient use of the network</span></span>

<span data-ttu-id="40822-112">このコンテキストで用語*ネットワーク*(送信者) のクライアントとサービス (受信側) の間の通信の基礎として使用するすべてに対応しています。</span><span class="sxs-lookup"><span data-stu-id="40822-112">In this context, the term *network* corresponds to everything used as the basis of communication between a client (sender) and a service (receiver).</span></span> <span data-ttu-id="40822-113">これは、SOAP ルーターや HTTP プロキシ/ファイアウォールなどのトランスポート接続や任意の仲介者間のブリッジ含まれます。</span><span class="sxs-lookup"><span data-stu-id="40822-113">This includes the transport connections and any intermediary or bridges in between, including SOAP routers or HTTP proxies/firewalls.</span></span>

<span data-ttu-id="40822-114">ネットワーク効率が高いとは、その伝送容量を最大限に活用できるということです。</span><span class="sxs-lookup"><span data-stu-id="40822-114">Efficient use of the network ensures that network capacity is fully used.</span></span> <span data-ttu-id="40822-115">ネットワーク経由で 1 秒あたりに転送できるデータの量 (*データ レート*) と、送信者から受信側にデータを転送する所要時間 (*待機時間*) どのくらい効果的に影響を与えるネットワーク利用します。</span><span class="sxs-lookup"><span data-stu-id="40822-115">Both the amount of data that can be transferred per second over the network (*data rate*) and the time it takes to transfer data from the sender to the receiver (*latency*) impact how effectively the network is utilized.</span></span>

<span data-ttu-id="40822-116">送信側については、転送ウィンドウに保持できる受信確認の到着を待機しているメッセージの数が <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> プロパティによって表されます。</span><span class="sxs-lookup"><span data-stu-id="40822-116">On the sender, the property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indicates how many messages its transfer window can hold while waiting for acknowledgements.</span></span> <span data-ttu-id="40822-117">ネットワークの待機時間が高いと、応答性を高めてネットワーク利用効率を確保できるように、転送ウィンドウ サイズを増やす必要があります。</span><span class="sxs-lookup"><span data-stu-id="40822-117">If the network latency is high and in order to ensure a responsive sender and effective network utilization, you should increase the transfer window size.</span></span>

<span data-ttu-id="40822-118">たとえば、送信者から最新の状態がデータ レートを場合でも、待機時間でした高場合にいくつかの中継ぎ局が送信者と受信者の間に存在するか、またはデータが損失を伴う中継ぎ局またはネットワークを通過する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40822-118">For example even if the sender keeps up with data rate, latency could be high if several intermediaries exist between the sender and receiver or the data must pass through a lossy intermediary or network.</span></span> <span data-ttu-id="40822-119">したがって、送信者を待っている転送ウィンドウにメッセージに対する受信確認、ネットワーク上で送信するための新しいメッセージを受け入れる前にします。</span><span class="sxs-lookup"><span data-stu-id="40822-119">Thus, the sender has to wait for acknowledgements for the messages in its transfer window before accepting new messages to send on the wire.</span></span> <span data-ttu-id="40822-120">待機時間の長い、有効性は小さくのバッファー、ネットワーク使用率。</span><span class="sxs-lookup"><span data-stu-id="40822-120">The smaller the buffer with high latency, the less effective the network utilization.</span></span> <span data-ttu-id="40822-121">その一方で、転送ウィンドウ サイズが大きすぎる可能性がありますに影響を与えるサービスのため、サービスは、クライアントによって送信されるデータの速度が高速に遅延を解消する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40822-121">On the other hand, too high a transfer window size may impact the service because the service may need to catch up to the high rate of data sent by the client.</span></span>

### <a name="running-the-service-to-capacity"></a><span data-ttu-id="40822-122">容量にサービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="40822-122">Running the service to capacity</span></span>

<span data-ttu-id="40822-123">ネットワークを効率的に使用すると、できるだけ多くことをお勧めするも最適処理能力で実行するサービスです。</span><span class="sxs-lookup"><span data-stu-id="40822-123">As much as the network is used efficiently, ideally you also want the service to run at optimal capacity.</span></span> <span data-ttu-id="40822-124">受信側の転送ウィンドウ サイズは、処理待ちのメッセージをいくつまで保持しておけるかを表します。</span><span class="sxs-lookup"><span data-stu-id="40822-124">The transfer window size property on the receiver indicates how many messages the receiver can buffer.</span></span> <span data-ttu-id="40822-125">メッセージをこのようにバッファーに保持することは、ネットワークのフロー制御だけでなく、処理能力を最大限に活用したサービス稼働にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="40822-125">This message buffering helps not only the network flow control but also enables the service to run to full capacity.</span></span> <span data-ttu-id="40822-126">たとえば、バッファーが 1 つのメッセージと、サービスが処理できるよりも早くメッセージが到着した場合、ネットワーク メッセージを削除する場合があり、容量を無駄になるまたは使用率が低い可能性があります。</span><span class="sxs-lookup"><span data-stu-id="40822-126">For example if the buffer is one message and messages arrive faster than the service can process them, then the network might drop messages and capacity might be wasted or underutilized.</span></span>

<span data-ttu-id="40822-127">同時に受信して、以前に受信したメッセージの処理中にメッセージをバッファーすると、バッファーを使用して、サービスの可用性が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="40822-127">Using a buffer increases the availability of the service as it concurrently receives and buffers a message while processing the previously received messages.</span></span>

<span data-ttu-id="40822-128">同じを使用することをお勧め`MaxTransferWindowSize`送信者および受信者の両方にします。</span><span class="sxs-lookup"><span data-stu-id="40822-128">We recommended that you use the same `MaxTransferWindowSize` on both the sender and receiver.</span></span>

### <a name="enabling-flow-control"></a><span data-ttu-id="40822-129">フロー制御を有効にします。</span><span class="sxs-lookup"><span data-stu-id="40822-129">Enabling flow control</span></span>

<span data-ttu-id="40822-130">*フロー制御*により、送信者と受信者、互いに対応する、メッセージし、処理が処理する機構は、生成されている高速です。</span><span class="sxs-lookup"><span data-stu-id="40822-130">*Flow control* is a mechanism that ensures that the sender and receiver keep pace with each other, that is, the messages are consumed and acted upon as fast as they're produced.</span></span> <span data-ttu-id="40822-131">クライアントとサービスの転送ウィンドウ サイズは、送信側と受信側が妥当な許容範囲内で同期できるように設定しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="40822-131">The transfer window size on the client and service ensures that the sender and receiver are within a reasonable window of synchronization.</span></span>

<span data-ttu-id="40822-132">プロパティを設定することを強くお勧め<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A>に`true`間で信頼できるセッションを使用しているときに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアントと[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。</span><span class="sxs-lookup"><span data-stu-id="40822-132">We highly recommended that you set the property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> to `true` when you're using a reliable session between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>

## <a name="setting-maxpendingchannels"></a><span data-ttu-id="40822-133">MaxPendingChannels の設定</span><span class="sxs-lookup"><span data-stu-id="40822-133">Setting MaxPendingChannels</span></span>

<span data-ttu-id="40822-134">さまざまなクライアントからの通信を信頼できるセッションを有効にするサービスを記述する場合、多くのクライアントが同時に、サービスに信頼できるセッションを確立することができます。</span><span class="sxs-lookup"><span data-stu-id="40822-134">When writing a service that enables reliable session communication from different clients, it's possible to have many clients establish a reliable session to the service at the same time.</span></span> <span data-ttu-id="40822-135">このとき、サービスの応答性は、`MaxPendingChannels` プロパティによって決まります。</span><span class="sxs-lookup"><span data-stu-id="40822-135">The response of the service in these situations depends on the `MaxPendingChannels` property.</span></span>

<span data-ttu-id="40822-136">信頼できるセッション チャネルが送信側によって作成されると、両者のハンドシェイクによって信頼できるセッションが確立します。</span><span class="sxs-lookup"><span data-stu-id="40822-136">When the sender creates a reliable session channel to a receiver, a handshake between them establishes a reliable session.</span></span> <span data-ttu-id="40822-137">これが終わるとチャネルは保留チャネル キューに入り、サービス側からの応答を待機する状態になります。</span><span class="sxs-lookup"><span data-stu-id="40822-137">After the reliable session is established, the channel is put in a pending channel queue for acceptance by the service.</span></span> <span data-ttu-id="40822-138">`MaxPendingChannels` プロパティは、この状態にできるチャネルの数を表します。</span><span class="sxs-lookup"><span data-stu-id="40822-138">The `MaxPendingChannels` property indicates how many channels can be in this state.</span></span>

<span data-ttu-id="40822-139">サービス チャネルを受け付けられない状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="40822-139">It's possible for the service to be in a state where it can't accept more channels.</span></span> <span data-ttu-id="40822-140">キューがいっぱいの場合、信頼できるセッションを確立しようとするは拒否され、クライアントは再試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40822-140">If the queue is full, an attempt to establish a reliable session is rejected, and the client must retry.</span></span>

<span data-ttu-id="40822-141">キューに入った保留チャネルが長期間キューに残っていることもできます。</span><span class="sxs-lookup"><span data-stu-id="40822-141">It's also possible that the pending channels in the queue remain in the queue for a longer duration.</span></span> <span data-ttu-id="40822-142">その間は、信頼できるセッションのアイドル タイムアウトが発生し、エラーが発生した状態に遷移するチャネルの原因します。</span><span class="sxs-lookup"><span data-stu-id="40822-142">In the meantime, an inactivity timeout on the reliable session may occur, causing the channel to transition to a faulted state.</span></span>

<span data-ttu-id="40822-143">複数のクライアントのサービスを同時にサービスを記述する場合は、お客様のニーズに適した値を設定してください。</span><span class="sxs-lookup"><span data-stu-id="40822-143">When writing a service that services multiple clients simultaneously, you should set a value that's suitable for your needs.</span></span> <span data-ttu-id="40822-144">設定の値が高すぎる、`MaxPendingChannels`プロパティ、ワーキング セットに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="40822-144">Setting too high a value for the `MaxPendingChannels` property impacts your working set.</span></span>

<span data-ttu-id="40822-145">既定値<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A>4 つのチャンネルがします。</span><span class="sxs-lookup"><span data-stu-id="40822-145">The default value for <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> is four channels.</span></span>

## <a name="reliable-sessions-and-hosting"></a><span data-ttu-id="40822-146">信頼できるセッションとホスティング</span><span class="sxs-lookup"><span data-stu-id="40822-146">Reliable sessions and hosting</span></span>

<span data-ttu-id="40822-147">信頼できるセッションを使用するサービスをホストしているときに web は、次の重要な考慮事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="40822-147">When web hosting a service that uses reliable sessions, you should keep the following important considerations in mind:</span></span>

- <span data-ttu-id="40822-148">信頼できるセッションはステートフルであり、状態は AppDomain で管理されます。</span><span class="sxs-lookup"><span data-stu-id="40822-148">Reliable sessions are stateful, and state is maintained in the AppDomain.</span></span> <span data-ttu-id="40822-149">したがって、信頼できるセッションでやりとりするメッセージはすべて、同じ AppDomain で処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40822-149">This means that all messages that are part of a reliable session must be processed in the same AppDomain.</span></span> <span data-ttu-id="40822-150">Web ファームと web ガーデン ファームやガーデンのサイズが 1 つのノードより大きいは、この制約を保証できません。</span><span class="sxs-lookup"><span data-stu-id="40822-150">Web farms and web gardens where the size of the farm or garden is greater than one node can't guarantee this constraint.</span></span>

- <span data-ttu-id="40822-151">双方向 HTTP チャネルを使用して、信頼できるセッション (たとえばを使用して`WsDualHttpBinding`) の 2 つ HTTP 接続クライアントごとの既定値よりも多く必要なことができます。</span><span class="sxs-lookup"><span data-stu-id="40822-151">Reliable sessions using dual HTTP channels (for example, using `WsDualHttpBinding`) can require more than the default of two HTTP connections per-client.</span></span> <span data-ttu-id="40822-152">つまり、双方向の信頼できるセッションは同時実行アプリケーションとプロトコル メッセージは、特定の時点で各方法転送可能性があるために最大 2 つの接続を要求できます。</span><span class="sxs-lookup"><span data-stu-id="40822-152">This means a duplex reliable session can require up to two connections each way because concurrent application and protocol messages may be transferring each way at any given time.</span></span> <span data-ttu-id="40822-153">状況によって、サービスのメッセージ交換パターンによって、つまり、双方向 HTTP と信頼できるセッションを使用して、web でホストされるサービスのデッドロックを起こす可能性があること。</span><span class="sxs-lookup"><span data-stu-id="40822-153">Under certain conditions depending on the message exchange pattern of the service, this means that it's possible to deadlock a web-hosted service using dual HTTP and reliable sessions.</span></span> <span data-ttu-id="40822-154">クライアントごとの許容の HTTP 接続の数を増やすには、関連する構成ファイルに次の追加 (たとえば、 *web.config*当該サービスの)。</span><span class="sxs-lookup"><span data-stu-id="40822-154">To increase the number of allowable HTTP connections per client, add the following to the relevant configuration file (for example, *web.config* of the service in question):</span></span>

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  <span data-ttu-id="40822-155">値、`maxconnection`属性が必要な接続の数。</span><span class="sxs-lookup"><span data-stu-id="40822-155">The value of the `maxconnection` attribute is the number of connections needed.</span></span> <span data-ttu-id="40822-156">ここでは、最小値は、4 つの接続を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40822-156">The minimum in this case should be four connections.</span></span>

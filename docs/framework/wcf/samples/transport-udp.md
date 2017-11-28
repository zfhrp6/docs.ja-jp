---
title: "トランスポート: UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae7df5531abf2efcb7ba0059da1d8393e5a3f7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transport-udp"></a><span data-ttu-id="529d6-102">トランスポート: UDP</span><span class="sxs-lookup"><span data-stu-id="529d6-102">Transport: UDP</span></span>
<span data-ttu-id="529d6-103">UDP トランスポートのサンプルでは、UDP ユニキャストとマルチキャストを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] カスタム トランスポートとして実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="529d6-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="529d6-104">このサンプルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でカスタム トランスポートを作成するための推奨手順について説明します。作成時には、チャネル フレームワークと次に示す [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のベスト プラクティスを使用します。</span><span class="sxs-lookup"><span data-stu-id="529d6-104">The sample describes the recommended procedure for creating a custom transport in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], by using the channel framework and following [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] best practices.</span></span> <span data-ttu-id="529d6-105">カスタム トランスポートを作成する手順は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="529d6-105">The steps to create a custom transport are as follows:</span></span>  
  
1.  <span data-ttu-id="529d6-106">チャネルの決定[メッセージ交換パターン](#MessageExchangePatterns)(IOutputChannel、IInputChannel、IDuplexChannel、IRequestChannel、または IReplyChannel) ChannelFactory と ChannelListener でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="529d6-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="529d6-107">次に、こうしたインターフェイスのセッションフル バリエーションをサポートするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="529d6-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2.  <span data-ttu-id="529d6-108">メッセージ交換パターンをサポートするチャネル ファクトリおよびリスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="529d6-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3.  <span data-ttu-id="529d6-109">ネットワーク固有の例外が、<xref:System.ServiceModel.CommunicationException> の適切な派生クラスに標準化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="529d6-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4.  <span data-ttu-id="529d6-110">追加、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素をチャネル スタックにカスタム トランスポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="529d6-111">詳細については、次を参照してください。[バインド要素の追加](#AddingABindingElement)です。</span><span class="sxs-lookup"><span data-stu-id="529d6-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5.  <span data-ttu-id="529d6-112">バインド要素拡張セクションを追加して、新しいバインド要素を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="529d6-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6.  <span data-ttu-id="529d6-113">他のエンドポイントに機能を伝達するメタデータ拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7.  <span data-ttu-id="529d6-114">適切に定義されたプロファイルに従って、バインド要素のスタックを事前構成するバインディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="529d6-115">詳細については、次を参照してください。[標準のバインディングの追加](#AddingAStandardBinding)です。</span><span class="sxs-lookup"><span data-stu-id="529d6-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8.  <span data-ttu-id="529d6-116">構成システムにバインディングを開示する、バインディング セクションおよびバインド構成要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="529d6-117">詳細については、次を参照してください。[構成サポートの追加](#AddingConfigurationSupport)です。</span><span class="sxs-lookup"><span data-stu-id="529d6-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="529d6-118">メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="529d6-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="529d6-119">カスタム トランスポートを記述する最初の手順として、どのメッセージ交換パターン (MEP) がトランスポートに必要かを判断します。</span><span class="sxs-lookup"><span data-stu-id="529d6-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="529d6-120">次の 3 つの MEP から選択できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-120">There are three MEPs to choose from:</span></span>  
  
-   <span data-ttu-id="529d6-121">データグラム (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="529d6-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="529d6-122">データグラム MEP を使用している場合、クライアントは "ファイア アンド フォーゲット (撃ち放し)" の交換を使用してメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="529d6-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="529d6-123">このような交換では、配信の成否について帯域外での確認が必要になります。</span><span class="sxs-lookup"><span data-stu-id="529d6-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="529d6-124">メッセージが移動中に失われて、サービスに到達しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="529d6-125">クライアントで送信操作が正常に完了したとしても、リモート エンドポイントでメッセージが受信されたとは限りません。</span><span class="sxs-lookup"><span data-stu-id="529d6-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="529d6-126">データグラムはメッセージングの基礎となるビルド ブロックであり、その上に信頼できるプロトコルや安全なプロトコルなどの独自のプロトコルを構築できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="529d6-127">クライアント データグラム チャネルには、<xref:System.ServiceModel.Channels.IOutputChannel> インターフェイスが実装され、サービス データグラム チャネルには <xref:System.ServiceModel.Channels.IInputChannel> インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
-   <span data-ttu-id="529d6-128">要求 - 応答 (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="529d6-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="529d6-129">この MEP では、メッセージが送信されて、応答が受信されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="529d6-130">パターンは、要求 - 応答のペアで構成されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="529d6-131">要求 - 応答呼び出しの例には、リモート プロシージャ コール (RPC) やブラウザ GET などがあります。</span><span class="sxs-lookup"><span data-stu-id="529d6-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="529d6-132">このパターンは、半二重とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="529d6-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="529d6-133">この MEP では、クライアント チャネルには <xref:System.ServiceModel.Channels.IRequestChannel> が実装され、サービス チャネルには <xref:System.ServiceModel.Channels.IReplyChannel> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
-   <span data-ttu-id="529d6-134">二重 (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="529d6-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="529d6-135">二重 MEP では、クライアントにより任意の数のメッセージを送信して、任意の順序で受信できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="529d6-136">二重 MEP は、話される語の 1 つずつがメッセージである電話の会話に似ています。</span><span class="sxs-lookup"><span data-stu-id="529d6-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="529d6-137">この MEP ではどちらの側も送信および受信できるので、クライアントおよびサービス チャネルによって実装されるインターフェイスは <xref:System.ServiceModel.Channels.IDuplexChannel> になります。</span><span class="sxs-lookup"><span data-stu-id="529d6-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="529d6-138">これらの MEP では、それぞれセッションをサポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="529d6-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="529d6-139">セッション対応チャネルにより追加される機能として、チャネルで送信および受信されるすべてのメッセージが関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="529d6-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="529d6-140">要求/応答パターンはスタンドアロンの 2 メッセージ セッションで、要求と応答が相互に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="529d6-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="529d6-141">一方、セッションをサポートする要求 - 応答パターンは、そのチャネルのすべての要求/応答ペアが互いに関連付けられることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="529d6-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="529d6-142">これにより、合計で 6 つの MEP (データグラム、要求 - 応答、二重、セッション対応データグラム、セッション対応要求 - 応答、およびセッション対応二重) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="529d6-143">UDP トランスポートでは、サポートされている MEP はデータグラムだけです。これは、UDP が "ファイア アンド フォーゲット (撃ち放し)" のプロトコルだからです。</span><span class="sxs-lookup"><span data-stu-id="529d6-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="529d6-144">ICommunicationObject および WCF オブジェクトのライフサイクル</span><span class="sxs-lookup"><span data-stu-id="529d6-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d6-145"> は、通信に使用される <xref:System.ServiceModel.Channels.IChannel>、<xref:System.ServiceModel.Channels.IChannelFactory>、および <xref:System.ServiceModel.Channels.IChannelListener> などのオブジェクトのライフサイクルの管理に使用される共通ステート マシンです。</span><span class="sxs-lookup"><span data-stu-id="529d6-145"> has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="529d6-146">これらの通信オブジェクトには、5 つの状態があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="529d6-147">これらの状態は、<xref:System.ServiceModel.CommunicationState> 列挙値で表され、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="529d6-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
-   <span data-ttu-id="529d6-148">Created: <xref:System.ServiceModel.ICommunicationObject> が初めてインスタンス化されたときの状態です。</span><span class="sxs-lookup"><span data-stu-id="529d6-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="529d6-149">この状態では、入出力 (I/O) は行われません。</span><span class="sxs-lookup"><span data-stu-id="529d6-149">No input/output (I/O) occurs in this state.</span></span>  
  
-   <span data-ttu-id="529d6-150">Opening: <xref:System.ServiceModel.ICommunicationObject.Open%2A> が呼び出されると、オブジェクトはこの状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="529d6-151">この時点では、プロパティは不変であり、入出力を開始できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="529d6-152">この移行は、Created 状態からのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="529d6-152">This transition is valid only from the Created state.</span></span>  
  
-   <span data-ttu-id="529d6-153">Opened: オープン処理が完了すると、オブジェクトはこの状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="529d6-154">この移行は、Opening 状態からのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="529d6-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="529d6-155">この時点では、オブジェクトは完全に転送に使用可能です。</span><span class="sxs-lookup"><span data-stu-id="529d6-155">At this point, the object is fully usable for transfer.</span></span>  
  
-   <span data-ttu-id="529d6-156">Closing: 正常なシャットダウンを行うために <xref:System.ServiceModel.ICommunicationObject.Close%2A> が呼び出されると、オブジェクトはこの状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="529d6-157">この移行は、Opened 状態からのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="529d6-157">This transition is valid only from the Opened state.</span></span>  
  
-   <span data-ttu-id="529d6-158">Closed: Closed 状態では、オブジェクトは使用できません。</span><span class="sxs-lookup"><span data-stu-id="529d6-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="529d6-159">通常、ほとんどの構成には検査中もアクセスできますが、通信が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="529d6-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="529d6-160">この状態は、破棄されるのと同じです。</span><span class="sxs-lookup"><span data-stu-id="529d6-160">This state is equivalent to being disposed.</span></span>  
  
-   <span data-ttu-id="529d6-161">Faulted: Faulted 状態では、オブジェクトにアクセスして検査できますが、使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="529d6-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="529d6-162">回復不可能なエラーが発生した場合、オブジェクトはこの状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="529d6-163">この状態からの唯一の有効な移行、`Closed`状態です。</span><span class="sxs-lookup"><span data-stu-id="529d6-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="529d6-164">各状態移行には、発生するイベントがあります。</span><span class="sxs-lookup"><span data-stu-id="529d6-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="529d6-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> メソッドはいつでも呼び出すことができます。このメソッドを呼び出すことにより、オブジェクトは現在の状態から直ちに Closed 状態に移行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="529d6-166"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> を呼び出すと、完了していない作業が終了します。</span><span class="sxs-lookup"><span data-stu-id="529d6-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="529d6-167">チャネル ファクトリとチャネル リスナー</span><span class="sxs-lookup"><span data-stu-id="529d6-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="529d6-168">カスタム トランスポートを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装とサービス チャネルでの <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="529d6-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="529d6-169">チャネル レイヤーでは、チャネルの構築にファクトリ パターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-169">The channel layer uses a factory pattern for constructing channels.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d6-170"> には、このプロセスに対する基本クラス ヘルパーが用意されています</span><span class="sxs-lookup"><span data-stu-id="529d6-170"> provides base class helpers for this process.</span></span>  
  
-   <span data-ttu-id="529d6-171"><xref:System.ServiceModel.Channels.CommunicationObject> クラスには <xref:System.ServiceModel.ICommunicationObject> が実装され、前述の手順 2. で説明したステート マシンが強制実行されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

-   <span data-ttu-id="529d6-172">「<xref:System.ServiceModel.Channels.ChannelManagerBase>クラスが実装する<xref:System.ServiceModel.Channels.CommunicationObject>の統一された基本クラスを提供し<xref:System.ServiceModel.Channels.ChannelFactoryBase>と<xref:System.ServiceModel.Channels.ChannelListenerBase>です。</span><span class="sxs-lookup"><span data-stu-id="529d6-172">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="529d6-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。</span><span class="sxs-lookup"><span data-stu-id="529d6-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="529d6-174">'<xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスが実装する<xref:System.ServiceModel.Channels.ChannelManagerBase>と<xref:System.ServiceModel.Channels.IChannelFactory>し、統合、`CreateChannel`を 1 つにオーバー ロード`OnCreateChannel`抽象メソッドです。</span><span class="sxs-lookup"><span data-stu-id="529d6-174">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="529d6-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> クラスは、<xref:System.ServiceModel.Channels.IChannelListener> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="529d6-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="529d6-176">基本状態管理を行います。</span><span class="sxs-lookup"><span data-stu-id="529d6-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="529d6-177">このサンプルのファクトリの実装は UdpChannelFactory.cs に、リスナーの実装は UdpChannelListener.cs に含まれています。</span><span class="sxs-lookup"><span data-stu-id="529d6-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="529d6-178"><xref:System.ServiceModel.Channels.IChannel> 実装は、UdpOutputChannel.cs と UdpInputChannel.cs に含まれています。</span><span class="sxs-lookup"><span data-stu-id="529d6-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="529d6-179">UDP チャネル ファクトリ</span><span class="sxs-lookup"><span data-stu-id="529d6-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="529d6-180">`UdpChannelFactory` は <xref:System.ServiceModel.Channels.ChannelFactoryBase> から派生します。</span><span class="sxs-lookup"><span data-stu-id="529d6-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="529d6-181">サンプルでは、<xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> をオーバーライドして、メッセージ エンコーダーのメッセージ バージョンにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="529d6-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="529d6-182">さらに、<xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> をオーバーライドして、ステート マシンの移行時に <xref:System.ServiceModel.Channels.BufferManager> のインスタンスを破棄できるようにします。</span><span class="sxs-lookup"><span data-stu-id="529d6-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="529d6-183">UDP 出力チャネル</span><span class="sxs-lookup"><span data-stu-id="529d6-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="529d6-184">`UdpOutputChannel` では、<xref:System.ServiceModel.Channels.IOutputChannel> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="529d6-185">このコンストラクターは、引数を検証し、渡される <xref:System.Net.EndPoint> に基づいて出力先の <xref:System.ServiceModel.EndpointAddress> オブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="529d6-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="529d6-186">チャネルが閉じる際には、正常終了することも異常終了することもあります。</span><span class="sxs-lookup"><span data-stu-id="529d6-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="529d6-187">チャネルが正常に閉じた場合はソケットも終了し、基本クラスの `OnClose` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="529d6-188">このときに例外がスローされると、インフラストラクチャによって `Abort` が呼び出され、チャネルがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="529d6-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="529d6-189">実装し、`Send()`と`BeginSend()` /`EndSend()`です。</span><span class="sxs-lookup"><span data-stu-id="529d6-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="529d6-190">この実装は、2 つの主要セクションに分かれます。</span><span class="sxs-lookup"><span data-stu-id="529d6-190">This breaks down into two main sections.</span></span> <span data-ttu-id="529d6-191">最初に、メッセージを次のようにシリアル化してバイト配列で表します。</span><span class="sxs-lookup"><span data-stu-id="529d6-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="529d6-192">次に、結果として生成されたデータを次のようにネットワークに送信します。</span><span class="sxs-lookup"><span data-stu-id="529d6-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="529d6-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="529d6-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="529d6-194">' から派生して、サンプルを実装する UdpChannelListener、<xref:System.ServiceModel.Channels.ChannelListenerBase>クラスです。</span><span class="sxs-lookup"><span data-stu-id="529d6-194">The``UdpChannelListener that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="529d6-195">単一の UDP ソケットを使用して、データグラムを受信します。</span><span class="sxs-lookup"><span data-stu-id="529d6-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="529d6-196">`OnOpen` メソッドは、非同期ループ内で UDP ソケットを使用してデータを受信します。</span><span class="sxs-lookup"><span data-stu-id="529d6-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="529d6-197">その後、メッセージ エンコーディング フレームワークを使用して、データを次のようにメッセージに変換します。</span><span class="sxs-lookup"><span data-stu-id="529d6-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="529d6-198">複数のソースから到着するメッセージが同じデータグラム チャネルで表されるので、`UdpChannelListener` はシングルトン リスナーです。</span><span class="sxs-lookup"><span data-stu-id="529d6-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="529d6-199">ほとんどの場合、1 つはアクティブで<xref:System.ServiceModel.Channels.IChannel>'、時に、このリスナーに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="529d6-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel>``associated with this listener at a time.</span></span> <span data-ttu-id="529d6-200">このサンプルでは、`AcceptChannel` メソッドによって返されるチャネルがその後破棄される場合のみ、もう 1 つ生成されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="529d6-201">メッセージが受信されると、このシングルトン チャネルのキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="529d6-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="529d6-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="529d6-202">UdpInputChannel</span></span>  
 <span data-ttu-id="529d6-203">`UdpInputChannel` クラスは、`IInputChannel` を実装しています。</span><span class="sxs-lookup"><span data-stu-id="529d6-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="529d6-204">このクラスは `UdpChannelListener` のソケットによって設定される受信メッセージのキューで構成されています。</span><span class="sxs-lookup"><span data-stu-id="529d6-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="529d6-205">これらのメッセージは、`IInputChannel.Receive` メソッドによってキューから削除されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="529d6-206">バインド要素の追加</span><span class="sxs-lookup"><span data-stu-id="529d6-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="529d6-207">ファクトリおよびチャネルを作成したので、バインディングを使用してそれらを ServiceModel ランタイムに開示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="529d6-208">バインディングは、サービス アドレスに関連する通信スタックを表すバインディング要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="529d6-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="529d6-209">スタック内の各要素で表される、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="529d6-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="529d6-210">このサンプルでは、バインディング要素は `UdpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。</span><span class="sxs-lookup"><span data-stu-id="529d6-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="529d6-211">バインディングに関連したファクトリを作成すると、次のメソッドが無効になります。</span><span class="sxs-lookup"><span data-stu-id="529d6-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="529d6-212">また、この要素には、`BindingElement` を複製したり、スキーム (soap.udp) を返したりするためのメンバーも含まれます。</span><span class="sxs-lookup"><span data-stu-id="529d6-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="529d6-213">トランスポート バインディング要素のメタデータ サポートの追加</span><span class="sxs-lookup"><span data-stu-id="529d6-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="529d6-214">トランスポートをメタデータ システムに統合するには、ポリシーのインポートとエクスポートの両方をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="529d6-215">これにより、バインドからのクライアントを生成する、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="529d6-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="529d6-216">WSDL サポートの追加</span><span class="sxs-lookup"><span data-stu-id="529d6-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="529d6-217">バインディングのトランスポート バインド要素は、メタデータのアドレス指定情報のインポートとエクスポートを行います。</span><span class="sxs-lookup"><span data-stu-id="529d6-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="529d6-218">SOAP バインディングを使用する場合は、トランスポート バインド要素によっても、メタデータの正しいトランスポート URI がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="529d6-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="529d6-219">WSDL エクスポート</span><span class="sxs-lookup"><span data-stu-id="529d6-219">WSDL Export</span></span>  
 <span data-ttu-id="529d6-220">アドレス指定情報をエクスポートするには、`UdpTransportBindingElement` に `IWsdlExportExtension` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="529d6-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="529d6-221">`ExportEndpoint` メソッドにより、正しいアドレス指定情報が WSDL ポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="529d6-222">エンドポイントが SOAP バインディングを使用する場合、`UdpTransportBindingElement` メソッドの `ExportEndpoint` の実装でも、次のようにトランスポート URI がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="529d6-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="529d6-223">WSDL インポート</span><span class="sxs-lookup"><span data-stu-id="529d6-223">WSDL Import</span></span>  
 <span data-ttu-id="529d6-224">WSDL インポート システムを拡張してアドレスのインポートを処理するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="529d6-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="529d6-225">Svcutil.exe を実行する場合、Svcutil.exe に WSDL インポートの拡張を読み込ませるために次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="529d6-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="529d6-226">/SvcutilConfig を使用して、構成ファイルに Svcutil.exe:\<ファイル >。</span><span class="sxs-lookup"><span data-stu-id="529d6-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="529d6-227">Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="529d6-228">`UdpBindingElementImporter` 型は、`IWsdlImportExtension` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="529d6-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="529d6-229">`ImportEndpoint` メソッドは、次のようにして WSDL ポートからアドレスをインポートします。</span><span class="sxs-lookup"><span data-stu-id="529d6-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="529d6-230">ポリシー サポートの追加</span><span class="sxs-lookup"><span data-stu-id="529d6-230">Adding Policy Support</span></span>  
 <span data-ttu-id="529d6-231">カスタム バインド要素では、WSDL バインディング内のポリシー アサーションをエクスポートして、サービス エンドポイントでそのバインド要素の機能を表現します。</span><span class="sxs-lookup"><span data-stu-id="529d6-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="529d6-232">ポリシーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="529d6-232">Policy Export</span></span>  
 <span data-ttu-id="529d6-233">`UdpTransportBindingElement`実装を型`IPolicyExportExtension`ポリシーをエクスポートするためのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="529d6-234">その結果、`System.ServiceModel.MetadataExporter` には、これを含む任意のバインディングでのポリシーの生成時に `UdpTransportBindingElement` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="529d6-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="529d6-235">マルチキャスト モードの場合、`IPolicyExportExtension.ExportPolicy` には UDP のアサーションや他のアサーションが追加されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="529d6-236">これは、マルチキャスト モードは通信スタックの構築方法に影響を与えるため、両方の側において調整される必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="529d6-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="529d6-237">カスタム トランスポート バインド要素はアドレス指定の処理を実行するため、`IPolicyExportExtension` への `UdpTransportBindingElement` の実装でも、WS-Addressing ポリシー アサーションのエクスポートが処理されて、使用されている WS-Addressing のバージョンが示されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="529d6-238">ポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="529d6-238">Policy Import</span></span>  
 <span data-ttu-id="529d6-239">ポリシー インポート システムを拡張するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="529d6-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="529d6-240">次に、登録されたクラス (`IPolicyImporterExtension`) から `UdpBindingElementImporter` を実装します。</span><span class="sxs-lookup"><span data-stu-id="529d6-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="529d6-241">`ImportPolicy()` で、名前空間内のアサーションを調べ、そのアサーションを処理してトランスポートを生成し、マルチキャストであるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="529d6-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="529d6-242">さらに、処理したアサーションをバインディング アサーションの一覧から削除する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="529d6-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="529d6-243">Svcutil.exe を実行する場合、ここでも、統合用に次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="529d6-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="529d6-244">/SvcutilConfig を使用して、構成ファイルに Svcutil.exe:\<ファイル >。</span><span class="sxs-lookup"><span data-stu-id="529d6-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="529d6-245">Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="529d6-246">標準バインディング要素の追加</span><span class="sxs-lookup"><span data-stu-id="529d6-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="529d6-247">バインディング要素は、次の 2 つの方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-247">Our binding element can be used in the following two ways:</span></span>  
  
-   <span data-ttu-id="529d6-248">カスタム バインディングの使用 : カスタム バインディングを使用すれば、バインディング要素の任意のセットに基づいて独自のバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
-   <span data-ttu-id="529d6-249">バインディング要素が含まれるシステム指定のバインディングを使用することによって、</span><span class="sxs-lookup"><span data-stu-id="529d6-249">By using a system-provided binding that includes our binding element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="529d6-250"> は `BasicHttpBinding`、`NetTcpBinding`、`WsHttpBinding` など、これらのシステム定義バインディングの数々を提供します。</span><span class="sxs-lookup"><span data-stu-id="529d6-250"> provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="529d6-251">これらの各バインドは、適切に定義されたプロファイルに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="529d6-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="529d6-252">このサンプルでは、プロファイル バインディングを、`SampleProfileUdpBinding` から派生した <xref:System.ServiceModel.Channels.Binding> に実装します。</span><span class="sxs-lookup"><span data-stu-id="529d6-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="529d6-253">`SampleProfileUdpBinding` は、`UdpTransportBindingElement`、`TextMessageEncodingBindingElement CompositeDuplexBindingElement`、および `ReliableSessionBindingElement` の、最大 4 つのバインディング要素を格納します。</span><span class="sxs-lookup"><span data-stu-id="529d6-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="529d6-254">カスタムの標準バインディング インポーターの追加</span><span class="sxs-lookup"><span data-stu-id="529d6-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="529d6-255">Svcutil.exe と `WsdlImporter` 型は、既定でシステム定義のバインディングを識別してインポートします。</span><span class="sxs-lookup"><span data-stu-id="529d6-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="529d6-256">これ以外の場合、バインディングは、`CustomBinding` インスタンスとしてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="529d6-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="529d6-257">Svcutil.exe と `WsdlImporter` を有効にして `SampleProfileUdpBinding` をインポートする場合、`UdpBindingElementImporter` もカスタムの標準バインディング インポーターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="529d6-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="529d6-258">カスタムの標準バインディング インポーターは、`ImportEndpoint` インターフェイスの `IWsdlImportExtension` メソッドを実装しており、メタデータからインポートされた `CustomBinding` インスタンスを調べて、これが特定の標準バインディングによって生成されたものであるかどうかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="529d6-259">一般に、カスタムの標準バインディング インポーターを実装すると、インポートしたバインド要素のプロパティを調べて、標準バインディングによって設定されたプロパティのみが変更され、その他のすべてのプロパティは既定のままであることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="529d6-260">標準バインディング インポーターを実装する場合の基本的な方法は、標準バインディングのインスタンスを作成し、標準バインディングがサポートするバインド要素のプロパティを標準バインディング インスタンスに反映し、標準バインディングのバインド要素とインポートしたバインド要素とを比較します。</span><span class="sxs-lookup"><span data-stu-id="529d6-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="529d6-261">構成サポートの追加</span><span class="sxs-lookup"><span data-stu-id="529d6-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="529d6-262">構成を通じてトランスポートを公開するには、2 つの構成セクションを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="529d6-263">1 つ目のクラスは、`BindingElementExtensionElement` の `UdpTransportBindingElement` です。</span><span class="sxs-lookup"><span data-stu-id="529d6-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="529d6-264">これは、`CustomBinding` の実装がバインディング要素を参照するためのものです。</span><span class="sxs-lookup"><span data-stu-id="529d6-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="529d6-265">2 つ目のクラスは、`Configuration` の `SampleProfileUdpBinding` です。</span><span class="sxs-lookup"><span data-stu-id="529d6-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="529d6-266">バインディング要素の拡張要素</span><span class="sxs-lookup"><span data-stu-id="529d6-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="529d6-267">セクション `UdpTransportElement` は `BindingElementExtensionElement` で、`UdpTransportBindingElement` を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="529d6-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="529d6-268">いくつかの基本的なオーバーライドを行うことで、構成セクションの名前、バインド要素の種類とバインド要素の作成方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="529d6-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="529d6-269">その後、次のコードに示すように、拡張セクションを構成ファイルに登録できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="529d6-270">この拡張は、UDP をトランスポートとして使用するためにカスタム バインディングから参照されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="529d6-271">バインディング セクション</span><span class="sxs-lookup"><span data-stu-id="529d6-271">Binding Section</span></span>  
 <span data-ttu-id="529d6-272">セクション `SampleProfileUdpBindingCollectionElement` は `StandardBindingCollectionElement` で、`SampleProfileUdpBinding` を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="529d6-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="529d6-273">実装の大部分は `SampleProfileUdpBindingConfigurationElement` で代行されます。これは `StandardBindingElement` の派生です。</span><span class="sxs-lookup"><span data-stu-id="529d6-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="529d6-274">`SampleProfileUdpBindingConfigurationElement`でプロパティに対応するプロパティを持つ`SampleProfileUdpBinding`、およびからマップする関数、`ConfigurationElement`バインドします。</span><span class="sxs-lookup"><span data-stu-id="529d6-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="529d6-275">最後に、`OnApplyConfiguration` 内で `SampleProfileUdpBinding` メソッドをオーバーライドします。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="529d6-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="529d6-276">このハンドラを構成システムに登録するには、次のセクションを関連する構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="529d6-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="529d6-277">これは serviceModel 構成セクションから参照できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="529d6-278">UDP テスト サービスとクライアント</span><span class="sxs-lookup"><span data-stu-id="529d6-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="529d6-279">このサンプルのトランスポートを使用するテスト コードは、UdpTestService ディレクトリと UdpTestClient ディレクトリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="529d6-280">サービス コードは 2 つのテストで構成されています。1 つ目はコードからバインディングとエンドポイントをセットアップするテストで、2 つ目は構成を使用してバインディングとエンドポイントをセットアップするテストです。</span><span class="sxs-lookup"><span data-stu-id="529d6-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="529d6-281">両方のテストで、2 つのエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="529d6-281">Both tests use two endpoints.</span></span> <span data-ttu-id="529d6-282">1 つのエンドポイントを使用して、`SampleUdpProfileBinding`で[ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 'éý'`true`です。</span><span class="sxs-lookup"><span data-stu-id="529d6-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `true`.</span></span> <span data-ttu-id="529d6-283">もう 1 つのエンドポイントでは、 `UdpTransportBindingElement` が含まれるカスタム バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="529d6-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="529d6-284">これを使用すると、`SampleUdpProfileBinding`で[ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 'éý'`false`です。</span><span class="sxs-lookup"><span data-stu-id="529d6-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `false`.</span></span> <span data-ttu-id="529d6-285">両方のテストでサービスが作成され、各バインドのエンドポイントが追加されてサービスが開きます。その後 Enter キーを押すと、サービスが閉じます。</span><span class="sxs-lookup"><span data-stu-id="529d6-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="529d6-286">このサービス テスト アプリケーションを開始すると、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="529d6-287">次に、公開されたエンドポイントに対してクライアント テスト アプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="529d6-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="529d6-288">このクライアント テスト アプリケーションでは、各エンドポイントに対してクライアントが作成され、5 つのメッセージが各エンドポイントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="529d6-289">クライアントでの出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="529d6-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="529d6-290">サービスでのすべての出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="529d6-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="529d6-291">構成を使用して公開されたエンドポイントに対してクライアント アプリケーションを実行するには、サービス側で Enter キーを押してテスト クライアントを再実行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="529d6-292">サービスには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="529d6-293">クライアントを再実行すると、前と同じ結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="529d6-294">Svcutil.exe を使用してクライアント コードと構成を再生成するには、サービス アプリケーションを開始し、その後、サンプルのルート ディレクトリで次のように Svcutil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="529d6-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="529d6-295">Svcutil.exe を実行しても `SampleProfileUdpBinding` のバインディング拡張構成は生成されません。したがって、次のコードを手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="529d6-296">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="529d6-296">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="529d6-297">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="529d6-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="529d6-298">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="529d6-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="529d6-299">前の「UDP テスト サービスとクライアント」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="529d6-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="529d6-300">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="529d6-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="529d6-301">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="529d6-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="529d6-302">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="529d6-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="529d6-303">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="529d6-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`

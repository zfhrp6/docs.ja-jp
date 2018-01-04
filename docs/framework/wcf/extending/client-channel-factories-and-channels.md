---
title: "クライアント : チャネル ファクトリとチャネル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82e42a3dd4fbb29970b8e1a17333b66d85d2887b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="27b4c-102">クライアント : チャネル ファクトリとチャネル</span><span class="sxs-lookup"><span data-stu-id="27b4c-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="27b4c-103">ここでは、チャネル ファクトリとチャネルの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="27b4c-104">チャネル ファクトリとチャネル</span><span class="sxs-lookup"><span data-stu-id="27b4c-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="27b4c-105">チャネル ファクトリには、チャネルを作成する役割があります。</span><span class="sxs-lookup"><span data-stu-id="27b4c-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="27b4c-106">チャネル ファクトリによって作成されるチャネルは、メッセージの送信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="27b4c-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="27b4c-107">このチャネルは、上の層からメッセージを取得し、必要な処理を実行し、そのメッセージを下の層に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27b4c-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="27b4c-108">このプロセスを説明する図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="27b4c-109">![クライアント ファクトリおよびチャネル](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="27b4c-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="27b4c-110">チャネル ファクトリがチャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="27b4c-111">終了時に、チャネル ファクトリは、作成したチャネルのうちまだ閉じていないチャネルを閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="27b4c-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="27b4c-112">チャネル リスナーを閉じたとき、新しいチャネルの受け入れだけが停止され、既存のチャネルは開いたままで、メッセージの受信を続行できるので、ここに示すモデルは非対称です。</span><span class="sxs-lookup"><span data-stu-id="27b4c-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="27b4c-113"> には、このプロセスに対する基本クラス ヘルパーが用意されています</span><span class="sxs-lookup"><span data-stu-id="27b4c-113"> provides base class helpers for this process.</span></span> <span data-ttu-id="27b4c-114">(このトピックで説明するチャネルのヘルパー クラスのダイアグラムの場合、次を参照してください[チャネル モデルの概要](../../../../docs/framework/wcf/extending/channel-model-overview.md)。)。</span><span class="sxs-lookup"><span data-stu-id="27b4c-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="27b4c-115"><xref:System.ServiceModel.Channels.CommunicationObject>クラスが実装する<xref:System.ServiceModel.ICommunicationObject>し、適用のステップ 2 で説明されているステート マシン[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)です。</span><span class="sxs-lookup"><span data-stu-id="27b4c-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="27b4c-116">「<xref:System.ServiceModel.Channels.ChannelManagerBase>クラスが実装する<xref:System.ServiceModel.Channels.CommunicationObject>の統一された基本クラスを提供し<xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType>と<xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="27b4c-116">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="27b4c-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="27b4c-118">'<xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスが実装する<xref:System.ServiceModel.Channels.ChannelManagerBase>と<xref:System.ServiceModel.Channels.IChannelFactory>し、統合、`CreateChannel`を 1 つにオーバー ロード`OnCreateChannel`抽象メソッドです。</span><span class="sxs-lookup"><span data-stu-id="27b4c-118">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="27b4c-119">「<xref:System.ServiceModel.Channels.ChannelListenerBase>クラスが実装する<xref:System.ServiceModel.Channels.IChannelListener>です。</span><span class="sxs-lookup"><span data-stu-id="27b4c-119">The``<xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="27b4c-120">基本状態管理を行います。</span><span class="sxs-lookup"><span data-stu-id="27b4c-120">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="27b4c-121">次の説明がに基づいて、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="27b4c-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="27b4c-122">チャネル ファクトリの作成</span><span class="sxs-lookup"><span data-stu-id="27b4c-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="27b4c-123">`UdpChannelFactory` は <xref:System.ServiceModel.Channels.ChannelFactoryBase> から派生します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="27b4c-124">サンプルでは、<xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> をオーバーライドして、メッセージ エンコーダーのメッセージ バージョンにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="27b4c-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="27b4c-125">さらに、<xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> をオーバーライドして、ステート マシンの移行時に <xref:System.ServiceModel.Channels.BufferManager> のインスタンスを破棄します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="27b4c-126">UDP 出力チャネル</span><span class="sxs-lookup"><span data-stu-id="27b4c-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="27b4c-127">`UdpOutputChannel` では、<xref:System.ServiceModel.Channels.IOutputChannel> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="27b4c-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="27b4c-128">このコンストラクターは、引数を検証し、渡される <xref:System.Net.EndPoint> に基づいて出力先の <xref:System.ServiceModel.EndpointAddress> オブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="27b4c-129"><xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> のオーバーライドによって、この <xref:System.Net.EndPoint> にメッセージを送信するために使用されるソケットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="27b4c-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 <span data-ttu-id="27b4c-130">チャネルが閉じる際には、正常終了することも異常終了することもあります。</span><span class="sxs-lookup"><span data-stu-id="27b4c-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="27b4c-131">チャネルが正常に閉じた場合はソケットも終了し、基本クラスの `OnClose` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="27b4c-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="27b4c-132">このときに例外がスローされると、インフラストラクチャによって `Abort` が呼び出され、チャネルがクリーンアップされます。</span><span class="sxs-lookup"><span data-stu-id="27b4c-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="27b4c-133">実装`Send()`と`BeginSend()` /`EndSend()`です。</span><span class="sxs-lookup"><span data-stu-id="27b4c-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="27b4c-134">この実装は、2 つの主要セクションに分かれます。</span><span class="sxs-lookup"><span data-stu-id="27b4c-134">This breaks down into two main sections.</span></span> <span data-ttu-id="27b4c-135">最初に、メッセージを次のようにシリアル化してバイト配列で表します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-135">First serialize the message into a byte array:</span></span>  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="27b4c-136">次に、結果として生成されたデータを次のようにネットワークに送信します。</span><span class="sxs-lookup"><span data-stu-id="27b4c-136">Then send the resulting data on the wire:</span></span>  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="27b4c-137">参照</span><span class="sxs-lookup"><span data-stu-id="27b4c-137">See Also</span></span>  
 [<span data-ttu-id="27b4c-138">チャネルの開発</span><span class="sxs-lookup"><span data-stu-id="27b4c-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)

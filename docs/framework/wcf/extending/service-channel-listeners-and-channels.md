---
title: "サービス : チャネル リスナーとチャネル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6f0eeb0d859f6fe508019085709464fab806ea2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service-channel-listeners-and-channels"></a>サービス : チャネル リスナーとチャネル
チャネル オブジェクトには、チャネル、チャネル リスナー、およびチャネル ファクトリという 3 つのカテゴリがあります。 チャネルはアプリケーションおよびチャネル スタックとのインターフェイスです。 チャネル リスナーは受信 (またはリッスン) する側のチャネルを作成する役割を果たします。通常は、新しい受信メッセージまたは接続への応答を行います。 チャネル ファクトリは送信側のチャネルを作成し、エンドポイントとの通信を開始する役割を果たします。  
  
## <a name="channel-listeners-and-channels"></a>チャネル リスナーとチャネル  
 チャネル リスナーには、チャネルを作成し、下の層またはネットワークからメッセージを受信する役割があります。 受信されたメッセージは、チャネル リスナーによって作成されるチャネルを使用して、上の層に配信されます。  
  
 メッセージを受信して上の層に配信するプロセスを次の図に示します。  
  
 ![チャネル リスナーとチャネル](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")  
メッセージを受信してチャネル経由で上の層に配信するチャネル リスナー。  
  
 このプロセスは、概念上、各チャネル内のキューとしてモデル化できますが、実際には実装がキューを使用しない場合もあります。 チャネル リスナーには、下の層またはネットワークからメッセージを受信し、キューに配置する役割があります。 また、チャネルには、キューからメッセージを取得し、上の層から (たとえば、チャネル上で `Receive` を呼び出すことによって) メッセージが要求されたときにそのメッセージを渡す役割があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、このプロセスに対する基本クラス ヘルパーが用意されています (このトピックで説明するチャネルのヘルパー クラスのダイアグラムの場合、次を参照してください[チャネル モデルの概要](../../../../docs/framework/wcf/extending/channel-model-overview.md)。)。  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject>クラスが実装する<xref:System.ServiceModel.ICommunicationObject>し、適用のステップ 2 で説明されているステート マシン[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)です。  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> クラスには <xref:System.ServiceModel.Channels.CommunicationObject> が実装され、<xref:System.ServiceModel.Channels.ChannelFactoryBase> と <xref:System.ServiceModel.Channels.ChannelListenerBase> の統合基本クラスが提供されます。 <xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。  
  
-   '<xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスが実装する<xref:System.ServiceModel.Channels.ChannelManagerBase>と<xref:System.ServiceModel.Channels.IChannelFactory>し、統合、`CreateChannel`を 1 つにオーバー ロード`OnCreateChannel`抽象メソッドです。  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> クラスは、<xref:System.ServiceModel.Channels.IChannelListener> を実装しています。 基本状態管理を行います。  
  
 次の説明がに基づいて、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。  
  
## <a name="creating-a-channel-listener"></a>チャネル リスナーの作成  
 ' から派生して、サンプルを実装する UdpChannelListener、<xref:System.ServiceModel.Channels.ChannelListenerBase>クラスです。 単一の UDP ソケットを使用して、データグラムを受信します。 `OnOpen` メソッドは、非同期ループ内で UDP ソケットを使用してデータを受信します。 その後、メッセージ エンコーディング システムを使用して、データを次のようにメッセージに変換します。  
  
```  
message = UdpConstants.MessageEncoder.ReadMessage(  
  new ArraySegment<byte>(buffer, 0, count),   
  bufferManager  
);  
```  
  
 複数のソースから到着するメッセージが同じデータグラム チャネルで表されるので、`UdpChannelListener` はシングルトン リスナーです。 ほとんどの 1 つのアクティブである<xref:System.ServiceModel.Channels.IChannel>'、時に、このリスナーに関連付けられています。 このサンプルでは、<xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> メソッドによって返されるチャネルがその後破棄される場合のみ、もう 1 つ生成されます。 メッセージが受信されると、このシングルトン チャネルのキューに置かれます。  
  
### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` クラスは、<xref:System.ServiceModel.Channels.IInputChannel> を実装しています。 このクラスは `UdpChannelListener` のソケットによって設定される受信メッセージのキューで構成されています。 これらのメッセージは、<xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> メソッドによってキューから削除されます。

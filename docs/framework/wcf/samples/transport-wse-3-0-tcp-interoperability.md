---
title: 'トランスポート : WSE 3.0 TCP 相互運用性'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ce948a9239e7a8171424fa9f1cf0fa8624d0156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="transport-wse-30-tcp-interoperability"></a>トランスポート : WSE 3.0 TCP 相互運用性
WSE 3.0 TCP 相互運用性トランスポートのサンプルでは、カスタムの Windows Communication Foundation (WCF) トランスポートとして、TCP 二重セッションを実装する方法を示します。 さらに、チャネル レイヤーの拡張機能を使用して、ネットワーク経由で既存の配置システムと連結する方法も示します。 この [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] カスタム トランスポートを作成する方法を、次の手順に示します。  
  
1.  まず TCP ソケットを使用して、DIME フレームを使用する <xref:System.ServiceModel.Channels.IDuplexSessionChannel> のクライアント実装とサーバー実装を作成し、メッセージ境界を決定します。  
  
2.  WSE TCP サービスに接続してクライアント <xref:System.ServiceModel.Channels.IDuplexSessionChannel> 経由でフレーム メッセージを送信する、チャネル ファクトリを作成します。  
  
3.  受信 TCP 接続を受け入れて対応するチャネルを作成するチャネル リスナーを作成します。  
  
4.  ネットワーク固有の例外が、<xref:System.ServiceModel.CommunicationException> の適切な派生クラスに標準化されていることを確認します。  
  
5.  チャネル スタックにカスタム トランスポートを追加するバインド要素を追加します。 詳細については、[バインド要素の追加] を参照してください。  
  
## <a name="creating-iduplexsessionchannel"></a>IDuplexSessionChannel の作成  
 WSE 3.0 TCP 相互運用性トランスポートを作成するには、まず、<xref:System.ServiceModel.Channels.IDuplexSessionChannel> 上に <xref:System.Net.Sockets.Socket> の実装を作成します。 `WseTcpDuplexSessionChannel` は、<xref:System.ServiceModel.Channels.ChannelBase> から派生します。 メッセージ送信のロジックは、(1) メッセージをバイトにエンコードし、(2) それらのバイトをフレーム化してネットワーク上に送信するという、2 つの主要部分で構成されます。  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 さらに、Send() 呼び出しが IDuplexSessionChannel の順序の保証を保持し、基になるソケットに対する呼び出しが正しく同期されるように、ロックを取得します。  
  
 `WseTcpDuplexSessionChannel` は、<xref:System.ServiceModel.Channels.MessageEncoder> と byte[] を相互に変換するために、<xref:System.ServiceModel.Channels.Message> を使用します。 `WseTcpDuplexSessionChannel` はトランスポートであるため、チャネルが構成されたリモート アドレスの適用も行います。 `EncodeMessage` は、この変換ロジックをカプセル化します。  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message> がバイトにエンコードされたら、ネットワーク上に送信する必要があります。 これを行うには、メッセージ境界を定義するシステムが必要です。 WSE 3.0 のバージョンを使用する[DIME](http://go.microsoft.com/fwlink/?LinkId=94999)フレーミング プロトコルにします。 `WriteData` はこのフレーム ロジックをカプセル化して、byte[] を一連の DIME レコードにラップします。  
  
 メッセージ受信用のロジックは、上記のロジックとほぼ同じです。 複雑な点は、主に、読み取られたソケットによって返されるバイトが、要求されたバイトよりも少ない場合があることに関する処理です。 メッセージを受信するには、`WseTcpDuplexSessionChannel` がネットワーク経由でないバイトを読み取って DIME フレームを復号化し、その後<xref:System.ServiceModel.Channels.MessageEncoder> を使用して byte[] を <xref:System.ServiceModel.Channels.Message> に変換します。  
  
 基本の `WseTcpDuplexSessionChannel` は、接続されたソケットを受信することを前提とします。 この基本クラスでは、ソケットのシャットダウンが処理されます。 ソケットの終了と連動する場所は、次の 3 つです。  
  
-   OnAbort -- ソケットを異常終了します (強制終了)。  
  
-   On[Begin]Close -- ソケットを正常に終了します (正常終了)。  
  
-   session.CloseOutputSession --  送信データ ストリームをシャットダウンします (半終了)。  
  
## <a name="channel-factory"></a>チャネル ファクトリ  
 TCP トランスポートを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装を作成します。  
  
-   `WseTcpChannelFactory` 派生した<xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >。 このファクトリは、`OnCreateChannel` をオーバーライドして、クライアント チャネルを作成します。  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` ベースにロジックを追加`WseTcpDuplexSessionChannel`に TCP サーバーに接続する`channel.Open`時間。 まず、次のコードに示すようにホスト名を解決して IP アドレスに変換します。  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   次のコードに示すように、ホスト名はループ内で最初に利用可能な IP アドレスに接続されます。  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   チャネル コントラクトの一部として、`SocketException` の <xref:System.ServiceModel.CommunicationException> など、ドメイン固有の任意の例外をラップします。  
  
## <a name="channel-listener"></a>チャネル リスナー  
 TCP トランスポートを記述する次の手順では、サーバー チャネルを受け入れるための <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。  
  
-   `WseTcpChannelListener` 派生した<xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > および [Begin] Open と On [Begin] の上書きに近いリッスン ソケットの有効期間を制御します。 OnOpen で、IP_ANY でリッスンするソケットを作成します。 より高度な実装では、同様に IPv6 でリッスンする 2 つ目のソケットを作成できます。 そのような実装では、IP アドレスをホスト名で指定することもできます。  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 新しいソケットが受け入れられると、サーバー チャネルがこのソケットで初期化されます。 すべての入出力は既に基本クラスに実装されているので、このチャネルでソケットの初期化に対応します。  
  
## <a name="adding-a-binding-element"></a>バインド要素の追加  
 ファクトリおよびチャネルを作成したら、バインディングを使用してそれらを ServiceModel ランタイムに開示する必要があります。 バインディングは、サービス アドレスに関連する通信スタックを表すバインド要素のコレクションです。 スタックの各要素は、バインディング要素によって表されます。  
  
 このサンプルでは、バインディング要素は `WseTcpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。 <xref:System.ServiceModel.Channels.IDuplexSessionChannel> がサポートされており、次のメソッドをオーバーライドして、バインディングに関連したファクトリを作成します。  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 また、この要素には、`BindingElement` を複製したり、スキーム (wse.tcp) を返したりするためのメンバーも含まれます。  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP テスト コンソール  
 このサンプルのトランスポートを使用するテスト コードは、TestCode.cs で使用できます。 WSE `TcpSyncStockService` サンプルの設定方法を次の手順に示します。  
  
 このテスト コードでは、MTOM をエンコーディングとして使用し、`WseTcpTransport` をトランスポートとして使用するカスタム バインディングを作成します。 さらに、AddressingVersion を、次のコードに示すように WSE 3.0 に準拠するように設定します。  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 テスト コードは 2 つのテストで構成されます。1 つ目のテストは、WSE 3.0 WSDL から生成されたコードを使用して型指定のあるクライアントを設定します。 2 つ目のテストは、メッセージを直接チャネル API 上に送信することによって、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] をクライアントとサーバーの両方として使用します。  
  
 このサンプルを実行すると、次の出力が予測されます。  
  
 クライアント:  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 サーバー:  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  このサンプルを実行するには、WSE 3.0 と WSE `TcpSyncStockService` サンプルがインストールされている必要があります。 ダウンロードできる[MSDN から WSE 3.0](http://go.microsoft.com/fwlink/?LinkId=95000)です。  
  
> [!NOTE]
>  [!INCLUDE[lserver](../../../../includes/lserver-md.md)] では WSE 3.0 がサポートされていないので、このオペレーティング システムでは `TcpSyncStockService` サンプルをインストールすることも、実行することもできません。  
  
1.  `TcpSyncStockService` サンプルをインストールしたら、次の手順を実行します。  
  
    1.  Visual Studio で `TcpSyncStockService` を開きます (TcpSyncStockService サンプルは WSE 3.0 と共にインストールされます。 このサンプル コードの一部ではありません)。  
  
    2.  StockService プロジェクトをスタートアップ プロジェクトに設定します。  
  
    3.  StockService プロジェクトの StockService.cs を開き、`StockService` クラスの [Policy] 属性をコメント化します。 これにより、サンプルのセキュリティが無効になります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は WSE 3.0 のセキュリティで保護されたエンドポイントと相互運用できますが、このサンプルではカスタム TCP トランスポートに重点を置くため、セキュリティを無効にします。  
  
    4.  F5 キーを押して、`TcpSyncStockService` を開始します。 サービスが新しいコンソール ウィンドウで開始します。  
  
    5.  Visual Studio で、この TCP トランスポートのサンプルを開きます。  
  
    6.  TestCode.cs 内の hostname 変数の値を、`TcpSyncStockService` が実行されているコンピューター名に一致するように更新します。  
  
    7.  F5 キーを押して、TCP トランスポートのサンプルを開始します。  
  
    8.  TCP トランスポートのテスト クライアントが、新しいコンソールで開始します。 クライアントはサービスに株価情報を要求し、その結果がコンソール ウィンドウに表示されます。  
  
## <a name="see-also"></a>関連項目

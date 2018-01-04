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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1933d216f991b78e21a56ec67826dce0b4a7b24a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="transport-udp"></a>トランスポート: UDP
UDP トランスポートのサンプルでは、UDP ユニキャストとマルチキャストを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] カスタム トランスポートとして実装する方法を示します。 このサンプルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でカスタム トランスポートを作成するための推奨手順について説明します。作成時には、チャネル フレームワークと次に示す [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のベスト プラクティスを使用します。 カスタム トランスポートを作成する手順は、次のとおりです。  
  
1.  チャネルの決定[メッセージ交換パターン](#MessageExchangePatterns)(IOutputChannel、IInputChannel、IDuplexChannel、IRequestChannel、または IReplyChannel) ChannelFactory と ChannelListener でサポートされます。 次に、こうしたインターフェイスのセッションフル バリエーションをサポートするかどうかを決定します。  
  
2.  メッセージ交換パターンをサポートするチャネル ファクトリおよびリスナーを作成します。  
  
3.  ネットワーク固有の例外が、<xref:System.ServiceModel.CommunicationException> の適切な派生クラスに標準化されていることを確認します。  
  
4.  追加、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素をチャネル スタックにカスタム トランスポートを追加します。 詳細については、次を参照してください。[バインド要素の追加](#AddingABindingElement)です。  
  
5.  バインド要素拡張セクションを追加して、新しいバインド要素を構成システムに公開します。  
  
6.  他のエンドポイントに機能を伝達するメタデータ拡張を追加します。  
  
7.  適切に定義されたプロファイルに従って、バインド要素のスタックを事前構成するバインディングを追加します。 詳細については、次を参照してください。[標準のバインディングの追加](#AddingAStandardBinding)です。  
  
8.  構成システムにバインディングを開示する、バインディング セクションおよびバインド構成要素を追加します。 詳細については、次を参照してください。[構成サポートの追加](#AddingConfigurationSupport)です。  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>メッセージ交換パターン  
 カスタム トランスポートを記述する最初の手順として、どのメッセージ交換パターン (MEP) がトランスポートに必要かを判断します。 次の 3 つの MEP から選択できます。  
  
-   データグラム (IInputChannel/IOutputChannel)  
  
     データグラム MEP を使用している場合、クライアントは "ファイア アンド フォーゲット (撃ち放し)" の交換を使用してメッセージを送信します。 このような交換では、配信の成否について帯域外での確認が必要になります。 メッセージが移動中に失われて、サービスに到達しない可能性があります。 クライアントで送信操作が正常に完了したとしても、リモート エンドポイントでメッセージが受信されたとは限りません。 データグラムはメッセージングの基礎となるビルド ブロックであり、その上に信頼できるプロトコルや安全なプロトコルなどの独自のプロトコルを構築できます。 クライアント データグラム チャネルには、<xref:System.ServiceModel.Channels.IOutputChannel> インターフェイスが実装され、サービス データグラム チャネルには <xref:System.ServiceModel.Channels.IInputChannel> インターフェイスが実装されます。  
  
-   要求 - 応答 (IRequestChannel/IReplyChannel)  
  
     この MEP では、メッセージが送信されて、応答が受信されます。 パターンは、要求 - 応答のペアで構成されます。 要求 - 応答呼び出しの例には、リモート プロシージャ コール (RPC) やブラウザ GET などがあります。 このパターンは、半二重とも呼ばれます。 この MEP では、クライアント チャネルには <xref:System.ServiceModel.Channels.IRequestChannel> が実装され、サービス チャネルには <xref:System.ServiceModel.Channels.IReplyChannel> が実装されます。  
  
-   二重 (IDuplexChannel)  
  
     二重 MEP では、クライアントにより任意の数のメッセージを送信して、任意の順序で受信できます。 二重 MEP は、話される語の 1 つずつがメッセージである電話の会話に似ています。 この MEP ではどちらの側も送信および受信できるので、クライアントおよびサービス チャネルによって実装されるインターフェイスは <xref:System.ServiceModel.Channels.IDuplexChannel> になります。  
  
 これらの MEP では、それぞれセッションをサポートすることもできます。 セッション対応チャネルにより追加される機能として、チャネルで送信および受信されるすべてのメッセージが関連付けられます。 要求/応答パターンはスタンドアロンの 2 メッセージ セッションで、要求と応答が相互に関連付けられています。 一方、セッションをサポートする要求 - 応答パターンは、そのチャネルのすべての要求/応答ペアが互いに関連付けられることを意味しています。 これにより、合計で 6 つの MEP (データグラム、要求 - 応答、二重、セッション対応データグラム、セッション対応要求 - 応答、およびセッション対応二重) を選択できます。  
  
> [!NOTE]
>  UDP トランスポートでは、サポートされている MEP はデータグラムだけです。これは、UDP が "ファイア アンド フォーゲット (撃ち放し)" のプロトコルだからです。  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject および WCF オブジェクトのライフサイクル  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、通信に使用される <xref:System.ServiceModel.Channels.IChannel>、<xref:System.ServiceModel.Channels.IChannelFactory>、および <xref:System.ServiceModel.Channels.IChannelListener> などのオブジェクトのライフサイクルの管理に使用される共通ステート マシンです。 これらの通信オブジェクトには、5 つの状態があります。 これらの状態は、<xref:System.ServiceModel.CommunicationState> 列挙値で表され、次のようになります。  
  
-   Created: <xref:System.ServiceModel.ICommunicationObject> が初めてインスタンス化されたときの状態です。 この状態では、入出力 (I/O) は行われません。  
  
-   Opening: <xref:System.ServiceModel.ICommunicationObject.Open%2A> が呼び出されると、オブジェクトはこの状態に移行します。 この時点では、プロパティは不変であり、入出力を開始できます。 この移行は、Created 状態からのみ有効です。  
  
-   Opened: オープン処理が完了すると、オブジェクトはこの状態に移行します。 この移行は、Opening 状態からのみ有効です。 この時点では、オブジェクトは完全に転送に使用可能です。  
  
-   Closing: 正常なシャットダウンを行うために <xref:System.ServiceModel.ICommunicationObject.Close%2A> が呼び出されると、オブジェクトはこの状態に移行します。 この移行は、Opened 状態からのみ有効です。  
  
-   Closed: Closed 状態では、オブジェクトは使用できません。 通常、ほとんどの構成には検査中もアクセスできますが、通信が発生することはありません。 この状態は、破棄されるのと同じです。  
  
-   Faulted: Faulted 状態では、オブジェクトにアクセスして検査できますが、使用することはできません。 回復不可能なエラーが発生した場合、オブジェクトはこの状態に移行します。 この状態からの唯一の有効な移行、`Closed`状態です。  
  
 各状態移行には、発生するイベントがあります。 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> メソッドはいつでも呼び出すことができます。このメソッドを呼び出すことにより、オブジェクトは現在の状態から直ちに Closed 状態に移行します。 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> を呼び出すと、完了していない作業が終了します。  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>チャネル ファクトリとチャネル リスナー  
 カスタム トランスポートを記述する次の手順では、クライアント チャネルでの <xref:System.ServiceModel.Channels.IChannelFactory> の実装とサービス チャネルでの <xref:System.ServiceModel.Channels.IChannelListener> の実装を作成します。 チャネル レイヤーでは、チャネルの構築にファクトリ パターンが使用されます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、このプロセスに対する基本クラス ヘルパーが用意されています  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> クラスには <xref:System.ServiceModel.ICommunicationObject> が実装され、前述の手順 2. で説明したステート マシンが強制実行されます。 

-   「<xref:System.ServiceModel.Channels.ChannelManagerBase>クラスが実装する<xref:System.ServiceModel.Channels.CommunicationObject>の統一された基本クラスを提供し<xref:System.ServiceModel.Channels.ChannelFactoryBase>と<xref:System.ServiceModel.Channels.ChannelListenerBase>です。 <xref:System.ServiceModel.Channels.ChannelManagerBase> クラスは、<xref:System.ServiceModel.Channels.ChannelBase> を実装する基本クラスである <xref:System.ServiceModel.Channels.IChannel> との組み合わせによって動作します。  
  
-   '<xref:System.ServiceModel.Channels.ChannelFactoryBase>クラスが実装する<xref:System.ServiceModel.Channels.ChannelManagerBase>と<xref:System.ServiceModel.Channels.IChannelFactory>し、統合、`CreateChannel`を 1 つにオーバー ロード`OnCreateChannel`抽象メソッドです。  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> クラスは、<xref:System.ServiceModel.Channels.IChannelListener> を実装しています。 基本状態管理を行います。  
  
 このサンプルのファクトリの実装は UdpChannelFactory.cs に、リスナーの実装は UdpChannelListener.cs に含まれています。 <xref:System.ServiceModel.Channels.IChannel> 実装は、UdpOutputChannel.cs と UdpInputChannel.cs に含まれています。  
  
### <a name="the-udp-channel-factory"></a>UDP チャネル ファクトリ  
 `UdpChannelFactory` は <xref:System.ServiceModel.Channels.ChannelFactoryBase> から派生します。 サンプルでは、<xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> をオーバーライドして、メッセージ エンコーダーのメッセージ バージョンにアクセスできるようにします。 さらに、<xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> をオーバーライドして、ステート マシンの移行時に <xref:System.ServiceModel.Channels.BufferManager> のインスタンスを破棄できるようにします。  
  
#### <a name="the-udp-output-channel"></a>UDP 出力チャネル  
 `UdpOutputChannel` では、<xref:System.ServiceModel.Channels.IOutputChannel> が実装されます。 このコンストラクターは、引数を検証し、渡される <xref:System.Net.EndPoint> に基づいて出力先の <xref:System.ServiceModel.EndpointAddress> オブジェクトを構築します。  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 チャネルが閉じる際には、正常終了することも異常終了することもあります。 チャネルが正常に閉じた場合はソケットも終了し、基本クラスの `OnClose` メソッドが呼び出されます。 このときに例外がスローされると、インフラストラクチャによって `Abort` が呼び出され、チャネルがクリーンアップされます。  
  
```csharp
this.socket.Close(0);  
```  
  
 実装し、`Send()`と`BeginSend()` /`EndSend()`です。 この実装は、2 つの主要セクションに分かれます。 最初に、メッセージを次のようにシリアル化してバイト配列で表します。  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 次に、結果として生成されたデータを次のようにネットワークに送信します。  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 ' から派生して、サンプルを実装する UdpChannelListener、<xref:System.ServiceModel.Channels.ChannelListenerBase>クラスです。 単一の UDP ソケットを使用して、データグラムを受信します。 `OnOpen` メソッドは、非同期ループ内で UDP ソケットを使用してデータを受信します。 その後、メッセージ エンコーディング フレームワークを使用して、データを次のようにメッセージに変換します。  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 複数のソースから到着するメッセージが同じデータグラム チャネルで表されるので、`UdpChannelListener` はシングルトン リスナーです。 ほとんどの場合、1 つはアクティブで<xref:System.ServiceModel.Channels.IChannel>'、時に、このリスナーに関連付けられています。 このサンプルでは、`AcceptChannel` メソッドによって返されるチャネルがその後破棄される場合のみ、もう 1 つ生成されます。 メッセージが受信されると、このシングルトン チャネルのキューに置かれます。  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` クラスは、`IInputChannel` を実装しています。 このクラスは `UdpChannelListener` のソケットによって設定される受信メッセージのキューで構成されています。 これらのメッセージは、`IInputChannel.Receive` メソッドによってキューから削除されます。  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>バインド要素の追加  
 ファクトリおよびチャネルを作成したので、バインディングを使用してそれらを ServiceModel ランタイムに開示する必要があります。 バインディングは、サービス アドレスに関連する通信スタックを表すバインド要素のコレクションです。 スタック内の各要素で表される、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素。  
  
 このサンプルでは、バインディング要素は `UdpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。 バインディングに関連したファクトリを作成すると、次のメソッドが無効になります。  
  
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
  
 また、この要素には、`BindingElement` を複製したり、スキーム (soap.udp) を返したりするためのメンバーも含まれます。  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>トランスポート バインディング要素のメタデータ サポートの追加  
 トランスポートをメタデータ システムに統合するには、ポリシーのインポートとエクスポートの両方をサポートする必要があります。 これにより、バインドからのクライアントを生成する、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。  
  
### <a name="adding-wsdl-support"></a>WSDL サポートの追加  
 バインディングのトランスポート バインド要素は、メタデータのアドレス指定情報のインポートとエクスポートを行います。 SOAP バインディングを使用する場合は、トランスポート バインド要素によっても、メタデータの正しいトランスポート URI がエクスポートされます。  
  
#### <a name="wsdl-export"></a>WSDL エクスポート  
 アドレス指定情報をエクスポートするには、`UdpTransportBindingElement` に `IWsdlExportExtension` インターフェイスを実装します。 `ExportEndpoint` メソッドにより、正しいアドレス指定情報が WSDL ポートに追加されます。  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 エンドポイントが SOAP バインディングを使用する場合、`UdpTransportBindingElement` メソッドの `ExportEndpoint` の実装でも、次のようにトランスポート URI がエクスポートされます。  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL インポート  
 WSDL インポート システムを拡張してアドレスのインポートを処理するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。  
  
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
  
 Svcutil.exe を実行する場合、Svcutil.exe に WSDL インポートの拡張を読み込ませるために次の 2 つのオプションがあります。  
  
1.  /SvcutilConfig を使用して、構成ファイルに Svcutil.exe:\<ファイル >。  
  
2.  Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。  
  
 `UdpBindingElementImporter` 型は、`IWsdlImportExtension` インターフェイスを実装します。 `ImportEndpoint` メソッドは、次のようにして WSDL ポートからアドレスをインポートします。  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>ポリシー サポートの追加  
 カスタム バインド要素では、WSDL バインディング内のポリシー アサーションをエクスポートして、サービス エンドポイントでそのバインド要素の機能を表現します。  
  
#### <a name="policy-export"></a>ポリシーのエクスポート  
 `UdpTransportBindingElement`実装を型`IPolicyExportExtension`ポリシーをエクスポートするためのサポートを追加します。 その結果、`System.ServiceModel.MetadataExporter` には、これを含む任意のバインディングでのポリシーの生成時に `UdpTransportBindingElement` が含まれます。  
  
 マルチキャスト モードの場合、`IPolicyExportExtension.ExportPolicy` には UDP のアサーションや他のアサーションが追加されます。 これは、マルチキャスト モードは通信スタックの構築方法に影響を与えるため、両方の側において調整される必要があるためです。  
  
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
  
 カスタム トランスポート バインド要素はアドレス指定の処理を実行するため、`IPolicyExportExtension` への `UdpTransportBindingElement` の実装でも、WS-Addressing ポリシー アサーションのエクスポートが処理されて、使用されている WS-Addressing のバージョンが示されます。  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>ポリシーのインポート  
 ポリシー インポート システムを拡張するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。  
  
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
  
 次に、登録されたクラス (`IPolicyImporterExtension`) から `UdpBindingElementImporter` を実装します。 `ImportPolicy()` で、名前空間内のアサーションを調べ、そのアサーションを処理してトランスポートを生成し、マルチキャストであるかどうかをチェックします。 さらに、処理したアサーションをバインディング アサーションの一覧から削除する必要もあります。 Svcutil.exe を実行する場合、ここでも、統合用に次の 2 つのオプションがあります。  
  
1.  /SvcutilConfig を使用して、構成ファイルに Svcutil.exe:\<ファイル >。  
  
2.  Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>標準バインディング要素の追加  
 バインディング要素は、次の 2 つの方法で使用できます。  
  
-   カスタム バインディングの使用 : カスタム バインディングを使用すれば、バインディング要素の任意のセットに基づいて独自のバインディングを作成できます。  
  
-   バインディング要素が含まれるシステム指定のバインディングを使用することによって、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は `BasicHttpBinding`、`NetTcpBinding`、`WsHttpBinding` など、これらのシステム定義バインディングの数々を提供します。 これらの各バインドは、適切に定義されたプロファイルに関連付けられます。  
  
 このサンプルでは、プロファイル バインディングを、`SampleProfileUdpBinding` から派生した <xref:System.ServiceModel.Channels.Binding> に実装します。 `SampleProfileUdpBinding` は、`UdpTransportBindingElement`、`TextMessageEncodingBindingElement CompositeDuplexBindingElement`、および `ReliableSessionBindingElement` の、最大 4 つのバインディング要素を格納します。  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>カスタムの標準バインディング インポーターの追加  
 Svcutil.exe と `WsdlImporter` 型は、既定でシステム定義のバインディングを識別してインポートします。 これ以外の場合、バインディングは、`CustomBinding` インスタンスとしてインポートされます。 Svcutil.exe と `WsdlImporter` を有効にして `SampleProfileUdpBinding` をインポートする場合、`UdpBindingElementImporter` もカスタムの標準バインディング インポーターとして機能します。  
  
 カスタムの標準バインディング インポーターは、`ImportEndpoint` インターフェイスの `IWsdlImportExtension` メソッドを実装しており、メタデータからインポートされた `CustomBinding` インスタンスを調べて、これが特定の標準バインディングによって生成されたものであるかどうかを判別できます。  
  
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
  
 一般に、カスタムの標準バインディング インポーターを実装すると、インポートしたバインド要素のプロパティを調べて、標準バインディングによって設定されたプロパティのみが変更され、その他のすべてのプロパティは既定のままであることが検証されます。 標準バインディング インポーターを実装する場合の基本的な方法は、標準バインディングのインスタンスを作成し、標準バインディングがサポートするバインド要素のプロパティを標準バインディング インスタンスに反映し、標準バインディングのバインド要素とインポートしたバインド要素とを比較します。  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>構成サポートの追加  
 構成を通じてトランスポートを公開するには、2 つの構成セクションを実装する必要があります。 1 つ目のクラスは、`BindingElementExtensionElement` の `UdpTransportBindingElement` です。 これは、`CustomBinding` の実装がバインディング要素を参照するためのものです。 2 つ目のクラスは、`Configuration` の `SampleProfileUdpBinding` です。  
  
### <a name="binding-element-extension-element"></a>バインド要素の拡張要素  
 セクション `UdpTransportElement` は `BindingElementExtensionElement` で、`UdpTransportBindingElement` を構成システムに公開します。 いくつかの基本的なオーバーライドを行うことで、構成セクションの名前、バインド要素の種類とバインド要素の作成方法を定義します。 その後、次のコードに示すように、拡張セクションを構成ファイルに登録できます。  
  
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
  
 この拡張は、UDP をトランスポートとして使用するためにカスタム バインディングから参照されます。  
  
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
  
### <a name="binding-section"></a>バインディング セクション  
 セクション `SampleProfileUdpBindingCollectionElement` は `StandardBindingCollectionElement` で、`SampleProfileUdpBinding` を構成システムに公開します。 実装の大部分は `SampleProfileUdpBindingConfigurationElement` で代行されます。これは `StandardBindingElement` の派生です。 `SampleProfileUdpBindingConfigurationElement`でプロパティに対応するプロパティを持つ`SampleProfileUdpBinding`、およびからマップする関数、`ConfigurationElement`バインドします。 最後に、`OnApplyConfiguration` 内で `SampleProfileUdpBinding` メソッドをオーバーライドします。次のサンプル コードを参照してください。  
  
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
  
 このハンドラを構成システムに登録するには、次のセクションを関連する構成ファイルに追加します。  
  
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
  
 これは serviceModel 構成セクションから参照できます。  
  
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
  
## <a name="the-udp-test-service-and-client"></a>UDP テスト サービスとクライアント  
 このサンプルのトランスポートを使用するテスト コードは、UdpTestService ディレクトリと UdpTestClient ディレクトリで使用できます。 サービス コードは 2 つのテストで構成されています。1 つ目はコードからバインディングとエンドポイントをセットアップするテストで、2 つ目は構成を使用してバインディングとエンドポイントをセットアップするテストです。 両方のテストで、2 つのエンドポイントを使用します。 1 つのエンドポイントを使用して、`SampleUdpProfileBinding`で[ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 'éý'`true`です。 もう 1 つのエンドポイントでは、 `UdpTransportBindingElement` が含まれるカスタム バインディングを使用します。 これを使用すると、`SampleUdpProfileBinding`で[ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 'éý'`false`です。 両方のテストでサービスが作成され、各バインドのエンドポイントが追加されてサービスが開きます。その後 Enter キーを押すと、サービスが閉じます。  
  
 このサービス テスト アプリケーションを開始すると、次の出力が表示されます。  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 次に、公開されたエンドポイントに対してクライアント テスト アプリケーションを実行できます。 このクライアント テスト アプリケーションでは、各エンドポイントに対してクライアントが作成され、5 つのメッセージが各エンドポイントに送信されます。 クライアントでの出力を次に示します。  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 サービスでのすべての出力を次に示します。  
  
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
  
 構成を使用して公開されたエンドポイントに対してクライアント アプリケーションを実行するには、サービス側で Enter キーを押してテスト クライアントを再実行します。 サービスには、次の出力が表示されます。  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 クライアントを再実行すると、前と同じ結果が表示されます。  
  
 Svcutil.exe を使用してクライアント コードと構成を再生成するには、サービス アプリケーションを開始し、その後、サンプルのルート ディレクトリで次のように Svcutil.exe を実行します。  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Svcutil.exe を実行しても `SampleProfileUdpBinding` のバインディング拡張構成は生成されません。したがって、次のコードを手動で追加する必要があります。  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
2.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
3.  前の「UDP テスト サービスとクライアント」セクションを参照してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`

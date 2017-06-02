---
title: "BindingElement の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# BindingElement の作成
バインディングとバインド要素 \(それぞれ、<xref:System.ServiceModel.Channels.Binding?displayProperty=fullName> と <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> を拡張するオブジェクト\) は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーション モデルがチャネル ファクトリおよびチャネル リスナーと関連付けられる場所です。バインディングを使用せずにカスタム チャネルを使用する場合は、「[サービス チャネル レベルのプログラミング](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)」および「[クライアントのチャネル レベルのプログラミング](../../../../docs/framework/wcf/extending/client-channel-level-programming.md)」に示すように、チャネル レベルでのプログラミングが必要になります。このトピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でチャネルを使用するための最小要件、チャネルの <xref:System.ServiceModel.Channels.BindingElement> の開発、および「[チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)」の手順 4. に示す "アプリケーションからのチャネル使用" を有効にする方法について説明します。  
  
## 概要  
 チャネルの <xref:System.ServiceModel.Channels.BindingElement> を作成しておくと、開発者は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーション内でチャネルを使用できるようになります。<xref:System.ServiceModel.Channels.BindingElement> オブジェクトを <xref:System.ServiceModel.ServiceHost?displayProperty=fullName> クラスから使用することにより、チャネルの正確な型情報を指定しなくても [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションをチャネルに接続できます。  
  
 一度 <xref:System.ServiceModel.Channels.BindingElement> を作成しておくと、「[チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)」に示す残りのチャネル開発手順に従って、さらに多くの機能を、要件に応じて有効にできます。  
  
## バインド要素の追加  
 カスタムの <xref:System.ServiceModel.Channels.BindingElement> を実装するには、<xref:System.ServiceModel.Channels.BindingElement> を継承するクラスを記述します。たとえば、サイズの大きいメッセージをチャンクに分割し、接続先で元のメッセージを再構築できる `ChunkingChannel` を開発している場合、<xref:System.ServiceModel.Channels.BindingElement> を実装してこれを使用するようにバインディングを構成することによって、任意のバインディングでこのチャネルを使用できるようになります。このトピックの残りの部分では、`ChunkingChannel` を例にして、バインド要素を実装する際の要件を示します。  
  
 `ChunkingBindingElement` は、`ChunkingChannelFactory` および `ChunkingChannelListener` を作成します。このバインド要素は、<xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> 実装および <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> 実装をオーバーライドし、型パラメーターが <xref:System.ServiceModel.Channels.IDuplexSessionChannel> \(この例では、これが `ChunkingChannel` でサポートされる唯一のチャネル形状です\) であることと、バインディングの他のバインド要素がこのチャネル形状をサポートすることを確認します。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> は、要求されたチャネル形状を構築できることをまず確認し、次にチャンク対象のメッセージ アクションのリストを取得します。さらに、新しい `ChunkingChannelFactory` を作成してこれに内部チャネル ファクトリを渡します \(トランスポート バインド要素を作成する場合、これはバインディング スタック内の最後の要素となるため、チャネル リスナーとチャネル ファクトリを作成する必要があります\)。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> には、`ChunkingChannelListener` を作成してこれに内部チャネル リスナーを渡す同様の実装があります。  
  
 トランスポート チャネルを使用する別の例として、「[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)」のサンプルでは次のオーバーライドが示されています。  
  
 このサンプルでは、バインド要素は `UdpTransportBindingElement` で、<xref:System.ServiceModel.Channels.TransportBindingElement> から派生しています。このバインド要素は、チャネルに関連付けられているファクトリを作成する、次のメソッドをオーバーライドします。  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 また、この要素には、`BindingElement` を複製したり、スキーム \(soap.udp\) を返したりするためのメンバーも含まれます。  
  
#### プロトコル バインド要素  
 含まれているバインド要素を新しいバインド要素で置き換えたり補足したりすることにより、新しいトランスポート、エンコーディング、または高レベルのプロトコルを追加できます。新しいプロトコル バインド要素を作成するには、まず <xref:System.ServiceModel.Channels.BindingElement> クラスを拡張します。次に、<xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=fullName> を使用して、少なくとも <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=fullName> と  `ChannelProtectionRequirements` を実装する必要があります。これにより、このバインド要素の <xref:System.ServiceModel.Security.ChannelProtectionRequirements> が返されます。詳細については、<xref:System.ServiceModel.Security.ChannelProtectionRequirements> を参照してください。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> は、このバインド要素の新しいコピーを返します。最善の方法としては、バインド要素の作成者は基本の copy コンストラクターを呼び出す copy コンストラクターを使用して、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A> を実装し、このクラスに含まれるすべての追加フィールドを複製することをお勧めします。  
  
#### トランスポート バインド要素  
 新しいトランスポート バインド要素を作成するには、<xref:System.ServiceModel.Channels.TransportBindingElement> インターフェイスを拡張します。次に、少なくとも <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> メソッドと <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=fullName> プロパティを実装する必要があります。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> \- このバインド要素の新しいコピーを返します。最善の方法としては、バインディング要素の作成者は基本の copy コンストラクターを呼び出す copy コンストラクターを使用して、複製を実装し、このクラスに含まれるすべての追加フィールドを複製することをお勧めします。  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> get プロパティは、バインディング要素によって表されるトランスポート プロトコルの URI スキームを返します。たとえば、<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName> および <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=fullName> は、それぞれの <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> プロパティから "http" および "net.tcp" を返します。  
  
#### エンコーディング バインディング要素  
 新しいエンコーディング バインド要素を作成するには、まず <xref:System.ServiceModel.Channels.BindingElement> クラスを拡張し、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=fullName> クラスを実装します。次に、少なくとも、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A> メソッド、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=fullName> メソッド、および <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=fullName> プロパティを実装する必要があります。  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>.このバインド要素の新しいコピーを返します。最善の方法としては、バインド要素の作成者は基本の copy コンストラクターを呼び出す copy コンストラクターを使用して、<xref:System.ServiceModel.Channels.BindingElement.Clone%2A> を実装し、このクラスに含まれるすべての追加フィールドを複製することをお勧めします。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>.<xref:System.ServiceModel.Channels.MessageEncoderFactory> を返します。これは、新しいエンコーダーを実装する実際のクラスを識別するハンドルを提供し、<xref:System.ServiceModel.Channels.MessageEncoder> を拡張します。詳細については、<xref:System.ServiceModel.Channels.MessageEncoderFactory>、<xref:System.ServiceModel.Channels.MessageEncoder> の各トピックを参照してください。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>.このエンコーディングで使用する <xref:System.ServiceModel.Channels.MessageVersion> を返します。これは、使用する SOAP および WS\-Addressing のバージョンを表します。  
  
 ユーザー定義エンコーディング バインド要素のオプション メソッドとプロパティの完全な一覧については、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> を参照してください。  
  
 新しいバインド要素の作成の詳細については、「[ユーザー定義バインディングの作成](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)」を参照してください。  
  
 チャネルのバインド要素を作成したら、「[チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)」のトピックに戻り、作成したバインド要素で構成ファイルをサポートする必要性の有無、メタデータの公開をサポートする必要性の有無とその方法、およびバインド要素を使用するユーザー定義のバインディングを作成する必要性の有無とその方法について確認します。  
  
## 参照  
 <xref:System.ServiceModel.Channels.BindingElement>   
 [チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)   
 [トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
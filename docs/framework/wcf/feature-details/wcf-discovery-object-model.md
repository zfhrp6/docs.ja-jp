---
title: "WCF Discovery オブジェクト モデル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 68d6e156612ce707aa678b6589510b710b73e38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-discovery-object-model"></a>WCF Discovery オブジェクト モデル
WCF Discovery は、実行時に探索可能なサービスと、これらのサービスを検索して使用するクライアントの作成を可能にする統合プログラミング モデルを提供する型のセットで構成されています。  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>探索可能なサービスの作成とサービスの検索  
 WCF サービスを探索可能にするには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> をサービス ホストの <xref:System.ServiceModel.Description.ServiceDescription> に追加し、探索エンドポイントを追加します。 サービスがアナウンス メッセージを送信するように構成されている (<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> を追加して) 場合は、サービス ホストが開かれるとき、および閉じられるときにアナウンスが送信されます。  
  
 サービスのアナウンス メッセージをリッスンするクライアントは、アナウンス サービスをホストし、1 つ以上のアナウンス エンドポイントを追加します。 アナウンス サービスは、アナウンス メッセージを受信し、アナウンス イベントを発生させます。  
  
 クライアントは、<xref:System.ServiceModel.Discovery.DiscoveryClient> クラスを使用して、利用可能なサービスを検索します。 クライアント アプリケーションは <xref:System.ServiceModel.Discovery.DiscoveryClient> クラスをインスタンス化し、探索メッセージの送信元を指定する探索エンドポイントを渡します。 クライアントは <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドを呼び出し、`Probe` 要求を送ります。 探索メッセージをリッスンしているサービスが、この `Probe` 要求を受信します。 サービスが `Probe` に指定されている条件に一致している場合は、`ProbeMatch` メッセージがクライアントに返されます。  
  
## <a name="object-model"></a>オブジェクト モデル  
 WCF Discovery API は、次のクラスを定義します。  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
  
-   <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> クラスは、アナウンス メッセージを送信するための同期メソッドと非同期メソッドを提供します。 アナウンス メッセージには Hello と Bye の 2 種類があります。 Hello メッセージは、サービスが使用可能になったことを示すために送信され、Bye メッセージは、既存のサービスが使用不可になったことを示すために送信されます。 開発者は、<xref:System.ServiceModel.Discovery.AnnouncementClient> インスタンスを作成して、<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> のインスタンスをコンストラクター パラメーターとして渡します。  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> は、固定アナウンス コントラクトが設定されている標準エンドポイントを表します。 サービスまたはクライアントは、これを使用して、アナウンス メッセージの送受信を行います。 既定では、<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> クラスは、WS_Discovery 11 プロトコル バージョンを使用するように設定されています。  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> は、アナウンス メッセージを受信して処理するアナウンス サービスの実装で、システムによって提供されています。 Hello または Bye メッセージが受信されると、<xref:System.ServiceModel.Discovery.AnnouncementService> のインスタンスが、適切な仮想メソッド <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> または <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A> を呼び出し、アナウンス イベントを発生させます。  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> クラスは、使用可能なサービスを検索および解決するために、クライアント アプリケーションによって使用されます。 指定されている <xref:System.ServiceModel.Discovery.FindCriteria> を基にサービスを検索し、<xref:System.ServiceModel.Discovery.ResolveCriteria> を基にサービスを解決するための同期メソッドと非同期メソッドを提供します。 開発者は、<xref:System.ServiceModel.Discovery.DiscoveryClient> インスタンスを作成して、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> のインスタンスをコンストラクター パラメーターとして提供します。  
  
 開発者が同期または非同期に呼び出すサービスを検索する`Find`を提供するメソッド、 <!--zz <xref:System.ServiceModel.Discription.FindCriteria> --> `FindCriteria`を使用する検索条件を含むインスタンス。 <xref:System.ServiceModel.Discovery.DiscoveryClient> は、適切なヘッダーを設定して `Probe` メッセージを作成し、検索要求を送信します。 どの時点でも、未処理の `Find` 要求が 1 つ以上存在する可能性があるため、クライアントは、受信した応答を関連付けて、応答を検証します。 その後、`Find` を使用して、結果を <xref:System.ServiceModel.Discovery.FindResponse> 操作の呼び出し元に渡します。  
  
 開発者が同期または非同期に呼び出す既知のサービスを解決するには、`Resolve`メソッドのインスタンスを提供する<!--zz <xref:System.ServiceModel.ResolveCriteria>-->`ResolveCriteria`を格納している、<xref:System.ServiceModel.EndpointAddress>の既知のサービスです。 <xref:System.ServiceModel.Discovery.DiscoveryClient> は、適切なヘッダーを設定して `Resolve` メッセージを作成し、解決要求を送信します。 受信された応答が未処理の解決要求と関連付けられ、その結果が、`Resolve` を使用して、<xref:System.ServiceModel.Discovery.ResolveResponse> 操作の呼び出し元に渡されます。  
  
 探索プロキシがネットワーク上に存在する場合、 <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient`検出要求が送信、マルチキャストで探索プロキシがマルチキャスト抑制こんにちはメッセージに応答できます。 <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient`を生成、`ProxyAvailable`未処理への応答でこんにちはメッセージを受信したときにイベント`Find`または`Resolve`要求します。 `ProxyAvailable` イベントには、探索プロキシについての <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> が含まれています。 管理者は、この情報を使用して、アドホック モードからマネージ モードに切り替えるかどうかを制御できます。  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> は、固定探索コントラクトが設定されている標準エンドポイントを表します。 サービスまたはクライアントによる探索メッセージの送受信に使用されます。 既定では、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>を使用する設定<!--zz <xref:System.ServiceModel.Discovery.DiscoveryMode.Managed>-->`Managed`モードと WSDiscovery11 Ws-discovery バージョン。  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> は、サービスが探索メッセージまたはアナウンス メッセージを送信するときに、<xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> を生成するために使用されます。  
  
## <a name="discoveryservice"></a>DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> 抽象クラスは、`Probe` メッセージおよび `Resolve` メッセージの受信と処理のフレームワークを提供します。 `Probe` メッセージが受信されると、<xref:System.ServiceModel.Discovery.DiscoveryService> は、受信メッセージに基づいて <xref:System.ServiceModel.Discovery.FindRequestContext> のインスタンスを作成し、<xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> 仮想メソッドを呼び出します。 `Resolve` メッセージが受信されると、<xref:System.ServiceModel.Discovery.DiscoveryService> は <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> 仮想メソッドを呼び出します。 このクラスから継承して、カスタムの探索サービス実装を提供できます。  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 抽象クラスは、探索メッセージおよびアナウンス メッセージの受信と処理のフレームワークを提供します。 カスタムの探索プロキシを実装するときは、このクラスを継承します。 `Probe` メッセージがマルチキャストで受信されると、<xref:System.ServiceModel.Discovery.DiscoveryProxy> クラスは `BeginShouldRedirectFind` 仮想メソッドを呼び出して、マルチキャスト抑制メッセージの送信が必要かどうかを決定します。 開発者の判断により、マルチキャスト抑制メッセージを送信しない場合、または、`Probe` メッセージがユニキャストで受信された場合は、受信メッセージに基づいて <xref:System.ServiceModel.Discovery.FindRequestContext> クラスのインスタンスを作成し、`OnBeginFind` 仮想メソッドを呼び出します。 `Resolve` メッセージがマルチキャストで受信されると、<xref:System.ServiceModel.Discovery.DiscoveryProxy> クラスは `ShouldRedirectResolve` 仮想メソッドを呼び出して、マルチキャスト抑制メッセージの送信が必要かどうかを決定します。 開発者の判断により、マルチキャスト抑制メッセージを送信しない場合、または、`Resolve` メッセージがユニキャストで受信された場合は、受信メッセージに基づいて <xref:System.ServiceModel.Discovery.ResolveCriteria> クラスのインスタンスを作成し、`OnBeginResolve` 仮想メソッドを呼び出します。 Hello または Bye メッセージが受信されると、<xref:System.ServiceModel.Discovery.DiscoveryProxy> のインスタンスが、適切な仮想メソッド (`OnBeginOnlineAnnouncement` または `OnBeingOfflineAnnouncement`) を呼び出し、アナウンス イベントを発生させます。  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> クラスは、使用する探索プロトコルのバージョンを表します。  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> クラスは、エンドポイントを探索可能にするかどうかの制御と、拡張機能、追加のコントラクト型の名前、 およびそのエンドポイントに関連付けるスコープの指定に使用されます。 この動作は、アプリケーション エンドポイントに追加されて、そのエンドポイントの <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> を構成します。 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> がサービス ホストに追加されると、既定では、そのサービス ホストがホストしているすべてのアプリケーション エンドポイントが探索可能になります。 開発者を設定して、特定のエンドポイントの検出を無効にできます、 <!--zz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enable%2A>--> `Enable`プロパティを`false`です。  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> クラスは、サービスによって公開されるエンドポイントのバージョンに依存しない表現を提供します。 これには、サービスの開発者によって指定されたエンドポイントのアドレス、リッスン URI、コントラクト型名、スコープ、メタデータのバージョン、および拡張機能が含まれます。 <xref:System.ServiceModel.Discovery.FindCriteria> は、`Probe` 操作と <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> との照合中に、クライアントによって送信されます。 基準が一致した場合は、<xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> がクライアントに返されます。 <xref:System.ServiceModel.Discovery.ResolveCriteria> 内のエンドポイント アドレスが、<xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のエンドポイント アドレスと照合されます。 基準が一致した場合は、<xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> がクライアントに返されます。  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> クラスは、サービスの検索時に使用される条件の指定に使用するバージョンに依存しないクラスです。 サービスを照合するための WS-Discovery 定義の条件を完全にサポートします。 また、このクラスには、照合プロセス中に使用できるカスタム値を指定するために開発者が使用できる拡張機能もあります。 開発者は、の終了条件を提供できます、`Find`操作を指定して、 <!--zz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResult%2A>--> `MaxResult`は開発者を探して、またはを指定するサービスの合計数を指定する、 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>、これは、クライアントが応答を待機する時間を指定する値。  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> クラスは、クライアントが `Probe` 操作を開始するときに受信する `Find` メッセージに基づいて、探索サービスによってインスタンス化されます。 これには、クライアントによって指定された <xref:System.ServiceModel.Discovery.FindCriteria> のインスタンスが含まれます。  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> クラスは、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 操作の応答と共に、`Find` の呼び出し元に返されます。 これは、<xref:System.ServiceModel.Discovery.FindCompletedEventArgs> にも存在します。 これには、探索されたエンドポイントのコレクションである <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションと、<xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> および <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> のディクショナリが含まれます。  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> クラスは、既知のサービスの解決時に使用される条件の指定に使用するバージョンに依存しないクラスです。 これには、既知のサービスのエンドポイント アドレスが含まれます。 開発者は、クライアントが応答を待機する時間を指定する <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A> を指定して、解決操作の終了条件を提供できます。  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> は、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> 操作の応答と共に、`Resolve` メソッドの呼び出し元に返されます。 これは、<xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs> にも存在します。 これには、探索されたエンドポイントである <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のインスタンスと、<xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> のインスタンスが含まれます。  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> クラスを使用すると、探索機能をサービスに追加できます。 この動作は <xref:System.ServiceModel.ServiceHost> に追加します。 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> クラスは、サービス ホストに追加されているアプリケーション エンドポイントに対して反復処理され、探索可能なエンドポイントに基づいて <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションを作成します。 既定では、すべてのエンドポイントが探索可能です。 特定のエンドポイントが探索可能になるかどうかは、<xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> をその特定のエンドポイントに追加することで制御できます。 アナウンス エンドポイントが <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> に追加されると、サービス ホストが開かれるときまたは閉じられるときに、すべての探索可能なエンドポイントのアナウンスが、各アナウンス エンドポイントから送られます。  
  
## <a name="servicediscoveryextension"></a>ServiceDiscoveryExtension  
 <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`クラスを作成、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>クラスです。 探索可能にされているエンドポイントから取得できる<!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> -->`ServiceDiscoveryExtension`です。 このクラスは、カスタムの探索サービス実装を指定する目的でも使用されます。  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> クラスは、UDP マルチキャスト バインディングを使用するアナウンス用に事前に構成しておく標準のアナウンス エンドポイントです。 既定では、<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> が WSApril2005 WS_Discovery バージョンを使用するように設定されています。  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> クラスは、UDP マルチキャスト バインディングを使用する探索のために事前に構成された標準の探索エンドポイントです。 既定では、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>は WSDiscovery11 Ws-discovery バージョンを使用する設定と<!--zz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.Adhoc>-->`Adhoc`モード。

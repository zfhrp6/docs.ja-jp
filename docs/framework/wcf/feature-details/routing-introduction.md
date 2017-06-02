---
title: "ルーティングの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
caps.latest.revision: 11
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 11
---
# ルーティングの概要
ルーティング サービスは、メッセージの内容を基にメッセージをルーティングできる、プラグ可能な汎用の SOAP 中継局を提供します。  ルーティング サービスを使用すると、サービスの集計、サービスのバージョン管理、優先度ルーティング、マルチキャスト ルーティングなどのシナリオを実装できる複雑なルーティング ロジックを作成できます。  また、ルーティング サービスは、バックアップ エンドポイントのリストを設定できるエラー処理機能も提供します。バックアップ エンドポイントは、プライマリ送信先エンドポイントへの送信時に障害が発生した場合に、メッセージの送信先になります。  
  
 このトピックでは、ルーティング サービスをご存じない方を対象としています。ここでは、ルーティング サービスの基本的な構成とホストについて説明します。  
  
## 構成  
 ルーティング サービスは、1 つ以上のサービス エンドポイントを公開する WCF サービスとして実装されます。サービス エンドポイントは、クライアント アプリケーションからメッセージを受信し、受信したメッセージを 1 つ以上の送信先エンドポイントにルーティングします。  ルーティング サービスには <xref:System.ServiceModel.Routing.RoutingBehavior> があります。これは、このサービスによって公開されるサービス エンドポイントに適用されます。  この動作を使用して、サービスの稼働方法について詳細を構成します。  構成ファイルを使用する場合に構成しやすいように、パラメーターを **RoutingBehavior** に指定します。  コード ベースのシナリオでは、これらのパラメーターを <xref:System.ServiceModel.Routing.RoutingConfiguration> オブジェクトの一部として指定し、このオブジェクトを **RoutingBehavior** に渡すことができます。  
  
 開始時に、この動作はメッセージの SOAP 処理の実行に使用される <xref:System.ServiceModel.Routing.SoapProcessingBehavior> をクライアントのエンドポイントに追加します。  追加されると、ルーティング サービスが、メッセージを受信したエンドポイントとは異なる **MessageVersion** が必要なエンドポイントにメッセージを転送できるようになります。  **RoutingBehavior** は、サービス拡張である <xref:System.ServiceModel.Routing.RoutingExtension> も登録します。この機能拡張は、実行時にルーティング サービスを変更するためのアクセス ポイントを提供します。  
  
 **RoutingConfiguration** クラスは、ルーティング サービスの構成および構成の更新を一貫性を持って実行できる手段を提供します。  このクラスには、ルーティング サービスの設定となるパラメーターが含まれます。これらのパラメーターは、サービスの開始時に **RoutingBehavior** を構成するために使用されるか、実行時にルーティング構成を変更するために **RoutingExtension** に渡されます。  
  
 メッセージのコンテンツ ベースのルーティングを実行するために使用するルーティング ロジックは、複数の <xref:System.ServiceModel.Dispatcher.MessageFilter> オブジェクトをフィルター テーブル \(<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> オブジェクト\) にまとめて定義します。  受信メッセージは、フィルター テーブルに保持されているメッセージ フィルターに対して評価され、メッセージに一致する各 **MessageFilter** に従って、送信先エンドポイントに転送されます。  メッセージのルーティングに使用するフィルター テーブルは、構成で **RoutingBehavior** を使用するか、**RoutingConfiguration** オブジェクトを使用してコードにより指定します。  
  
### エンドポイントの定義  
 構成を行うには、使用するルーティング ロジックの定義から始めるように思えますが、実際には、まず、メッセージのルーティング先になるエンドポイントの形状を決定する必要があります。  ルーティング サービスは、メッセージの送受信に使用するチャネルの形状を定義するコントラクトを使用するため、入力チャネルの形状と出力チャネルの形状が一致する必要があります。  たとえば、要求\/応答チャネル形状を使用するエンドポイントにルーティングする場合は、<xref:System.ServiceModel.Routing.IRequestReplyRouter> など、着信エンドポイントでも、互換性のあるコントラクトを使用する必要があります。  
  
 つまり、複数の送信先エンドポイントが、複数の通信パターン \(一方向の操作と双方向の操作の混合など\) のコントラクトを使用している場合は、すべての送信先エンドポイントへのメッセージの受信とルーティングを行う単一のサービス エンドポイントを作成することはできません。  互換性のある形状を使用するエンドポイントを特定し、送信先エンドポイントにルーティングされるメッセージの受信に使用するサービス エンドポイントを 1 つ以上定義する必要があります。  
  
> [!NOTE]
>  複数の通信パターン \(一方向の操作と双方向の操作の混合など\) を指定するコントラクトを使用している場合は、<xref:System.ServiceModel.Routing.IDuplexSessionRouter> など、二重のコントラクトをルーティング サービスで使用して対処します。  ただし、この場合は、バインドが二重通信に対応可能である必要があり、シナリオによっては、それが可能でない場合もあります。  対応が不可能なシナリオでは、複数のエンドポイントに通信をファクタリングするか、アプリケーションの変更が必要になる可能性があります。  
  
 ルーティング コントラクトの詳細については、「[ルーティング コントラクト](../../../../docs/framework/wcf/feature-details/routing-contracts.md)」を参照してください。  
  
 サービス エンドポイントが定義されたら、**RoutingBehavior** を使用して特定の **RoutingConfiguration** をエンドポイントに関連付けることができます。  構成ファイルを使用してルーティング サービスを構成する場合は、**RoutingBehavior** を使用して、このエンドポイントで受信されるメッセージの処理に使用するルーティング ロジックを保持しているフィルター テーブルを指定します。  ルーティング サービスをプログラムにより構成する場合は、**RoutingConfiguration** を使用して、フィルター テーブルを指定できます。  
  
 以下に、プログラムによる方法と構成ファイルを使用する方法の両方で、ルーティング サービスが使用するサービスおよびクライアント エンドポイントを定義する例を示します。  
  
```xml  
<services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 この例では、アドレスが "http:\/\/localhost:8000\/routingservice\/router" である単一のエンドポイントを公開するようにルーティング サービスを構成しています。このエンドポイントは、ルーティングされるメッセージの受信に使用されます。  メッセージは要求\/応答エンドポイントにルーティングされるため、サービス エンドポイントは <xref:System.ServiceModel.Routing.IRequestReplyRouter> コントラクトを使用します。  この構成では、メッセージのルーティング先となる単一のクライアント エンドポイント "http:\/\/localhost:8000\/servicemodelsample\/service" も定義しています。  "routingTable1" という名前のフィルター テーブル \(例には含まれていません\) は、メッセージのルーティングに使用されるルーティング ロジックを保持しており、**RoutingBehavior** \(構成ファイルの場合\) または **RoutingConfiguration** \(プログラムによる構成の場合\) を使用してサービス エンドポイントに関連付けられています。  
  
### ルーティング ロジック  
 メッセージのルーティングに使用されるルーティング ロジックを定義するには、受信メッセージに含まれるデータのうち、一意に識別して処理できるものを特定する必要があります。  たとえば、ルーティング先のすべてのエンドポイントが同じ SOAP アクションを共有する場合、メッセージに含まれる Action の値は、メッセージのルーティング先となる特定のエンドポイントを示す値としては不適切です。  ある特定のエンドポイントにメッセージを一意にルーティングする必要がある場合は、メッセージのルーティング先エンドポイントを一意に識別できるデータを基に、フィルター処理を行います。  
  
 ルーティング サービスには、アドレス、アクション、エンドポイント名、さらには XPath クエリなど、メッセージ内の特定の値を確認する **MessageFilter** 実装がいくつかあります。  これらの実装の中にニーズに合うものがない場合は、カスタムの **MessageFilter** 実装を作成できます。  メッセージ フィルターの詳細およびルーティング サービスが使用する実装の比較については、「[メッセージ フィルター](../../../../docs/framework/wcf/feature-details/message-filters.md)」および「[フィルターの選択](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)」を参照してください。  
  
 複数のメッセージ フィルターをまとめて、フィルター テーブルで管理します。このテーブルで、各 **MessageFilter** と送信先エンドポイントが関連付けられます。  または、フィルター テーブルを使用して、通信エラーが発生した場合に、ルーティング サービスがメッセージを送信するバックアップ エンドポイントのリストを指定することもできます。  
  
 既定では、フィルター テーブル内のすべてのメッセージ フィルターが同時に評価されます。ただし、<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> を指定すると、特定の順序でメッセージ フィルターが評価されるようにすることができます。  優先度が最も高いすべてのエントリが最初に評価されます。優先度レベルが高いフィルターの中に一致するものが見つかった場合、それよりも優先度の低いメッセージ フィルターは評価されません。  フィルター テーブルの詳細については、「[メッセージ フィルター](../../../../docs/framework/wcf/feature-details/message-filters.md)」を参照してください。  
  
 次の例では <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> を使用しています。これは、すべてのメッセージに対して `true` に評価されます。  この **MessageFilter** は "routingTable1" フィルター テーブルに追加され、このテーブルで **MessageFilter** が、"CalculatorService" という名前のクライアント エンドポイントに関連付けられます。  次に、**RoutingBehavior** で、サービス エンドポイントが処理するメッセージのルーティングに、このテーブルが使用されるように指定しています。  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
>  既定でルーティング サービスによって評価されるのは、メッセージのヘッダーのみです。  フィルターがメッセージ本文にアクセスできるようにするには、<xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> を `false` に設定します。  
  
 **マルチキャスト**  
  
 多くのルーティング サービス構成では、特定の 1 つのエンドポイントにのみメッセージをルーティングする排他的なフィルター ロジックが使用されますが、特定のメッセージを、複数の送信先エンドポイントにルーティングすることが必要な場合もあります。  メッセージを複数の送信先にマルチキャストするには、次の条件を満たす必要があります。  
  
-   要求への応答時にクライアント アプリケーションが受信できるのは 1 つの応答のみであるため、チャネル形状が要求\/応答でない \(一方向または二重のどちらでもよい\) ことが必要である。  
  
-   複数のフィルターが、メッセージの評価時に `true` を返す必要がある。  
  
 これらの条件が満たされる場合は、メッセージが、`true` に評価されたすべてのフィルターのすべてのエンドポイントにルーティングされます。  次の例では、メッセージ内のエンドポイント アドレスが http:\/\/localhost:8000\/routingservice\/router\/rounding である場合、両方のエンドポイントにメッセージがルーティングされるルーティング構成を定義しています。  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### SOAP 処理  
 異種プロトコル間でのメッセージのルーティングをサポートするために、既定では、**RoutingBehavior** が、メッセージのルーティング先であるすべてのクライアント エンドポイントに <xref:System.ServiceModel.Routing.SoapProcessingBehavior> を追加します。  この動作は、メッセージがエンドポイントにルーティングされる前に、自動的に新しい **MessageVersion** を作成するだけでなく、要求側クライアント アプリケーションに応答ドキュメントを返す前に、応答ドキュメント用に互換性のある **MessageVersion** を作成します。  
  
 送信メッセージ用に新しい **MessageVersion** を作成する手順は、次のとおりです。  
  
 **要求の処理**  
  
-   送信バインドおよびチャネルの **MessageVersion** を取得します。  
  
-   元のメッセージの本文のリーダーを取得します。  
  
-   同じ操作、同じ本文のリーダーと、新しい **MessageVersion** を使用して新しいメッセージを作成します。  
  
-   <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> \!\= **Addressing.None** の場合は、To、From、FaultTo、および RelatesTo の各ヘッダーを新しいメッセージにコピーします。  
  
-   新しいメッセージにすべてのメッセージ プロパティをコピーします。  
  
-   応答の処理時に使用するために、元の要求メッセージを保存します。  
  
-   新しい要求メッセージを返します。  
  
 **応答の処理**  
  
-   元の要求メッセージの **MessageVersion** を取得します。  
  
-   受信した応答メッセージの本文のリーダーを取得します。  
  
-   同じ操作、同じ本文のリーダー、および、元の要求メッセージの **MessageVersion** を使用して、新しい応答メッセージを作します。  
  
-   <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> \!\= **Addressing.None** の場合は、To、From、FaultTo、および RelatesTo の各ヘッダーを新しいメッセージにコピーします。  
  
-   新しいメッセージにメッセージ プロパティをコピーします。  
  
-   新しい応答メッセージを返します。  
  
 既定では、サービスの開始時に **SoapProcessingBehavior** が <xref:System.ServiceModel.Routing.RoutingBehavior> によって自動的にクライアント エンドポイントに追加されますが、<xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> プロパティを使用することで、すべてのクライアント エンドポイントに SOAP 処理を追加するかどうかを制御できます。  また、この動作を直接特定のエンドポイントに追加したり、SOAP 処理をより細かく制御する必要がある場合に、エンドポイント レベルでこの動作を無効にしたりすることもできます。  
  
> [!NOTE]
>  元の要求メッセージとは異なる MessageVersion を必要とするエンドポイントで SOAP 処理を無効にする場合は、送信先エンドポイントにメッセージを送信する前に必要な SOAP の変更を実行するカスタムのメカニズムを提供する必要があります。  
  
 次の例では、**soapProcessingEnabled** プロパティを使用して、**SoapProcessingBehavior** が自動的にすべてのクライアント エンドポイントに追加されないようにしています。  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### 動的構成  
 追加のクライアント エンドポイントを追加する場合、またはメッセージのルーティングに使用されるフィルターを変更する必要がある場合は、ルーティング サービスを介してメッセージを現在受信しているエンドポイントへのサービスを中断しないように、実行時に動的に構成を更新できる手段を用意する必要があります。  ホスト アプリケーションの構成ファイルまたはコードを変更するだけでは、不十分な場合があります。どちらの方法にもアプリケーションのリサイクルが必要で、現在転送中のメッセージが失われたり、サービスの再起動の処理中にダウンタイムが発生したりする可能性があるためです。  
  
 **RoutingConfiguration** は、プログラムによってのみ変更できます。  サービスの初期構成は構成ファイルで実行できますが、実行時に構成を変更する方法は、新しい **RoutingConfigution** を作成して、<xref:System.ServiceModel.Routing.RoutingExtension> サービス拡張が公開する <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> メソッドにパラメーターとして渡すことのみです。  現在転送中のメッセージでは、以前の構成を使用してルーティングの処理が続けられますが、**ApplyConfiguration** への呼び出し後に受信されたメッセージでは、新しい構成が使用されます。  次の例では、ルーティング サービスのインスタンスを作成し、次に、構成を変更しています。  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
>  この場合は、新しい構成を渡すことが、ルーティング サービスを更新する唯一の方法です。  現在の構成から選択した要素のみを変更することも、新しいエントリを現在の構成に追加することもできません。既存の構成に代わる新しい構成を作成して、これを渡す必要があります。  
  
> [!NOTE]
>  以前の構成を使用して開かれているセッションでは、引き続き、以前の構成が使用されます。  新しい構成は、新しいセッションでのみ使用されます。  
  
## エラー処理  
 メッセージの送信時に <xref:System.ServiceModel.CommunicationException> が発生した場合は、エラー処理が実行されます。  これらの例外は、一般的に、<xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException>、<xref:System.ServiceModel.CommunicationObjectFaultedException> など、定義されているクライアント エンドポイントとの通信を試みている間に問題が発生したことを示します。  また、エラー処理コードは、<xref:System.TimeoutException> が発生すると、それをキャッチして再送信を試みます。この例外も、**CommunicationException** から派生したのではない、一般的な例外です。  
  
 上記の例外のいずれかが発生した場合、ルーティング サービスは、バックアップ エンドポイントのリストにフェールオーバーします。  すべてのバックアップ エンドポイントで通信エラーが発生した場合、または、送信先サービス内でのエラーを示す例外がエンドポイントから返された場合は、ルーティング サービスがクライアント アプリケーションにエラーを返します。  
  
> [!NOTE]
>  エラー処理機能は、メッセージの送信時とチャネルの終了時に発生した例外をキャプチャーし、処理します。  エラー処理コードは、通信対象のアプリケーション エンドポイントによって作成された例外については、検出も処理も行いません。サービスからスローされた <xref:System.ServiceModel.FaultException> は、ルーティング サービスでは **FaultMessage** として扱われ、クライアントに戻されます。  
>   
>  ルーティング サービスによってメッセージを転送しようとしてエラーが発生した場合、通常、ルーティング サービスが行われない場合に受け取る <xref:System.ServiceModel.EndpointNotFoundException> ではなく、<xref:System.ServiceModel.FaultException> をクライアント サイドで受け取る可能性があります。  入れ子になった例外を調べないと、このようにルーティング サービスによって例外がマスクされて完全な透過性が提供されない可能性があります。  
  
### 例外のトレース  
 メッセージをリスト内のエンドポイントに送信できなかった場合、ルーティング サービスは、生成された例外データをトレースして、**Exceptions** という名前のメッセージ プロパティに例外の詳細をアタッチします。  これで、例外データを保存し、ユーザーがメッセージ インスペクターを利用して、プログラムでアクセスできるようにします。  例外データは、メッセージごとにディクショナリに格納されます。ディクショナリでは、エンドポイント名と、そのエンドポイントにメッセージを送信する際に発生した例外の詳細がマップされます。  
  
### バックアップ エンドポイント  
 フィルター テーブル内の各フィルター エントリには、必要に応じて、バックアップ エンドポイントのリストを指定できます。バックアップ エンドポイントは、プライマリ エンドポイントへの送信時に通信エラーが発生した場合に使用されます。  このようなエラーが発生した場合、ルーティング サービスでは、このバックアップ エンドポイントのリスト内の最初のエントリに対して、メッセージの転送を試みます。  この送信でも通信エラーが発生した場合は、バックアップ リスト内の次のエンドポイントが試されます。  ルーティング サービスは、メッセージの受信が成功するか、すべてのエンドポイントが通信エラーを返すか、またはエンドポイントによって通信エラー以外のエラーが返されるまで、リスト内の各エンドポイントに対してメッセージの送信を続行します。  
  
 次の例では、バックアップ リストを使用するようにルーティング サービスを構成しています。  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### サポートされるエラー パターン  
 次の表に、バックアップ エンドポイント リストを使用できるパターンと、各パターンのエラー処理の詳細な説明を示します。  
  
|パターン|セッション|トランザクション|受信コンテキスト|サポートされるバックアップ リスト|メモ|  
|----------|-----------|--------------|--------------|-----------------------|--------|  
|一方向||||はい|バックアップ エンドポイントでメッセージの再送を試みます。  このメッセージがマルチキャストされる場合は、エラーが発生したチャネルのメッセージのみが、バックアップ先に移動されます。|  
|一方向||![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||Ｘ|例外がスローされ、トランザクションがロールバックされます。|  
|一方向|||![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|はい|バックアップ エンドポイントでメッセージの再送を試みます。  メッセージの受信が成功したら、すべての受信コンテキストを完了します。  どのエンドポイントでもメッセージを受信できなかった場合は、受信コンテキストを完了しません。<br /><br /> このメッセージがマルチキャストされる場合は、少なくとも 1 つのエンドポイント \(プライマリでもバックアップでも\) でメッセージが受信された場合にのみ、受信コンテキストが完了されます。  どのマルチキャスト パスのエンドポイントでもメッセージを受信できなかった場合は、受信コンテキストを完了しません。|  
|一方向||![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|はい|前のトランザクションを中止し、新しいトランザクションを作成して、すべてのメッセージを再送します。  エラーが発生したメッセージは、バックアップ先に転送されます。<br /><br /> すべての転送が成功するトランザクションが作成されたら、受信コンテキストを完了して、転送をコミットします。|  
|一方向|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|||はい|バックアップ エンドポイントでメッセージの再送を試みます。  マルチキャスト セッションの場合は、エラーが発生したセッションまたはセッションを終了できなかったセッションのメッセージのみが、バックアップ先に送信されます。|  
|一方向|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||Ｘ|例外がスローされ、トランザクションがロールバックされます。|  
|一方向|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|はい|バックアップ エンドポイントでメッセージの再送を試みます。  エラーが発生せずに、すべてのメッセージ送信が完了したら、セッションが他にメッセージがないことを通知して、ルーティング サービスがすべての送信セッション チャネルを終了します。また、受信コンテキストが完了し、受信セッション チャネルが終了します。|  
|一方向|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|はい|現在のトランザクションを中止し、新しいトランザクションを作成します。  セッションに含まれる、以前のメッセージをすべて再送します。  すべてのメッセージ送信が成功したトランザクションが作成され、セッションが他にメッセージがないことを通知すると、すべての送信セッション チャネルが終了します。また、そのトランザクションのすべての受信コンテキストが完了し、受信セッション チャネルが終了して、トランザクションがコミットされます。<br /><br /> セッションがマルチキャストされる場合は、エラーが発生していないメッセージが、前回と同じ送信先に再送され、エラーが発生したメッセージはバックアップ先に送信されます。|  
|双方向||||はい|バックアップ先に送信します。  チャネルが応答メッセージを返した後に、元のクライアントに応答を返します。|  
|双方向|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|||はい|チャネルのすべてのメッセージをバックアップ先に送信します。  チャネルが応答メッセージを返した後に、元のクライアントに応答を返します。|  
|双方向||![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||Ｘ|例外がスローされ、トランザクションがロールバックされます。|  
|双方向|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")||Ｘ|例外がスローされ、トランザクションがロールバックされます。|  
|二重||||Ｘ|セッションのない二重通信は、現在サポートされていません。|  
|二重|![チェック マーク](../../../../docs/framework/wcf/feature-details/media/checkmark.gif "Checkmark")|||はい|バックアップ先に送信します。|  
  
## ホスト  
 ルーティング サービスは WCF サービスとして実装されるため、アプリケーション内に自己ホストされるか、IIS または WAS によってホストされる必要があります。  ルーティング サービスは、IIS、WAS、または Windows サービス アプリケーションにホストし、これらのホスト環境で提供される自動開始機能やライフ サイクル管理機能を利用できるようにすることをお勧めします。  
  
 次の例では、アプリケーションでルーティング サービスをホストしています。  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
  
```  
  
 ルーティング サービスを IIS または WAS 内でホストするには、サービス ファイル \(.svc\) を作成するか、サービスの構成ベースのアクティブ化を使用する必要があります。  サービス ファイルを使用する場合は、Service パラメーターを使用して <xref:System.ServiceModel.Routing.RoutingService> を指定する必要があります。  次の例は、IIS または WAS によるルーティング サービスのホストに使用できるサンプルのサービス ファイルです。  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
  
```  
  
## ルーティング サービスと偽装  
 WCF ルーティング サービスは、メッセージの送受信両方の偽装で使用できます。  偽装に関する通常の Windows のすべての制約が適用されます。  独自のサービスを作成する際、偽装を使用するためにサービスまたはアカウントのアクセス許可を設定する必要があった場合は、ルーティング サービスで偽装を使用する場合と同じ手順を実行する必要があります。  詳細については、「[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)」を参照してください。  
  
 ルーティング サービスでの偽装には、ASP.NET 互換モードで ASP.NET の偽装を使用するか、偽装を許可するように構成された Windows 資格情報を使用する必要があります。  ASP.NET 互換モードの詳細については、「[WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)」を参照してください。  
  
> [!WARNING]
>  WCF ルーティング サービスは、基本認証での偽装をサポートしません。  
  
 ルーティング サービスで ASP.NET の偽装を使用するには、サービス ホスティング環境で ASP.NET 互換モードを有効にします。  ルーティング サービスは既に ASP.NET 互換モードを許可するようにマークされているため、偽装が自動的に有効になります。  偽装は、ルーティング サービスとの ASP.NET 統合で唯一サポートされている用法です。  
  
 ルーティング サービスで Windows 資格情報の偽装を使用するには、資格情報とサービスの両方を構成する必要があります。  クライアント資格情報オブジェクト \(<xref:System.ServiceModel.ChannelFactory> からアクセス可能な <xref:System.ServiceModel.Security.WindowsClientCredential>\) は、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> プロパティを定義します。偽装を許可するには、このプロパティを設定する必要があります。  最後に、サービスで、<xref:System.ServiceModel.Description.ServiceAuthorization> 動作を構成して、`ImpersonateCallerForAllOperations` を `true` に設定する必要があります。  ルーティング サービスでは、偽装が有効になっているメッセージを転送するためのクライアントを作成するかどうかを、このフラグを使用して決定します。  
  
## 参照  
 [メッセージ フィルター](../../../../docs/framework/wcf/feature-details/message-filters.md)   
 [ルーティング コントラクト](../../../../docs/framework/wcf/feature-details/routing-contracts.md)   
 [フィルターの選択](../../../../docs/framework/wcf/feature-details/choosing-a-filter.md)
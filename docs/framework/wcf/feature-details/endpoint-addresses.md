---
title: "エンドポイントのアドレス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アドレス [WCF]"
  - "WCF [WCF], アドレス"
  - "Windows Communication Foundation [WCF], アドレス"
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# エンドポイントのアドレス
すべてのエンドポイントにはこれと関連するアドレスがあり、エンドポイントの検索と識別に使用されます。このアドレスは主にエンドポイントの位置を指定する URI \(Uniform Resource Identifier\) で構成されます。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のプログラミング モデルでは、エンドポイント アドレスは <xref:System.ServiceModel.EndpointAddress> クラスによって表されます。このクラスには、このエンドポイントとメッセージを交換する他のエンドポイントがエンドポイントを認証できるようにする、オプションの <xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティ、およびサービスに到達するために必要な他の任意の SOAP ヘッダーを定義するオプションの <xref:System.ServiceModel.EndpointAddress.Headers%2A> プロパティが含まれます。オプションのヘッダーは、サービス エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。エンドポイントのアドレスは、ネットワーク上では WS\-Addressing エンドポイント参照 \(EPR\) として表されます。  
  
## アドレスの URI 構造  
 ほとんどのトランスポートの URI アドレスは、4 つの部分から構成されます。たとえば、http:\/\/www.fabrikam.com:322\/mathservice.svc\/secureEndpoint という URI は、次の 4 つの部分から構成されます。  
  
-   スキーム : http:  
  
-   コンピューター : www.fabrikam.com  
  
-   \(省略可能\) ポート : 322  
  
-   パス : \/mathservice.svc\/secureEndpoint  
  
## サービスのアドレスの定義  
 サービスのエンドポイント アドレスは、コードを使用して命令的に、または構成を通じて宣言的に指定できます。展開済みサービスのバインディングおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
### 構成によるアドレス定義  
 構成ファイルでエンドポイントを定義するには、[\<endpoint\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) 要素を使用します。使用例と詳細については、「[エンドポイント アドレスの指定](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)」を参照してください。  
  
### コードによるアドレス定義  
 エンドポイント アドレスは、コードで <xref:System.ServiceModel.EndpointAddress> クラスを使用して作成できます。使用例と詳細については、「[エンドポイント アドレスの指定](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)」を参照してください。  
  
### WSDL のエンドポイント  
 エンドポイント アドレスは、対応するエンドポイントの `wsdl:port` 要素内の WS\-Addressing EPR 要素として WSDL で表すこともできます。EPR には、エンドポイントのアドレスのほかに、アドレスのすべてのプロパティが含まれます。使用例と詳細については、「[エンドポイント アドレスの指定](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)」を参照してください。  
  
## .NET Framework 3.5 での複数の IIS バインディングのサポート  
 インターネット サービス プロバイダーは、多くの場合、サイトの密度を高めて総所有コストを抑えるため、同じサーバーまたはサイト上で複数のアプリケーションをホストしています。通常、これらのアプリケーションは、異なるベース アドレスにバインドされています。インターネット インフォメーション サービス \(IIS\) Web サイトは、複数のアプリケーションを格納できます。サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。  
  
 IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。バインディング プロトコルは通信を行うスキームを定義するもので、バインディング情報はサイトにアクセスするために使用する情報です。  
  
 IIS バインディングに使用されるコンポーネントの例を次に示します。  
  
-   バインディング プロトコル : HTTP  
  
-   バインディング情報 : IP アドレス、ポート、ホスト ヘッダー  
  
 IIS ではサイトごとに複数の IIS バインディングを指定でき、これによりスキームごとに複数のベース アドレスをサポートできます。[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 以前は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではスキームごとに複数のアドレスがサポートされておらず、複数のアドレスが指定された場合は、アクティブ化の間に <xref:System.ArgumentException> がスローされました。  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] により、インターネット サービス プロバイダーは同じサイト上の同じスキームに対して別のベース アドレスを使用して複数のアプリケーションをホストできます。  
  
 たとえば、サイトで次のベース アドレスを使用できます。  
  
-   http:\/\/payroll.myorg.com\/Service.svc  
  
-   http:\/\/shipping.myorg.com\/Service.svc  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] では、構成ファイルの AppDomain レベルでプレフィックス フィルターを指定できます。これには、プレフィックスの一覧を格納する [\<baseAddressPrefixFilters\>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) 要素を使用します。IIS によって指定される受信ベース アドレスは、オプションのプレフィックス一覧に基づいてフィルター処理されます。既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。プレフィックスを指定すると、そのスキームに一致するベース アドレスだけが渡されます。  
  
 プレフィックス フィルターを使用する構成コード例を次に示します。  
  
```  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 上記の例では、net.tcp:\/\/payroll.myorg.com:8000 と http:\/\/shipping.myorg.com:8000 が、対応するスキームに対して渡されるベース アドレスです。  
  
 `baseAddressPrefixFilter` では、ワイルカードはサポートされません。  
  
 IIS が提供するベース アドレスには、`baseAddressPrefixFilters` 一覧に存在しない他のスキームにバインドされたアドレスが指定される場合があります。これらのアドレスはフィルターで除外されません。  
  
## .NET Framework 4 以降での複数の IIS バインディングのサポート  
 .NET 4 以降、<xref:System.ServiceModel.ServiceHostingEnvironment> の <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 設定を true に設定するだけで、1 つのベース アドレスを選択しなくても、IIS で複数のバインディングのサポートが有効になります。このサポートは、HTTP プロトコル スキームに限定されます。  
  
 [\<serviceHostingEnvironment\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) 上で multipleSiteBindingsEnabled を使用する構成コード例を次に示します。  
  
```  
  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled=”true” >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 複数のサイト バインディングがこの設定を使用して有効になっている場合、HTTP プロトコルと非 HTTP プロトコルの両方について、baseAddressPrefixFilters 設定は無視されます。  
  
 詳細および例については、「[複数の IIS サイト バインディングのサポート](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)」および「<xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>」を参照してください。  
  
## WCF サービスによるアドレスの拡張  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの既定のアドレス指定モデルでは、エンドポイント アドレス URI を次の目的で使用します。  
  
-   サービスがリッスンするアドレス、つまりエンドポイントがメッセージをリッスンする位置の指定  
  
-   SOAP アドレス フィルター、つまりエンドポイントが SOAP ヘッダーとして待機するアドレスの指定  
  
 これらの目的で使用する値は個別に指定することができるため、アドレス指定の拡張が可能になり、次に示すような役に立つシナリオに対応します。  
  
-   SOAP 中継局 : クライアントが送信したメッセージは、最終目的地に到達する前にメッセージを処理する 1 つ以上の追加サービスを経由します。SOAP 中継局は、メッセージのキャッシュ、ルーティング、負荷分散、スキーム検証など多様なタスクを実行できます。このシナリオは、最終的な送信先である論理アドレス \(`wsa:To`\) ではなく、中継局を目的とする独立した物理アドレス \(`via`\) にメッセージを送信することによって実現されます。  
  
-   エンドポイントがリッスンするアドレスはプライベート URI であり、`listenURI` プロパティとは異なる値が設定されます。  
  
 `via` が指定するトランスポート アドレスはメッセージが最初に送信される場所で、この後にメッセージは、`to` パラメーターによって指定された、サービスが存在する別のリモート アドレスに送信されます。インターネットの場合、`via` URI は、サービスの最終的な `to` アドレスの <xref:System.ServiceModel.EndpointAddress.Uri%2A> プロパティと同じになります。この 2 つのアドレスを区別するのは、手動ルーティングを行う必要がある場合のみです。  
  
### ヘッダーのアドレス指定  
 エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。  
  
 カスタムのアドレス ヘッダーは、コードまたは構成のいずれかを使用して次のように定義できます。  
  
-   コードを使用する場合、カスタムのアドレス ヘッダーは <xref:System.ServiceModel.Channels.AddressHeader> クラスを使用して作成し、<xref:System.ServiceModel.EndpointAddress> の構築時に使用されます。  
  
-   構成を使用する場合、カスタムの [\<headers\>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)[\<endpoint\> は、](http://msdn.microsoft.com/ja-jp/13aa23b7-2f08-4add-8dbf-a99f8127c017) 要素の子要素として指定します。  
  
 配置後もヘッダーを変更できるため、コードよりも構成を使用する方法を一般的にお勧めします。  
  
### カスタム リッスン アドレス  
 リッスンするアドレスには、エンドポイントの URI とは異なる値を設定できます。これは、SOAP アドレスがパブリックな SOAP 中継局として公開される一方、エンドポイントが実際にリッスンするアドレスはプライベートなネットワーク アドレスであるような中継局シナリオの場合に便利です。  
  
 カスタム リッスン アドレスは、コードまたは構成のいずれかを使用して指定できます。  
  
-   コードを使用する場合、カスタム リッスン アドレスはエンドポイントの動作コレクションに <xref:System.ServiceModel.Description.ClientViaBehavior> クラスを追加して指定します。  
  
-   構成を使用する場合、カスタム リッスン アドレスはサービスの [\<endpoint\>](http://msdn.microsoft.com/ja-jp/13aa23b7-2f08-4add-8dbf-a99f8127c017) 要素の `ListenUri` 属性で指定します。  
  
### カスタム SOAP アドレス フィルター  
 エンドポイントの SOAP アドレス フィルター \(<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>\) を定義するには、<xref:System.ServiceModel.EndpointAddress.Uri%2A> に任意の <xref:System.ServiceModel.EndpointAddress.Headers%2A> プロパティを組み合わせて使用します。既定では、このフィルターは受信メッセージの `To` メッセージ ヘッダーが、エンドポイントの URI に一致し、必要なすべてのエンドポイント ヘッダーがメッセージ内に存在していることを検証します。  
  
 シナリオによっては、適切な `To` ヘッダーを持つメッセージだけではなく、基になるトランスポートに到着したすべてのメッセージをエンドポイントで受信します。これを行うには、ユーザーは <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> クラスを使用します。  
  
## 参照  
 [エンドポイント アドレスの指定](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)   
 [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
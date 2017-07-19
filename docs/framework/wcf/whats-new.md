---
title: "Windows Communication Foundation 4.5 の新機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF [WCF], 新機能"
  - "Windows Communication Foundation [WCF], 新機能"
ms.assetid: 7e93fe73-af93-46b5-9f63-32f761ee40cf
caps.latest.revision: 35
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 35
---
# Windows Communication Foundation 4.5 の新機能
このトピックでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] の新しい機能について説明します。  
  
## WCF の単純化機能  
 WCF 4.5 アプリケーションの開発および保守を容易にするために多大な労力が費やされてきました。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF の単純化機能](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### タスク ベースの非同期のサポート  
 既定では、サービス参照の追加によって、タスクを返す非同期サービス操作メソッドが生成されます。この処理は、同期メソッドと非同期メソッドの両方に対して行われます。これにより、新しいタスク ベースの非同期プログラミング モデルを使用して、サービス操作を非同期に呼び出すことができます。生成されたプロキシ メソッドを呼び出すと、WCF によって非同期操作を表すタスク オブジェクトが構築され、そのタスクが返されます。タスクは操作の完了時に完了します。非同期操作を実装する場合は、その操作をタスク ベースの非同期操作として実装できます。詳細については、「[同期操作と非同期操作](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)」を参照してください。  
  
### 生成された構成ファイルの簡略化  
 Visual Studio でサービス参照を追加したり、SvcUtil.exe ツールを使用したりすると、クライアント構成ファイルが生成されます。以前のバージョンの WCF では、このような構成ファイルには、各バインド プロパティの値が既定値であっても、その値が含まれていました。WCF 4.5 では、生成された構成ファイルには、既定値以外の値に設定されているバインド プロパティのみが含まれます。  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [WCF の単純化機能](../../../docs/framework/wcf/wcf-simplification-features.md)  
  
### コントラクト優先の開発  
 WCF では、コントラクト優先の開発がサポートされるようになりました。svcutl.exe には、WSDL ドキュメントからサービス コントラクトとデータ コントラクトを生成できるようにする \/serviceContract スイッチがあります。  
  
### ポータブル サブセット プロジェクトからのサービス参照の追加  
 ポータブル サブセット プロジェクトにより、.NET アセンブリ プログラマは 1 つのソース ツリーを保持しつつ、システムを構築できるようになります。また、ポータブル サブセット プロジェクトは、複数の .NET プラットフォーム \(デスクトップ、Silverlight、Windows Phone、および XBOX\) をサポートしています。ポータブル サブセット プロジェクトは、コア .NET プラットフォームで使用できる .NET Framework アセンブリである .NET ポータブル ライブラリのみを参照します。開発者から見れば、他の WCF クライアント アプリケーション内でサービス参照を追加するのと同じです。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][ポータブル サブセット プロジェクトでサービス参照を追加する](../../../docs/framework/wcf/add-service-reference-in-a-portable-subset-project.md).  
  
### ASP.NET 互換性モードの既定値の変更  
 WCF には ASP.NET 互換性モードが用意されています。これにより、開発者は WCF サービスを作成する際に ASP.NET HTTP パイプラインの機能へのフル アクセスが付与されます。このモードを使用するには、web.config の [\<serviceHostingEnvironment\>](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) セクションで `aspNetCompatibilityEnabled` 属性を true に設定する必要があります。さらに、この appDomain 内のサービスでは、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> の `RequirementsMode` プロパティを <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> または <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> に設定しておく必要があります。既定では、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> は <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> に設定されています。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)]「[What's New in Windows Communication Foundation](../../../docs/framework/wcf/whats-new.md)」および「[WCF サービスと ASP.NET](../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)」を参照してください。  
  
### トランスポートの新しい既定値  
 構成を簡略化するため、多くのトランスポート プロパティの既定値が変更されました。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF の単純化機能](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### XmlDictionaryReaderQuotas  
 <xref:System.Xml.XmlDictionaryReaderQuotas> には、メッセージの作成中にエンコーダーで使用されるメモリの量を制限する XML ディクショナリ リーダーの構成可能なクォータ値が格納されます。これらのクォータは構成可能ですが、開発者がこのクォータを明示的に設定する必要性を低くするために既定値が変更されました。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF の単純化機能](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
### WCF 構成検証  
 Visual Studio 内のビルド プロセスの一環として、プロジェクト内で定義された属性について WCF 構成ファイルが検証されるようになりました。検証に失敗すると、Visual Studio では検証エラーと警告の一覧が表示されます。  
  
### XML エディターのツールヒント  
 新規および既存の WCF サービスの開発者がサービスを構成するうえで役立つよう、Visual Studio の XML エディターでは、サービス構成ファイルに含まれる各構成要素とそのプロパティにツールヒントが表示されるようになりました。  
  
## ストリーミングの強化  
 非同期ストリーミングのサポートが追加されました。これにより、受信側が読み取らない場合または読み取り速度が遅い場合に送信側がスレッドをブロックすることはなくなったため、スケーラビリティが向上します。IIS でホストされる WCF サービスにクライアントがストリーム メッセージを送信する際のメッセージ バッファーの制限を解除しました。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF の単純化機能](../../../docs/framework/wcf/wcf-simplification-features.md).  
  
## IIS での HTTPS 上のエンドポイントの公開の簡略化  
 HTTPS 上のエンドポイントの公開を簡単にするため、HTTPS のプロトコル マッピングが追加されました。HTTPS のエンドポイントを有効にするには、Web サイトで HTTPS バインドと SSL 証明書が構成されていることを確認した後、サービスをホストする仮想ディレクトリに対して HTTPS を有効にするだけです。サービスのメタデータが有効になっている場合は、それも HTTPS を介して公開されます。  
  
## 単一の WSDL ドキュメントの生成  
 サード パーティの WSDL の処理スタックには、xsd:import を使用して他のドキュメントに依存している WSDL ドキュメントを処理できないものもあります。WCF により、すべての WSDL 情報が 1 つのドキュメントで返されるように指定できるようになりました。単一の WSDL ドキュメントを要求するには、サービスからメタデータを要求するときに URI に "?singleWSDL" を追加してください。  
  
## WebSocket のサポート  
 Websocket は、TCP と同様のパフォーマンス特性を持つポート 80 と 443 で真の双方向通信を実現するテクノロジです。WebSocket トランスポート経由の通信をサポートするために 2 つの新しいバインドが追加されました。<xref:System.ServiceModel.NetHttpBinding> および <xref:System.ServiceModel.NetHttpsBinding>。詳細については、「[システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。  
  
## トランスポートの新しい既定値  
 次の表は、変更された設定と追加情報の場所を示しています。  
  
|プロパティ|場所|新しい既定値|参照先|  
|-----------|--------|------------|---------|  
|channelInitializationTimeout|<xref:System.ServiceModel.NetTcpBinding>|30 秒|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.ChannelInitializationTimeout%2A>|  
|listenBacklog|<xref:System.ServiceModel.NetTcpBinding>|12 \* プロセッサの数|<xref:System.ServiceModel.NetTcpBinding.ListenBacklog%2A>|  
|maxPendingAccepts|ConnectionOrientedTransportBindingElement<br /><br /> SMSvcHost.exe|2 \* トランスポート用のプロセッサの数<br /><br /> 4 \* SMSvcHost.exe 用のプロセッサの数|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingAccepts%2A> [Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/ja-jp/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
|maxPendingConnections|ConnectionOrientedTransportBindingElement|12 \* プロセッサの数|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement.MaxPendingConnections%2A>|  
|receiveTimeout|SMSvcHost.exe|30 秒|[Configuring the Net.TCP Port Sharing Service](http://msdn.microsoft.com/ja-jp/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)|  
  
## XML エディターのツールヒント  
 新規および既存の WCF サービスの開発者がサービスを構成するうえで役立つよう、Visual Studio の XML エディターでは、サービス構成ファイルに含まれる各構成要素とそのプロパティにツールヒントが表示されるようになりました。  
  
## コード内での WCF サービスの構成  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、開発者が構成ファイルまたはコードを使用してサービスを構成できます。構成ファイルは、サービスを配置した後に構成する必要がある場合に便利です。構成ファイルを使用する場合、IT 専門家は構成ファイルを更新するだけで、再コンパイルの必要はありません。ただし、構成ファイルの管理は複雑で難しくなる場合があります。構成ファイルのデバッグはサポートされていません。また、構成要素は名前で参照されるため、構成ファイルの作成時にエラーが発生しやすく、構成ファイルの作成が困難になります。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、コードでサービスを構成することもできます。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の以前のバージョン \(4.0 以前\) では、自己ホスト型のシナリオであれば、コードで簡単にサービスを構成できました。また、<xref:System.ServiceModel.ServiceHost> クラスを使用すると、ServiceHost.Open を呼び出す前にエンドポイントと動作を構成できました。ただし、Web ホストのシナリオでは、<xref:System.ServiceModel.ServiceHost> クラスにアクセスできません。Web ホスト サービスを構成するには、<xref:System.ServiceModel.ServiceHost> を作成して必要な構成を実行する <xref:System.ServiceModel.ServiceHostFactory> を作成する必要がありました。.NET 4.5 以降では、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用すると、自己ホスト型サービスと Web ホスト サービスの両方をコードで簡単に構成できます。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][コード内での WCF サービスの構成](../../../docs/framework/wcf/configuring-wcf-services-in-code.md).  
  
## ChannelFactory のキャッシュ  
 WCF クライアント アプリケーションでは、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して WCF サービスとの通信チャネルを作成します。<xref:System.ServiceModel.ChannelFactory%601> インスタンスを作成する場合は、次の操作が必要になるため、オーバーヘッドが生じます。  
  
1.  <xref:System.ServiceModel.Description.ContractDescription> ツリーの構築  
  
2.  必要なすべての CLR 型の反映  
  
3.  チャネル スタックの構築  
  
4.  リソースの破棄  
  
 このオーバーヘッドを最小限に抑えるために、WCF では、WCF クライアント プロキシの使用時にチャネル ファクトリをキャッシュできます。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][チャネル ファクトリとキャッシュ](../../../docs/framework/wcf/feature-details/channel-factory-and-caching.md).  
  
## 圧縮およびバイナリ エンコーダー  
 WCF 4.5 以降の WCF バイナリ エンコーダーでは、圧縮がサポートされます。圧縮の種類は <xref:System.ServiceModel.Channels.BinaryMessageEncodingElement.CompressionFormat%2A> プロパティで構成されます。クライアントとサービスの両方で <xref:System.ServiceModel.Channels.BinaryMessageEncodingElement.CompressionFormat%2A> のプロパティを構成する必要があります。圧縮は、HTTP、HTTPS、および TCP の各プロトコルに対して有効です。クライアントが圧縮を使用するよう指定しても、サービスで圧縮がサポートされていない場合は、プロトコルの不一致を示すプロトコルの例外がスローされます。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][メッセージ エンコーダーを選択する](../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
  
## UDP  
 UDP トランスポートのサポートが追加されたため、開発者は "ファイア アンド フォーゲット \(撃ち放し\)" メッセージングを使用するサービスを作成できるようになります。クライアントは、サービスにメッセージを送信しますが、サービスからの応答を期待しません。  
  
## 複数認証のサポート  
 HTTP トランスポートとトランスポート セキュリティを使用する際に、IIS でサポートされている複数の認証モードを単一の WCF エンドポイントで使用できるようになりました。IIS では仮想ディレクトリで複数の認証モードを有効にできます。この機能によって、単一の WCF エンドポイントでは、WCF サービスがホストされている仮想ディレクトリで有効になっている複数の認証モードをサポートできます。  
  
## IDN サポート  
 国際化ドメイン名を持つ WCF サービスのためのサポートが追加されました。詳細については、「[WCF と国際化ドメイン名](../../../docs/framework/wcf/feature-details/wcf-and-internationalized-domain-names.md)」を参照してください。  
  
## HttpClient  
 HTTP 要求の処理が容易になるように <xref:System.Net.Http.HttpClient> という新しいクラスが追加されました。詳細については、「[ソーシャル アプリの開発と HTTP サービスへの接続](http://go.microsoft.com/fwlink/?LinkId=231886)」および「[HttpClient サンプル](http://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)」を参照してください。  
  
## 構成の Intellisense  
 プロジェクトで定義されるカスタム属性の構成ファイル内の属性値では、構成の迅速で正確な操作を簡単にするために Intellisense がサポートされています。  
  
## 構成のツールヒント  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の要素と属性のツールヒントが XML エディターで表示され、要素または属性の目的をより簡単かつ正確に特定できるようになりました。  
  
## クラスとしてのデータの貼り付け  
 WCF プロジェクトでは、XML で定義されたデータ型 \(サービスで公開されるデータ型など\) をコード ページに直接貼り付けることができます。XML 型は CLR 型として貼り付けられます。詳細については、「[XML からのデータ型クラスの生成](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)」を参照してください。  
  
## WebServiceHost と既定のエンドポイント  
 Visual Studio 2010 では、明示的にエンドポイントを指定したかどうかにかかわらず、WebServiceHost によって自動的に既定のエンドポイントが作成されました。Visual Studio 2012 では、エンドポイントが明示的に追加されていない場合にのみ、WebServiceHost によって既定のエンドポイントが作成されます。クライアントが既定のエンドポイントを必要としている場合は、明示的にエンドポイントを追加し、クライアントで参照することができます。または、アプリケーションの構成ファイルに次の設定を追加することで、以前の動作に戻すように WCF に指定することもできます。  
  
```xml  
<appSettings>  
    <add key="wcf:webservicehost:enableautomaticendpointscompatability" value="true"/>  
  </appSettings>  
  
```  
  
## IHttpCookieContainerManager  
 このインターフェイスは、<xref:System.ServiceModel.Channels.HttpChannelFactory> によって公開されます。これにより、クライアント側でのクッキーの操作がさらに容易になります。AllowCookies がバインドで true に設定されている場合は、次のコードを使用してクッキーにアクセスできます。  
  
```csharp  
IHttpCookieContainerManager cookieManager = factory.GetProperty<IHttpCookieContainerManager>();   
System.Net.CookieContainer container = cookieManager.CookieContainer;  
  
```  
  
 その後、<xref:System.Net.CookieContainer> からクッキーを取得または設定できます。AllowCookies が false に設定されている場合は、<xref:System.ServiceModel.OperationContext> を使用して手動でクッキーを取得し、別の <xref:System.ServiceModel.OperationContext> またはメッセージ インスペクターを使用して他の要求でそのクッキーを送信できます。IHttpCookieContainerManager インターフェイスを使用すると、サービスを使用してユーザーを認証し、そのサービスから返される認証クッキーを使用して他のサービスで認証することができます。
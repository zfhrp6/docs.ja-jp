---
title: "ストリーミング プロバイダー (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ストリーミング データ プロバイダー (WCF Data Services)"
  - "WCF Data Services, バイナリ データ"
  - "WCF Data Services, プロバイダー"
  - "WCF Data Services, ストリーム"
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ストリーミング プロバイダー (WCF Data Services)
データ サービスは、ラージ オブジェクトのバイナリ データを公開できます。  このバイナリ データは、ビデオ ストリームとオーディオ ストリーム、画像、ドキュメント ファイル、またはその他の種類のバイナリのメディアを表すことができます。  データ モデルのエンティティに 1 つ以上のバイナリ プロパティが含まれている場合、データ サービスは、このバイナリ データを応答フィードのエントリ内に Base\-64 としてエンコードして返します。  この方法で大きなバイナリ データを読み込んでシリアル化するとパフォーマンスに影響を及ぼす可能性があるため、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] では、属するエンティティとは独立してバイナリ データを取得するためのメカニズムが定義されています。  これは、バイナリ データとエンティティを分離して 1 つ以上のデータ ストリームを生成することで実現されます。  
  
-   メディア リソース \- エンティティに属するバイナリ データ \(ビデオ、オーディオ、画像、その他の種類のメディア リソース ストリームなど\)。  
  
-   メディア リンク エントリ \- 関連するメディア リソース ストリームへの参照を含むエンティティ。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、ストリーミング データ プロバイダーを実装してバイナリ リソース ストリームを定義します。  ストリーミング プロバイダーを実装すると、<xref:System.IO.Stream> オブジェクトとして特定のエンティティに関連付けられているメディア リソース ストリームがデータ サービスに提供されます。  この実装によって、データ サービスでは、指定された MIME の種類のバイナリ データ ストリームとしてメディア リソースを HTTP 経由で受け入れて、返すことができます。  
  
 バイナリ データのストリーミングをサポートするデータ サービスを構成するには、次の手順に従う必要があります。  
  
1.  データ モデル内の 1 つ以上のエンティティをメディア リンク エントリとして属性化します。  これらのエンティティには、ストリーミング対象のバイナリ データを含めないでください。  エンティティのバイナリ プロパティは、常に Base\-64 でエンコードされたバイナリとしてエントリで返されます。  
  
2.  T:System.Data.Services.Providers.IDataServiceStreamProvider インターフェイスを実装します。  
  
3.  <xref:System.IServiceProvider> インターフェイスを実装するデータ サービスを定義します。  データ サービスは、<xref:System.IServiceProvider.GetService%2A> の実装を使用してストリーミング データ プロバイダーの実装にアクセスします。  このメソッドは、適切なストリーミング プロバイダーの実装を返します。  
  
4.  Web アプリケーション構成で大きいメッセージ ストリームを有効にします。  
  
5.  サーバー上またはデータ ソース内のバイナリ リソースへのアクセスを有効にします。  
  
 このトピックの例はサンプルのストリーミング フォト サービスに基づいています。詳細については、ブログの記事「[Data Services ストリーミング プロバイダー シリーズ: ストリーミング プロバイダーの実装 \(パート 1\)](http://go.microsoft.com/fwlink/?LinkID=198989)」を参照してください。  このサンプル サービスのソース コードは、MSDN コード ギャラリーにある [Streaming Photo Data Service サンプルのページ](http://go.microsoft.com/fwlink/?LinkID=198988)から入手できます。  
  
## データ モデル内のメディア リンク エントリの定義  
 エンティティがデータ モデル内のメディア リンク エントリとして定義される方法は、データ ソース プロバイダーによって決定されます。  
  
 **Entity Framework プロバイダー**  
 エンティティがメディア リンク エントリであることを示すには、概念モデルのエンティティ型定義に `HasStream` 属性を追加します。次にその例を示します。  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 また、エンティティまたはデータ モデルを定義する .edmx ファイルまたは .csdl ファイルのルートに名前空間 `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` を追加する必要があります。  
  
 [!INCLUDE[crexample](../../../../includes/crexample-md.md)] [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダーを使用してメディア リソースを公開するデータ サービス 、ブログの記事「[Data Services ストリーミング プロバイダー シリーズ: ストリーミング プロバイダーの実装 \(パート 1\)](http://go.microsoft.com/fwlink/?LinkID=198989)」を参照してください。  
  
 **リフレクション プロバイダー**  
 エンティティがメディア リンク エントリであることを示すには、リフレクション プロバイダーのエンティティ型を定義するクラスに <xref:System.Data.Services.Common.HasStreamAttribute> を追加します。  
  
 **カスタム データ サービス プロバイダー**  
 カスタム サービス プロバイダーを使用する場合は、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを実装してデータ サービスのメタデータを定義します。  詳細については、「[カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)」を参照してください。  エンティティ型 \(メディア リンク エントリ\) を表す <xref:System.Data.Services.Providers.ResourceType> で <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> プロパティを `true` に設定して、バイナリ リソース ストリームが <xref:System.Data.Services.Providers.ResourceType> に属することを示します。  
  
## IDataServiceStreamProvider インターフェイスの実装  
 バイナリ データ ストリームをサポートするデータ サービスを作成するには、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装する必要があります。  これを実装すると、データ サービスはバイナリ データをストリームとしてクライアントに返し、クライアントから送信されたストリームとしてバイナリ データを使用できます。  データ サービスでは、バイナリ データへのストリームとしてのアクセスが必要になるたびに、このインターフェイスのインスタンスを作成します。  <xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスでは次のメンバーを指定します。  
  
|メンバー名|説明|  
|-----------|--------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|このメソッドはデータ サービスにより呼び出され、メディア リンク エントリが削除されたときに対応するメディア リソースを削除します。  <xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する場合、このメソッドには、指定されたメディア リンク エントリに関連付けられたメディア リソースを削除するコードが含まれます。|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|このメソッドはデータ サービスにより呼び出され、メディア リソースをストリームとして返します。  <xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する場合、このメソッドには、指定されたメディア リンク エントリに関連付けられたメディア リソースを返すためにデータ サービスが使用するストリームを提供するコードが含まれます。|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|このメソッドはデータ サービスにより呼び出され、メディア リンク エントリのメディア リソースを要求するために使用される URI を返します。  この値を使用して、メディア リンク エントリのコンテンツ要素の `src` 属性が作成され、データ ストリームが要求されます。  このメソッドから `null` が返されると、データ サービスによって URI が自動的に決定されます。  このメソッドは、ストリーミング プロバイダーを使用しないバイナリ データへの直接アクセスをクライアントに提供する必要がある場合に使用します。|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|このメソッドはデータ サービスにより呼び出され、指定されたメディア リンク エントリに関連付けられたメディア リソースの Content\-Type 値を返します。|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|このメソッドはデータ サービスにより呼び出され、指定されたエンティティに関連付けられたデータ ストリームの eTag を返します。  このメソッドは、バイナリ データの同時実行を管理する場合に使用されます。  このメソッドが null を返す場合、データ サービスでは同時実行が追跡されません。|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|このメソッドはデータ サービスにより呼び出され、クライアントから送信されたストリームの受信時に使用されるストリームを取得します。  <xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する場合、データ サービスが受信したストリーム データを書き込む先である書き込み可能なストリームを返す必要があります。|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|名前空間で修飾された型名を返します。この型は、挿入されるメディア リソースのデータ ストリームに関連付けられたメディア リンク エントリに対してデータ サービス ランタイムが作成する必要がある型を表します。|  
  
## ストリーミング データ サービスの作成  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ランタイムに <xref:System.Data.Services.Providers.IDataServiceStreamProvider> の実装へのアクセスを提供するには、作成するデータ サービスで <xref:System.IServiceProvider> インターフェイスも実装する必要があります。  次の例は、<xref:System.IServiceProvider.GetService%2A> メソッドを実装して、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する `PhotoServiceStreamProvider` クラスのインスタンスを返す方法を示しています。  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 データ サービスの作成方法に関する一般的な情報については、「[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
## ホスト環境での大きなバイナリ ストリームの有効化  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web アプリケーションのデータ サービスを作成する場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して HTTP プロトコルが実装されます。既定では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では HTTP メッセージのサイズは 65K バイトのみに制限されます。  また、データ サービスに対する大きなバイナリ データのストリーミングを可能にするには、大きなバイナリ ファイルを有効にして、転送にストリームを使用するように Web アプリケーションを構成する必要もあります。  そのためには、アプリケーションの Web.config ファイルの `<configuration />` 要素に次の内容を追加します。  
  
  
  
> [!NOTE]
>  <xref:System.ServiceModel.TransferMode?displayProperty=fullName> 転送モードを使用して、要求メッセージと応答メッセージの両方のバイナリ データをストリーミングし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によってバッファリングされないようにする必要があります。  
  
 詳細については、「[メッセージ転送ストリーミング](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)」および「[トランスポート クォータ](../../../../docs/framework/wcf/feature-details/transport-quotas.md)」を参照してください。  
  
 また、既定では、インターネット インフォメーション サービス \(IIS\) でも要求のサイズが 4 MB に制限されます。  IIS 上で実行時にデータ サービスが 4 MB を超えるストリームを受信できるようにするには、次の例に示すように、`<system.web />` 構成セクション内の [httpRuntime 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/e9b81350-8aaf-47cc-9843-5f7d0c59f369) の `maxRequestLength` 属性を設定する必要があります。  
  
  
  
## クライアント アプリケーションでのデータ ストリームの使用  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用すると、クライアントのバイナリ ストリームとして公開されたリソースを取得および更新できます。  詳細については、「[バイナリ データの操作](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)」を参照してください。  
  
## ストリーミング プロバイダーの使用に関する考慮事項  
 ストリーミング プロバイダーを実装する場合およびデータ サービスからメディア リソースにアクセスする場合には、次の点を考慮してください。  
  
-   MERGE 要求は、メディア リソースではサポートされません。  既存のエンティティのメディア リソースを変更するには、PUT 要求を使用します。  
  
-   POST 要求を使用して新しいメディア リンク エントリを作成することはできません。  代わりに、POST 要求を発行して新しいメディア リソースを作成する必要があります。データ サービスによって、既定値で新しいメディア リンク エントリが作成されます。  その後に MERGE 要求または PUT 要求を使用してこの新しいエンティティを更新できます。  プロパティ値を POST 要求の Slug ヘッダーの値に設定するなど、エンティティをキャッシュしてディスポーザーで更新を行うこともできます。  
  
-   POST 要求を受信すると、データ サービスは <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> を呼び出してメディア リソースを作成してから、<xref:System.Data.Services.IUpdatable.SaveChanges%2A> を呼び出してメディア リンク エントリを作成します。  
  
-   <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> を実装すると、<xref:System.IO.MemoryStream> オブジェクトは返されません。  この種類のストリームを使用すると、サービスが非常に大きなデータ ストリームを受信した場合に、メモリ リソースの問題が発生します。  
  
-   データベースにメディア リソースを格納する場合は、次の点を考慮してください。  
  
    -   メディア リソースであるバイナリ プロパティをデータ モデルに含めないようにしてください。  データ モデルで公開されるプロパティはすべて、応答フィードのエントリで返されます。  
  
    -   大きなバイナリ ストリームのパフォーマンスを向上させるには、カスタム ストリーム クラスを作成してバイナリ データをデータベースに格納することをお勧めします。  このクラスは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> の実装によって返され、バイナリ データをチャンク単位でデータベースに送信します。  [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] データベースでは、バイナリ データが 1 MB を超える場合、FILESTREAM を使用してデータをデータベースにストリーミングすることをお勧めします。  
  
    -   データ サービスによって受信される大きなバイナリ ストリームを格納できるようにデータベースが設計されていることを確認してください。  
  
    -   クライアントが POST 要求を送信して、1 回の要求でメディア リソースと共にメディア リンク エントリを挿入する場合は、データ サービスによって新しいエンティティがデータベースに挿入される前に、<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> を呼び出してストリームを取得します。  ストリーミング プロバイダーは、このデータ サービスの動作を処理できるように実装する必要があります。  エンティティがデータベースに挿入されるまで、個別のデータ テーブルを使用してバイナリ データを格納するか、データ ストリームをファイルに格納することを検討してください。  
  
-   <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A> メソッド、<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A> メソッド、または <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> メソッドを実装する場合は、メソッドのパラメーターとして指定される eTag 値および Content\-Type 値を使用する必要があります。  <xref:System.Data.Services.Providers.IDataServiceStreamProvider> プロバイダーの実装には、eTag ヘッダーまたは Content\-Type ヘッダーを設定しないでください。  
  
-   既定では、クライアントはチャンクされた HTTP Transfer\-Encoding を使用して、大きなバイナリ ストリームを送信します。  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発サーバーはこの種類のエンコーディングをサポートしていないので、この Web サーバーを使用して大きなバイナリ ストリームを受け取る必要があるストリーミング データ サービスをホストすることはできません。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開発サーバーの詳細については、「[Web Servers in Visual Studio for ASP.NET Web Projects](http://msdn.microsoft.com/ja-jp/31d4f588-df59-4b7e-b9ea-e1f2dd204328)」を参照してください。  
  
<a name="versioning"></a>   
## バージョン管理の要件  
 ストリーミング プロバイダーには、次に示す [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのバージョン管理の要件があります。  
  
-   ストリーミング プロバイダーを使用するには、データ サービスでバージョン 2.0 以降の [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルがサポートされている必要があります。  
  
 詳細については、「[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)」を参照してください。  
  
## 参照  
 [データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)   
 [バイナリ データの操作](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
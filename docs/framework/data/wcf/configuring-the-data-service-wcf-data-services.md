---
title: "データ サービスの構成 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 構成"
ms.assetid: 59efd4c8-cc7a-4800-a0a4-d3f8abe6c55c
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# データ サービスの構成 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを公開するデータ サービスを作成できます。  これらのフィードには、さまざまなデータ ソースからのデータが含まれることがあります。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、データ プロバイダーを使用して、このデータを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開します。  これらのプロバイダーには、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダー、リフレクション プロバイダー、およびカスタム データ サービス プロバイダー インターフェイスのセットがあります。  プロバイダーの実装は、サービスのデータ モデルを定義します。  詳細については、「[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)」を参照してください。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスは、データ サービスの種類がデータ モデルのエンティティ コンテナーである <xref:System.Data.Services.DataService%601> クラスから継承するクラスです。  このエンティティ コンテナーには、データ モデルのエンティティ セットにアクセスするために使用される <xref:System.Linq.IQueryable%601> を返す 1 つ以上のプロパティがあります。  
  
 データ サービスの動作は、<xref:System.Data.Services.DataServiceConfiguration> クラスのメンバー、および <xref:System.Data.Services.DataServiceConfiguration> クラスの <xref:System.Data.Services.DataServiceConfiguration.DataServiceBehavior%2A> プロパティからアクセスされる <xref:System.Data.Services.DataServiceBehavior> クラスのメンバーによって定義されます。  <xref:System.Data.Services.DataServiceConfiguration> クラスは、Northwind データ サービスの次の実装のように、データ サービスによって実装される `InitializeService` メソッドに提供されます。  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigcomplete)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigcomplete)]  
  
## データ サービス構成設定  
 <xref:System.Data.Services.DataServiceConfiguration> クラスでは、以下のデータ サービスの動作を指定できます。  
  
|メンバー|動作|  
|----------|--------|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptCountRequests%2A>|`$count` パス セグメントおよび `$inlinecount` クエリ オプションを使用してデータ サービスに送信したカウント要求を無効にできます。  詳細については、「[OData: URI 規則](http://go.microsoft.com/fwlink/?LinkId=185564)」を参照してください。|  
|<xref:System.Data.Services.DataServiceBehavior.AcceptProjectionRequests%2A>|`$select` クエリ オプションを使用してデータ サービスに送信された要求のデータ プロジェクションのサポートを無効にできます。  詳細については、「[OData: URI 規則](http://go.microsoft.com/fwlink/?LinkId=185564)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeAccess%2A>|<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを使用して定義された動的メタデータ プロバイダーのメタデータでデータ型を公開します。|  
|<xref:System.Data.Services.DataServiceConfiguration.EnableTypeConversion%2A>|ペイロードに含まれている型を、要求で指定された実際のプロパティ型にデータ サービス ランタイムで変換するかどうかを指定できます。|  
|<xref:System.Data.Services.DataServiceBehavior.InvokeInterceptorsOnLinkDelete%2A>|2 つのエンティティ間のリレーションシップ リンクを削除するときに、関連エンティティで登録済みの変更インターセプターを呼び出すかどうかを指定できます。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxBatchCount%2A>|単一のバッチで許可される変更セットおよびクエリ操作の数を制限できます。  詳細については、「[OData: バッチ](http://go.microsoft.com/fwlink/?LinkId=185602)」および「[バッチ処理](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxChangesetCount%2A>|単一の変更セットに含めることができる変更の数を制限できます。  詳細については、「[方法: データ サービスの結果のページングを有効にする](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandCount%2A>|`$expand` クエリ演算子を使用して 1 つの要求に含めることのできる関連エンティティの数を制限することによって応答のサイズを制限できます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[OData: URI 規則](http://go.microsoft.com/fwlink/?LinkId=185564)」および「[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxExpandDepth%2A>|`$expand` クエリ演算子を使用して 1 つの要求に含めることのできる関連エンティティのグラフの深度を制限することによって応答のサイズを制限できます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[OData: URI 規則](http://go.microsoft.com/fwlink/?LinkId=185564)」および「[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxObjectCountOnInsert%2A>|1 つの POST 要求に挿入できるエンティティの数を制限できます。|  
|<xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>|データ サービスによって使用される Atom プロトコルのバージョンを定義します。  <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> に <xref:System.Data.Services.Common.DataServiceProtocolVersion> の最大値よりも低い値を設定した場合、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の最新の機能はデータ サービスにアクセスするクライアントで使用できなくなります。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).|  
|<xref:System.Data.Services.DataServiceConfiguration.MaxResultsPerCollection%2A>|データ フィードとして返される各エンティティ セットのエンティティの数を制限することによって応答のサイズを制限できます。|  
|<xref:System.Data.Services.DataServiceConfiguration.RegisterKnownType%2A>|データ サービスで認識される型のリストにデータ型を追加します。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetAccessRule%2A>|データ サービスで使用可能なエンティティ セット リソースへのアクセス権を設定します。  アスタリスク \(`*`\) 値を名前パラメーターに使用すると、残りのすべてのエンティティ セットへのアクセスを同じレベルに設定できます。  エンティティ セットへのアクセスを設定する場合は、クライアント アプリケーションに必要なデータ サービス リソースへの最小アクセス特権を設定することをお勧めします。  詳細については、「[WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。  特定の URI および HTTP アクションに必要な最小限のアクセス権の例については、以下の「[最小限のリソース アクセス要件](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements)」セクションを参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetEntitySetPageSize%2A>|エンティティ セット リソースの最大ページ サイズを設定します。  詳細については、「[方法: データ サービスの結果のページングを有効にする](../../../../docs/framework/data/wcf/how-to-enable-paging-of-data-service-results-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.SetServiceOperationAccessRule%2A>|データ サービスで定義されるサービス操作へのアクセス権を設定します。  詳細については、「[サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)」を参照してください。  アスタリスク \(`*`\) 値を名前パラメーターに使用すると、残りのすべてのサービス操作へのアクセスを同じレベルに設定できます。  サービス操作へのアクセスを設定する場合は、クライアント アプリケーションに必要なデータ サービス リソースへの最小アクセス特権を設定することをお勧めします。  詳細については、「[WCF Data Services のセキュリティ保護](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)」を参照してください。|  
|<xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A>|この構成プロパティを使用すると、エラー応答メッセージで多くの情報を返すことによってデータ サービスのトラブルシューティングを容易にすることができます。  このオプションは、運用環境で使用することを目的としたものではありません。  詳細については、「[WCF Data Services の開発と配置](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)」を参照してください。|  
  
<a name="accessRequirements"></a>   
## 最小限のリソース アクセス要件  
 次の表に、特定の操作を実行するために付与されている必要があるエンティティ セットの最小限の権限を示します。  パスの例は、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)の完了時に作成される Northwind データ サービスに基づいています。  <xref:System.Data.Services.EntitySetRights> 列挙体および <xref:System.Data.Services.ServiceOperationRights> 列挙体は <xref:System.FlagsAttribute> を使用して定義されているので、論理和演算子を使用して 1 つのエンティティ セットまたは操作に複数のアクセス許可を指定できます。  詳細については、「[方法: データ サービスへのアクセスを有効にする](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)」を参照してください。  
  
|パス\/アクション|`GET`|`DELETE`|`MERGE`|`POST`|`PUT`|  
|---------------|-----------|--------------|-------------|------------|-----------|  
|`/Customers`|<xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|<xref:System.Data.Services.EntitySetRights>|サポートなし|  
|`/Customers('ALFKI')`|<xref:System.Data.Services.EntitySetRights>|<xref:System.Data.Services.EntitySetRights> および<xref:System.Data.Services.EntitySetRights>|<xref:System.Data.Services.EntitySetRights> および<xref:System.Data.Services.EntitySetRights>|適用なし|<xref:System.Data.Services.EntitySetRights> および<xref:System.Data.Services.EntitySetRights>|  
|`/Customers('ALFKI')/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights> または <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders` `:` および<xref:System.Data.Services.EntitySetRights>|サポートなし|  
|`/Customers('ALFKI')/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights>|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights>|  
|`/Orders(10643)/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights>|サポートなし|  
|`/Customers('ALFKI')/$links/Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights> または <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|サポートなし|  
|`/Customers('ALFKI')/$links/Orders(10643)`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights> または <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|サポートなし|  
|`/Orders(10643)/$links/Customer`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|`Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights> または <xref:System.Data.Services.EntitySetRights>|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights>|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights>;<br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights> および <xref:System.Data.Services.EntitySetRights>|  
|`/Customers/$count`|<xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|サポートなし|サポートなし|  
|`/Customers('ALFKI')/ContactName`|<xref:System.Data.Services.EntitySetRights>|サポートなし|<xref:System.Data.Services.EntitySetRights>|サポートなし|<xref:System.Data.Services.EntitySetRights>|  
|`/Customers('ALFKI')/Address/StreetAddress/$value` <sup>1</sup>|<xref:System.Data.Services.EntitySetRights>|<xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|サポートなし|  
|`/Customers('ALFKI')/ContactName/$value`|<xref:System.Data.Services.EntitySetRights>|<xref:System.Data.Services.EntitySetRights> および<xref:System.Data.Services.EntitySetRights>|<xref:System.Data.Services.EntitySetRights>|サポートなし|<xref:System.Data.Services.EntitySetRights>|  
|`/Customers('ALFKI')/$value` <sup>2</sup>|<xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|サポートなし|<xref:System.Data.Services.EntitySetRights>|  
|`/Customers?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|`Customers`: <xref:System.Data.Services.EntitySetRights>|サポートなし|  
|`/Customers('ALFKI')?$select=Orders/*&$expand=Orders`|`Customers`: <xref:System.Data.Services.EntitySetRights><br /><br /> および<br /><br /> `Orders`: <xref:System.Data.Services.EntitySetRights>|サポートなし|サポートなし|サポートなし|サポートなし|  
  
 <sup>1</sup> この例では、`Address` は `StreetAddress` という名前のプロパティを持つ `Customers` エンティティの複合型プロパティを表します。  Northwind データ サービスによって使用されるモデルでは、この複合型は明示的に定義されていません。  [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] プロバイダーを使用してデータ モデルを定義している場合、[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] ツールを使用して、このような複合型を定義できます。  詳細については、「[How to: Create and Modify Complex Types](http://msdn.microsoft.com/ja-jp/afb8e206-0ffe-4597-b6d4-6ab566897e1d)」を参照してください。  
  
 <sup>2</sup> この URI は、バイナリ ラージ オブジェクト \(BLOB\) を返すプロパティがメディア リンク エントリであるエンティティ \(この場合、`Customers`\) に属するメディア リソースとして定義されている場合にサポートされます。  詳細については、「[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)」を参照してください。  
  
<a name="versioning"></a>   
## バージョン管理の要件  
 次のデータ サービス構成の動作には、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのバージョン 2 またはそれ以降のバージョンが必要です。  
  
-   カウント要求のサポート。  
  
-   射影の $select クエリ オプションのサポート。  
  
 詳細については、「[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)」を参照してください。  
  
## 参照  
 [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [データ サービスのホスティング](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)
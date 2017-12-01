---
title: "単純なデータ ドリブン CRUD マイクロ サービスを作成します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |単純なデータ ドリブン CRUD マイクロ サービスを作成します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>単純なデータ ドリブン CRUD マイクロ サービスを作成します。

このセクションのアウトライン方法、単純なを作成するを実行するマイクロ サービスを作成、読み取り、更新、およびデータ ソースの削除 (CRUD) 操作です。

## <a name="designing-a-simple-crud-microservice"></a>単純な CRUD マイクロ サービスの設計

設計の観点からは、この種類のコンテナー化マイクロ サービスは非常に単純です。 解決する問題は単純な場合、おそらくかおそらく実装では、概念実証のみ。

![](./media/image4.png)

**図 8-4**です。 単純な CRUD microservices の内部設計

この種の単純なデータ ドライブのサービスの例は、eShopOnContainers サンプル アプリケーションからカタログ マイクロ サービスです。 この種類のサービスでは、そのデータ モデル、そのビジネス ロジック、およびそのデータ アクセス コードのクラスを含む 1 つの ASP.NET Core Web API プロジェクト内のすべての機能を実装します。 (別のコンテナーとして開発/テスト目的で)、SQL Server で実行されているデータベースに関連するデータを保存もある場合も、通常の SQL Server ホスト図 8-5 に示すようにします。

![](./media/image5.png)

**図 8-5**です。 単純なデータ ドリブン/CRUD マイクロ サービスの設計

この種のサービスを開発するときに必要なだけ[ASP.NET Core](https://docs.microsoft.com/aspnet/core/)などのデータ アクセス API または ORM および[Entity Framework Core](https://docs.microsoft.com/ef/core/index)です。 生成することも[Swagger](http://swagger.io/)メタデータを使用して自動的に[Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)次のセクションで説明したように、サービスの提供の説明を入力します。

すべての依存関係を持てないため、Docker コンテナー内の SQL Server の開発環境に適したようなデータベース サーバーを実行して、クラウドまたは内部設置型データベースをプロビジョニングすることがなく実行されていることに注意してください。 これは、機能は、テストの統合を実行している場合に非常に便利です。 ただし、実稼働環境では、データベース サーバーをコンテナーで実行されているはお勧めしません、通常、高可用性アプローチと取得できません。 Azure で実稼働環境では、Azure SQL DB、または高可用性と高スケーラビリティを提供できるその他のデータベース テクノロジを使用することをお勧めします。 たとえば、NoSQL のアプローチの可能性があります、DocumentDB を選択します。

最後に、Dockerfile と docker compose.yml メタデータ ファイルを編集するを構成できますが、このコンテナーのイメージの作成方法: どのような基本イメージを使用するし、内部および外部の名前と TCP ポート番号などの設定を設計はします。 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>ASP.NET Core を単純な CRUD マイクロ サービスを実装します。

.NET Core と Visual Studio を使用して、単純な CRUD マイクロ サービスを実装するには、開始する (で実行されている .NET Core Linux Docker ホスト上で実行できるように)、単純な ASP.NET Core Web API プロジェクトを作成することでとして図 8-6。

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**図 8-6**です。 Visual Studio での ASP.NET Core Web API プロジェクトの作成

プロジェクトを作成した後は、エンティティ フレームワーク API またはその他の API を使用して、他の Web API プロジェクトの場合ほど、MVC コント ローラーを実装できます。 EShopOnContainers.Catalog.API プロジェクトで確認できますをそのマイクロ サービスの主な依存関係は、だけ ASP.NET Core 自体、Entity Framework と Swashbuckle、図 8-7 に示すようにします。

![](./media/image8.PNG)

**図 8-7**です。 単純な Web API の CRUD マイクロ サービス内の依存関係

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Entity Framework のコアでの CRUD Web API サービスを実装します。

Entity Framework (EF) のコアは軽量で拡張性があると、クロスプラット フォームのバージョンの人気のある Entity Framework データ アクセス テクノロジです。 EF Core とは、.NET 開発者は .NET オブジェクトを使用してデータベースを使用するオブジェクト リレーショナル マッパー (ORM) です。

カタログ マイクロ サービスは、そのデータベースが Linux Docker イメージ用の SQL Server のコンテナーで実行されて、EF と SQL Server プロバイダーを使用します。 ただし、データベースは、Windows、オンプレミスまたは Azure SQL DB など、任意の SQL Server に展開できます。 変更する必要は唯一の機能は、ASP.NET Web API マイクロ サービス内の接続文字列です。

#### <a name="add-entity-framework-core-to-your-dependencies"></a>依存関係に Entity Framework のコアを追加します。

使用して、この場合は、SQL Server から、Visual Studio IDE 内、または NuGet コンソールを使用するデータベース プロバイダーの NuGet パッケージをインストールすることができます。 次のコマンドを使用します。

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a>データ モデル

EF コアでデータ アクセスは、モデルを使用して実行されます。 モデルは、エンティティ クラスと派生コンテキストを表すクエリを実行し、データを保存することができます、データベースとのセッションの構成されます。 既存のデータベースからモデルを生成、手動でのデータベースに一致するモデルのコードまたは EF の移行を使用して、モデルからデータベースを作成 (および時間の経過と共に変更では、モデルの進化) をします。 カタログ マイクロ サービスを最後のアプローチを使用します。 次のコード例では、単純な Plain Old CLR Object CatalogItem エンティティ クラスの例を見ることができます ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) エンティティ クラスです。

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

データベースとのセッションを表す DbContext 必要もあります。 カタログ マイクロ サービスの CatalogContext クラスの派生元 DbContext 基底クラスでは、次の例で示すようにします。

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }

    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

DbContext 実装でコードを追加ことができます。 たとえば、サンプル アプリケーションでお OnModelCreating メソッド クラスにある CatalogContext データベースにアクセスしようとすると、最初にサンプル データを自動的に設定します。 このメソッドは、デモのデータに役立ちます。 その他多数のオブジェクトまたはデータベース エンティティのマッピングをカスタマイズする OnModelCreating メソッドを使用することもできます。 [EF 機能拡張ポイント](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)です。

OnModelCreating に関する詳細をさらに確認できます、[の Entity Framework のコア インフラストラクチャの永続性レイヤーの実装](#implementing_infrastructure_persistence)このドキュメントで後述する「します。

##### <a name="querying-data-from-web-api-controllers"></a>Web API コント ローラーからデータを照会します。

エンティティ クラスのインスタンスは、次の例で示すように通常言語統合クエリ (LINQ) を使用して、データベースから取得されます。

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10,
    [FromQuery]int pageIndex = 0)
    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();
        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();
        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);
        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);
        return Ok(model);
    } 

    //...
}
```

##### <a name="saving-data"></a>データの保存

データが作成、削除、およびエンティティ クラスのインスタンスを使用してデータベースで変更されました。 次のようハード コーディングされた (モック データ、ここでは)、Web API コント ローラーにコードを追加できます。

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>ASP.NET Core および Web API コント ローラーで依存関係の挿入

ASP.NET Core では、すぐ依存関係の挿入 (DI) を使用できます。 場合は、ASP.NET Core インフラストラクチャに優先 IoC コンテナーをプラグインすることができますが、サード パーティ製の制御の反転 (IoC) コンテナーを設定する必要はありません。 この場合、必須の EF DBContext またはコント ローラーのコンス トラクターの追加のリポジトリを挿入できます直接ことを意味します。 CatalogController クラスの上記の例では、CatalogContext 型のオブジェクトとその他のオブジェクト CatalogController コンス トラクターを提供します。

Web API プロジェクトを設定する構成の重要なは、DbContext クラスをサービスの IoC コンテナーに登録します。 通常これを行うスタートアップ クラスでサービスを呼び出すことによってです。次の例のように、ConfigureServices メソッドの内部 AddDbContext メソッド:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
               typeof(Startup).
               GetTypeInfo().
               Assembly.
               GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a>その他の技術情報

-   **データを照会する**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **データの保存**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Docker コンテナーで使用される DB 接続文字列と環境変数

次の例のように、settings.json ファイルに ConnectionString プロパティを追加および ASP.NET Core 設定を使用することができます。

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

Settings.json ファイルには、ConnectionString プロパティや、他のプロパティの既定値を持つことができます。 ただし、これらのプロパティは、docker compose.override.yml ファイルで指定した環境変数の値によってオーバーライドされます。

Docker compose.yml または docker compose.override.yml ファイルから初期化できますそれらの環境変数のため、その Docker、それらの設定が OS に環境変数として、次の docker compose.override.yml ファイル (接続のようにこの例では文字列とその他の行を折り返すが独自のファイルに折り返すことができませんが)。

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

Docker compose.yml ファイル、ソリューション レベルでのみ構成ファイル、プロジェクトまたはマイクロ サービス レベルより柔軟なはないものより安全な。 検討ファイル、バイナリ ファイルと、Dockerfile を含む各マイクロ サービスの構成ファイルのみ、Docker イメージあたりマイクロ サービスをビルドするには、docker compose.yml が含まれていないこと。 Docker compose.yml ファイルが、アプリケーションと共に配置されません。展開時にのみ使用されます。 そのため、(しなくても、値を暗号化)、それらの docker compose.yml ファイル環境変数の値を配置することは、コード内に配置されている通常の .NET 構成ファイルでそれらの値を配置するより安全です。

構成を使用して、コードからその値を取得する最後に、\["ConnectionString"\]ConfigureServices メソッド前のコード例に示すように、します。

ただし、実稼働環境では、エクスプ ローラーの接続文字列などの機密情報を格納する方法の他の方法をする可能性があります。 通常をで管理される、選択した orchestrator で実行できるように[シークレットの管理の Docker Swarm](https://docs.docker.com/engine/swarm/secrets/)です。

### <a name="implementing-versioning-in-aspnet-web-apis"></a>ASP.NET Web Api のバージョン管理を実装します。

ビジネス要件を変更すると、リソースの新しいコレクションを追加することがあります、リソース間のリレーションシップを変更する可能性があります、およびリソース内のデータの構造を修正できる可能性があります。 新しい要件を処理する Web API の更新はプロセスは比較的簡単ですが、このような変更がある Web API を使用するクライアント アプリケーションに影響を考慮する必要があります。 開発者向けの設計と Web API を実装するには、その API を完全に制御が、開発者は同程度のサードパーティの組織でのリモート オペレーティングによって構築されているクライアント アプリケーションに制御がありません。

バージョン管理は、機能と表示されているリソースを示すために Web API を使用します。 クライアント アプリケーションは、特定のバージョンの機能やリソースへの要求を送信し、できます。 バージョン管理を実装する方法はいくつかあります。

-   URI のバージョン管理

-   クエリ文字列のバージョン管理

-   ヘッダーのバージョン管理

クエリ文字列と URI のバージョン管理は、実装する最も簡単なのです。 ヘッダーのバージョン管理は、適切なアプローチです。 ただし、ヘッダーのバージョン管理と明示的なされず、URI のバージョン管理するように単純です。 URL のバージョン管理は最も単純で最も明示的なので、eShopOnContainers サンプル アプリケーションは、URI のバージョン管理を使用します。

EShopOnContainers サンプル アプリケーションと同様に、URI のバージョン管理に Web API を変更したり、リソースのスキーマを変更する追加するたびにバージョン番号を各リソースの URI。 既存の Uri は、前述のように、要求されたバージョンに対応するスキーマに準拠しているリソースを返す動作を続行する必要があります。

これにより、バージョンを URI に明示的な Web API のルート属性を使用して、バージョンを設定することができます次のコード例に示すように、(このケースで v1)。

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

このバージョン管理メカニズムは単純な適切なエンドポイントに要求をルーティング サーバーによって異なります。 ただしより高度なバージョン管理と REST を使用するときに最適な方法は、する必要があります hypermedia を使用して実装した[HATEOAS (エンジンのアプリケーションの状態とハイパー テキスト)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources)です。

### <a name="additional-resources"></a>その他の技術情報

-   **Scott Hanselman です。ASP.NET Core RESTful Web API のバージョン管理が簡単に作成**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **RESTful web API のバージョン管理**

    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **者を務める Roy Fielding です。バージョン管理、Hypermedia、および REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>ASP.NET Core Web API から Swagger 説明メタデータを生成します。 

[Swagger](http://swagger.io/)一般的に使用されるオープン ソース フレームワークは、設計、構築、ドキュメント、際に役立つツールの大規模なエコシステムによってサポートされ、RESTful Api を使用します。 これにより、Api の説明のメタデータのドメインの標準が高まっています。 マイクロ サービス、データ ドリブン microservices または (次のセクションで説明されている) と、ドメインに基づく microservices を高度な複数の種類を問わず Swagger 説明のメタデータを含める必要があります。

Swagger の中心となるは、API の説明ファイル内のメタデータ、JSON または YAML が Swagger の仕様です。 仕様では、すべてのリソースと容易に開発、探索、および統合の両方を人間と machine readable 形式の処理の詳細を示す、API の RESTful コントラクトを作成します。

仕様では、OpenAPI 仕様 (OAS) の基になるし、RESTful インターフェイスを定義する方法を標準化するために、開いている、透過的なおよび共同作業コミュニティで開発されました。

仕様では、サービスの検出方法と、そのような機能の理解、構造体を定義します。 詳細については、web エディターおよび Spotify、Uber、余裕期間、および、Microsoft などの企業から Swagger 仕様の例を含むサイトを参照して、Swagger (<http://swagger.io>)。

### <a name="why-use-swagger"></a>Swagger を使用する理由

独自の Api は、次の Swagger メタデータを生成する主な理由です。

**自動的に使用し、独自の Api を統合するには、他の製品の機能**します。 数十個の製品と[商用ツール](http://swagger.io/commercial-tools/)と多[ライブラリ、およびフレームワーク](http://swagger.io/open-source-integrations/)Swagger をサポートします。 Microsoft では、高度な製品と、次のような Swagger ベースの Api が自動的に使用できるツールがあります。

-   [AutoRest](https://github.com/Azure/AutoRest)です。 Swagger を呼び出すための .NET クライアント クラスを自動的に生成することができます。 This

-   CLI からツールを使用してそのも統合 Visual Studio の GUI から使用を容易にします。

-   [Microsoft Flow](https://flow.microsoft.com/en-us/)です。 自動的に実行できます[を使用し、API の統合](https://flow.microsoft.com/en-us/blog/integrating-custom-api/)なしでプログラミングに必要なスキルを高レベルの Microsoft Flow ワークフローにします。

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/)です。 API を使用できる自動的に[PowerApps モバイル アプリ](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/)でビルドされた[PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/)、ありませんプログラミング技能を必要とします。

-   [Azure App Service の Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)です。 自動的に実行できます[を使用し、Azure App Service の Logic App に API を統合](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)、ありませんプログラミング技能を必要とします。

**API のドキュメントを自動的に生成する機能**します。 複雑なマイクロ サービス ベースのアプリケーションなど、大規模な RESTful Api を作成するときに、要求と応答のペイロードで使用されるさまざまなデータ モデルに多数のエンドポイントに対応する必要があります。 適切なドキュメントを持つ、純色の API explorer Swagger をポイントするとは、API を開発者が導入の成功のためのキーです。

Swagger のメタデータは Microsoft Flow、PowerApps、および Azure Logic Apps 際に使用する Api を使用して接続する方法を理解します。

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Swashbuckle NuGet パッケージと API の Swagger メタデータの生成を自動化する方法

手動で (JSON または YAML ファイル) での Swagger メタデータを生成すると、面倒な作業を指定できます。 ただしを使用して ASP.NET Web API サービスの API の検出を自動化することができます、 [Swashbuckle NuGet パッケージ](http://aka.ms/swashbuckledotnetcore)API の Swagger メタデータを動的に生成します。

Swashbuckle には、ASP.NET Web API プロジェクトの Swagger メタデータが自動的に生成されます。 ASP.NET Core Web API プロジェクトと従来の ASP.NET Web API と、Azure API アプリを Azure のモバイル アプリ、ASP.NET に基づく Azure Service Fabric microservices などその他のフレーバーをサポートします。 また、プレーンの Web API の参照をアプリケーションのように、コンテナー上に展開をサポートします。

Swashbuckle は API Explorer と Swagger 結合または[swagger ui](https://github.com/swagger-api/swagger-ui)豊富な検出およびドキュメントは、API のコンシューマーのエクスペリエンスを提供します。 Swagger メタデータ ジェネレーター エンジンに加えて Swashbuckle には、埋め込みのバージョンに自動的になるを Swashbuckle がインストールされる swagger ui のも含まれています。

これは、nice 探索 API を使用する開発者を支援するための UI と API を補完することを意味します。 これは自動的に生成されるため、API の構築に専念することができます、非常に少量のコードとメンテナンスが必要です。 API エクスプ ローラーの結果は、図 8-8 などを検索します。

![](./media/image9.png)

**図 8-8**です。 Swagger メタデータに基づいて Swashbuckle API Explorer — eShopOnContainers カタログ マイクロ サービス

API エクスプ ローラーは、最も重要な点は、ここではありません。 Swagger メタデータで自己記述できますを Web API を作成したら、API が多くのプラットフォームを対象とするクライアント プロキシ クラスのコード ジェネレーターを含む、Swagger ベースのツールからシームレスに使用できます。 たとえば、説明したように、 [AutoRest](https://github.com/Azure/AutoRest) .NET クライアント クラスが自動的に生成されます。 などの他のツールが、 [swagger codegen](https://github.com/swagger-api/swagger-codegen)も使用できるようにする API のクライアントのコード生成ライブラリ、サーバーのスタブ、およびドキュメントに自動的にします。

現在、Swashbuckle から成る 2 つの NuGet パッケージ: Swashbuckle.SwaggerGen と Swashbuckle.SwaggerUi です。 前者は、1 つ以上の Swagger ドキュメントから直接生成 API の実装および JSON エンドポイントとして公開する機能を提供します。 後者は、埋め込みのバージョンのアプリケーションによって処理および API を記述する Swagger ドキュメントを生成して電源できる swagger ui ツールを提供します。 ただし、Swashbuckle の最新バージョンでは、これら Swashbuckle.AspNetCore metapackage をラップします。

.NET Core の Web API プロジェクトに対して指定する必要を使用する[Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0)バージョン 1.0.0 またはそれ以降。

Web API プロジェクトでこれらの NuGet パッケージをインストールした後は、スタートアップ クラスで、次のコードのように、Swagger を構成する必要があります。

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
            });
        });
        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUi();
    }
}
```

これを完了すると、アプリケーションを起動し、上記のような Url を使用して次の Swagger JSON と UI のエンドポイントを参照することができます。

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

生成された UI Swashbuckle によって http:// ような URL の作成に紹介した&lt;、ルート url&gt;swagger/ui。 図 8-9 にも表示 API メソッドをテストする方法です。

![](./media/image10.png)

**図 8-9**です。 カタログ アイテム/API メソッドをテスト Swashbuckle UI

図 8-10 eShopOnContainers マイクロ サービスから生成された JSON の Swagger メタデータを示しています (これは、ツールの使用を下にある) を要求すると&lt;、ルート url&gt;/swagger/v1/swagger.json を使用して[Postman](https://www.getpostman.com/).

![](./media/image11.png)

**図 8-10**です。 Swagger JSON メタデータ

これは簡単です。 API をより多くの機能を追加する場合に、Swagger メタデータが拡張されますが自動的に生成されるためです。

### <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Web API のヘルプを使用してページ Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[前](マイクロ サービス-アプリケーション-design.md) [次へ] (マルチ-container-アプリケーション-docker-compose.md)

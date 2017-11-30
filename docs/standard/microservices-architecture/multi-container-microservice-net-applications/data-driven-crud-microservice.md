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
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="50072-104">単純なデータ ドリブン CRUD マイクロ サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="50072-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="50072-105">このセクションのアウトライン方法、単純なを作成するを実行するマイクロ サービスを作成、読み取り、更新、およびデータ ソースの削除 (CRUD) 操作です。</span><span class="sxs-lookup"><span data-stu-id="50072-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="50072-106">単純な CRUD マイクロ サービスの設計</span><span class="sxs-lookup"><span data-stu-id="50072-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="50072-107">設計の観点からは、この種類のコンテナー化マイクロ サービスは非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="50072-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="50072-108">解決する問題は単純な場合、おそらくかおそらく実装では、概念実証のみ。</span><span class="sxs-lookup"><span data-stu-id="50072-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="50072-109">**図 8-4**です。</span><span class="sxs-lookup"><span data-stu-id="50072-109">**Figure 8-4**.</span></span> <span data-ttu-id="50072-110">単純な CRUD microservices の内部設計</span><span class="sxs-lookup"><span data-stu-id="50072-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="50072-111">この種の単純なデータ ドライブのサービスの例は、eShopOnContainers サンプル アプリケーションからカタログ マイクロ サービスです。</span><span class="sxs-lookup"><span data-stu-id="50072-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="50072-112">この種類のサービスでは、そのデータ モデル、そのビジネス ロジック、およびそのデータ アクセス コードのクラスを含む 1 つの ASP.NET Core Web API プロジェクト内のすべての機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="50072-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="50072-113">(別のコンテナーとして開発/テスト目的で)、SQL Server で実行されているデータベースに関連するデータを保存もある場合も、通常の SQL Server ホスト図 8-5 に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="50072-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="50072-114">**図 8-5**です。</span><span class="sxs-lookup"><span data-stu-id="50072-114">**Figure 8-5**.</span></span> <span data-ttu-id="50072-115">単純なデータ ドリブン/CRUD マイクロ サービスの設計</span><span class="sxs-lookup"><span data-stu-id="50072-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="50072-116">この種のサービスを開発するときに必要なだけ[ASP.NET Core](https://docs.microsoft.com/aspnet/core/)などのデータ アクセス API または ORM および[Entity Framework Core](https://docs.microsoft.com/ef/core/index)です。</span><span class="sxs-lookup"><span data-stu-id="50072-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="50072-117">生成することも[Swagger](http://swagger.io/)メタデータを使用して自動的に[Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)次のセクションで説明したように、サービスの提供の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="50072-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="50072-118">すべての依存関係を持てないため、Docker コンテナー内の SQL Server の開発環境に適したようなデータベース サーバーを実行して、クラウドまたは内部設置型データベースをプロビジョニングすることがなく実行されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="50072-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="50072-119">これは、機能は、テストの統合を実行している場合に非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="50072-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="50072-120">ただし、実稼働環境では、データベース サーバーをコンテナーで実行されているはお勧めしません、通常、高可用性アプローチと取得できません。</span><span class="sxs-lookup"><span data-stu-id="50072-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="50072-121">Azure で実稼働環境では、Azure SQL DB、または高可用性と高スケーラビリティを提供できるその他のデータベース テクノロジを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="50072-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="50072-122">たとえば、NoSQL のアプローチの可能性があります、DocumentDB を選択します。</span><span class="sxs-lookup"><span data-stu-id="50072-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="50072-123">最後に、Dockerfile と docker compose.yml メタデータ ファイルを編集するを構成できますが、このコンテナーのイメージの作成方法: どのような基本イメージを使用するし、内部および外部の名前と TCP ポート番号などの設定を設計はします。</span><span class="sxs-lookup"><span data-stu-id="50072-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="50072-124">ASP.NET Core を単純な CRUD マイクロ サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="50072-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="50072-125">.NET Core と Visual Studio を使用して、単純な CRUD マイクロ サービスを実装するには、開始する (で実行されている .NET Core Linux Docker ホスト上で実行できるように)、単純な ASP.NET Core Web API プロジェクトを作成することでとして図 8-6。</span><span class="sxs-lookup"><span data-stu-id="50072-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="50072-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="50072-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="50072-127">**図 8-6**です。</span><span class="sxs-lookup"><span data-stu-id="50072-127">**Figure 8-6**.</span></span> <span data-ttu-id="50072-128">Visual Studio での ASP.NET Core Web API プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="50072-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="50072-129">プロジェクトを作成した後は、エンティティ フレームワーク API またはその他の API を使用して、他の Web API プロジェクトの場合ほど、MVC コント ローラーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="50072-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="50072-130">EShopOnContainers.Catalog.API プロジェクトで確認できますをそのマイクロ サービスの主な依存関係は、だけ ASP.NET Core 自体、Entity Framework と Swashbuckle、図 8-7 に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="50072-130">In the eShopOnContainers.Catalog.API project, you can see that the main dependencies for that microservice are just ASP.NET Core itself, Entity Framework, and Swashbuckle, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="50072-131">**図 8-7**です。</span><span class="sxs-lookup"><span data-stu-id="50072-131">**Figure 8-7**.</span></span> <span data-ttu-id="50072-132">単純な Web API の CRUD マイクロ サービス内の依存関係</span><span class="sxs-lookup"><span data-stu-id="50072-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="50072-133">Entity Framework のコアでの CRUD Web API サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="50072-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="50072-134">Entity Framework (EF) のコアは軽量で拡張性があると、クロスプラット フォームのバージョンの人気のある Entity Framework データ アクセス テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="50072-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="50072-135">EF Core とは、.NET 開発者は .NET オブジェクトを使用してデータベースを使用するオブジェクト リレーショナル マッパー (ORM) です。</span><span class="sxs-lookup"><span data-stu-id="50072-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="50072-136">カタログ マイクロ サービスは、そのデータベースが Linux Docker イメージ用の SQL Server のコンテナーで実行されて、EF と SQL Server プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="50072-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="50072-137">ただし、データベースは、Windows、オンプレミスまたは Azure SQL DB など、任意の SQL Server に展開できます。</span><span class="sxs-lookup"><span data-stu-id="50072-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="50072-138">変更する必要は唯一の機能は、ASP.NET Web API マイクロ サービス内の接続文字列です。</span><span class="sxs-lookup"><span data-stu-id="50072-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="add-entity-framework-core-to-your-dependencies"></a><span data-ttu-id="50072-139">依存関係に Entity Framework のコアを追加します。</span><span class="sxs-lookup"><span data-stu-id="50072-139">Add Entity Framework Core to your dependencies</span></span>

<span data-ttu-id="50072-140">使用して、この場合は、SQL Server から、Visual Studio IDE 内、または NuGet コンソールを使用するデータベース プロバイダーの NuGet パッケージをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="50072-140">You can install the NuGet package for the database provider you want to use, in this case SQL Server, from within the Visual Studio IDE or with the NuGet console.</span></span> <span data-ttu-id="50072-141">次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="50072-141">Use the following command:</span></span>

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a><span data-ttu-id="50072-142">データ モデル</span><span class="sxs-lookup"><span data-stu-id="50072-142">The data model</span></span>

<span data-ttu-id="50072-143">EF コアでデータ アクセスは、モデルを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="50072-143">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="50072-144">モデルは、エンティティ クラスと派生コンテキストを表すクエリを実行し、データを保存することができます、データベースとのセッションの構成されます。</span><span class="sxs-lookup"><span data-stu-id="50072-144">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="50072-145">既存のデータベースからモデルを生成、手動でのデータベースに一致するモデルのコードまたは EF の移行を使用して、モデルからデータベースを作成 (および時間の経過と共に変更では、モデルの進化) をします。</span><span class="sxs-lookup"><span data-stu-id="50072-145">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="50072-146">カタログ マイクロ サービスを最後のアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="50072-146">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="50072-147">次のコード例では、単純な Plain Old CLR Object CatalogItem エンティティ クラスの例を見ることができます ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) エンティティ クラスです。</span><span class="sxs-lookup"><span data-stu-id="50072-147">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="50072-148">データベースとのセッションを表す DbContext 必要もあります。</span><span class="sxs-lookup"><span data-stu-id="50072-148">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="50072-149">カタログ マイクロ サービスの CatalogContext クラスの派生元 DbContext 基底クラスでは、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="50072-149">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="50072-150">DbContext 実装でコードを追加ことができます。</span><span class="sxs-lookup"><span data-stu-id="50072-150">You can have additional code in the DbContext implementation.</span></span> <span data-ttu-id="50072-151">たとえば、サンプル アプリケーションでお OnModelCreating メソッド クラスにある CatalogContext データベースにアクセスしようとすると、最初にサンプル データを自動的に設定します。</span><span class="sxs-lookup"><span data-stu-id="50072-151">For example, in the sample application, we have an OnModelCreating method in the CatalogContext class that automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="50072-152">このメソッドは、デモのデータに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="50072-152">This method is useful for demo data.</span></span> <span data-ttu-id="50072-153">その他多数のオブジェクトまたはデータベース エンティティのマッピングをカスタマイズする OnModelCreating メソッドを使用することもできます。 [EF 機能拡張ポイント](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)です。</span><span class="sxs-lookup"><span data-stu-id="50072-153">You can also use the OnModelCreating method to customize object/database entity mappings with many other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

<span data-ttu-id="50072-154">OnModelCreating に関する詳細をさらに確認できます、[の Entity Framework のコア インフラストラクチャの永続性レイヤーの実装](#implementing_infrastructure_persistence)このドキュメントで後述する「します。</span><span class="sxs-lookup"><span data-stu-id="50072-154">You can see further details about OnModelCreating in the [Implementing the infrastructure-persistence layer with Entity Framework Core](#implementing_infrastructure_persistence) section later in this book.</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="50072-155">Web API コント ローラーからデータを照会します。</span><span class="sxs-lookup"><span data-stu-id="50072-155">Querying data from Web API controllers</span></span>

<span data-ttu-id="50072-156">エンティティ クラスのインスタンスは、次の例で示すように通常言語統合クエリ (LINQ) を使用して、データベースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="50072-156">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="50072-157">データの保存</span><span class="sxs-lookup"><span data-stu-id="50072-157">Saving data</span></span>

<span data-ttu-id="50072-158">データが作成、削除、およびエンティティ クラスのインスタンスを使用してデータベースで変更されました。</span><span class="sxs-lookup"><span data-stu-id="50072-158">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="50072-159">次のようハード コーディングされた (モック データ、ここでは)、Web API コント ローラーにコードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="50072-159">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="50072-160">ASP.NET Core および Web API コント ローラーで依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="50072-160">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="50072-161">ASP.NET Core では、すぐ依存関係の挿入 (DI) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="50072-161">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="50072-162">場合は、ASP.NET Core インフラストラクチャに優先 IoC コンテナーをプラグインすることができますが、サード パーティ製の制御の反転 (IoC) コンテナーを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="50072-162">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="50072-163">この場合、必須の EF DBContext またはコント ローラーのコンス トラクターの追加のリポジトリを挿入できます直接ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="50072-163">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="50072-164">CatalogController クラスの上記の例では、CatalogContext 型のオブジェクトとその他のオブジェクト CatalogController コンス トラクターを提供します。</span><span class="sxs-lookup"><span data-stu-id="50072-164">In the example above of the CatalogController class, we are injecting an object of CatalogContext type plus other objects through the CatalogController constructor.</span></span>

<span data-ttu-id="50072-165">Web API プロジェクトを設定する構成の重要なは、DbContext クラスをサービスの IoC コンテナーに登録します。</span><span class="sxs-lookup"><span data-stu-id="50072-165">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="50072-166">通常これを行うスタートアップ クラスでサービスを呼び出すことによってです。次の例のように、ConfigureServices メソッドの内部 AddDbContext メソッド:</span><span class="sxs-lookup"><span data-stu-id="50072-166">You typically do so in the Startup class by calling the services.AddDbContext method inside the ConfigureServices method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="50072-167">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="50072-167">Additional resources</span></span>

-   <span data-ttu-id="50072-168">**データを照会する**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="50072-168">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="50072-169">**データの保存**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="50072-169">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="50072-170">Docker コンテナーで使用される DB 接続文字列と環境変数</span><span class="sxs-lookup"><span data-stu-id="50072-170">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="50072-171">次の例のように、settings.json ファイルに ConnectionString プロパティを追加および ASP.NET Core 設定を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="50072-171">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="50072-172">Settings.json ファイルには、ConnectionString プロパティや、他のプロパティの既定値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="50072-172">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="50072-173">ただし、これらのプロパティは、docker compose.override.yml ファイルで指定した環境変数の値によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="50072-173">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file.</span></span>

<span data-ttu-id="50072-174">Docker compose.yml または docker compose.override.yml ファイルから初期化できますそれらの環境変数のため、その Docker、それらの設定が OS に環境変数として、次の docker compose.override.yml ファイル (接続のようにこの例では文字列とその他の行を折り返すが独自のファイルに折り返すことができませんが)。</span><span class="sxs-lookup"><span data-stu-id="50072-174">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="50072-175">Docker compose.yml ファイル、ソリューション レベルでのみ構成ファイル、プロジェクトまたはマイクロ サービス レベルより柔軟なはないものより安全な。</span><span class="sxs-lookup"><span data-stu-id="50072-175">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure.</span></span> <span data-ttu-id="50072-176">検討ファイル、バイナリ ファイルと、Dockerfile を含む各マイクロ サービスの構成ファイルのみ、Docker イメージあたりマイクロ サービスをビルドするには、docker compose.yml が含まれていないこと。</span><span class="sxs-lookup"><span data-stu-id="50072-176">Consider that the Docker images that you build per microservice do not contain the docker-compose.yml files, only binary files and configuration files for each microservice, including the Dockerfile.</span></span> <span data-ttu-id="50072-177">Docker compose.yml ファイルが、アプリケーションと共に配置されません。展開時にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="50072-177">But the docker-compose.yml file is not deployed along with your application; it is used only at deployment time.</span></span> <span data-ttu-id="50072-178">そのため、(しなくても、値を暗号化)、それらの docker compose.yml ファイル環境変数の値を配置することは、コード内に配置されている通常の .NET 構成ファイルでそれらの値を配置するより安全です。</span><span class="sxs-lookup"><span data-stu-id="50072-178">Therefore, placing environment variables values in those docker-compose.yml files (even without encrypting the values) is more secure than placing those values in regular .NET configuration files that are deployed with your code.</span></span>

<span data-ttu-id="50072-179">構成を使用して、コードからその値を取得する最後に、\["ConnectionString"\]ConfigureServices メソッド前のコード例に示すように、します。</span><span class="sxs-lookup"><span data-stu-id="50072-179">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="50072-180">ただし、実稼働環境では、エクスプ ローラーの接続文字列などの機密情報を格納する方法の他の方法をする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50072-180">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="50072-181">通常をで管理される、選択した orchestrator で実行できるように[シークレットの管理の Docker Swarm](https://docs.docker.com/engine/swarm/secrets/)です。</span><span class="sxs-lookup"><span data-stu-id="50072-181">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="50072-182">ASP.NET Web Api のバージョン管理を実装します。</span><span class="sxs-lookup"><span data-stu-id="50072-182">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="50072-183">ビジネス要件を変更すると、リソースの新しいコレクションを追加することがあります、リソース間のリレーションシップを変更する可能性があります、およびリソース内のデータの構造を修正できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50072-183">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="50072-184">新しい要件を処理する Web API の更新はプロセスは比較的簡単ですが、このような変更がある Web API を使用するクライアント アプリケーションに影響を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50072-184">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="50072-185">開発者向けの設計と Web API を実装するには、その API を完全に制御が、開発者は同程度のサードパーティの組織でのリモート オペレーティングによって構築されているクライアント アプリケーションに制御がありません。</span><span class="sxs-lookup"><span data-stu-id="50072-185">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="50072-186">バージョン管理は、機能と表示されているリソースを示すために Web API を使用します。</span><span class="sxs-lookup"><span data-stu-id="50072-186">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="50072-187">クライアント アプリケーションは、特定のバージョンの機能やリソースへの要求を送信し、できます。</span><span class="sxs-lookup"><span data-stu-id="50072-187">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="50072-188">バージョン管理を実装する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="50072-188">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="50072-189">URI のバージョン管理</span><span class="sxs-lookup"><span data-stu-id="50072-189">URI versioning</span></span>

-   <span data-ttu-id="50072-190">クエリ文字列のバージョン管理</span><span class="sxs-lookup"><span data-stu-id="50072-190">Query string versioning</span></span>

-   <span data-ttu-id="50072-191">ヘッダーのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="50072-191">Header versioning</span></span>

<span data-ttu-id="50072-192">クエリ文字列と URI のバージョン管理は、実装する最も簡単なのです。</span><span class="sxs-lookup"><span data-stu-id="50072-192">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="50072-193">ヘッダーのバージョン管理は、適切なアプローチです。</span><span class="sxs-lookup"><span data-stu-id="50072-193">Header versioning is a good approach.</span></span> <span data-ttu-id="50072-194">ただし、ヘッダーのバージョン管理と明示的なされず、URI のバージョン管理するように単純です。</span><span class="sxs-lookup"><span data-stu-id="50072-194">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="50072-195">URL のバージョン管理は最も単純で最も明示的なので、eShopOnContainers サンプル アプリケーションは、URI のバージョン管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="50072-195">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="50072-196">EShopOnContainers サンプル アプリケーションと同様に、URI のバージョン管理に Web API を変更したり、リソースのスキーマを変更する追加するたびにバージョン番号を各リソースの URI。</span><span class="sxs-lookup"><span data-stu-id="50072-196">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="50072-197">既存の Uri は、前述のように、要求されたバージョンに対応するスキーマに準拠しているリソースを返す動作を続行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50072-197">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="50072-198">これにより、バージョンを URI に明示的な Web API のルート属性を使用して、バージョンを設定することができます次のコード例に示すように、(このケースで v1)。</span><span class="sxs-lookup"><span data-stu-id="50072-198">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="50072-199">このバージョン管理メカニズムは単純な適切なエンドポイントに要求をルーティング サーバーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="50072-199">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="50072-200">ただしより高度なバージョン管理と REST を使用するときに最適な方法は、する必要があります hypermedia を使用して実装した[HATEOAS (エンジンのアプリケーションの状態とハイパー テキスト)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources)です。</span><span class="sxs-lookup"><span data-stu-id="50072-200">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="50072-201">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="50072-201">Additional resources</span></span>

-   <span data-ttu-id="50072-202">**Scott Hanselman です。ASP.NET Core RESTful Web API のバージョン管理が簡単に作成**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="50072-202">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="50072-203">**RESTful web API のバージョン管理**</span><span class="sxs-lookup"><span data-stu-id="50072-203">**Versioning a RESTful web API**</span></span>

    [<span data-ttu-id="50072-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span><span class="sxs-lookup"><span data-stu-id="50072-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   <span data-ttu-id="50072-205">**者を務める Roy Fielding です。バージョン管理、Hypermedia、および REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="50072-205">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="50072-206">ASP.NET Core Web API から Swagger 説明メタデータを生成します。</span><span class="sxs-lookup"><span data-stu-id="50072-206">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="50072-207">[Swagger](http://swagger.io/)一般的に使用されるオープン ソース フレームワークは、設計、構築、ドキュメント、際に役立つツールの大規模なエコシステムによってサポートされ、RESTful Api を使用します。</span><span class="sxs-lookup"><span data-stu-id="50072-207">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="50072-208">これにより、Api の説明のメタデータのドメインの標準が高まっています。</span><span class="sxs-lookup"><span data-stu-id="50072-208">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="50072-209">マイクロ サービス、データ ドリブン microservices または (次のセクションで説明されている) と、ドメインに基づく microservices を高度な複数の種類を問わず Swagger 説明のメタデータを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="50072-209">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="50072-210">Swagger の中心となるは、API の説明ファイル内のメタデータ、JSON または YAML が Swagger の仕様です。</span><span class="sxs-lookup"><span data-stu-id="50072-210">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="50072-211">仕様では、すべてのリソースと容易に開発、探索、および統合の両方を人間と machine readable 形式の処理の詳細を示す、API の RESTful コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="50072-211">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="50072-212">仕様では、OpenAPI 仕様 (OAS) の基になるし、RESTful インターフェイスを定義する方法を標準化するために、開いている、透過的なおよび共同作業コミュニティで開発されました。</span><span class="sxs-lookup"><span data-stu-id="50072-212">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="50072-213">仕様では、サービスの検出方法と、そのような機能の理解、構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="50072-213">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="50072-214">詳細については、web エディターおよび Spotify、Uber、余裕期間、および、Microsoft などの企業から Swagger 仕様の例を含むサイトを参照して、Swagger (<http://swagger.io>)。</span><span class="sxs-lookup"><span data-stu-id="50072-214">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="50072-215">Swagger を使用する理由</span><span class="sxs-lookup"><span data-stu-id="50072-215">Why use Swagger?</span></span>

<span data-ttu-id="50072-216">独自の Api は、次の Swagger メタデータを生成する主な理由です。</span><span class="sxs-lookup"><span data-stu-id="50072-216">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="50072-217">**自動的に使用し、独自の Api を統合するには、他の製品の機能**します。</span><span class="sxs-lookup"><span data-stu-id="50072-217">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="50072-218">数十個の製品と[商用ツール](http://swagger.io/commercial-tools/)と多[ライブラリ、およびフレームワーク](http://swagger.io/open-source-integrations/)Swagger をサポートします。</span><span class="sxs-lookup"><span data-stu-id="50072-218">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="50072-219">Microsoft では、高度な製品と、次のような Swagger ベースの Api が自動的に使用できるツールがあります。</span><span class="sxs-lookup"><span data-stu-id="50072-219">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="50072-220">[AutoRest](https://github.com/Azure/AutoRest)です。</span><span class="sxs-lookup"><span data-stu-id="50072-220">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="50072-221">Swagger を呼び出すための .NET クライアント クラスを自動的に生成することができます。</span><span class="sxs-lookup"><span data-stu-id="50072-221">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="50072-222">This</span><span class="sxs-lookup"><span data-stu-id="50072-222">This</span></span>

-   <span data-ttu-id="50072-223">CLI からツールを使用してそのも統合 Visual Studio の GUI から使用を容易にします。</span><span class="sxs-lookup"><span data-stu-id="50072-223">tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="50072-224">[Microsoft Flow](https://flow.microsoft.com/en-us/)です。</span><span class="sxs-lookup"><span data-stu-id="50072-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="50072-225">自動的に実行できます[を使用し、API の統合](https://flow.microsoft.com/en-us/blog/integrating-custom-api/)なしでプログラミングに必要なスキルを高レベルの Microsoft Flow ワークフローにします。</span><span class="sxs-lookup"><span data-stu-id="50072-225">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="50072-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/)です。</span><span class="sxs-lookup"><span data-stu-id="50072-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="50072-227">API を使用できる自動的に[PowerApps モバイル アプリ](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/)でビルドされた[PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/)、ありませんプログラミング技能を必要とします。</span><span class="sxs-lookup"><span data-stu-id="50072-227">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="50072-228">[Azure App Service の Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)です。</span><span class="sxs-lookup"><span data-stu-id="50072-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="50072-229">自動的に実行できます[を使用し、Azure App Service の Logic App に API を統合](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)、ありませんプログラミング技能を必要とします。</span><span class="sxs-lookup"><span data-stu-id="50072-229">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="50072-230">**API のドキュメントを自動的に生成する機能**します。</span><span class="sxs-lookup"><span data-stu-id="50072-230">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="50072-231">複雑なマイクロ サービス ベースのアプリケーションなど、大規模な RESTful Api を作成するときに、要求と応答のペイロードで使用されるさまざまなデータ モデルに多数のエンドポイントに対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50072-231">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="50072-232">適切なドキュメントを持つ、純色の API explorer Swagger をポイントするとは、API を開発者が導入の成功のためのキーです。</span><span class="sxs-lookup"><span data-stu-id="50072-232">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="50072-233">Swagger のメタデータは Microsoft Flow、PowerApps、および Azure Logic Apps 際に使用する Api を使用して接続する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="50072-233">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="50072-234">Swashbuckle NuGet パッケージと API の Swagger メタデータの生成を自動化する方法</span><span class="sxs-lookup"><span data-stu-id="50072-234">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="50072-235">手動で (JSON または YAML ファイル) での Swagger メタデータを生成すると、面倒な作業を指定できます。</span><span class="sxs-lookup"><span data-stu-id="50072-235">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="50072-236">ただしを使用して ASP.NET Web API サービスの API の検出を自動化することができます、 [Swashbuckle NuGet パッケージ](http://aka.ms/swashbuckledotnetcore)API の Swagger メタデータを動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="50072-236">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="50072-237">Swashbuckle には、ASP.NET Web API プロジェクトの Swagger メタデータが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="50072-237">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="50072-238">ASP.NET Core Web API プロジェクトと従来の ASP.NET Web API と、Azure API アプリを Azure のモバイル アプリ、ASP.NET に基づく Azure Service Fabric microservices などその他のフレーバーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="50072-238">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="50072-239">また、プレーンの Web API の参照をアプリケーションのように、コンテナー上に展開をサポートします。</span><span class="sxs-lookup"><span data-stu-id="50072-239">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="50072-240">Swashbuckle は API Explorer と Swagger 結合または[swagger ui](https://github.com/swagger-api/swagger-ui)豊富な検出およびドキュメントは、API のコンシューマーのエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="50072-240">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="50072-241">Swagger メタデータ ジェネレーター エンジンに加えて Swashbuckle には、埋め込みのバージョンに自動的になるを Swashbuckle がインストールされる swagger ui のも含まれています。</span><span class="sxs-lookup"><span data-stu-id="50072-241">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="50072-242">これは、nice 探索 API を使用する開発者を支援するための UI と API を補完することを意味します。</span><span class="sxs-lookup"><span data-stu-id="50072-242">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="50072-243">これは自動的に生成されるため、API の構築に専念することができます、非常に少量のコードとメンテナンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="50072-243">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="50072-244">API エクスプ ローラーの結果は、図 8-8 などを検索します。</span><span class="sxs-lookup"><span data-stu-id="50072-244">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="50072-245">**図 8-8**です。</span><span class="sxs-lookup"><span data-stu-id="50072-245">**Figure 8-8**.</span></span> <span data-ttu-id="50072-246">Swagger メタデータに基づいて Swashbuckle API Explorer — eShopOnContainers カタログ マイクロ サービス</span><span class="sxs-lookup"><span data-stu-id="50072-246">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="50072-247">API エクスプ ローラーは、最も重要な点は、ここではありません。</span><span class="sxs-lookup"><span data-stu-id="50072-247">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="50072-248">Swagger メタデータで自己記述できますを Web API を作成したら、API が多くのプラットフォームを対象とするクライアント プロキシ クラスのコード ジェネレーターを含む、Swagger ベースのツールからシームレスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="50072-248">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="50072-249">たとえば、説明したように、 [AutoRest](https://github.com/Azure/AutoRest) .NET クライアント クラスが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="50072-249">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="50072-250">などの他のツールが、 [swagger codegen](https://github.com/swagger-api/swagger-codegen)も使用できるようにする API のクライアントのコード生成ライブラリ、サーバーのスタブ、およびドキュメントに自動的にします。</span><span class="sxs-lookup"><span data-stu-id="50072-250">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="50072-251">現在、Swashbuckle から成る 2 つの NuGet パッケージ: Swashbuckle.SwaggerGen と Swashbuckle.SwaggerUi です。</span><span class="sxs-lookup"><span data-stu-id="50072-251">Currently, Swashbuckle consists of two NuGet packages: Swashbuckle.SwaggerGen and Swashbuckle.SwaggerUi.</span></span> <span data-ttu-id="50072-252">前者は、1 つ以上の Swagger ドキュメントから直接生成 API の実装および JSON エンドポイントとして公開する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="50072-252">The former provides functionality to generate one or more Swagger documents directly from your API implementation and expose them as JSON endpoints.</span></span> <span data-ttu-id="50072-253">後者は、埋め込みのバージョンのアプリケーションによって処理および API を記述する Swagger ドキュメントを生成して電源できる swagger ui ツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="50072-253">The latter provides an embedded version of the swagger-ui tool that can be served by your application and powered by the generated Swagger documents to describe your API.</span></span> <span data-ttu-id="50072-254">ただし、Swashbuckle の最新バージョンでは、これら Swashbuckle.AspNetCore metapackage をラップします。</span><span class="sxs-lookup"><span data-stu-id="50072-254">However, the latest versions of Swashbuckle wrap these with the Swashbuckle.AspNetCore metapackage.</span></span>

<span data-ttu-id="50072-255">.NET Core の Web API プロジェクトに対して指定する必要を使用する[Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0)バージョン 1.0.0 またはそれ以降。</span><span class="sxs-lookup"><span data-stu-id="50072-255">Note that for .NET Core Web API projects, you need to use [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 or later.</span></span>

<span data-ttu-id="50072-256">Web API プロジェクトでこれらの NuGet パッケージをインストールした後は、スタートアップ クラスで、次のコードのように、Swagger を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50072-256">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

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

<span data-ttu-id="50072-257">これを完了すると、アプリケーションを起動し、上記のような Url を使用して次の Swagger JSON と UI のエンドポイントを参照することができます。</span><span class="sxs-lookup"><span data-stu-id="50072-257">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

<span data-ttu-id="50072-258">生成された UI Swashbuckle によって http:// ような URL の作成に紹介した&lt;、ルート url&gt;swagger/ui。</span><span class="sxs-lookup"><span data-stu-id="50072-258">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="50072-259">図 8-9 にも表示 API メソッドをテストする方法です。</span><span class="sxs-lookup"><span data-stu-id="50072-259">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="50072-260">**図 8-9**です。</span><span class="sxs-lookup"><span data-stu-id="50072-260">**Figure 8-9**.</span></span> <span data-ttu-id="50072-261">カタログ アイテム/API メソッドをテスト Swashbuckle UI</span><span class="sxs-lookup"><span data-stu-id="50072-261">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="50072-262">図 8-10 eShopOnContainers マイクロ サービスから生成された JSON の Swagger メタデータを示しています (これは、ツールの使用を下にある) を要求すると&lt;、ルート url&gt;/swagger/v1/swagger.json を使用して[Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="50072-262">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="50072-263">**図 8-10**です。</span><span class="sxs-lookup"><span data-stu-id="50072-263">**Figure 8-10**.</span></span> <span data-ttu-id="50072-264">Swagger JSON メタデータ</span><span class="sxs-lookup"><span data-stu-id="50072-264">Swagger JSON metadata</span></span>

<span data-ttu-id="50072-265">これは簡単です。</span><span class="sxs-lookup"><span data-stu-id="50072-265">It is that simple.</span></span> <span data-ttu-id="50072-266">API をより多くの機能を追加する場合に、Swagger メタデータが拡張されますが自動的に生成されるためです。</span><span class="sxs-lookup"><span data-stu-id="50072-266">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="50072-267">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="50072-267">Additional resources</span></span>

-   <span data-ttu-id="50072-268">**ASP.NET Web API のヘルプを使用してページ Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="50072-268">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="50072-269">[前](マイクロ サービス-アプリケーション-design.md) [次へ] (マルチ-container-アプリケーション-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="50072-269">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>

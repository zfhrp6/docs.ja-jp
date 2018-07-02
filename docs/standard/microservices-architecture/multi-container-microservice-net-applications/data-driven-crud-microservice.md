---
title: 単純なデータ ドリブン CRUD マイクロサービスの作成
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 単純なデータ ドリブン CRUD マイクロサービスの作成
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: d99480c1b703bc46228e25f6acd7e7fbbcae6228
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106448"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="538e1-103">単純なデータ ドリブン CRUD マイクロサービスの作成</span><span class="sxs-lookup"><span data-stu-id="538e1-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="538e1-104">このセクションでは、データ ソースに対して作成、読み取り、更新、削除 (CRUD) 操作を実行する単純なマイクロサービスの作成方法について概説します。</span><span class="sxs-lookup"><span data-stu-id="538e1-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="538e1-105">単純な CRUD マイクロサービスの設計</span><span class="sxs-lookup"><span data-stu-id="538e1-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="538e1-106">設計の観点からは、この種類のコンテナー化されたマイクロサービスはとても単純です。</span><span class="sxs-lookup"><span data-stu-id="538e1-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="538e1-107">おそらく、解決する問題は単純であるか、実装は概念実証のみです。</span><span class="sxs-lookup"><span data-stu-id="538e1-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="538e1-108">**図 8-4**</span><span class="sxs-lookup"><span data-stu-id="538e1-108">**Figure 8-4**.</span></span> <span data-ttu-id="538e1-109">単純な CRUD マイクロサービスの内部設計</span><span class="sxs-lookup"><span data-stu-id="538e1-109">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="538e1-110">この種の単純なデータ ドリブン サービスの例として、eShopOnContainers サンプル アプリケーションのカタログ マイクロサービスがあります。</span><span class="sxs-lookup"><span data-stu-id="538e1-110">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="538e1-111">この種類のサービスでは、そのデータ モデル、ビジネス ロジック、データ アクセス コードのクラスを含む 1 つの ASP.NET Core Web API プロジェクト内のすべての機能が実装されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-111">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="538e1-112">また、関連データは (開発/テストが目的の別のコンテナーとして) SQL Server で実行されているデータベース内に格納されますが、図 8-5 に示すように、通常の SQL Server ホストにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="538e1-112">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="538e1-113">**図 8-5**</span><span class="sxs-lookup"><span data-stu-id="538e1-113">**Figure 8-5**.</span></span> <span data-ttu-id="538e1-114">単純なデータ ドリブン/CRUD マイクロサービスの設計</span><span class="sxs-lookup"><span data-stu-id="538e1-114">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="538e1-115">この種のサービスを開発するときに必要なのは、[ASP.NET Core](https://docs.microsoft.com/aspnet/core/) と、データ アクセス API または [Entity Framework Core](https://docs.microsoft.com/ef/core/index) のような ORM だけです。</span><span class="sxs-lookup"><span data-stu-id="538e1-115">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="538e1-116">次のセクションで説明するように、[Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) を通じて [Swagger](https://swagger.io/) メタデータを自動的に生成して、サービスが提供する内容の説明を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="538e1-116">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="538e1-117">クラウドまたはオンプレミスでデータベースをプロビジョニングしなくてもすべての依存関係を稼働させることができるので、Docker コンテナー内の SQL Server のようなデータベース サーバーの実行は開発環境に適しています。</span><span class="sxs-lookup"><span data-stu-id="538e1-117">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="538e1-118">これは、統合テストの実行時にとても便利です。</span><span class="sxs-lookup"><span data-stu-id="538e1-118">This is very convenient when running integration tests.</span></span> <span data-ttu-id="538e1-119">ただし運用環境では、コンテナーでデータベース サーバーを実行すると、通常は高可用性が実現されないため、このアプローチはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="538e1-119">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="538e1-120">Azure の運用環境では、Azure SQL DB、または高可用性と高スケーラビリティを提供できるその他のデータベース テクノロジを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="538e1-120">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="538e1-121">たとえば、NoSQL アプローチでは、DocumentDB を選択できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-121">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="538e1-122">最後に、Dockerfile と docker-compose.yml メタデータ ファイルを編集して、このコンテナーのイメージの作成方法 (使用される基本イメージに加えて、内部および外部の名前と TCP ポートなどの設計設定) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-122">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="538e1-123">ASP.NET Core での単純な CRUD マイクロサービスの実装</span><span class="sxs-lookup"><span data-stu-id="538e1-123">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="538e1-124">.NET Core と Visual Studio を使用して単純な CRUD マイクロサービスを実装するには、図 8-6 に示すように、まず単純な ASP.NET Core Web API プロジェクトを作成します (.NET Core で稼働するため Linux Docker ホスト上で実行できます)。</span><span class="sxs-lookup"><span data-stu-id="538e1-124">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="538e1-125">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="538e1-125">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="538e1-126">**図 8-6**</span><span class="sxs-lookup"><span data-stu-id="538e1-126">**Figure 8-6**.</span></span> <span data-ttu-id="538e1-127">Visual Studio での ASP.NET Core Web API プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="538e1-127">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="538e1-128">プロジェクトを作成した後、Entity Framework API またはその他の API を使用して、他の Web API プロジェクトの場合と同様に MVC コントローラーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-128">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="538e1-129">新しい Web API プロジェクトでは、そのマイクロサービスの依存関係が ASP.NET Core 自体のみにあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="538e1-129">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="538e1-130">内部的には、`Microsoft.AspNetCore.All` 依存関係内で、図 8-7 に示すように Entity Framework やその他の多くの .NET Core Nuget パッケージを参照しています。</span><span class="sxs-lookup"><span data-stu-id="538e1-130">Internally, within the `Microsoft.AspNetCore.All` dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="538e1-131">**図 8-7**</span><span class="sxs-lookup"><span data-stu-id="538e1-131">**Figure 8-7**.</span></span> <span data-ttu-id="538e1-132">単純な CRUD Web API マイクロサービス内の依存関係</span><span class="sxs-lookup"><span data-stu-id="538e1-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="538e1-133">Entity Framework Core での CRUD Web API サービスの実装</span><span class="sxs-lookup"><span data-stu-id="538e1-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="538e1-134">Entity Framework (EF) Core は人気の Entity Framework データ アクセス テクノロジの軽量版であり、拡張性に優れ、プラットフォームに依存しません。</span><span class="sxs-lookup"><span data-stu-id="538e1-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="538e1-135">EF Core はオブジェクト リレーショナル マッパー (ORM) であり、.NET 開発者は .NET オブジェクトを利用してデータベースを操作できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="538e1-136">カタログ マイクロサービスは、そのデータベースが Linux Docker イメージ用の SQL Server を持つコンテナーで実行されているため、EF と SQL Server プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="538e1-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="538e1-137">ただし、データベースは、Windows オンプレミスや Azure SQL DB など、任意の SQL Server にデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="538e1-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="538e1-138">変更が必要なのは、ASP.NET Web API マイクロサービス内の接続文字列だけです。</span><span class="sxs-lookup"><span data-stu-id="538e1-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>


#### <a name="the-data-model"></a><span data-ttu-id="538e1-139">データ モデル</span><span class="sxs-lookup"><span data-stu-id="538e1-139">The data model</span></span>

<span data-ttu-id="538e1-140">EF Core では、データ アクセスはモデルを利用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-140">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="538e1-141">モデルはエンティティ クラスと、データベースとのセッションを表す、派生コンテキストから構成されます。このセッションにより、データのクエリと保存が可能になります。</span><span class="sxs-lookup"><span data-stu-id="538e1-141">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="538e1-142">既存データベースからモデルを生成したり、自分のデータベースに合わせてモデルのコードを手動で記述したり、EF 移行を利用してモデルからデータベースを作成したり (モデルが時間の経過と共に変化するのに合わせ、進化させたり) できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-142">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="538e1-143">カタログ マイクロサービスでは、最後のアプローチを使用しています。</span><span class="sxs-lookup"><span data-stu-id="538e1-143">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="538e1-144">次のコード例には、CatalogItem エンティティ クラスの例があります。これは単純な従来の CLR オブジェクト ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) エンティティ クラスです。</span><span class="sxs-lookup"><span data-stu-id="538e1-144">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

<span data-ttu-id="538e1-145">データベースとのセッションを表す DbContext も必要です。</span><span class="sxs-lookup"><span data-stu-id="538e1-145">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="538e1-146">カタログ マイクロサービスでは、CatalogContext クラスは次の例で示すように DbContext 基底クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="538e1-146">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="538e1-147">追加の `DbContext` 実装も使用できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-147">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="538e1-148">たとえば、サンプルの Catalog.API マイクロサービスには `CatalogContextSeed` という名前の 2 番目の `DbContext` があり、データベースに初めてアクセスしようとしたときにサンプル データが自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-148">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="538e1-149">このメソッドは、デモ データと自動テストのシナリオにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="538e1-149">This method is useful for demo data and for automated testing scenarios, as well.</span></span> <span data-ttu-id="538e1-150">`DbContext` 内で、`OnModelCreating` メソッドを使用して、オブジェクト/データベース エンティティのマッピングおよびその他の [EF 機能拡張ポイント](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="538e1-150">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings with and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="538e1-151">Web API コントローラーからのデータのクエリ</span><span class="sxs-lookup"><span data-stu-id="538e1-151">Querying data from Web API controllers</span></span>

<span data-ttu-id="538e1-152">エンティティ クラスのインスタンスは、次の例に示すように、通常は統合言語クエリ (LINQ) を利用してデータベースから取得されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-152">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
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

##### <a name="saving-data"></a><span data-ttu-id="538e1-153">データの保存</span><span class="sxs-lookup"><span data-stu-id="538e1-153">Saving data</span></span>

<span data-ttu-id="538e1-154">データはエンティティ クラスのインスタンスを利用し、データベース内で作成、削除、変更されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-154">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="538e1-155">次のハード コーディングされた例のようなコード (この場合はモック データ) を Web API コントローラーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-155">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="538e1-156">ASP.NET Core と Web API コントローラーでの依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="538e1-156">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="538e1-157">ASP.NET Core では、既定の依存関係の挿入 (DI) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-157">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="538e1-158">優先 IoC コンテナーを ASP.NET Core インフラストラクチャに接続することもできますが、サード パーティ製の制御の反転 (IoC) コンテナーを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="538e1-158">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="538e1-159">この場合、必須の EF DBContext またはコントローラー コンストラクターを通じた追加のリポジトリを直接挿入できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="538e1-159">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="538e1-160">上記の `CatalogController` クラスの例では、`CatalogController()` コンストラクターを通じて `CatalogContext` 型のオブジェクトやその他のオブジェクトを挿入しています。</span><span class="sxs-lookup"><span data-stu-id="538e1-160">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="538e1-161">Web API プロジェクトを設定するための重要な構成は、サービスの IoC コンテナーへの DbContext クラスの登録です。</span><span class="sxs-lookup"><span data-stu-id="538e1-161">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="538e1-162">通常この操作は、次の例で示すように `ConfigureServices()` メソッド内で `services.AddDbContext<DbContext>()` メソッドを呼び出して `Startup` クラス内で行います。</span><span class="sxs-lookup"><span data-stu-id="538e1-162">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

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

### <a name="additional-resources"></a><span data-ttu-id="538e1-163">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="538e1-163">Additional resources</span></span>

-   <span data-ttu-id="538e1-164">**データのクエリ**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="538e1-164">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="538e1-165">**データの保存**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="538e1-165">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="538e1-166">Docker コンテナーで使用される DB 接続文字列と環境変数</span><span class="sxs-lookup"><span data-stu-id="538e1-166">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="538e1-167">次の例に示すように、ASP.NET Core 設定を使用でき、ConnectionString プロパティを settings.json ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-167">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="538e1-168">settings.json ファイルには、ConnectionString プロパティやその他のプロパティの既定値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-168">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="538e1-169">ただし、Docker を使用する場合、これらのプロパティは docker-compose.override.yml ファイルで指定した環境変数の値でオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="538e1-169">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="538e1-170">次の docker-compose.override.yml ファイルに示すように、docker-compose.yml または docker-compose.override.yml ファイルからこれらの環境変数を初期化して、Docker がそれらを OS 環境変数として設定するようにすることができます (この例では接続文字列とその他の行が折り返されていますが、実際のコード ファイルでは折り返されません)。</span><span class="sxs-lookup"><span data-stu-id="538e1-170">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own code file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="538e1-171">ソリューション レベルでの docker-compose.yml ファイルは、プロジェクトまたはマイクロサービス レベルの構成ファイルよりも柔軟性が高いだけでなく、docker-compose ファイルで宣言されている環境変数を VSTS Docker デプロイ タスクからの値のようなデプロイ ツールで設定された値でオーバーライドするとセキュリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="538e1-171">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from VSTS Docker deployment tasks.</span></span> 

<span data-ttu-id="538e1-172">最後に、前のコード例の ConfigureServices メソッドで示されているように、構成 \["ConnectionString"\] を使用してコードから値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-172">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="538e1-173">ただし、運用環境では、接続文字列などのシークレットを格納する方法について、追加の方法を調べることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-173">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="538e1-174">通常は、[Docker Swarm シークレットの管理](https://docs.docker.com/engine/swarm/secrets/)で行えるのと同様に、選択したオーケストレーターで管理されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-174">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="538e1-175">ASP.NET Web API でのバージョン管理の実装</span><span class="sxs-lookup"><span data-stu-id="538e1-175">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="538e1-176">ビジネス要件が変わると、リソースの新しいコレクションが追加され、リソース間の関係が変更され、リソース内のデータの構造が修正される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-176">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="538e1-177">新しい要件を処理する Web API の更新は比較的簡単なプロセスですが、このような変更が Web API を使用するクライアント アプリケーションに与える影響を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-177">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="538e1-178">Web API を設計および実装する開発者はその API を完全に制御できますが、遠隔地で操業しているサード パーティ組織が構築した可能性のあるクライアント アプリケーションを同じように制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="538e1-178">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="538e1-179">バージョン管理によって、Web API が公開する機能とリソースを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="538e1-179">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="538e1-180">クライアント アプリケーションは、特定のバージョンの機能やリソースに要求を送信できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-180">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="538e1-181">バージョン管理を実装するアプローチはいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="538e1-181">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="538e1-182">URI バージョン管理</span><span class="sxs-lookup"><span data-stu-id="538e1-182">URI versioning</span></span>

-   <span data-ttu-id="538e1-183">クエリ文字列バージョン管理</span><span class="sxs-lookup"><span data-stu-id="538e1-183">Query string versioning</span></span>

-   <span data-ttu-id="538e1-184">ヘッダー バージョン管理</span><span class="sxs-lookup"><span data-stu-id="538e1-184">Header versioning</span></span>

<span data-ttu-id="538e1-185">クエリ文字列および URI バージョン管理は、実装するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="538e1-185">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="538e1-186">ヘッダー バージョン管理は適切なアプローチです。</span><span class="sxs-lookup"><span data-stu-id="538e1-186">Header versioning is a good approach.</span></span> <span data-ttu-id="538e1-187">ただし、ヘッダー バージョン管理は URI バージョン管理ほど明示的でも簡単でもありません。</span><span class="sxs-lookup"><span data-stu-id="538e1-187">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="538e1-188">URL バージョン管理は最も単純で最も明示的なので、eShopOnContainers サンプル アプリケーションでは URI バージョン管理を使用します。</span><span class="sxs-lookup"><span data-stu-id="538e1-188">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="538e1-189">eShopOnContainers サンプル アプリケーションのように、URI バージョン管理では、Web API を変更したりリソースのスキーマを変更したりするたびに、各リソースの URI にバージョン番号が追加されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-189">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="538e1-190">既存の URI はそれまでと同様に動作を続け、要求されたバージョンに対応するスキーマに準拠したリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="538e1-190">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="538e1-191">次のコード例に示すように、バージョンは Web API の Route 属性を使用して設定でき、これにより URI でバージョン (このケースでは v1) が明示的になります。</span><span class="sxs-lookup"><span data-stu-id="538e1-191">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="538e1-192">このバージョン管理メカニズムは単純で、要求を適切なエンドポイントにルーティングするサーバーに依存します。</span><span class="sxs-lookup"><span data-stu-id="538e1-192">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="538e1-193">ただし、より高度なバージョン管理と REST を使用するときに最適な方法としては、ハイパーメディアを使用し、[HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-193">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="538e1-194">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="538e1-194">Additional resources</span></span>

-   <span data-ttu-id="538e1-195">**Scott Hanselman。簡単になった ASP.NET Core RESTful Web API のバージョン管理**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="538e1-195">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="538e1-196">**RESTful Web API のバージョン管理**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="538e1-196">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="538e1-197">**Roy Fielding。バージョン管理、ハイパーメディア、REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="538e1-197">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="538e1-198">ASP.NET Core Web API からの Swagger 記述メタデータの生成</span><span class="sxs-lookup"><span data-stu-id="538e1-198">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="538e1-199">[Swagger](https://swagger.io/) は一般に使用されるオープン ソース フレームワークであり、RESTful API の設計、構築、文書化、使用に役立つツールの大規模なエコシステムによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="538e1-199">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="538e1-200">API 記述メタデータ ドメインの標準になりつつあります。</span><span class="sxs-lookup"><span data-stu-id="538e1-200">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="538e1-201">Swagger 記述メタデータを任意の種類のマイクロサービス (次のセクションで説明するデータ ドリブン マイクロサービスまたはより高度なドメイン ドリブン マイクロサービス) と共に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-201">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="538e1-202">Swagger の中心となるのは、JSON または YAML ファイル内の API 記述メタデータである Swagger 仕様です。</span><span class="sxs-lookup"><span data-stu-id="538e1-202">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="538e1-203">仕様では、API の RESTful コントラクトを作成し、開発、検出、統合を簡単にするためにすべてのリソースと操作を人間とマシンの両方が判読できる形式で詳しく記述します。</span><span class="sxs-lookup"><span data-stu-id="538e1-203">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="538e1-204">仕様は、OpenAPI 仕様 (OAS) の基盤であり、RESTful インターフェイスを定義する方法を標準化するためにオープンで透過的なコラボレーション コミュニティで開発されています。</span><span class="sxs-lookup"><span data-stu-id="538e1-204">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="538e1-205">仕様では、サービスの検出方法とその機能を理解する方法に関する構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="538e1-205">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="538e1-206">Web エディターや、Spotify、Uber、Slack、Microsoft などの企業の Swagger 仕様の例については、Swagger のサイト (<https://swagger.io/>) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="538e1-206">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io/>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="538e1-207">Swagger を使用する理由</span><span class="sxs-lookup"><span data-stu-id="538e1-207">Why use Swagger?</span></span>

<span data-ttu-id="538e1-208">API 用の Swagger メタデータを生成する主な理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="538e1-208">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="538e1-209">**他の製品が API を自動的に使用して統合できる**。</span><span class="sxs-lookup"><span data-stu-id="538e1-209">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="538e1-210">数十個の製品と[商用ツール](https://swagger.io/commercial-tools/)、多くの[ライブラリとフレームワーク](https://swagger.io/open-source-integrations/)で Swagger がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="538e1-210">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="538e1-211">Microsoft には、Swagger ベースの API を自動的に使用できる次のような高度な製品とツールがあります。</span><span class="sxs-lookup"><span data-stu-id="538e1-211">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="538e1-212">[AutoRest](https://github.com/Azure/AutoRest)。</span><span class="sxs-lookup"><span data-stu-id="538e1-212">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="538e1-213">Swagger を呼び出すための .NET クライアント クラスを自動的に生成することができます。</span><span class="sxs-lookup"><span data-stu-id="538e1-213">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="538e1-214">このツールは CLI から使用することができ、GUI から簡単に使用できるように Visual Studio とも統合されています。</span><span class="sxs-lookup"><span data-stu-id="538e1-214">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="538e1-215">[Microsoft Flow](https://flow.microsoft.com/en-us/)。</span><span class="sxs-lookup"><span data-stu-id="538e1-215">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="538e1-216">自動的に [API 使用し、高レベルの Microsoft Flow ワークフローと統合](https://flow.microsoft.com/en-us/blog/integrating-custom-api/)できます。プログラミング スキルは不要です。</span><span class="sxs-lookup"><span data-stu-id="538e1-216">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="538e1-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/)。</span><span class="sxs-lookup"><span data-stu-id="538e1-217">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="538e1-218">[PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/) で作成された [PowerApps モバイル アプリ](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/)から API を自動的に使用できます。プログラミング スキルは不要です。</span><span class="sxs-lookup"><span data-stu-id="538e1-218">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="538e1-219">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="538e1-219">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="538e1-220">自動的に [API を使用でき、Azure App Service Logic App に統合](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)できます。プログラミング スキルは不要です。</span><span class="sxs-lookup"><span data-stu-id="538e1-220">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="538e1-221">**API のドキュメントを自動的に生成できる**。</span><span class="sxs-lookup"><span data-stu-id="538e1-221">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="538e1-222">複雑なマイクロサービス ベースのアプリケーションなど、大規模な RESTful API を作成する場合は、要求と応答のペイロードで使用されるさまざまなデータ モデルで多数のエンドポイントを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-222">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="538e1-223">Swagger で利用できるような適切なドキュメントと堅牢な API Explorer があることは、API の成功と開発者による採用の鍵となります。</span><span class="sxs-lookup"><span data-stu-id="538e1-223">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="538e1-224">Swagger のメタデータは、Microsoft Flow、PowerApps、Azure Logic Apps が API の使用方法と API への接続方法を理解するために使用するものです。</span><span class="sxs-lookup"><span data-stu-id="538e1-224">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="538e1-225">Swashbuckle NuGet パッケージで API Swagger メタデータの生成を自動化する方法</span><span class="sxs-lookup"><span data-stu-id="538e1-225">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="538e1-226">手動での (JSON または YAML ファイルでの) Swagger メタデータの生成は面倒な作業となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-226">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="538e1-227">ただし、[Swashbuckle NuGet パッケージ](http://aka.ms/swashbuckledotnetcore)を使用して Swagger API メタデータを動的に生成して、ASP.NET Web API サービスの API 検出を自動化することができます。</span><span class="sxs-lookup"><span data-stu-id="538e1-227">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="538e1-228">Swashbuckle では、ASP.NET Web API プロジェクトの Swagger メタデータが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-228">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="538e1-229">ASP.NET Core Web API プロジェクトと従来の ASP.NET Web API、さらに Azure API アプリ、Azure Mobile App、ASP.NET に基づく Azure Service Fabric マイクロサービスなどのその他のフレーバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="538e1-229">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="538e1-230">また、参照アプリケーションの場合と同様に、コンテナーにデプロイされている単純な Web API もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="538e1-230">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="538e1-231">Swashbuckle は API Explorer と Swagger または [swagger-ui](https://github.com/swagger-api/swagger-ui) を結合して API コンシューマーに充実した検出およびドキュメント エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="538e1-231">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="538e1-232">Swagger メタデータ ジェネレーター エンジンに加えて、Swashbuckle には、Swashbuckle のインストール後に自動的に提供される埋め込みバージョンの swagger-ui も含まれています。</span><span class="sxs-lookup"><span data-stu-id="538e1-232">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="538e1-233">これは、優れた検出 UI で API を補完し、開発者による API の使用を支援できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="538e1-233">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="538e1-234">これは自動的に生成されるため、必要なコードとメンテナンスの量がとても少なく、API の構築に専念することができます。</span><span class="sxs-lookup"><span data-stu-id="538e1-234">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="538e1-235">API Explorer の結果は、図 8-8 のようになります。</span><span class="sxs-lookup"><span data-stu-id="538e1-235">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="538e1-236">**図 8-8**</span><span class="sxs-lookup"><span data-stu-id="538e1-236">**Figure 8-8**.</span></span> <span data-ttu-id="538e1-237">Swagger メタデータに基づく Swashbuckle API Explorer - eShopOnContainers カタログ マイクロサービス</span><span class="sxs-lookup"><span data-stu-id="538e1-237">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="538e1-238">API Explorer は、ここで最も重要なものではありません。</span><span class="sxs-lookup"><span data-stu-id="538e1-238">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="538e1-239">Swagger メタデータで自身を記述できる Web API があると、多くのプラットフォームを対象とするクライアント プロキシ クラス コード ジェネレーターなど、Swagger ベースのツールから API をシームレスに使用できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-239">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="538e1-240">たとえば、前に説明したように、[AutoRest](https://github.com/Azure/AutoRest) では .NET クライアント クラスが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-240">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="538e1-241">ただし、API クライアント ライブラリ、サーバー スタブ、ドキュメントのコード生成を自動化できる [swagger-codegen](https://github.com/swagger-api/swagger-codegen) のようなツールも利用できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-241">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="538e1-242">現時点では、Swashbuckle は、ASP.NET Core アプリケーション用の [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) バージョン 1.0.0 以降のハイレベルなメタ パッケージ下の 2 つの内部 NuGet パッケージから構成されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-242">Currently, Swashbuckle consists of two several internal NuGet packages under the high-level meta- package [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) version 1.0.0 or later for ASP.NET Core applications.</span></span>

<span data-ttu-id="538e1-243">Web API プロジェクトでこれらの NuGet パッケージをインストールした後、次のコードのように、Startup クラスで Swagger を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="538e1-243">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
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
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

<span data-ttu-id="538e1-244">これが完了したら、アプリケーションを起動し、次のような URL を使用して次の Swagger JSON および UI エンドポイントを参照することができます。</span><span class="sxs-lookup"><span data-stu-id="538e1-244">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="538e1-245">http://&lt;your-root-url&gt;/swagger/ui のような URL に対して Swashbuckle で作成された生成済みの UI を前に参照しました。</span><span class="sxs-lookup"><span data-stu-id="538e1-245">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="538e1-246">図 8-9 では、API メソッドをテストする方法も確認できます。</span><span class="sxs-lookup"><span data-stu-id="538e1-246">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="538e1-247">**図 8-9**</span><span class="sxs-lookup"><span data-stu-id="538e1-247">**Figure 8-9**.</span></span> <span data-ttu-id="538e1-248">カタログ/アイテム API メソッドをテストする Swashbuckle UI</span><span class="sxs-lookup"><span data-stu-id="538e1-248">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="538e1-249">図 8-10 は、[Postman](https://www.getpostman.com/) を使用して &lt;your-root-url&gt;/swagger/v1/swagger.json を要求したときに eShopOnContainers マイクロサービス (これは、ツールが下で使用するものです) から生成された Swagger JSON メタデータを示しています。</span><span class="sxs-lookup"><span data-stu-id="538e1-249">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="538e1-250">**図 8-10**</span><span class="sxs-lookup"><span data-stu-id="538e1-250">**Figure 8-10**.</span></span> <span data-ttu-id="538e1-251">Swagger JSON メタデータ</span><span class="sxs-lookup"><span data-stu-id="538e1-251">Swagger JSON metadata</span></span>

<span data-ttu-id="538e1-252">これは単純です。</span><span class="sxs-lookup"><span data-stu-id="538e1-252">It is that simple.</span></span> <span data-ttu-id="538e1-253">自動的に生成されるため、API に機能を追加すると Swagger メタデータが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="538e1-253">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="538e1-254">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="538e1-254">Additional resources</span></span>

-   <span data-ttu-id="538e1-255">**Swagger を使用する ASP.NET Web API のヘルプ ページ**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="538e1-255">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="538e1-256">[前へ](microservice-application-design.md)
[次へ](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="538e1-256">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>

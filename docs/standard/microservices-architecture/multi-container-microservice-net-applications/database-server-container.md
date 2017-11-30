---
title: "コンテナーとして実行されているデータベース サーバーの使用"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |コンテナーとして実行されているデータベース サーバーの使用"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7e5f33c4e7edf9d0d4551c5125976fcb8fda392f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="3e6f8-104">コンテナーとして実行されているデータベース サーバーの使用</span><span class="sxs-lookup"><span data-stu-id="3e6f8-104">Using a database server running as a container</span></span>

<span data-ttu-id="3e6f8-105">正規のスタンドアロン サーバー、クラスターでは、内部設置型、または Azure SQL DB のように、クラウド内に PaaS サービスでは、データベース (SQL Server、PostgreSQL、MySQL など) ことができます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="3e6f8-106">ただし、開発およびテスト環境では、コンテナーとして実行されている、データベースを持つが、外部の依存関係があるないため、便利で実行するだけ、docker 構成コマンドは、アプリケーション全体を開始します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency, and simply running the docker-compose command starts the whole application.</span></span> <span data-ttu-id="3e6f8-107">データベースのコンテナーの開始が常に同じサンプル データに設定されるため、テストをより予測可能なことができるため、コンテナーとしてのこれらのデータベースを持つは統合テストでは、優れたもです。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="3e6f8-108">マイクロ サービスに関連するデータベースのコンテナーとして実行している SQL サーバー</span><span class="sxs-lookup"><span data-stu-id="3e6f8-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="3e6f8-109">EShopOnContainers で定義されている sql.data をという名前のコンテナー、 [docker compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) Linux 用、microservices に必要なすべての SQL Server データベースと SQL Server を実行しているファイル。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="3e6f8-110">(データベースごとに 1 つの SQL Server コンテナーこともできますが、Docker に割り当てられているより多くのメモリが必要となります)。Microservices で重要な点が各マイクロ サービスを所有してその関連データでは、そのため、関連する SQL データベースここでです。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="3e6f8-111">データベースには、任意の場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="3e6f8-112">実行するときに実行される docker compose.yml ファイルに次の YAML コード、サンプル アプリケーションのコンテナーが構成されている SQL Server docker の構成をします。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run docker-compose up.</span></span> <span data-ttu-id="3e6f8-113">YAML コードがジェネリックの docker compose.yml ファイルと docker compose.override.yml ファイルから構成情報を統合されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="3e6f8-114">(通常は区別する SQL Server イメージに関連する基本または静的の情報から、環境の設定です。)</span><span class="sxs-lookup"><span data-stu-id="3e6f8-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

<span data-ttu-id="3e6f8-115">次の docker run コマンドでは、そのコンテナーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-115">The following docker run command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

<span data-ttu-id="3e6f8-116">ただし、eShopOnContainers などの複数のコンテナー アプリケーションを展開する場合は使いやすい、docker の構成コマンドをアプリケーションの必要なすべてのコンテナーが配置されるようにします。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the docker-compose up command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="3e6f8-117">最初にこの SQL Server のコンテナーを開始するときに、コンテナーは、指定したパスワードを使用して SQL Server を初期化します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="3e6f8-118">SQL Server Management Studio、Visual Studio、または C からなど、通常の SQL 接続を介して接続してデータベースを更新するには、コンテナーとして SQL Server が実行されると、\#コード。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="3e6f8-119">EShopOnContainers アプリケーションでは、次のセクションで説明したように、スタートアップ時に、データをシードすることにより各マイクロ サービス データベースにサンプル データを初期化します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="3e6f8-120">SQL Server のコンテナーとしての実行はありませんデモについては、単に便利です、SQL Server のインスタンスへのアクセスがないです。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="3e6f8-121">特に記載のない限りも開発およびテスト環境に最適に簡単にクリーンな SQL Server イメージから起動統合テストを実行したり、新しいサンプル データのシード処理でデータを認識できるようにできます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3e6f8-122">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="3e6f8-122">Additional resources</span></span>

-   <span data-ttu-id="3e6f8-123">**Linux、Mac、またはウィンドウで、SQL Server の Docker イメージを実行**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span><span class="sxs-lookup"><span data-stu-id="3e6f8-123">**Run the SQL Server Docker image on Linux, Mac, or Windows**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span></span>

-   <span data-ttu-id="3e6f8-124">**接続し、クエリ sqlcmd での SQL Server on Linux**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="3e6f8-124">**Connect and query SQL Server on Linux with sqlcmd**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span></span>

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="3e6f8-125">Web アプリケーションの起動時にテスト データのシード処理</span><span class="sxs-lookup"><span data-stu-id="3e6f8-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="3e6f8-126">アプリケーションの起動時には、データベースにデータを追加するには、Web API プロジェクトのスタートアップ クラス内の構成メソッドに次のようにコードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="3e6f8-127">カスタムの CatalogContextSeed クラスに次のコードでは、データを追加します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="3e6f8-128">統合テストを実行すると、統合テストで一貫性のあるデータを生成する方法が便利です。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="3e6f8-129">すべてのコンテナーで実行されている SQL Server のインスタンスを含む、最初から作成することは、テスト環境に最適。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="3e6f8-130">SQL Server のコンテナーとしての実行と EF コア InMemory データベース</span><span class="sxs-lookup"><span data-stu-id="3e6f8-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="3e6f8-131">テストの実行時に別の適切な選択では、Entity Framework InMemory データベース プロバイダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="3e6f8-132">Web API プロジェクトでのスタートアップ クラス ConfigureServices メソッドにその構成を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...

}
```

<span data-ttu-id="3e6f8-133">ただし、重要な落とし穴があります。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-133">There is an important catch, though.</span></span> <span data-ttu-id="3e6f8-134">メモリ内のデータベースでは、特定のデータベースに固有の多くの制約はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="3e6f8-135">インスタンス、EF の主要なモデルで列に一意のインデックスを追加およびを確認することはできません、重複する値を追加するインメモリ データベースに対してテストを記述する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="3e6f8-136">メモリ内のデータベースを使用している場合は、列に一意のインデックスを処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="3e6f8-137">そのため、メモリ内のデータベースが動作しない、実際の SQL Server データベースと同じ-データベース固有の制約はエミュレートしません。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="3e6f8-138">メモリ内のデータベースはテストやプロトタイピングでも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="3e6f8-139">特定のデータベースの実装の動作を考慮する正確な統合テストを作成する場合は、SQL Server のような実際のデータベースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="3e6f8-140">その目的は、SQL Server のコンテナーの実行は優れた選択肢と EF コア InMemory データベース プロバイダーよりも正確です。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="3e6f8-141">コンテナーで実行されている Redis キャッシュ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="3e6f8-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="3e6f8-142">Redis は、コンテナー、特に開発およびテストや概念実証のシナリオで実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="3e6f8-143">このシナリオでは便利で、コンテナーで実行されているすべての依存関係があることができます: ローカル開発用コンピューターは、CI/CD パイプラインで、テスト環境だけでなくです。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="3e6f8-144">ただし、実稼働環境で Redis を実行するときは Redis Microsoft Azure PaaS (サービスとしてのプラットフォーム) として実行されているような高可用性ソリューションを検索することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="3e6f8-145">コード内だけに、接続文字列を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="3e6f8-146">Redis は、Redis で Docker イメージを提供します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="3e6f8-147">そのイメージは、この URL での Docker Hub から入手できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-147">That image is available from Docker Hub at this URL:</span></span>

<span data-ttu-id="3e6f8-148"><https://hub.docker.com/_/redis/></span><span class="sxs-lookup"><span data-stu-id="3e6f8-148"><https://hub.docker.com/_/redis/></span></span>

<span data-ttu-id="3e6f8-149">Docker Redis コンテナーは、コマンド プロンプトで次の Docker CLI コマンドを実行することによって直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-149">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="3e6f8-150">コンテナーのための標準リンクは自動的に使用できるようにリンクのコンテナー、Redis イメージには公開: 6379 (Redis で使用されるポート) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-150">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="3e6f8-151">EShopOnContainers、basket.api マイクロ サービスはコンテナーとして実行されている、Redis cache を使用します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-151">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="3e6f8-152">その basket.data コンテナーは、次の例で示すように、複数のコンテナー docker compose.yml ファイルの一部として定義されます。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-152">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="3e6f8-153">Docker compose.yml でこのコードでは、redis イメージに基づいており、ポート 6379 を内部的には、発行、Docker ホスト内で実行されているその他のコンテナーからのみアクセスできることを意味 basket.data をという名前のコンテナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-153">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="3e6f8-154">最後に、docker compose.override.yml ファイル eShopOnContainers サンプル basket.api マイクロ サービスはその Redis コンテナーに使用する接続文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="3e6f8-154">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
<span data-ttu-id="3e6f8-155">[前](マルチ-container-アプリケーション-docker-compose.md) [次へ] (integration-イベント-ベースのマイクロ サービス-communications.md)</span><span class="sxs-lookup"><span data-stu-id="3e6f8-155">[Previous] (multi-container-applications-docker-compose.md) [Next] (integration-event-based-microservice-communications.md)</span></span>

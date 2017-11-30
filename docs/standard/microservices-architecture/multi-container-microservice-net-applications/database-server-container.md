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
# <a name="using-a-database-server-running-as-a-container"></a>コンテナーとして実行されているデータベース サーバーの使用

正規のスタンドアロン サーバー、クラスターでは、内部設置型、または Azure SQL DB のように、クラウド内に PaaS サービスでは、データベース (SQL Server、PostgreSQL、MySQL など) ことができます。 ただし、開発およびテスト環境では、コンテナーとして実行されている、データベースを持つが、外部の依存関係があるないため、便利で実行するだけ、docker 構成コマンドは、アプリケーション全体を開始します。 データベースのコンテナーの開始が常に同じサンプル データに設定されるため、テストをより予測可能なことができるため、コンテナーとしてのこれらのデータベースを持つは統合テストでは、優れたもです。

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>マイクロ サービスに関連するデータベースのコンテナーとして実行している SQL サーバー

EShopOnContainers で定義されている sql.data をという名前のコンテナー、 [docker compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) Linux 用、microservices に必要なすべての SQL Server データベースと SQL Server を実行しているファイル。 (データベースごとに 1 つの SQL Server コンテナーこともできますが、Docker に割り当てられているより多くのメモリが必要となります)。Microservices で重要な点が各マイクロ サービスを所有してその関連データでは、そのため、関連する SQL データベースここでです。 データベースには、任意の場所を指定できます。

実行するときに実行される docker compose.yml ファイルに次の YAML コード、サンプル アプリケーションのコンテナーが構成されている SQL Server docker の構成をします。 YAML コードがジェネリックの docker compose.yml ファイルと docker compose.override.yml ファイルから構成情報を統合されたことに注意してください。 (通常は区別する SQL Server イメージに関連する基本または静的の情報から、環境の設定です。)

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

次の docker run コマンドでは、そのコンテナーを実行できます。

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

ただし、eShopOnContainers などの複数のコンテナー アプリケーションを展開する場合は使いやすい、docker の構成コマンドをアプリケーションの必要なすべてのコンテナーが配置されるようにします。

最初にこの SQL Server のコンテナーを開始するときに、コンテナーは、指定したパスワードを使用して SQL Server を初期化します。 SQL Server Management Studio、Visual Studio、または C からなど、通常の SQL 接続を介して接続してデータベースを更新するには、コンテナーとして SQL Server が実行されると、\#コード。

EShopOnContainers アプリケーションでは、次のセクションで説明したように、スタートアップ時に、データをシードすることにより各マイクロ サービス データベースにサンプル データを初期化します。

SQL Server のコンテナーとしての実行はありませんデモについては、単に便利です、SQL Server のインスタンスへのアクセスがないです。 特に記載のない限りも開発およびテスト環境に最適に簡単にクリーンな SQL Server イメージから起動統合テストを実行したり、新しいサンプル データのシード処理でデータを認識できるようにできます。

#### <a name="additional-resources"></a>その他の技術情報

-   **Linux、Mac、またはウィンドウで、SQL Server の Docker イメージを実行**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **接続し、クエリ sqlcmd での SQL Server on Linux**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Web アプリケーションの起動時にテスト データのシード処理

アプリケーションの起動時には、データベースにデータを追加するには、Web API プロジェクトのスタートアップ クラス内の構成メソッドに次のようにコードを追加できます。

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

カスタムの CatalogContextSeed クラスに次のコードでは、データを追加します。

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

統合テストを実行すると、統合テストで一貫性のあるデータを生成する方法が便利です。 すべてのコンテナーで実行されている SQL Server のインスタンスを含む、最初から作成することは、テスト環境に最適。

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>SQL Server のコンテナーとしての実行と EF コア InMemory データベース

テストの実行時に別の適切な選択では、Entity Framework InMemory データベース プロバイダーを使用します。 Web API プロジェクトでのスタートアップ クラス ConfigureServices メソッドにその構成を指定できます。

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

ただし、重要な落とし穴があります。 メモリ内のデータベースでは、特定のデータベースに固有の多くの制約はサポートされません。 インスタンス、EF の主要なモデルで列に一意のインデックスを追加およびを確認することはできません、重複する値を追加するインメモリ データベースに対してテストを記述する可能性があります。 メモリ内のデータベースを使用している場合は、列に一意のインデックスを処理することはできません。 そのため、メモリ内のデータベースが動作しない、実際の SQL Server データベースと同じ-データベース固有の制約はエミュレートしません。

メモリ内のデータベースはテストやプロトタイピングでも役立ちます。 特定のデータベースの実装の動作を考慮する正確な統合テストを作成する場合は、SQL Server のような実際のデータベースを使用する必要があります。 その目的は、SQL Server のコンテナーの実行は優れた選択肢と EF コア InMemory データベース プロバイダーよりも正確です。

### <a name="using-a-redis-cache-service-running-in-a-container"></a>コンテナーで実行されている Redis キャッシュ サービスの使用

Redis は、コンテナー、特に開発およびテストや概念実証のシナリオで実行できます。 このシナリオでは便利で、コンテナーで実行されているすべての依存関係があることができます: ローカル開発用コンピューターは、CI/CD パイプラインで、テスト環境だけでなくです。

ただし、実稼働環境で Redis を実行するときは Redis Microsoft Azure PaaS (サービスとしてのプラットフォーム) として実行されているような高可用性ソリューションを検索することをお勧めします。 コード内だけに、接続文字列を変更する必要があります。

Redis は、Redis で Docker イメージを提供します。 そのイメージは、この URL での Docker Hub から入手できます。

<https://hub.docker.com/_/redis/>

Docker Redis コンテナーは、コマンド プロンプトで次の Docker CLI コマンドを実行することによって直接実行できます。

```
  docker run --name some-redis -d redis
```

コンテナーのための標準リンクは自動的に使用できるようにリンクのコンテナー、Redis イメージには公開: 6379 (Redis で使用されるポート) が含まれます。

EShopOnContainers、basket.api マイクロ サービスはコンテナーとして実行されている、Redis cache を使用します。 その basket.data コンテナーは、次の例で示すように、複数のコンテナー docker compose.yml ファイルの一部として定義されます。

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Docker compose.yml でこのコードでは、redis イメージに基づいており、ポート 6379 を内部的には、発行、Docker ホスト内で実行されているその他のコンテナーからのみアクセスできることを意味 basket.data をという名前のコンテナーを定義します。

最後に、docker compose.override.yml ファイル eShopOnContainers サンプル basket.api マイクロ サービスはその Redis コンテナーに使用する接続文字列を定義します。

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[前](マルチ-container-アプリケーション-docker-compose.md) [次へ] (integration-イベント-ベースのマイクロ サービス-communications.md)

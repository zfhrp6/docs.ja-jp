---
title: "回復力のある Entity Framework の主要な SQL 接続の実装"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |回復力のある Entity Framework の主要な SQL 接続の実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8600625c2022d69ebaa2645c2a8159a848b12ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>回復力のある Entity Framework の主要な SQL 接続の実装

Azure SQL DB、Entity Framework のコアには、既に内部データベース接続の回復性と再試行ロジックが用意されています。 する場合は、DbContext 接続ごとに、Entity Framework の実行方法を有効にする必要がありますが、[回復力のある EF コア接続](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)です。

たとえば、EF コア接続レベルでは、次のコードは、接続に失敗した場合に再試行回復力のある SQL 接続を有効します。

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>実行方法と BeginTransaction と複数 DbContexts を使用して明示的なトランザクション

EF コア接続では、再試行が有効な場合、EF コアを使用して実行する各操作は、独自の再試行可能な操作になります。 一時的なエラーが発生した場合、各クエリおよび SaveChanges に対する各呼び出しが単位として再試行されます。

ただし、コードでは、BeginTransaction を使用してトランザクションを開始する場合は、ユニットとして扱われる必要のある操作のグループを定義する — 障害が発生した場合に、トランザクション内のすべてロールバックされます。 EF の実行方法 (再試行ポリシー) を使用する場合は、そのトランザクションを実行しようとして、トランザクションに複数の DbContexts からいくつかの SaveChanges 呼び出しを含める場合、次のような例外が表示されます。

> System.invalidoperationexception: 構成済みの実行方法 'SqlServerRetryingExecutionStrategy' はユーザーが開始したトランザクションをサポートしていません。 'DbContext.Database.CreateExecutionStrategy()' によって返される実行方法を使用して、再試行可能な単位としてトランザクション内のすべての操作を実行します。

ソリューションでは、手動で実行する必要があるすべてのものを表すデリゲートを使用して EF の実行方法を呼び出します。 一時的な障害が発生した場合、実行方法は、デリゲートをもう一度呼び出されます。 たとえば、次のコードは、2 つ eShopOnContainers での実装方法を表示複数 DbContexts (\_catalogContext と、IntegrationEventLogContext) 製品とし、保存を更新するときに、ProductPriceChangedIntegrationEvent オブジェクトには、さまざまな DbContext を使用する必要があります。

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

First DbContext は\_内では、DbContext catalogContext と 2 番目、 \_integrationEventLogService オブジェクト。 EF の実行方法を使用して複数の DbContexts 間で、コミット操作が実行されます。

## <a name="additional-resources"></a>その他の技術情報

-   **接続の回復と、Entity Framework とコマンド インターセプト**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre。回復力のある Entity Framework Core Sql 接続とトランザクションを使用して**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[前](実装の再試行-指数-backoff.md) [次へ] (implement-custom-http-call-retries-exponential-backoff.md)

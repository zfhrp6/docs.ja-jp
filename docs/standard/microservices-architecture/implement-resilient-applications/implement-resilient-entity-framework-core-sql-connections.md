---
title: 回復力の高い Entity Framework Core SQL 接続の実装
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 回復力の高い Entity Framework Core SQL 接続の実装
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 54d0df517514c359c155de35d34e1e0f56eed4eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579224"
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>回復力の高い Entity Framework Core SQL 接続の実装

Azure SQL DB の場合、Entity Framework Core に内部データベース接続の復元機能と再試行ロジックが既に用意されています。 ただし、[回復力のある EF Core 接続](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)を使用する場合は、各 DbContext 接続に対して Entity Framework 実行戦略を有効にする必要があります。

たとえば、EF Core 接続レベルで次のコードを実行すると、接続が失敗した場合に再試行される回復力のある SQL 接続が有効になります。

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>BeginTransaction と複数の DbContext を使用した実行戦略と明示的なトランザクション

EF Core 接続で再試行を有効にすると、EF Core を使用して実行する各操作は、独自の再試行可能な操作になります。 一時的なエラーが発生した場合、SaveChanges への各クエリと各呼び出しは 1 つのユニットとして再試行されます。

一方、BeginTransaction を使用してトランザクションを開始するコードの場合、1 ユニットとして扱う必要のある独自の操作グループを定義しています。エラーが発生した場合、トランザクション内のすべてがロールバックされます。 EF 実行戦略 (再試行ポリシー) を使用し、複数の DbContext からの SaveChanges 呼び出しをいくつかトランザクションに含める場合、そのトランザクションを実行しようとすると、次のような例外が表示されます。

> System.InvalidOperationException: 構成された実行戦略 'SqlServerRetryingExecutionStrategy' は、ユーザーが開始したトランザクションをサポートしていません。 'DbContext.Database.CreateExecutionStrategy()' から返された実行戦略を使用して、再試行可能なユニットとしてトランザクション内のすべての操作を実行します。

この解決策では、実行する必要があるすべてを表すデリゲートを使用して EF 実行戦略を手動で呼び出します。 一時的なエラーが発生した場合、実行戦略によってデリゲートが再び呼び出されます。 たとえば、次のコードは、製品を更新し、別の DbContext を使用する必要がある ProductPriceChangedIntegrationEvent オブジェクトを保存するときに、2 つの DbContext (\_catalogContext と IntegrationEventLogContext) を使用して eShopOnContainers で実装する方法を示しています。

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

最初の DbContext は \_catalogContext で、2 つ目の DbContext\_ は integrationEventLogService オブジェクト内にあります。 Commit アクションは、EF 実行戦略を使用して複数の DbContext 全体で実行されます。

## <a name="additional-resources"></a>その他の技術情報

-   **Entity Framework での接続回復性とコマンド傍受**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre。回復力の高い Entity Framework Core SQL 接続とトランザクションの使用**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)

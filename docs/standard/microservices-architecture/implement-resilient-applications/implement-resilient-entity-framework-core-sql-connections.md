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
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="92d20-104">回復力のある Entity Framework の主要な SQL 接続の実装</span><span class="sxs-lookup"><span data-stu-id="92d20-104">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="92d20-105">Azure SQL DB、Entity Framework のコアには、既に内部データベース接続の回復性と再試行ロジックが用意されています。</span><span class="sxs-lookup"><span data-stu-id="92d20-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="92d20-106">する場合は、DbContext 接続ごとに、Entity Framework の実行方法を有効にする必要がありますが、[回復力のある EF コア接続](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)です。</span><span class="sxs-lookup"><span data-stu-id="92d20-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="92d20-107">たとえば、EF コア接続レベルでは、次のコードは、接続に失敗した場合に再試行回復力のある SQL 接続を有効します。</span><span class="sxs-lookup"><span data-stu-id="92d20-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="92d20-108">実行方法と BeginTransaction と複数 DbContexts を使用して明示的なトランザクション</span><span class="sxs-lookup"><span data-stu-id="92d20-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="92d20-109">EF コア接続では、再試行が有効な場合、EF コアを使用して実行する各操作は、独自の再試行可能な操作になります。</span><span class="sxs-lookup"><span data-stu-id="92d20-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="92d20-110">一時的なエラーが発生した場合、各クエリおよび SaveChanges に対する各呼び出しが単位として再試行されます。</span><span class="sxs-lookup"><span data-stu-id="92d20-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="92d20-111">ただし、コードでは、BeginTransaction を使用してトランザクションを開始する場合は、ユニットとして扱われる必要のある操作のグループを定義する — 障害が発生した場合に、トランザクション内のすべてロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="92d20-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="92d20-112">EF の実行方法 (再試行ポリシー) を使用する場合は、そのトランザクションを実行しようとして、トランザクションに複数の DbContexts からいくつかの SaveChanges 呼び出しを含める場合、次のような例外が表示されます。</span><span class="sxs-lookup"><span data-stu-id="92d20-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="92d20-113">System.invalidoperationexception: 構成済みの実行方法 'SqlServerRetryingExecutionStrategy' はユーザーが開始したトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="92d20-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="92d20-114">'DbContext.Database.CreateExecutionStrategy()' によって返される実行方法を使用して、再試行可能な単位としてトランザクション内のすべての操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="92d20-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="92d20-115">ソリューションでは、手動で実行する必要があるすべてのものを表すデリゲートを使用して EF の実行方法を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="92d20-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="92d20-116">一時的な障害が発生した場合、実行方法は、デリゲートをもう一度呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="92d20-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="92d20-117">たとえば、次のコードは、2 つ eShopOnContainers での実装方法を表示複数 DbContexts (\_catalogContext と、IntegrationEventLogContext) 製品とし、保存を更新するときに、ProductPriceChangedIntegrationEvent オブジェクトには、さまざまな DbContext を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92d20-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="92d20-118">First DbContext は\_内では、DbContext catalogContext と 2 番目、 \_integrationEventLogService オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="92d20-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="92d20-119">EF の実行方法を使用して複数の DbContexts 間で、コミット操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="92d20-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="92d20-120">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="92d20-120">Additional resources</span></span>

-   <span data-ttu-id="92d20-121">**接続の回復と、Entity Framework とコマンド インターセプト**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="92d20-121">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="92d20-122">**Cesar de la Torre。回復力のある Entity Framework Core Sql 接続とトランザクションを使用して**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="92d20-122">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="92d20-123">[前](実装の再試行-指数-backoff.md) [次へ] (implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="92d20-123">[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)</span></span>

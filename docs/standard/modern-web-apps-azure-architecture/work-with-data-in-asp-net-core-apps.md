---
title: "ASP.NET Core アプリケーションのデータを操作します。"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |asp でデータの操作"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648e0a4cdd388cf4a322f0fc049d5dcfca53d54b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="98966-103">ASP.NET Core アプリケーションのデータの操作</span><span class="sxs-lookup"><span data-stu-id="98966-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="98966-104">「データ貴重なこと、システム自体よりも長くなります。」</span><span class="sxs-lookup"><span data-stu-id="98966-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="98966-105">Tim Berners-lee</span><span class="sxs-lookup"><span data-stu-id="98966-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="98966-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="98966-106">Summary</span></span>

<span data-ttu-id="98966-107">データ アクセスは、ほぼすべてのソフトウェア アプリケーションの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="98966-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="98966-108">ASP.NET Core では、さまざまなデータ アクセス オプション、Entity Framework Core (と同様に、Entity Framework 6) を含むをサポートし、任意の .NET データ アクセス フレームワークを使用できます。</span><span class="sxs-lookup"><span data-stu-id="98966-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="98966-109">データ アクセス フレームワークを使用する選択は、アプリケーションのニーズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="98966-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="98966-110">抽象化して、ApplicationCore および UI プロジェクトから、これらの選択肢とインフラストラクチャでの実装の詳細をカプセル化は、疎結合、テスト可能なソフトウェアを生成するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="98966-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="98966-111">Entity Framework Core (用リレーショナル データベース)</span><span class="sxs-lookup"><span data-stu-id="98966-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="98966-112">リレーショナル データを操作する必要がある新しい ASP.NET Core アプリケーションを作成する場合は、そのデータにアクセスするアプリケーションに対して推奨される方法は Entity Framework コア (EF) です。</span><span class="sxs-lookup"><span data-stu-id="98966-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="98966-113">EF Core とは、.NET 開発者は、データ ソースとの間のオブジェクトを保持するオブジェクト リレーショナル マッパー (O/RM) です。</span><span class="sxs-lookup"><span data-stu-id="98966-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="98966-114">これにより、開発者が作成することも通常、データ アクセス コードのほとんどの必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="98966-115">ASP.NET Core と同様に EF コア書き直しましたモジュール型プラットフォーム アプリケーションをサポートして一からです。</span><span class="sxs-lookup"><span data-stu-id="98966-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="98966-116">スタートアップ時に、構成すること、およびでも、必要な依存性の注入を通じて要求 NuGet パッケージとしてアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="98966-117">EF コアを SQL Server データベースを使用するのには、次の dotnet CLI コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="98966-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="98966-118">dotnet は、Microsoft.EntityFrameworkCore.SqlServer のパッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="98966-119">テストするため、InMemory データ ソースのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="98966-120">dotnet は、Microsoft.EntityFrameworkCore.InMemory のパッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="98966-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="98966-121">The DbContext</span></span>

<span data-ttu-id="98966-122">EF コアを使用するには、DbContext のサブクラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="98966-123">このクラスは、アプリケーションの動作のエンティティのコレクションを表すプロパティを保持します。</span><span class="sxs-lookup"><span data-stu-id="98966-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="98966-124">EShopOnWeb サンプルには、項目、ブランド、および種類のコレクションで CatalogContext が含まれます。</span><span class="sxs-lookup"><span data-stu-id="98966-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="98966-125">DbContext は DbContextOptions を受け入れるコンス トラクターを持つし、基本 DbContext コンス トラクターにこの引数を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="98966-126">なお、アプリケーションで 1 つだけ DbContext がある場合、DbContextOptions のインスタンスを渡すことができますがある場合は、ジェネリック DbContextOptions を使用した 1 つ以上の必要があります<T>DbContext 型としてジェネリック パラメーターに渡す型。</span><span class="sxs-lookup"><span data-stu-id="98966-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="98966-127">EF Core の構成</span><span class="sxs-lookup"><span data-stu-id="98966-127">Configuring EF Core</span></span>

<span data-ttu-id="98966-128">ASP.NET Core アプリケーションでは、通常 ConfigureServices メソッドで EF コアを構成します。</span><span class="sxs-lookup"><span data-stu-id="98966-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="98966-129">EF コアを使用、DbContextOptionsBuilder では、その構成を合理化するいくつかの便利な拡張メソッドをサポートします。</span><span class="sxs-lookup"><span data-stu-id="98966-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="98966-130">構成で定義されている接続文字列で、SQL Server データベースを使用する CatalogContext を構成するのには、ConfigureServices に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="98966-131">メモリ内のデータベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="98966-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="98966-132">DbContext の子の種類を作成、EF コアをインストールして、ConfigureServices で構成したが後、は、EF コアを使用する準備ができたらです。</span><span class="sxs-lookup"><span data-stu-id="98966-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="98966-133">必要とする任意のサービスで、DbContext 型のインスタンスを要求する場合と同様、コレクション内だけでは、LINQ を使用して、永続化されたエンティティの操作を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="98966-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="98966-134">EF コアは、格納およびデータを取得する SQL クエリに、LINQ 式に変換する作業を行います。</span><span class="sxs-lookup"><span data-stu-id="98966-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="98966-135">ロガーを構成し、そのレベルが以上に設定ことを確認して EF Core を実行してクエリを表示については、図 8-1 に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="98966-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="98966-136">コンソールに図 8-1 EF コアのログのクエリ</span><span class="sxs-lookup"><span data-stu-id="98966-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="98966-137">フェッチとデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="98966-137">Fetching and Storing Data</span></span>

<span data-ttu-id="98966-138">EF コアからデータを取得するには、は、適切なプロパティにアクセスし、LINQ を使用して結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="98966-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="98966-139">1 つの型から別の結果を変換する投影法を実行するのに LINQ を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="98966-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="98966-140">次の例は、CatalogBrands、名前順で、それぞれの Enabled プロパティでフィルター処理し、SelectListItem 型に投影されてを取得します。</span><span class="sxs-lookup"><span data-stu-id="98966-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="98966-141">上記の例をすぐにクエリを実行するのには、ToListAsync への呼び出しを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="98966-142">それ以外の場合、ステートメントは、IQueryable を割り当てます<SelectListItem>brandItems にこれは実行されません列挙されるまでです。</span><span class="sxs-lookup"><span data-stu-id="98966-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="98966-143">長所と短所メソッドから IQueryable 結果を返すには。</span><span class="sxs-lookup"><span data-stu-id="98966-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="98966-144">これにより、EF コアを構築に変更することもできます、実行時にのみ発生するエラーになり、操作が EF コアが変換できない、クエリに追加された場合にクエリできます。</span><span class="sxs-lookup"><span data-stu-id="98966-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="98966-145">フィルターはすべてをデータ アクセスを実行するメソッドに渡すには一般に安全であるし、戻り値は、メモリ内コレクションのバックアップ (たとえば、一覧<T>)、結果として。</span><span class="sxs-lookup"><span data-stu-id="98966-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="98966-146">EF コアは、永続化ストアからデータをフェッチするエンティティの変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="98966-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="98966-147">保存する変更追跡対象エンティティでは、エンティティのフェッチに使用されたものと同じ DbContext インスタンスであることを確認、DbContext で SaveChanges メソッドを呼び出すだけです。</span><span class="sxs-lookup"><span data-stu-id="98966-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="98966-148">追加して、エンティティの削除は、データベース コマンドを実行する savechanges メソッドの呼び出しを使用して、適切な DbSet プロパティに直接です。</span><span class="sxs-lookup"><span data-stu-id="98966-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="98966-149">次の例では、追加、更新、および永続化ストアからエンティティの削除を示します。</span><span class="sxs-lookup"><span data-stu-id="98966-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="98966-150">EF コアは、同期の両方をサポートし、フェッチして保存するための非同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98966-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="98966-151">Web アプリケーション、ことをお勧め async と await パターンを使用して、非同期のメソッドとデータ アクセス操作の完了を待機中に web サーバーのスレッドがブロックされないようにします。</span><span class="sxs-lookup"><span data-stu-id="98966-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="98966-152">関連するデータのフェッチ</span><span class="sxs-lookup"><span data-stu-id="98966-152">Fetching Related Data</span></span>

<span data-ttu-id="98966-153">EF コアは、エンティティを取得するすべてのデータベースでは、そのエンティティに直接格納されているプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="98966-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="98966-154">関連エンティティのリストなどのナビゲーション プロパティが作成されないとその値に設定がありますは null です。</span><span class="sxs-lookup"><span data-stu-id="98966-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="98966-155">これにより、EF コアをフェッチしていないデータは、必要なよりも多く、すばやく要求を処理および効率的な方法で応答を返す必要がある web アプリケーションに特に重要であります。</span><span class="sxs-lookup"><span data-stu-id="98966-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="98966-156">使用して、エンティティとの関係を含める*一括読み込み*、ように、クエリに含める拡張メソッドを使用して、プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="98966-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="98966-157">複数のリレーションシップを含めることができ、サブ リレーションシップを含めることもできます ThenInclude を使用します。</span><span class="sxs-lookup"><span data-stu-id="98966-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="98966-158">EF コアでは、エンティティの結果セットを取得する 1 つのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="98966-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="98966-159">関連するデータを読み込むための別のオプションは、使用する*明示的な読み込み*です。</span><span class="sxs-lookup"><span data-stu-id="98966-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="98966-160">明示的な読み込みを使用すると、既に取得されているエンティティに追加のデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="98966-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="98966-161">このため、データベースを別の要求には、のでお勧めできませんデータベースの数を最小限に抑える必要があります、web アプリケーションの要求ごとのラウンド トリップされます。</span><span class="sxs-lookup"><span data-stu-id="98966-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="98966-162">*遅延読み込み*機能では、アプリケーションによって参照されているために、関連するデータを自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="98966-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="98966-163">EF Core でサポートされていないとして明示的な読み込みを使用にする必要があります通常無効に web アプリケーション用。</span><span class="sxs-lookup"><span data-stu-id="98966-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="98966-164">回復力のある接続</span><span class="sxs-lookup"><span data-stu-id="98966-164">Resilient Connections</span></span>

<span data-ttu-id="98966-165">SQL データベースなどの外部のリソースがときどき使用できません。</span><span class="sxs-lookup"><span data-stu-id="98966-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="98966-166">一時的な使用不可の場合は、アプリケーションは、例外の発生を回避する再試行ロジックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="98966-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="98966-167">この手法は一般に呼ば*接続の回復*です。</span><span class="sxs-lookup"><span data-stu-id="98966-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="98966-168">実装することができます、[指数バックオフによる独自の再試行](https://docs.microsoft.com/azure/architecture/patterns/retry)しようとして待機時間が指数関数的に増加する再試行されるまで、最大再試行回数に達している手法です。</span><span class="sxs-lookup"><span data-stu-id="98966-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="98966-169">この手法は、クラウド リソースが断続的に使用できなくなることをいくつかの要求のエラーが発生しました、短い期間のファクトを採用します。</span><span class="sxs-lookup"><span data-stu-id="98966-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="98966-170">Azure SQL DB、Entity Framework のコアには、既に内部データベース接続の回復性と再試行ロジックが用意されています。</span><span class="sxs-lookup"><span data-stu-id="98966-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="98966-171">回復力のある EF コア接続する場合は、DbContext 接続ごとに、Entity Framework の実行方法を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="98966-172">たとえば、EF コア接続レベルでは、次のコードは、接続に失敗した場合に再試行回復力のある SQL 接続を有効します。</span><span class="sxs-lookup"><span data-stu-id="98966-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
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
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="98966-173">実行方法と BeginTransaction と複数 DbContexts を使用して明示的なトランザクション</span><span class="sxs-lookup"><span data-stu-id="98966-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="98966-174">EF コア接続では、再試行が有効な場合、EF コアを使用して実行する各操作は、独自の再試行可能な操作になります。</span><span class="sxs-lookup"><span data-stu-id="98966-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="98966-175">一時的なエラーが発生した場合、各クエリおよび SaveChanges に対する各呼び出しが単位として再試行されます。</span><span class="sxs-lookup"><span data-stu-id="98966-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="98966-176">ただし、コードでは、BeginTransaction を使用してトランザクションを開始する場合は、ユニットとして扱われる必要のある操作のグループを定義する — 障害が発生した場合に、トランザクション内のすべてロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="98966-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="98966-177">EF の実行方法 (再試行ポリシー) を使用する場合は、そのトランザクションを実行しようとして、それらに含める複数 DbContexts からいくつかの SaveChanges いる場合、次のような例外が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98966-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="98966-178">System.invalidoperationexception: 構成済みの実行方法 'SqlServerRetryingExecutionStrategy' はユーザーが開始したトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="98966-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="98966-179">'DbContext.Database.CreateExecutionStrategy()' によって返される実行方法を使用して、再試行可能な単位としてトランザクション内のすべての操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="98966-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="98966-180">ソリューションでは、手動で実行する必要があるすべてのものを表すデリゲートを使用して EF の実行方法を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="98966-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="98966-181">一時的な障害が発生した場合、実行方法は、デリゲートをもう一度呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="98966-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="98966-182">次のコードは、このアプローチを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="98966-182">The following code shows how to implement this approach:</span></span>

```csharp
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
```

<span data-ttu-id="98966-183">First DbContext、\_内では、DbContext catalogContext と 2 番目、 \_integrationEventLogService オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="98966-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="98966-184">最後に、複数 DbContexts と EF の実行方法を使用して、コミット操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="98966-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="98966-185">参照: Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="98966-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="98966-186">**EF コア ドキュメント**</span><span class="sxs-lookup"><span data-stu-id="98966-186">**EF Core Docs**</span></span>  
> <span data-ttu-id="98966-187"><https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="98966-187"><https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="98966-188">**関連するデータの EF コア:**</span><span class="sxs-lookup"><span data-stu-id="98966-188">**EF Core: Related Data**</span></span>  
> <span data-ttu-id="98966-189"><https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="98966-189"><https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="98966-190">**ASPNET アプリケーション内のエンティティの遅延読み込みを回避します。**</span><span class="sxs-lookup"><span data-stu-id="98966-190">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <span data-ttu-id="98966-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="98966-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="98966-192">EF コアまたは MICRO-ORM しますか。</span><span class="sxs-lookup"><span data-stu-id="98966-192">EF Core or micro-ORM?</span></span>

<span data-ttu-id="98966-193">EF コアが永続化ストアの管理に最適の大部分はアプリケーションの開発者からのデータベースの詳細をカプセル化中にのみ選択ではありません。</span><span class="sxs-lookup"><span data-stu-id="98966-193">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="98966-194">別の一般的なオープン ソースの代替手段は[Dapper](https://github.com/StackExchange/Dapper)、いわゆる MICRO-ORM です。</span><span class="sxs-lookup"><span data-stu-id="98966-194">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="98966-195">MICRO-ORM は、以下のオブジェクトをデータ構造にマップするためのツールの全機能を備えた、軽量なです。</span><span class="sxs-lookup"><span data-stu-id="98966-195">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="98966-196">Dapper の場合は、完全を基になるカプセル化するクエリを実行してではなく、パフォーマンスの目標の中心の設計は、データを取得および更新使用します。</span><span class="sxs-lookup"><span data-stu-id="98966-196">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="98966-197">Developer から SQL を抽象にしないので、Dapper は「金属に最も近い」であり、開発者は、正確な記述できますクエリに指定されたデータを使用する操作にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="98966-197">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="98966-198">EF コアで提供されます Dapper から分離するためが、またそのパフォーマンスのオーバーヘッドを追加する 2 つの重要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="98966-198">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="98966-199">最初は、SQL に LINQ 式からの変換です。</span><span class="sxs-lookup"><span data-stu-id="98966-199">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="98966-200">これらの変換がキャッシュされるが、それでもオーバーヘッドで最初にそれらを実行します。</span><span class="sxs-lookup"><span data-stu-id="98966-200">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="98966-201">2 つ目は、変更の追跡エンティティ (できるようにする効率的な update ステートメントを生成できます) です。</span><span class="sxs-lookup"><span data-stu-id="98966-201">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="98966-202">この動作は AsNotTracking 拡張機能を使用して、特定のクエリをオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="98966-202">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="98966-203">EF Core では、通常は、非常に効率的ないずれの場合でもまったく問題ないパフォーマンスの観点から SQL クエリも生成されますが、実行するクエリを正確に制御を微調整する必要があるカスタム SQL で渡すことができます (またはストアド プロシージャを実行) EF を使用します。コアすぎます。</span><span class="sxs-lookup"><span data-stu-id="98966-203">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="98966-204">口ひげ静止が EF コアを上回るこの場合はごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="98966-204">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="98966-205">自分の一部のパフォーマンス データが 2016 MSDN の記事 Julie Lerman 表示[Dapper、エンティティ フレームワーク、およびハイブリッド アプリ](https://msdn.microsoft.com/magazine/mt703432.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="98966-205">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="98966-206">データ アクセス方法のさまざまな追加のパフォーマンス ベンチマーク データにあります[口ひげサイト](https://github.com/StackExchange/Dapper)です。</span><span class="sxs-lookup"><span data-stu-id="98966-206">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="98966-207">EF コアから Dapper の構文がどのように変化を表示するには、項目の一覧を取得するため、同じメソッドの 2 つのバージョンを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="98966-207">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="98966-208">Dapper でより複雑なオブジェクト グラフを作成する必要がある場合は、(EF コアの場合とは、インクルードを追加) ではなく自分で関連付けられているクエリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-208">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="98966-209">これは、さまざまな構文では、個々 の行を複数のマップされたオブジェクトにマップできるマルチ マッピングと呼ばれる機能を含むを通じてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="98966-209">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="98966-210">たとえば、ユーザーの種類のプロパティの所有者で Post クラスを指定するには、次の SQL と返されますのすべての必要なデータ。</span><span class="sxs-lookup"><span data-stu-id="98966-210">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="98966-211">返される各行には、ユーザーとポストの両方のデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="98966-211">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="98966-212">ユーザー データは、その所有者のプロパティを使用して Post データにアタッチする必要があります、ため、次の関数は使用されます。</span><span class="sxs-lookup"><span data-stu-id="98966-212">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="98966-213">完全なコード リストの Owner プロパティを関連付けられたユーザー データが設定されると投稿のコレクションを返すには次のようになります。</span><span class="sxs-lookup"><span data-stu-id="98966-213">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="98966-214">開発者は、そのデータの格納方法の詳細について以下のカプセル化を提供するため Dapper が必要です、効率的にクエリを実行して、それをフェッチするコードを書き込む方法です。</span><span class="sxs-lookup"><span data-stu-id="98966-214">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="98966-215">新しい移行 (EF コア、別の機能) を作成や、DbContext で 1 つの場所のマッピング情報を更新するだけではなく、モデルが変更されたときに、影響を受けるすべてのクエリを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-215">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="98966-216">これらのクエリがコンパイル時保証ないであるため、モデルまたはエラーを迅速に検出が困難なには、データベースに変更に応答実行時に中断する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="98966-216">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="98966-217">これらのトレードオフと引き換えに Dapper は非常に高速パフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="98966-217">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="98966-218">ほとんどのアプリケーションで、ほぼすべてのアプリケーションのほとんどの部分に対しては、EF コアは、許容されるパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="98966-218">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="98966-219">したがって、その開発者の生産性は、そのパフォーマンスのオーバーヘッドを上回る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="98966-219">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="98966-220">キャッシュから利点を活用できるクエリの実際のクエリのみ実行できます比較的小さいため、時間の割合を小さなクエリのパフォーマンスの違い問題になりません。</span><span class="sxs-lookup"><span data-stu-id="98966-220">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="98966-221">SQL または NoSQL</span><span class="sxs-lookup"><span data-stu-id="98966-221">SQL or NoSQL</span></span>

<span data-ttu-id="98966-222">従来は、SQL Server などのリレーショナル データベースに永続的なデータ記憶域は、marketplace が左右されますが、使用可能な唯一のソリューションではありません。</span><span class="sxs-lookup"><span data-stu-id="98966-222">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="98966-223">などの NoSQL データベース[MongoDB](https://www.mongodb.com/what-is-mongodb)オブジェクトを格納するためのさまざまなアプローチを提供します。</span><span class="sxs-lookup"><span data-stu-id="98966-223">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="98966-224">オブジェクトをテーブルと行にマップするのではなく別のオプションは、オブジェクト グラフ全体をシリアル化して、結果を格納するです。</span><span class="sxs-lookup"><span data-stu-id="98966-224">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="98966-225">この方法のメリットは、簡潔さとパフォーマンスに少なくとも最初です。</span><span class="sxs-lookup"><span data-stu-id="98966-225">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="98966-226">更新プログラムおよび可能性がありますので、オブジェクトが最後に変更された行をデータベースから取得し、リレーションシップを持つ多数のテーブルにオブジェクトを分解するよりもキーを持つ 1 つのシリアル化されたオブジェクトを格納するは確かにシンプルです。</span><span class="sxs-lookup"><span data-stu-id="98966-226">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="98966-227">同様に、フェッチして、キー ベースのストアから 1 つのオブジェクトを逆シリアル化は通常より迅速かつ複雑な結合または完全に同じリレーショナル データベースからオブジェクトを作成するために必要な複数のデータベース クエリよりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="98966-227">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="98966-228">ロックやトランザクションまたは固定スキーマがないことも、NoSQL データベース非常に大規模なデータセットをサポートする多数のマシン間でのスケーリングに非常に適したします。</span><span class="sxs-lookup"><span data-stu-id="98966-228">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="98966-229">その一方で、NoSQL データベース (ように、通常と呼ばれる) があるそれぞれの欠点です。</span><span class="sxs-lookup"><span data-stu-id="98966-229">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="98966-230">リレーショナル データベースでは、整合性を適用し、データの重複を避けるために正規化を使用します。</span><span class="sxs-lookup"><span data-stu-id="98966-230">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="98966-231">これにより、データベースの合計サイズが削減され、共有データへの更新プログラムがすぐに、データベース全体で使用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="98966-231">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="98966-232">リレーショナル データベース自体を更新することがなく、更新プログラムからアドレス レコードと効果的な国の名前が変更された場合になるよう、アドレス テーブルは ID を使用して国テーブルを参照する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="98966-232">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="98966-233">ただし、NoSQL database でのアドレスおよびその関連付けられている国可能性がありますシリアル化する多くの保存されているオブジェクトの一部として。</span><span class="sxs-lookup"><span data-stu-id="98966-233">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="98966-234">国の名前に更新プログラムは、1 つの行ではなく、更新するすべてのオブジェクトを必要となります。</span><span class="sxs-lookup"><span data-stu-id="98966-234">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="98966-235">リレーショナル データベースでは、外部キーのようにルールを適用することでもリレーショナル整合性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="98966-235">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="98966-236">通常、NoSQL データベースでは、そのデータには、このような制約は用意されません。</span><span class="sxs-lookup"><span data-stu-id="98966-236">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="98966-237">別の複雑な NoSQL データベースを扱う必要がありますが、バージョン管理します。</span><span class="sxs-lookup"><span data-stu-id="98966-237">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="98966-238">オブジェクトのプロパティを変更するときに、格納されていた過去のバージョンから逆シリアル化できません可能性があります。</span><span class="sxs-lookup"><span data-stu-id="98966-238">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="98966-239">したがって、オブジェクトのシリアル化された (以前の) バージョンがすべての既存のオブジェクトは、新しいスキーマに準拠するように更新しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="98966-239">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="98966-240">これは概念的には、リレーショナル データベースから別ではなく、スキーマの変更も更新スクリプトを必要とまたは更新プログラムをマッピングします。</span><span class="sxs-lookup"><span data-stu-id="98966-240">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="98966-241">ただし、変更する必要があるエントリの数は多くの場合、ほとんどのデータの複数の重複があるため NoSQL のアプローチで大きくします。</span><span class="sxs-lookup"><span data-stu-id="98966-241">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="98966-242">通常何かの固定スキーマのリレーショナル データベースがサポートされていない場合は、NoSQL データベース オブジェクトの複数のバージョンを格納することも可能です。</span><span class="sxs-lookup"><span data-stu-id="98966-242">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="98966-243">ただし、ここでは、アプリケーション コードは以前のバージョンの複雑さを追加するオブジェクトの存在を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-243">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="98966-244">通常 NoSQL データベースが適用されない[ACID](http://en.wikipedia.org/wiki/ACID)、リレーショナル データベースでパフォーマンスとスケーラビリティの両方の利点があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="98966-244">NoSQL databases typically do not enforce [ACID](http://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="98966-245">これらは、大量のデータセットとは正規化されたテーブルの構造内のストレージに適していないオブジェクトに最適です。</span><span class="sxs-lookup"><span data-stu-id="98966-245">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="98966-246">理由 1 つのアプリケーションを利用できません両方リレーショナルとを使用して各は、最適な NoSQL データベースが適しています理由はありません。</span><span class="sxs-lookup"><span data-stu-id="98966-246">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="98966-247">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="98966-247">Azure DocumentDB</span></span>

<span data-ttu-id="98966-248">Azure DocumentDB は、完全に管理された NoSQL データベース サービス スキーマのないデータのクラウド ベースの記憶域を提供します。</span><span class="sxs-lookup"><span data-stu-id="98966-248">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="98966-249">DocumentDB は、高速で予測可能なパフォーマンス、高可用性、柔軟なスケーリング、およびグローバル配布用に作成されています。</span><span class="sxs-lookup"><span data-stu-id="98966-249">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="98966-250">NoSQL database あるにもかかわらず、開発者は、JSON データの豊富な使い慣れた SQL のクエリ機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="98966-250">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="98966-251">DocumentDB のすべてのリソースは、JSON ドキュメントとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="98966-251">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="98966-252">リソースとして管理*項目*する、メタデータを含むドキュメントと*フィード*項目のコレクションであります。</span><span class="sxs-lookup"><span data-stu-id="98966-252">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="98966-253">図 8-2 は、別の DocumentDB リソース間の関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="98966-253">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![DocumentDB では、JSON の NoSQL データベース リソース間の階層関係](./media/image8-2.png)

<span data-ttu-id="98966-255">**図 8-2 です。**</span><span class="sxs-lookup"><span data-stu-id="98966-255">**Figure 8-2.**</span></span> <span data-ttu-id="98966-256">DocumentDB リソース組織。</span><span class="sxs-lookup"><span data-stu-id="98966-256">DocumentDB resource organization.</span></span>

<span data-ttu-id="98966-257">DocumentDB クエリ言語は、JSON ドキュメントを照会するための単純かつ強力なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="98966-257">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="98966-258">言語は ANSI SQL の文法のサブセットをサポートし、JavaScript オブジェクト、配列、オブジェクトの構築、および関数の呼び出しの緊密な統合を追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-258">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="98966-259">**参照: DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="98966-259">**References – DocumentDB**</span></span>

-   <span data-ttu-id="98966-260">DocumentDB Introduction\\</span><span class="sxs-lookup"><span data-stu-id="98966-260">DocumentDB Introduction\\</span></span>
    <span data-ttu-id="98966-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span><span class="sxs-lookup"><span data-stu-id="98966-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="98966-262">その他の持続性オプション</span><span class="sxs-lookup"><span data-stu-id="98966-262">Other Persistence Options</span></span>

<span data-ttu-id="98966-263">リレーショナルへの追加と NoSQL 記憶域オプションで ASP.NET Core アプリケーションは、スケーラブルなクラウド ベースの方法でさまざまなデータ形式とファイルを保存するのに Azure ストレージを使用できます。</span><span class="sxs-lookup"><span data-stu-id="98966-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="98966-264">Azure ストレージは非常にスケーラブルな少量のデータと、アプリケーションで必要な場合は、数百またはテラバイトを格納する最大の小数点以下桁数を格納するアウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="98966-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="98966-265">Azure ストレージには、次の 4 つの種類のデータがサポートしています。</span><span class="sxs-lookup"><span data-stu-id="98966-265">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="98966-266">非構造化テキストまたはオブジェクトの格納とも呼びますバイナリのストレージの blob ストレージです。</span><span class="sxs-lookup"><span data-stu-id="98966-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="98966-267">テーブル ストレージ構造化されたデータセットの場合、行キーを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="98966-267">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="98966-268">信頼性の高いキュー ベースのメッセージング キューの記憶域。</span><span class="sxs-lookup"><span data-stu-id="98966-268">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="98966-269">Azure の仮想マシンと内部設置型アプリケーション間でファイル共有にファイル記憶域。</span><span class="sxs-lookup"><span data-stu-id="98966-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="98966-270">**– Azure ストレージの参照**</span><span class="sxs-lookup"><span data-stu-id="98966-270">**References – Azure Storage**</span></span>

-   <span data-ttu-id="98966-271">Azure ストレージ Introduction\\</span><span class="sxs-lookup"><span data-stu-id="98966-271">Azure Storage Introduction\\</span></span>
    <span data-ttu-id="98966-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="98966-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="98966-273">キャッシュ</span><span class="sxs-lookup"><span data-stu-id="98966-273">Caching</span></span>

<span data-ttu-id="98966-274">Web アプリケーションで、各 web 要求をできるだけ短時間で完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-274">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="98966-275">これを実現する方法の 1 つでは、サーバーが、要求を完了に加える必要が外部の呼び出しの数を制限します。</span><span class="sxs-lookup"><span data-stu-id="98966-275">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="98966-276">キャッシュは、サーバー上のデータのコピーを保存する (または別のデータを格納されているデータのソースよりも簡単にクエリの詳細)。</span><span class="sxs-lookup"><span data-stu-id="98966-276">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="98966-277">Web アプリケーション、および特に非 SPA 従来の web アプリケーションは、すべての要求による全体のユーザー インターフェイスを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="98966-277">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="98966-278">これには、1 人のユーザーの要求から繰り返し、次に同じデータベースをクエリの多くを行う頻繁に行われます。</span><span class="sxs-lookup"><span data-stu-id="98966-278">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="98966-279">ほとんどの場合、このデータが変更されたまれに、データベースから常に要求したときに理由はほとんどがあるためです。</span><span class="sxs-lookup"><span data-stu-id="98966-279">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="98966-280">ASP.NET Core サポート全体のページ、およびデータのキャッシュをキャッシュに、応答のキャッシュをより詳細なキャッシュ動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="98966-280">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="98966-281">キャッシュを実装するときにすることが重要に関心の分離を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="98966-281">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="98966-282">または、ユーザー インターフェイスで、データ アクセス ロジックでのキャッシュ ロジックを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="98966-282">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="98966-283">代わりに、独自のクラスでのキャッシュをカプセル化し、その動作を管理する構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="98966-283">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="98966-284">これは、開く/解決済みと 1 つの役割の基本原則に従いますがやすくしたり拡張時に、アプリケーションでキャッシュを使用する方法を管理するためです。</span><span class="sxs-lookup"><span data-stu-id="98966-284">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="98966-285">ASP.NET Core 応答のキャッシュ</span><span class="sxs-lookup"><span data-stu-id="98966-285">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="98966-286">ASP.NET Core では、応答のキャッシュの 2 つのレベルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="98966-286">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="98966-287">最初のレベルは、キャッシュ サーバーで、何もしませんが、クライアントと応答をキャッシュするプロキシ サーバーを指示する HTTP ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-287">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="98966-288">これは、個々 のコント ローラーやアクションに ResponseCache 属性を追加することによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="98966-288">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="98966-289">応答のキャッシュ ミドルウェアは、一連のカスタマイズ可能な条件に基づいて応答を自動的にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="98966-289">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="98966-290">既定では、GET または HEAD メソッドを使用して要求のみ 200 (OK) 応答がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="98966-290">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="98966-291">さらに、要求がキャッシュ制御の応答をいる必要があります: パブリック ヘッダーは、承認または Set-cookie ヘッダーを含むことはできません。</span><span class="sxs-lookup"><span data-stu-id="98966-291">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="98966-292">参照してください、[応答のミドルウェアのキャッシュで使用されるキャッシュの条件の完全な一覧](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching)です。</span><span class="sxs-lookup"><span data-stu-id="98966-292">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="98966-293">データ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="98966-293">Data Caching</span></span>

<span data-ttu-id="98966-294">ではなく (またはそれらに加えて) 完全な web 応答のキャッシュ、個々 のデータのクエリの結果をキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="98966-294">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="98966-295">これは、web サーバー上のメモリ キャッシュの使用または使用[分散キャッシュ](https://docs.microsoft.com/aspnet/core/performance/caching/distributed)です。</span><span class="sxs-lookup"><span data-stu-id="98966-295">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="98966-296">このセクションでは、メモリ キャッシュに実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="98966-296">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="98966-297">メモリのサポートを追加 (または分散) ConfigureServices でのキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="98966-297">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="98966-298">同様に、Microsoft.Extensions.Caching.Memory NuGet パッケージを追加することを確認します。</span><span class="sxs-lookup"><span data-stu-id="98966-298">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="98966-299">サービスを追加したらを要求する IMemoryCache 依存関係の挿入を使用して、キャッシュにアクセスする必要がある場所にします。</span><span class="sxs-lookup"><span data-stu-id="98966-299">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="98966-300">この例では、CachedCatalogService がへのアクセス制御 (または動作を追加して) ICatalogService の代替実装を提供することで、プロキシ (またはデコレータ) のデザイン パターンを使用して基になる CatalogService 実装します。</span><span class="sxs-lookup"><span data-stu-id="98966-300">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="98966-301">サービスのキャッシュされたバージョンを使用する許可 CatalogService のコンス トラクターに必要なのインスタンスを取得するサービスを許可するアプリケーションを構成するのには、ConfigureServices で、次を追加します。</span><span class="sxs-lookup"><span data-stu-id="98966-301">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="98966-302">これで、カタログ データをフェッチするデータベースの呼び出しはできるだけのすべての要求ではなく、1 分ごと 1 回です。</span><span class="sxs-lookup"><span data-stu-id="98966-302">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="98966-303">によっては、サイトにトラフィックには、データベース、および現在このサービスによって公開されているクエリの 3 つすべてが依存するホーム ページの平均ページ読み込み時間に加えられたクエリの数に非常に大きく影響するこれがあります。</span><span class="sxs-lookup"><span data-stu-id="98966-303">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="98966-304">キャッシュが実装された場合に発生する問題は*古いデータ*: ソースが最新のバージョンで変更されたデータがキャッシュに保持する、します。</span><span class="sxs-lookup"><span data-stu-id="98966-304">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="98966-305">この問題を緩和する簡単な方法では、ビジー状態のアプリケーションのデータがキャッシュされる長さを拡張する制限の追加利点は小規模のキャッシュ期間を使用します。</span><span class="sxs-lookup"><span data-stu-id="98966-305">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="98966-306">たとえば、1 つのデータベース クエリを実行するページが 1 秒あたり 10 回要求されたとします。</span><span class="sxs-lookup"><span data-stu-id="98966-306">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="98966-307">このページは、1 分間キャッシュは、1 分あたり 1、99.8% の削減に 600 からドロップに対するデータベース クエリの数になります。</span><span class="sxs-lookup"><span data-stu-id="98966-307">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="98966-308">代わりにキャッシュの存続期間は 1 時間に加えられた場合、全体的な減少が 99.997% であっても今すぐ古いデータの尤度と潜在的な有効期間はどちらも大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="98966-308">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="98966-309">別の方法が含まれているデータが更新されたときに、キャッシュ エントリを能動的に削除を開始します。</span><span class="sxs-lookup"><span data-stu-id="98966-309">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="98966-310">そのキーがわかっている場合、任意の個々 のエントリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="98966-310">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="98966-311">アプリケーションでは、キャッシュされたエントリを更新するための機能を公開する場合は、更新プログラムを実行するコードで、対応するキャッシュ エントリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="98966-311">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="98966-312">場合によって特定のデータのセットに依存している多くの異なるエントリがあります。</span><span class="sxs-lookup"><span data-stu-id="98966-312">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="98966-313">その場合は、だということ、CancellationChangeToken を使用して、キャッシュ エントリ間の依存関係を作成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="98966-313">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="98966-314">CancellationChangeToken とできます期限切れにする複数のキャッシュ エントリを一度にトークンをキャンセルしています。</span><span class="sxs-lookup"><span data-stu-id="98966-314">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
<span data-ttu-id="98966-315">[前](develop-asp-net-core-mvc-apps.md) [次へ] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="98966-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>

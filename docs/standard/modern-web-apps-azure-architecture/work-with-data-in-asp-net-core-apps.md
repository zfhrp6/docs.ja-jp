---
title: ASP.NET Core アプリでのデータの操作
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | asp でのデータの操作
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7d160d23808832ff6456e5c95f6e5ed5f4d44fa5
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="2da5d-103">ASP.NET Core アプリでのデータの操作</span><span class="sxs-lookup"><span data-stu-id="2da5d-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="2da5d-104">"データは貴重なものであり、システム自体よりも長く存在します。"</span><span class="sxs-lookup"><span data-stu-id="2da5d-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="2da5d-105">Tim Berners-lee</span><span class="sxs-lookup"><span data-stu-id="2da5d-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="2da5d-106">まとめ</span><span class="sxs-lookup"><span data-stu-id="2da5d-106">Summary</span></span>

<span data-ttu-id="2da5d-107">データ アクセスは、ほぼすべてのソフトウェア アプリケーションの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="2da5d-108">ASP.NET Core は、Entity Framework Core (および Entity Framework 6 も) を含む、さまざまなデータ アクセス オプションをサポートし、どの .NET データ アクセス フレームワークでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="2da5d-109">使用するデータ アクセス フレームワークの選択は、アプリケーションのニーズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="2da5d-110">ApplicationCore および UI プロジェクトからのこれらの選択を抽象化し、インフラストラクチャに実装の詳細をカプセル化することは、疎結合のテスト可能なソフトウェアの生成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="2da5d-111">Entity Framework Core (リレーショナル データベース用)</span><span class="sxs-lookup"><span data-stu-id="2da5d-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="2da5d-112">リレーショナル データを操作する必要がある新しい ASP.NET Core アプリケーションを作成する場合、Entity Framework Core (EF Core) を使用して、アプリケーションからそのデータにアクセスすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2da5d-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="2da5d-113">EF Core はオブジェクト リレーショナル マッパー (O/RM) であり、.NET 開発者がデータ ソースのオブジェクトを保持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2da5d-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="2da5d-114">これにより、通常は開発者が記述する必要があるほとんどのデータ アクセス コードが不要になります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="2da5d-115">ASP.NET Core と同様、EF Core は、モジュラー型クロスプラットフォーム アプリケーションをサポートするために、完全に書き換えられました。</span><span class="sxs-lookup"><span data-stu-id="2da5d-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="2da5d-116">NuGet パッケージとしてご利用のアプリケーションに追加し、Startup で構成し、必要に応じて依存関係の挿入を介して要求します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="2da5d-117">SQL Server データベースで EE Core を使用するには、次の dotnet CLI コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="2da5d-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="2da5d-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="2da5d-119">テストのために、InMemory データ ソースのサポートを追加するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="2da5d-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="2da5d-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="2da5d-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="2da5d-121">The DbContext</span></span>

<span data-ttu-id="2da5d-122">EF Core を操作するには、DbContext のサブクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="2da5d-123">このクラスでは、ご利用のアプリケーションで操作するエンティティのコレクションを表すプロパティを保持します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="2da5d-124">eShopOnWeb サンプルには、アイテム、ブランド、型のコレクションと共に CatalogContext が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="2da5d-125">DbContext には、DbContextOptions を受け入れるコンストラクターが必要です。また、この引数を基本の DbContext コンストラクターに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="2da5d-126">ご利用のアプリケーションに DbContext が 1 つだけ存在する場合は、DbContextOptions のインスタンスを渡すことができますが、複数存在する場合は、ジェネリックの DbContextOptions<T> 型を使用して、ジェネリック パラメーターとして DbContext 型を渡す必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2da5d-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="2da5d-127">EF Core の構成</span><span class="sxs-lookup"><span data-stu-id="2da5d-127">Configuring EF Core</span></span>

<span data-ttu-id="2da5d-128">ASP.NET Core アプリケーションでは、通常、ConfigureServices メソッドで EF コアを構成します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="2da5d-129">EF Core では、構成を効率化するいくつかの便利な拡張メソッドをサポートする、DbContextOptionsBuilder を使用します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="2da5d-130">Configuration で定義されている接続文字列で SQL Server データベースを使用するように CatalogContext を構成するには、次のコードを ConfigureServices に追加します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="2da5d-131">メモリ内データベースを使用するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2da5d-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="2da5d-132">EF Core をインストールして、DbContext の子の型を作成し、それを ConfigureServices で構成したら、EE Core を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="2da5d-133">DbContext 型のインスタンスを必要とする任意のサービスで要求し、単にコレクション内にある場合と同じように、LINQ を使用して永続化されたエンティティの操作を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="2da5d-134">EF Core では、ご利用のデータを格納して取得するために、LINQ 式を SQL クエリに変換する作業を行います。</span><span class="sxs-lookup"><span data-stu-id="2da5d-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="2da5d-135">図 8-1 に示すように、ロガーを構成し、そのレベルが少なくとも Information に設定されていることを確認することで、EF Core で実行されるクエリを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="2da5d-136">図 8-1 コンソールへの EE Core クエリのログ記録</span><span class="sxs-lookup"><span data-stu-id="2da5d-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="2da5d-137">データのフェッチと格納</span><span class="sxs-lookup"><span data-stu-id="2da5d-137">Fetching and Storing Data</span></span>

<span data-ttu-id="2da5d-138">EF Core からデータを取得するには、適切なプロパティにアクセスし、LINQ を使用して結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="2da5d-139">また、LINQ を使用して射影を実行し、1 つの型から別の型に結果を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="2da5d-140">次の例では、CatalogBrands を取得します。ここでは、名前で並べ替え、Enabled プロパティでフィルター処理し、SelectListItem 型に射影します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="2da5d-141">上記の例では、クエリをすぐに実行するために、ToListAsync への呼び出しを追加することが重要です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="2da5d-142">それ以外の場合、ステートメントは IQueryable<SelectListItem> を brandItems に割り当て、列挙されるまで実行されません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="2da5d-143">メソッドから IQueryable 結果を返すことには長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="2da5d-144">EF Core で構築されるクエリをさらに変更できますが、EF Core で変換できないクエリに操作が追加された場合、実行時にのみ発生するエラーが発生する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="2da5d-145">データ アクセスを実行するメソッドにすべてのフィルターを渡して、結果としてメモリ内コレクション (List<T> など) を戻す方が一般的には安全です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="2da5d-146">EF Core は、永続化からフェッチするエンティティの変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="2da5d-147">追跡対象エンティティの変更を保存するには、DbContext で SaveChanges メソッドを呼び出すだけです。これで、エンティティのフェッチに使用されたものと同じ DbContext インスタンスであることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="2da5d-148">エンティティの追加と削除は適切な DbSet プロパティで直接行います。この場合も、データベース コマンドを実行するために SaveChanges を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="2da5d-149">次の例では、永続化のエンティティの追加、更新、および削除を示します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="2da5d-150">EF Core では、フェッチおよび保存のための同期と非同期の両方のメソッドがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="2da5d-151">Web アプリケーションでは、非同期メソッドで async/await パターンを使用することをお勧めします。これにより、データ アクセス操作が完了するのを待機している間に、Web サーバーのスレッドがブロックされなくなります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="2da5d-152">関連データのフェッチ</span><span class="sxs-lookup"><span data-stu-id="2da5d-152">Fetching Related Data</span></span>

<span data-ttu-id="2da5d-153">EF Core は、エンティティの取得時に、データベースのそのエンティティを直接格納されているすべてのプロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="2da5d-154">関連エンティティのリストなどの、ナビゲーション プロパティは設定されず、その値が null に設定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="2da5d-155">これにより、EF Core は必要以上のデータをフェッチしなくなります。これは、効率的な方法ですばやく要求を処理し、応答を返す必要がある、Web アプリケーションの場合に特に重要です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="2da5d-156">*一括読み込み*を使用して、エンティティとのリレーションシップを含めるには、次のように、クエリで Include 拡張メソッドを使用してプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="2da5d-157">複数のリレーションシップを含めることができます。また、ThenInclude を使用して、サブリレーションシップを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="2da5d-158">EF Core は単一のクエリを実行して、エンティティの結果セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="2da5d-159">関連データを読み込むために、*明示的読み込み*を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="2da5d-160">明示的読み込みを使用すれば、既に取得されているエンティティに追加データを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="2da5d-161">これにはデータベースへの個別の要求が必要になるため、要求ごとに行われるデータベース ラウンド トリップの数を最小限に抑える必要がある、Web アプリケーションではお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="2da5d-162">*遅延読み込み*は、アプリケーションでの参照時に関連データを自動的に読み込む機能です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="2da5d-163">現在、これは EF Core ではサポートされていませんが、明示的読み込みの場合と同様に、Web アプリケーションでは通常、無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="2da5d-164">回復力のある接続</span><span class="sxs-lookup"><span data-stu-id="2da5d-164">Resilient Connections</span></span>

<span data-ttu-id="2da5d-165">SQL データベースなどの外部リソースが使用できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="2da5d-166">一時的に使用できなくなった場合、アプリケーションは再試行ロジックを使用して、例外の発生を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="2da5d-167">この手法は一般的に*接続の復元性*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="2da5d-168">[指数バックオフを含む独自の再試行](https://docs.microsoft.com/azure/architecture/patterns/retry)手法は、最大再試行回数に達するまで、指数関数的に増加する待機時間で再試行することで実装できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="2da5d-169">この手法を使用すると、クラウド リソースが短時間、断続的に使用できなくなる可能性があり、その結果、一部の要求が失敗します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="2da5d-170">Azure SQL DB の場合、Entity Framework Core に内部データベース接続の復元機能と再試行ロジックが既に用意されています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="2da5d-171">ただし、回復力のある EF Core 接続を使用する場合は、各 DbContext 接続に対して Entity Framework 実行戦略を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="2da5d-172">たとえば、EF Core 接続レベルで次のコードを実行すると、接続が失敗した場合に再試行される回復力のある SQL 接続が有効になります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="2da5d-173">BeginTransaction と複数の DbContext を使用した実行戦略と明示的なトランザクション</span><span class="sxs-lookup"><span data-stu-id="2da5d-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="2da5d-174">EF Core 接続で再試行を有効にすると、EF Core を使用して実行する各操作は、独自の再試行可能な操作になります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="2da5d-175">一時的なエラーが発生した場合、SaveChanges への各クエリと各呼び出しは 1 つのユニットとして再試行されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="2da5d-176">一方、BeginTransaction を使用してトランザクションを開始するコードの場合、1 ユニットとして扱う必要のある独自の操作グループを定義しています。エラーが発生した場合、トランザクション内のすべてがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="2da5d-177">EF 実行戦略 (再試行ポリシー) を使用し、複数の DbContext からの SaveChanges をいくつかトランザクションに含める場合、そのトランザクションを実行しようとすると、次のような例外が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="2da5d-178">System.InvalidOperationException: 構成された実行戦略 'SqlServerRetryingExecutionStrategy' は、ユーザーが開始したトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="2da5d-179">'DbContext.Database.CreateExecutionStrategy()' から返された実行戦略を使用して、再試行可能なユニットとしてトランザクション内のすべての操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="2da5d-180">この解決策では、実行する必要があるすべてを表すデリゲートを使用して EF 実行戦略を手動で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="2da5d-181">一時的なエラーが発生した場合、実行戦略によってデリゲートが再び呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="2da5d-182">次のコードは、この方法を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-182">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="2da5d-183">最初の DbContext は \_catalogContext で、2 つ目の DbContext は \_integrationEventLogService オブジェクト内にあります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="2da5d-184">最後に、Commit アクションが、複数の DbContext で EF 実行戦略を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="2da5d-185">参照 – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="2da5d-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="2da5d-186">**EF Core ドキュメント**</span><span class="sxs-lookup"><span data-stu-id="2da5d-186">**EF Core Docs**</span></span>  
> <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="2da5d-187">**EF Core: 関連データ**</span><span class="sxs-lookup"><span data-stu-id="2da5d-187">**EF Core: Related Data**</span></span>  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="2da5d-188">**ASPNET アプリケーションでのエンティティの遅延読み込みを回避する**</span><span class="sxs-lookup"><span data-stu-id="2da5d-188">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="2da5d-189">EF Core または micro-ORM の選択</span><span class="sxs-lookup"><span data-stu-id="2da5d-189">EF Core or micro-ORM?</span></span>

<span data-ttu-id="2da5d-190">永続化を管理する場合は EF Core を選択することをお勧めしますが、アプリケーション開発者からのデータベースの詳細をカプセル化する場合はこれ以外も選択できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-190">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="2da5d-191">[Dapper](https://github.com/StackExchange/Dapper) (いわゆる micro-ORM) という一般的なオープン ソースも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-191">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="2da5d-192">micro-ORM はデータ構造にオブジェクトをマップするための軽量なツールであり、すべての機能が備わっているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-192">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="2da5d-193">Dapper の場合、その設計目標は、データの取得と更新に使用される基になるクエリの完全なカプセル化ではなく、パフォーマンスに重点を置くことです。</span><span class="sxs-lookup"><span data-stu-id="2da5d-193">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="2da5d-194">開発者からの SQL が抽象化されないため、Dapper は "機械により近い" ものであり、開発者は特定のデータ アクセス操作で使用する正確なクエリを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-194">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="2da5d-195">EF Core では 2 つの重要な機能が提供されます。これらは Dapper とは異なり、パフォーマンスのオーバーヘッドも増えます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-195">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="2da5d-196">1 つ目は、LINQ 式から SQL への変換です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-196">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="2da5d-197">これらの変換はキャッシュされますが、それでも最初の実行時にオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-197">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="2da5d-198">2 つ目は、エンティティの変更追跡です (効率的な更新ステートメントを生成できます)。</span><span class="sxs-lookup"><span data-stu-id="2da5d-198">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="2da5d-199">AsNotTracking 拡張機能を使用して、この動作を特定のクエリに対してオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-199">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="2da5d-200">また、EF Core は、通常は非常に効率的で、パフォーマンスの観点から完全に受け入れ可能である場合に SQL クエリを生成します。ただし、実行する正確なクエリを微調整する必要がある場合は、EF Core を使用して、カスタム SQL を渡す (またはストアド プロシージャを実行する) こともできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-200">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="2da5d-201">この場合も、Dapper はほんのわずかですが EE Core より優れています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-201">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="2da5d-202">Julie Lerman は、2016 年 5 月の MSDN 記事「[Dapper、Entity Framework、およびハイブリッド アプリ](https://msdn.microsoft.com/magazine/mt703432.aspx)」で一部のパフォーマンス データを提供しています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-202">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="2da5d-203">さまざまなデータ アクセス方法の追加のパフォーマンス ベンチマーク データについては、[Dapper サイト](https://github.com/StackExchange/Dapper)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2da5d-203">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="2da5d-204">EF Core と Dapper との構文の違いを確認するために、アイテム リストを取得する同じ方法の次の 2 つのバージョンについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-204">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="2da5d-205">Dapper でより複雑なオブジェクト グラフを作成する必要がある場合は、(EF Core の場合と同じように Include を追加するのではなく) 関連付けられているクエリを自分で記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-205">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="2da5d-206">これは、複数のマップされたオブジェクトに個々の行をマップできる、マルチ マッピングという機能を含む、さまざまな構文を通じてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-206">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="2da5d-207">たとえば、User という種類の Owner プロパティを指定した Post クラスの場合、次の SQL では必要なデータがすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-207">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="2da5d-208">返された各行には、User と Post の両方のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-208">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="2da5d-209">User データを Owner プロパティを使用して Post データにアタッチする必要があるため、次の関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-209">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="2da5d-210">関連付けられているユーザー データが設定された Owner プロパティを使用してポストのコレクションを返すための完全なコード リストは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-210">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="2da5d-211">あまり優れたカプセル化は提供されないため、Dapper では、開発者がデータの格納方法と、データを効率的にクエリし、さらにコードを記述してフェッチする方法の詳細を把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-211">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="2da5d-212">モデルが変更された場合、単に新しい移行を作成したり (EE Core の別の機能)、DbContext の 1 つの場所でマッピング情報を更新するのではなく、影響を受けるすべてのクエリを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-212">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="2da5d-213">これらのクエリではコンパイル時間が保証されないため、モデルやデータベースの変更に応じて実行時に中断し、エラーの迅速な検出がより困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-213">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="2da5d-214">これらのトレードオフと引き換えに、Dapper では非常に高速なパフォーマンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-214">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="2da5d-215">ほとんどのアプリケーション、およびほぼすべてのアプリケーションのほとんどの部分に対して、EE Core は許容可能なパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-215">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="2da5d-216">したがって、その開発者の生産性の利点が、そのパフォーマンスのオーバーヘッドを上回る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-216">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="2da5d-217">キャッシュから利点を得られるクエリの場合、実際のクエリはごくわずかな時間にのみ実行され、比較的小さなクエリ パフォーマンスの違いが問題になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-217">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="2da5d-218">SQL または NoSQL</span><span class="sxs-lookup"><span data-stu-id="2da5d-218">SQL or NoSQL</span></span>

<span data-ttu-id="2da5d-219">従来、SQL Server などのリレーショナル データベースが永続的なデータ記憶域のマーケットプレースの多くを占めますが、使用可能な唯一のソリューションではありません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-219">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="2da5d-220">[MongoDB](https://www.mongodb.com/what-is-mongodb) などの NoSQL データベースでは、オブジェクトを格納するさまざまな方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-220">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="2da5d-221">オブジェクトをテーブルと行にマップするのではなく、オブジェクト グラフ全体をシリアル化して、結果を格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-221">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="2da5d-222">この方法の利点は、少なくとも最初は単純さとパフォーマンスとなります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-222">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="2da5d-223">オブジェクトがデータベースから最後に取得されてから変更された可能性のある、リレーションシップ、更新プログラム、および行を持つ多くのテーブルにオブジェクトを分解するよりも、キーを持つ単一のシリアル化されたオブジェクトを格納する方が確実に簡単です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-223">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="2da5d-224">同様に、キーベースのストアから単一のオブジェクトをフェッチして逆シリアル化することは、リレーショナル データベースから同じオブジェクトを完全に構成するために必要な複雑な結合や複数のデータベース クエリよりも通常ははるかに速くて簡単です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-224">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="2da5d-225">また、ロックやトランザクションあるいは固定スキーマがないため、NoSQL データベースは多くのコンピューターでのスケーリングに非常に適しており、非常に大規模なデータセットをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-225">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="2da5d-226">その一方で、NoSQL データベース (通常は呼び出し時に) には欠点があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-226">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="2da5d-227">リレーショナル データベースでは、正規化を使用して整合性を適用し、データの重複を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-227">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="2da5d-228">これにより、データベースの合計サイズが小さくなり、共有データの更新プログラムがデータベース全体ですぐに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-228">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="2da5d-229">リレーショナル データベースでは、Address テーブルが ID で Country テーブルを参照する場合があります。国の名前が変更された場合、アドレス レコードは更新プログラムの利点が得られ、それ自体の更新は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-229">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="2da5d-230">ただし、NoSQL データベースでは、Address とそれに関連付けられている Country が、格納されている多くのオブジェクトの一部としてシリアル化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-230">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="2da5d-231">国の名前を更新するには、単一行ではなく、すべてのオブジェクトを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-231">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="2da5d-232">リレーショナル データベースでは、外部キーのようなルールを適用することで、リレーショナルの整合性を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-232">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="2da5d-233">通常、NoSQL データベースでは、そのデータに対するこのような制約は提供されません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-233">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="2da5d-234">NoSQL データベースで対処する必要があるもう 1 つの複雑なものとして、バージョン管理があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-234">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="2da5d-235">オブジェクトのプロパティが変更された場合、格納された過去のバージョンから逆シリアル化できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-235">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="2da5d-236">したがって、シリアル化された (以前の) バージョンのオブジェクトを持つ既存のすべてのオブジェクトを更新して、新しいスキーマに準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-236">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="2da5d-237">これは、スキーマの変更に更新スクリプトとマッピング更新が必要な場合がある、リレーショナル データベースとは概念的に異なります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-237">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="2da5d-238">ただし、NoSQL の方法では多くの場合、変更する必要があるエントリの数がはるかに増えます。これは、データの重複が増えるためです。</span><span class="sxs-lookup"><span data-stu-id="2da5d-238">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="2da5d-239">NoSQL データベースには、リレーショナル データベースでは通常サポートされない固定スキーマなど、複数のバージョンのオブジェクトを格納できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-239">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="2da5d-240">ただし、その場合、アプリケーション コードでは以前のバージョンのオブジェクトの存在を考慮する必要があり、複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-240">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="2da5d-241">通常、NoSQL データベースでは [ACID](https://en.wikipedia.org/wiki/ACID) が適用されません。つまり、リレーショナル データベースよりもパフォーマンスとスケーラビリティの両方が優れています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-241">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="2da5d-242">正規化されたテーブル構造には最適ではない、非常に大規模なデータセットとオブジェクトに最適です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-242">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="2da5d-243">単一のアプリケーションでリレーショナル データベースと NoSQL データベースの両方 (それぞれ適宜使用) を利用できない理由はありません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-243">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="2da5d-244">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="2da5d-244">Azure DocumentDB</span></span>

<span data-ttu-id="2da5d-245">Azure DocumentDB は完全に管理された NoSQL データベース サービスであり、クラウドベースのスキーマレスなデータ ストレージを提供します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-245">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="2da5d-246">DocumentDB は、高速で予測可能なパフォーマンス、高可用性、エラスティック スケーリング、およびグローバル配布用に作成されています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-246">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="2da5d-247">NoSQL データベースであるにもかかわらず、開発者は JSON データで豊富で使い慣れた SQL クエリ機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-247">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="2da5d-248">DocumentDB のすべてのリソースは、JSON ドキュメントとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-248">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="2da5d-249">リソースは、*アイテム* (メタデータを含むドキュメント) および*フィード* (アイテムのコレクション) として管理されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-249">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="2da5d-250">図 8-2 は、さまざまな DocumentDB リソース間の関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="2da5d-250">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![DocumentDB (NoSQL JSON データベース) のリソース間の階層関係](./media/image8-2.png)

<span data-ttu-id="2da5d-252">**図 8-2** </span><span class="sxs-lookup"><span data-stu-id="2da5d-252">**Figure 8-2.**</span></span> <span data-ttu-id="2da5d-253">DocumentDB リソースの組織。</span><span class="sxs-lookup"><span data-stu-id="2da5d-253">DocumentDB resource organization.</span></span>

<span data-ttu-id="2da5d-254">DocumentDB クエリ言語は、JSON ドキュメントを照会するための簡単かつ強力なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2da5d-254">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="2da5d-255">言語では ANSI SQL 文法のサブセットがサポートされ、JavaScript のオブジェクト、配列、オブジェクトの構築、関数呼び出しと緊密に統合できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-255">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="2da5d-256">**参照 – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="2da5d-256">**References – DocumentDB**</span></span>

-   <span data-ttu-id="2da5d-257">DocumentDB の概要\\</span><span class="sxs-lookup"><span data-stu-id="2da5d-257">DocumentDB Introduction\\</span></span>
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="2da5d-258">その他の永続性オプション</span><span class="sxs-lookup"><span data-stu-id="2da5d-258">Other Persistence Options</span></span>

<span data-ttu-id="2da5d-259">リレーショナルおよび NoSQL ストレージ オプションに加え、ASP.NET Core アプリケーションでは Azure Storage を使用して、クラウドベースのスケーラブルな方法でさまざまなデータ形式とファイルを格納できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-259">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="2da5d-260">Azure Storage は非常にスケーラブルであるため、最初に少量のデータを格納し、アプリケーションで必要になった場合に数百または数テラバイトのデータを格納するようにスケール アップできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-260">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="2da5d-261">Azure Storage では次の 4 つの種類のデータがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-261">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="2da5d-262">非構造化テキストまたはバイナリ ストレージ用の Blob Storage。これは、オブジェクト ストレージとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-262">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="2da5d-263">行キーを使用してアクセス可能な、構造化データセット用の Table Storage。</span><span class="sxs-lookup"><span data-stu-id="2da5d-263">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="2da5d-264">信頼性の高いキューベースのメッセージング用の Queue Storage。</span><span class="sxs-lookup"><span data-stu-id="2da5d-264">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="2da5d-265">Azure 仮想マシンとオンプレミス アプリケーション間での共有ファイル アクセス用の File Storage。</span><span class="sxs-lookup"><span data-stu-id="2da5d-265">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="2da5d-266">**参照 – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="2da5d-266">**References – Azure Storage**</span></span>

-   <span data-ttu-id="2da5d-267">Azure Storage の概要\\</span><span class="sxs-lookup"><span data-stu-id="2da5d-267">Azure Storage Introduction\\</span></span>
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="2da5d-268">キャッシュ</span><span class="sxs-lookup"><span data-stu-id="2da5d-268">Caching</span></span>

<span data-ttu-id="2da5d-269">Web アプリケーションでは、各 Web 要求をできるだけ短時間に完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-269">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="2da5d-270">これを実現する 1 つの方法は、サーバーが要求を完了するために行う必要がある、外部呼出しの数を制限することです。</span><span class="sxs-lookup"><span data-stu-id="2da5d-270">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="2da5d-271">キャッシュでは、サーバー (または、データ ソースよりクエリが簡単な別のデータ ストア) にデータのコピーを格納します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-271">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="2da5d-272">Web アプリケーション、および特に非 SPA の従来の Web アプリケーションでは、要求ごとにユーザー インターフェイス全体を構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-272">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="2da5d-273">そのため、ユーザー要求ごとに多くの同じデータベース クエリが何度も繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-273">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="2da5d-274">ほとんどの場合、このデータはめったに変更されないため、データベースから常に要求する理由はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-274">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="2da5d-275">ASP.NET Core では (ページ全体をキャッシュする) 応答キャッシュおよび (より詳細なキャッシュ動作をサポートする) データ キャッシュがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-275">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="2da5d-276">キャッシュを実装する場合、関心の分離に注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-276">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="2da5d-277">データ アクセス ロジック、またはユーザー インターフェイスでのキャッシュ ロジックの実装は避けてください。</span><span class="sxs-lookup"><span data-stu-id="2da5d-277">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="2da5d-278">代わりに、独自のクラスにキャッシュをカプセル化し、その動作を管理する構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-278">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="2da5d-279">これは開放/閉鎖および単一責任の原則に従っており、拡大するアプリケーションでのキャッシュの使用方法を管理しやすくします。</span><span class="sxs-lookup"><span data-stu-id="2da5d-279">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="2da5d-280">ASP.NET Core の応答キャッシュ</span><span class="sxs-lookup"><span data-stu-id="2da5d-280">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="2da5d-281">ASP.NET Core では、2 つのレベルの応答キャッシュがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-281">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="2da5d-282">最初のレベルではサーバーには何もキャッシュしませんが、応答をキャッシュするようにクライアントおよびプロキシ サーバーに指示する HTTP ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-282">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="2da5d-283">これは、個々のコントローラーまたはアクションに ResponseCache 属性を追加することで実装されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-283">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

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

<span data-ttu-id="2da5d-284">応答キャッシュ ミドルウェアは、カスタマイズ可能な一連の条件に基づいて、自動的に応答をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="2da5d-284">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="2da5d-285">既定では、GET または HEAD メソッドを使用して要求された 200 (OK) の応答のみがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-285">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="2da5d-286">さらに、要求には、Cache-Control: public ヘッダーを含む応答が必要であり、Authorization や Set-Cookie のヘッダーを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="2da5d-286">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="2da5d-287">[応答キャッシュ ミドルウェアで使用されるキャッシュ条件の完全なリスト](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2da5d-287">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="2da5d-288">データ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="2da5d-288">Data Caching</span></span>

<span data-ttu-id="2da5d-289">完全な Web 応答のキャッシュではなく (または、このようなキャッシュに加えて)、個々のデータ クエリの結果をキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-289">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="2da5d-290">その場合、Web サーバーでメモリ内キャッシュを使用するか、[分散キャッシュ](https://docs.microsoft.com/aspnet/core/performance/caching/distributed)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-290">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="2da5d-291">このセクションでは、メモリ内キャッシュの実装方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-291">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="2da5d-292">次のように、ConfigureServices でメモリ (または分散) キャッシュのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-292">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="2da5d-293">必ず、Microsoft.Extensions.Caching.Memory NuGet パッケージも追加してください。</span><span class="sxs-lookup"><span data-stu-id="2da5d-293">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="2da5d-294">サービスを追加したら、キャッシュにアクセスする必要がある場合は常に、依存関係の挿入を使用して IMemoryCache を要求します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-294">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="2da5d-295">この例では、CachedCatalogService で、基になる CatalogService 実装へのアクセスを制御する (または動作を追加する) ICatalogService の代替実装を提供して、プロキシ (またはデコレーター) 設計パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-295">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="2da5d-296">キャッシュされたバージョンのサービスを使用するが、コンストラクターで必要になる CatalogService のインスタンスをサービスが引き続き取得できるようにアプリケーションを構成するには、ConfigureServices に以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="2da5d-296">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="2da5d-297">こうすることで、カタログ データをフェッチするデータセット呼び出しは、要求ごとではなく、1 分ごとに 1 回だけ行われるようになります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-297">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="2da5d-298">サイトへのトラフィックによっては、データベースに対して行われるクエリの数と、このサービスによって公開される 3 つのすべてのクエリに現在依存しているホーム ページの平均ページ読み込み時間に非常に大きく影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-298">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="2da5d-299">キャッシュの実装時に問題になるのは、*古いデータ*です。つまり、データがソースで変更されても、その古いバージョンのデータがキャッシュに保持されます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-299">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="2da5d-300">この問題を緩和する簡単な方法は、短いキャッシュ期間を使用することです。ビジー状態のアプリケーションの場合、データのキャッシュ期間を延長することで得られる限られた追加の利点があるためです。</span><span class="sxs-lookup"><span data-stu-id="2da5d-300">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="2da5d-301">たとえば、単一のデータベース クエリを実行し、1 秒ごとに 10 回要求されるページがあるとします。</span><span class="sxs-lookup"><span data-stu-id="2da5d-301">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="2da5d-302">このページが 1 分間キャッシュされると、1 分ごとに実行されるデータベース クエリの数は 600 から 1 に減り、99.8% の減少率となります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-302">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="2da5d-303">代わりにキャッシュ期間を 1 時間にした場合、全体的な減少率は 99.997% となりますが、古いデータの確率的および潜在的な経過期間はどちらも大幅に増えます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-303">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="2da5d-304">含まれているデータを更新する場合、事前にキャッシュ エントリを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-304">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="2da5d-305">キーがわかっている場合は、個々のエントリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-305">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="2da5d-306">アプリケーションでキャッシュされているエントリを更新する機能が公開されている場合は、更新を実行するコードの対応するキャッシュ エントリを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-306">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="2da5d-307">特定のデータ セットに依存する多くの異なるエントリが存在する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2da5d-307">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="2da5d-308">その場合は、CancellationChangeToken を使用して、キャッシュ エントリ間の依存関係を作成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="2da5d-308">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="2da5d-309">CancellationChangeToken を使用すれば、トークンを取り消すことで一度に複数のキャッシュ エントリを期限切れにすることができます。</span><span class="sxs-lookup"><span data-stu-id="2da5d-309">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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
<span data-ttu-id="2da5d-310">[前へ] (develop-asp-net-core-mvc-apps.md) [次へ] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="2da5d-310">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>

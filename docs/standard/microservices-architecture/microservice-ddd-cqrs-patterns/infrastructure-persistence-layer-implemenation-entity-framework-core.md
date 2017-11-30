---
title: "Entity Framework のコア インフラストラクチャの永続性レイヤーの実装"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Entity Framework のコア インフラストラクチャの永続性レイヤーの実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="e58c7-104">Entity Framework のコア インフラストラクチャの永続性レイヤーの実装</span><span class="sxs-lookup"><span data-stu-id="e58c7-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="e58c7-105">SQL Server、Oracle、または PostgreSQL などのリレーショナル データベースを使用する場合、推奨される方法は、Entity Framework (EF) に基づく、永続性レイヤーを実装するがします。</span><span class="sxs-lookup"><span data-stu-id="e58c7-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="e58c7-106">EF は、LINQ をサポートしているし、モデルでは、できるだけでなく、データベースに簡略化された永続化する厳密に型指定されたオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="e58c7-107">Entity Framework では、.NET Framework の一部として長い歴史があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="e58c7-108">.NET Core を使用する場合も、.NET Core と同じ方法で Windows または Linux で実行するため、Entity Framework Core を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e58c7-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="e58c7-109">EF Core とは、Entity Framework、フット プリントがはるかに小さいとパフォーマンスで重要な機能強化を使用して実装の完全な書き直しです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="e58c7-110">Entity Framework Core の概要</span><span class="sxs-lookup"><span data-stu-id="e58c7-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="e58c7-111">Entity Framework (EF) のコアは軽量で拡張性があると、クロスプラット フォームのバージョンの人気のある Entity Framework データ アクセス テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="e58c7-112">これは、.NET Core の 2016 中旬で導入されました。</span><span class="sxs-lookup"><span data-stu-id="e58c7-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="e58c7-113">EF Core の概要については、Microsoft のドキュメントで使用可能なは既に、ためここで単に提供されていますその情報へのリンク。</span><span class="sxs-lookup"><span data-stu-id="e58c7-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e58c7-114">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="e58c7-114">Additional resources</span></span>

-   <span data-ttu-id="e58c7-115">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="e58c7-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="e58c7-116">**ASP.NET Core と Visual Studio を使用して Entity Framework Core の概要**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="e58c7-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="e58c7-117">**DbContext クラス**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="e58c7-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="e58c7-118">**EF コア & EF6.x 比較**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="e58c7-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="e58c7-119">DDD の観点からエンティティ フレームワークのコア インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="e58c7-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="e58c7-120">DDD の観点から EF の重要な機能は、EF 用語では POCO とも呼ばれます、POCO ドメイン エンティティを使用する機能*コード優先エンティティ*です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="e58c7-121">POCO ドメイン エンティティを使用する場合、ドメイン モデル クラスは永続化非依存、次の[持続性の無視が適用](http://deviq.com/persistence-ignorance/)と[インフラストラクチャの無視が適用](https://ayende.com/blog/3137/infrastructure-ignorance)原則です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="e58c7-122">DDD パターンごとは任意のコレクションにアクセスするとき、検証、およびルールは不変制御できるようにドメインの動作とルール自体、エンティティ クラス内でカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="e58c7-123">したがって、ddd でエンティティまたはオブジェクトの値は、子のコレクションへのパブリック アクセスを許可することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="e58c7-124">代わりに、その場合に制御する方法とタイミング、フィールドやプロパティ コレクションを更新できるメソッドとどのような動作と操作を実行するを公開します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="e58c7-125">DDD 要件を満たすために EF コア 1.1 でにパブリックおよびプライベートの setter のプロパティではなく、エンティティ内プレーンなフィールドを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="e58c7-126">外部からアクセスできるようにエンティティ フィールドしたくない場合は、属性またはプロパティではなくフィールドだけ作成できます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="e58c7-127">クリーナーこうしたい場合は、プライベート set アクセス操作子を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="e58c7-128">同様の方法で保持できますコレクションへのアクセスの読み取り専用 IEnumerable として型指定されたパブリック プロパティを使用して&lt;T&gt;、コレクションのプライベート フィールドのメンバーで補助されている (リストと同様に&lt;&gt;) で、永続化の EF に依存するエンティティ。</span><span class="sxs-lookup"><span data-stu-id="e58c7-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="e58c7-129">Entity Framework の以前のバージョンには、ICollection をサポートするコレクションのプロパティが必要な&lt;T&gt;、親エンティティ クラスを使用してすべての開発者が追加またはそのプロパティのコレクションから項目を削除できなかったことです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="e58c7-130">DDD で推奨されたパターンに対してその可能性になります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="e58c7-131">次のコード例に示すように、読み取り専用の IEnumerable オブジェクトを公開する際プライベート コレクションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
        decimal unitPrice, decimal discount,
        string pictureUrl, int units = 1)
    {
        // Validation logic...
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="e58c7-132">読み取り専用としてリストを使用して OrderItems プロパティにアクセスするだけことに注意してください&lt;&gt;です。AsReadOnly() です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="e58c7-133">このメソッドは、外部データの更新に対して保護されているように、プライベートの一覧をラップする読み取り専用のラッパーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="e58c7-134">新しいコレクションのすべてのアイテムのコピー先があるないため ToList メソッドを使用するよりもはるかに低コストでは、します。代わりに、ラッパーのインスタンスの 1 つのヒープ割り当て操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="e58c7-135">EF コアは、ドメイン モデルを行うことがなく、ドメイン モデルを物理データベースにマップする方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="e58c7-136">永続レイヤー、マップされた操作が実装されているために、純粋な .NET POCO、コードを勧めします。</span><span class="sxs-lookup"><span data-stu-id="e58c7-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="e58c7-137">そのマッピング操作では、データベースへのフィールド マッピングを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="e58c7-138">OnModelCreating メソッドの次の例では、強調表示されたコードは、そのフィールドを介して OrderItems プロパティにアクセスする EF コアを示します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

<span data-ttu-id="e58c7-139">リストがあった場合と同様に、OrderItem エンティティが永続化プロパティの代わりにフィールドを使用するときに&lt;OrderItem&gt;プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="e58c7-140">ただし、注文に新しい項目を追加するため、1 つのアクセサー (AddOrderItem メソッド) を公開します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="e58c7-141">その結果、動作とデータが一緒に扱わし、ドメイン モデルを使用するアプリケーション コード全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="e58c7-142">Entity Framework のコアでカスタムのリポジトリを実装します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="e58c7-143">実装レベルでは、リポジトリは単なるクラス (EF コアで DBContext) の作業単位によってコーディネートされたデータ永続化のコードでクラスを次に示すように、更新プログラムを実行するとき。</span><span class="sxs-lookup"><span data-stu-id="e58c7-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;

        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

<span data-ttu-id="e58c7-144">ドメイン モデル層から IBuyerRepository インターフェイスを取得することを注意してください。</span><span class="sxs-lookup"><span data-stu-id="e58c7-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="e58c7-145">ただし、リポジトリの実装は、永続化とインフラストラクチャ レイヤーで行われます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="e58c7-146">EF DbContext は、依存関係の挿入をコンス トラクターでは取得されます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="e58c7-147">複数のリポジトリ、同じ HTTP 要求のスコープ内で、その既定の有効期間 (ServiceLifetime.Scoped) (これも明示的に設定できますサービス IoC コンテナーにご協力に感謝間で共有されます。AddDbContext&lt;&gt;)。</span><span class="sxs-lookup"><span data-stu-id="e58c7-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="e58c7-148">(更新プログラムまたはクエリではなくトランザクション) リポジトリに実装するメソッド</span><span class="sxs-lookup"><span data-stu-id="e58c7-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="e58c7-149">各リポジトリ クラス内では、その関連する集計が含まれるエンティティの状態を更新する永続化メソッドを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="e58c7-150">集計と、関連するリポジトリの間の一対一のリレーションシップがある注意してください。</span><span class="sxs-lookup"><span data-stu-id="e58c7-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="e58c7-151">集計ルート エンティティ オブジェクトが埋め込まれている、EF グラフ内の子エンティティを考慮します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="e58c7-152">たとえば、購入者は、関連する子エンティティとして複数の支払方法があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="e58c7-153">EShopOnContainers で順序付けマイクロ サービスの実行方法については、CQS/CQRS に基づいても、ので、ほとんどのクエリでは、カスタム リポジトリで実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="e58c7-154">開発者では、クエリと集計、集計、および DDD ごとのカスタムのリポジトリで一般に課せられる制限なしのプレゼンテーション層に必要な結合を作成する自由があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="e58c7-155">このガイドで提案されたカスタムのリポジトリのほとんどにいくつかの更新やトランザクション メソッドですが、クエリ メソッドだけを更新するデータを取得するために必要です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="e58c7-156">たとえば、アプリケーションは、注文に関連する新しい buyer を作成する前に、特定の購入者が存在するかどうか知っておく必要があるために、BuyerRepository リポジトリは、FindAsync メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="e58c7-157">ただし、プレゼンテーション層またはクライアント アプリに送信するデータを取得する実際のクエリ メソッドが実装されて Dapper を使用して、柔軟なクエリに基づく CQRS クエリで、説明したようにします。</span><span class="sxs-lookup"><span data-stu-id="e58c7-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="e58c7-158">EF DbContext を直接使用するとカスタム リポジトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="e58c7-159">Entity Framework DbContext クラスは、作業単位とリポジトリ パターンに基づいて、およびとして使用できます、コードから直接など、ASP.NET Core MVC コント ローラーからです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="e58c7-160">つまり方法 eShopOnContainers で CRUD カタログ マイクロ サービスのように、最も単純なコードを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="e58c7-161">必要がある場合、最も単純なコード可能な場合 DbContext クラスを直接使用する多くの開発者と同様です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="e58c7-162">ただし、カスタムのリポジトリを実装する複数の利点より複雑な microservices またはアプリケーションを実装する場合。</span><span class="sxs-lookup"><span data-stu-id="e58c7-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="e58c7-163">作業単位とリポジトリ パターンは、アプリケーション層とドメイン モデル層から切り離され、インフラストラクチャの永続性レイヤーをカプセル化するものです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="e58c7-164">これらのパターンを実装すると、データベースへのアクセスをシミュレートするモック リポジトリの使用を容易にするためです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="e58c7-165">図 9-18 でそのリポジトリのモック作成を簡単にするためのリポジトリを使用すると (EF DbContext を使用して直接) リポジトリを使用していない間の相違点を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="e58c7-166">**図 9 18**です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-166">**Figure 9-18**.</span></span> <span data-ttu-id="e58c7-167">プレーンな DbContext ではなくカスタムのリポジトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="e58c7-168">モックする場合は、複数の代替にはあります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="e58c7-169">だけでリポジトリを模擬表示でしたか、全体の作業単位を模擬表示する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="e58c7-170">通常モック リポジトリだけであっても、および複雑さを抽象化し、全体の作業単位を模擬表示通常は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="e58c7-171">その後、アプリケーション層の説明とは、ASP.NET Core での依存関係の挿入のしくみし、リポジトリを使用する場合の実装方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="e58c7-172">つまり、カスタム リポジトリを使用すると、データ層の状態の影響を受けない単体テストのコードをより簡単にテストできます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="e58c7-173">また、Entity Framework で実際のデータベースにアクセスするテストを実行する場合はありません単体テストは統合テストがとても遅くなります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="e58c7-174">DbContext を直接を使用していた場合単体テストの予測可能なデータをメモリ内の SQL Server を使用して単体テストを実行する必要があります唯一の選択肢になります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="e58c7-175">リポジトリ レベルと同様に、モック オブジェクトと偽のデータを制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="e58c7-176">もちろん、MVC コント ローラーを常にテストする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="e58c7-177">EF DbContext および IUnitOfWork インスタンスの有効期間、IoC コンテナー内</span><span class="sxs-lookup"><span data-stu-id="e58c7-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="e58c7-178">(IUnitOfWork オブジェクトとして公開される) DbContext オブジェクトは、HTTP 要求のスコープ内の複数のリポジトリの間で共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="e58c7-179">たとえば、これは、true の場合実行されている操作は複数の集計、または単に対処する必要がある複数のリポジトリを使用しているためです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="e58c7-180">IUnitOfWork インターフェイスが EF 型ではなく、ドメインの一部であることは言うまでも重要です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="e58c7-181">これを実行するためには、DbContext オブジェクトのインスタンスに、そのサービスの有効期間を ServiceLifetime.Scoped に設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="e58c7-182">これは、サービスに DbContext を登録するときに既定の有効期間です。ASP.NET Core Web API プロジェクトに Startup.cs ファイルの ConfigureServices メソッドから IoC コンテナーで AddDbContext です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="e58c7-183">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
    .AddDbContext<OrderingContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
        Assembly.GetName().Name));
    },
    ServiceLifetime.Scoped // Note that Scoped is the default choice
    // in AddDbContext. It is shown here only for
    // pedagogic purposes.
    );
}
```

<span data-ttu-id="e58c7-184">DbContext インスタンス化モードは、ServiceLifetime.Transient または ServiceLifetime.Singleton として構成する必要がありますされません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="e58c7-185">IoC コンテナーでリポジトリ インスタンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="e58c7-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="e58c7-186">同様の方法でリポジトリの有効期間が通常 (InstancePerLifetimeScope Autofac で) スコープとして設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="e58c7-187">ある可能性もスコープを指定した有効期間を使用する場合に、サービスが一時的な (Autofac で InstancePerDependency) がにおいてはメモリ内で効率的であります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="e58c7-188">原因となる、リポジトリのシングルトン有効期間を使用する重大な同時実行の問題、DbContext に設定されているときに注意 (InstancePerLifetimeScope) 有効期間 (DBContext の既定の有効期間) のスコープ設定されます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e58c7-189">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="e58c7-189">Additional resources</span></span>

-   <span data-ttu-id="e58c7-190">**ASP.NET MVC アプリケーションのリポジトリと作業パターンの単位を実装する**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="e58c7-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="e58c7-191">**Jonathan Allen です。リポジトリの実装方法が口ひげ、Entity Framework でのパターンし、チェーン**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="e58c7-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="e58c7-192">**Cesar de la Torre。Autofac IoC コンテナー インスタンスのスコープを持つ ASP.NET Core IoC コンテナー サービスの有効期間を比較する**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="e58c7-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="e58c7-193">テーブルのマッピング</span><span class="sxs-lookup"><span data-stu-id="e58c7-193">Table mapping</span></span>

<span data-ttu-id="e58c7-194">テーブル マッピングからクエリを実行するテーブルのデータを識別し、データベースに保存します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="e58c7-195">以前ドメイン エンティティ (たとえば、製品または順序ドメイン) を使用して、関連するデータベース スキーマを生成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="e58c7-196">EF は強くという概念に設計された*規則*です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="e58c7-197">「どのようなテーブルの名前になりますか。」のような規則アドレス質問</span><span class="sxs-lookup"><span data-stu-id="e58c7-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="e58c7-198">「どのようなプロパティは、主キー」または</span><span class="sxs-lookup"><span data-stu-id="e58c7-198">or “What property is the primary key?”</span></span> <span data-ttu-id="e58c7-199">規則は、従来の名前に基づく通常 — たとえばが、一般に、主キー id を持つ最後のプロパティ</span><span class="sxs-lookup"><span data-stu-id="e58c7-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="e58c7-200">慣例により、各エンティティ設定されます、DbSet と同じ名前のテーブルにマップする&lt;TEntity&gt;派生のコンテキストにエンティティを公開するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="e58c7-201">場合ありません DbSet&lt;TEntity&gt;値が指定されたエンティティのクラス名を使用します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="e58c7-202">Fluent API ではなくデータ注釈</span><span class="sxs-lookup"><span data-stu-id="e58c7-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="e58c7-203">その他の多くの EF コア規則があり、それらのほとんどは、データ注釈または Fluent API、OnModelCreating メソッド内に実装を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="e58c7-204">データ注釈は DDD の観点からより侵入的な方法は、これ自体、エンティティ モデルのクラスに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="e58c7-205">これは、インフラストラクチャのデータベースに関連するデータ注釈を使用したモデルを行うがあるためです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="e58c7-206">その一方で、Fluent API は、完全であり、永続化インフラストラクチャから切り離されたエンティティ モデルが表示されるように、ほとんどの規則と、データの永続化インフラストラクチャ レイヤー内のマッピングを変更する便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="e58c7-207">Fluent API と OnModelCreating メソッド</span><span class="sxs-lookup"><span data-stu-id="e58c7-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="e58c7-208">前述のように、規則とのマッピングを変更するために使用できます OnModelCreating メソッドで DbContext クラス。</span><span class="sxs-lookup"><span data-stu-id="e58c7-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="e58c7-209">次の例では、方法を使う eShopOnContainers で順序付けマイクロ サービスを示します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

<span data-ttu-id="e58c7-210">同じ OnModelCreating メソッド内のすべての Fluent API マッピングを設定する可能性がありますが、そのコードをパーティション分割を用意し、エンティティごとに 1 つ、複数の submethods ことをお勧めの例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="e58c7-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="e58c7-211">特に大規模なモデルは、指定してもかまいません別のエンティティの種類を構成する別のソース ファイル (静的クラス) を持つことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e58c7-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="e58c7-212">コードの例では、明示的なです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-212">The code in the example is explicit.</span></span> <span data-ttu-id="e58c7-213">ただし、EF コア規則ので、同じことを実現するために作成することも、実際のコードが大幅に小さくなりますのほとんどは、自動的には。</span><span class="sxs-lookup"><span data-stu-id="e58c7-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="e58c7-214">EF コアでやあ/Lo アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="e58c7-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="e58c7-215">上記の例のコードでの特徴を使用する、[やあ/Lo アルゴリズム](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/)キーの生成方法として。</span><span class="sxs-lookup"><span data-stu-id="e58c7-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="e58c7-216">やあ/Lo アルゴリズムは、一意なキーが必要な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="e58c7-217">概要、としては、やあ-Lo アルゴリズムは、中にないによっては、データベースに行を格納すると、すぐに、テーブルの行に一意の識別子を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="e58c7-218">これにより、正規シーケンシャル データベース Id とが発生するとすぐに、識別子の使用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="e58c7-219">やあ/Lo アルゴリズムでは、データベースではなく、クライアント側での安全な Id を生成するためのメカニズムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="e58c7-220">*安全な*このコンテキストでの競合なしことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="e58c7-221">このアルゴリズムは、これらの理由から興味深い。</span><span class="sxs-lookup"><span data-stu-id="e58c7-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="e58c7-222">作業単位のパターンは中断されません。</span><span class="sxs-lookup"><span data-stu-id="e58c7-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="e58c7-223">その他の Dbms で操作を行う方法のシーケンス ジェネレーターのラウンド トリップは不要です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="e58c7-224">Guid を使用する手法とは異なりの人間が判読できる id を生成します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="e58c7-225">EF コアをサポートしている[HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo メソッドで、前の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="e58c7-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="e58c7-226">プロパティではなくフィールドのマッピング</span><span class="sxs-lookup"><span data-stu-id="e58c7-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="e58c7-227">フィールドを列にマップする EF コア 1.1 の機能を使用可能であればエンティティ クラスの任意のプロパティを使用しないと、フィールドをテーブルから列をマップするだけです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="e58c7-228">そのための一般的な用途を内部状態のプライベート フィールドをエンティティの外部からアクセスする必要がないとなります。</span><span class="sxs-lookup"><span data-stu-id="e58c7-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="e58c7-229">EF 1.1 には、データベース内の列に関連するプロパティを持たないフィールドをマップする方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e58c7-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="e58c7-230">これを行う 1 つのフィールドを持つかコレクションでは、リストのようにも&lt;&gt;フィールドです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="e58c7-231">このポイントが前述ドメイン モデル クラスをモデリングについて説明しましたが、前のコードで強調表示されている PropertyAccessMode.Field 構成でそのマッピングを実行する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e58c7-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="e58c7-232">インフラストラクチャ レベルで非表示の Id の値のオブジェクトでシャドウ プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="e58c7-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="e58c7-233">EF Core でシャドウ プロパティは、エンティティ クラス モデルに存在しないプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="e58c7-234">値とこれらのプロパティの状態が純粋に保持されます、 [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker)インフラストラクチャ レベルでのクラスです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="e58c7-235">DDD の観点からは、シャドウ プロパティは、シャドウ プロパティの主キーと ID を非表示にして値オブジェクトを実装する便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="e58c7-236">これは、値オブジェクトの id のないため、重要な (少なくとも、する必要はありません ID ドメイン モデル レイヤーにおいて値オブジェクトを整形するときに)。</span><span class="sxs-lookup"><span data-stu-id="e58c7-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="e58c7-237">ここでのポイントは EF コアの現在のバージョンの時点で EF コアがないとして値オブジェクトを実装する方法[複合型](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx)EF で利用できるように、6.x です。</span><span class="sxs-lookup"><span data-stu-id="e58c7-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="e58c7-238">現在シャドウ プロパティとして設定隠し ID (主キー) を持つエンティティとして値オブジェクトを実装する必要があるためにです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="e58c7-239">わかるように、[アドレス値オブジェクト](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)eShopOnContainers でアドレス モデルに表示されない、ID:</span><span class="sxs-lookup"><span data-stu-id="e58c7-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

<span data-ttu-id="e58c7-240">背後でを行う必要が EF コアが、データベース テーブルには、このデータを永続化できるように、ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="e58c7-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="e58c7-241">作業を行うことの ConfigureAddress メソッド内で、 [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) EF インフラストラクチャ コードを使用してドメイン モデルを汚染おはないため、インフラストラクチャ レベルでのクラスです。</span><span class="sxs-lookup"><span data-stu-id="e58c7-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a><span data-ttu-id="e58c7-242">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="e58c7-242">Additional resources</span></span>

-   <span data-ttu-id="e58c7-243">**テーブル マッピング**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="e58c7-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="e58c7-244">**HiLo を使用して Entity Framework のコアを使用してキーを生成する**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="e58c7-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="e58c7-245">**バッキング フィールド**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="e58c7-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="e58c7-246">**Steve Smith です。Entity Framework のコア内のコレクションをカプセル化された**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="e58c7-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="e58c7-247">**プロパティをシャドウ**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="e58c7-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e58c7-248">[前](インフラストラクチャ-永続化のレイヤー-design.md) [次へ] (nosql-データベースの永続化-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="e58c7-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>

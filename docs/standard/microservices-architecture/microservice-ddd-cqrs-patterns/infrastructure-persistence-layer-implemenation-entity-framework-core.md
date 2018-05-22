---
title: Entity Framework Core でインフラストラクチャの永続レイヤーを実装する
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Entity Framework Core でインフラストラクチャの永続レイヤーを実装する'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 0f3b4539156f3ba437c77dea721ca53206d1ed40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="32934-103">Entity Framework Core でインフラストラクチャの永続レイヤーを実装する</span><span class="sxs-lookup"><span data-stu-id="32934-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="32934-104">SQL Server、Oracle、PostgreSQL など、リレーショナル データベースを使用するとき、Entity Framework (EF) に基づいて永続レイヤーを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="32934-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="32934-105">EF は LINQ 対応であり、厳密に型指定されたオブジェクトをモデルに与えます。また、データベースにシンプルな永続性が与えられます。</span><span class="sxs-lookup"><span data-stu-id="32934-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="32934-106">Entity Framework は長い間、.NET Framework の一部でした。</span><span class="sxs-lookup"><span data-stu-id="32934-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="32934-107">.NET Core を使用するとき、Entity Framework Core も使用してください。 .NET Core と同様に、Windows または Linux で実行されます。</span><span class="sxs-lookup"><span data-stu-id="32934-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="32934-108">EF Core は Entity Framework を完全に書き換えたものであり、フットプリントが大幅に少なくなっており、パフォーマンス面で重要な改善が行われています。</span><span class="sxs-lookup"><span data-stu-id="32934-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="32934-109">Entity Framework Core の概要</span><span class="sxs-lookup"><span data-stu-id="32934-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="32934-110">Entity Framework (EF) Core は人気の Entity Framework データ アクセス テクノロジの軽量版であり、拡張性に優れ、プラットフォームに依存しません。</span><span class="sxs-lookup"><span data-stu-id="32934-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="32934-111">2016 年の中頃に .NET Core に導入されました。</span><span class="sxs-lookup"><span data-stu-id="32934-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="32934-112">EF Core の概要は Microsoft ドキュメントで既に利用可能になっているので、ここではそのリンクのみを掲載しておきます。</span><span class="sxs-lookup"><span data-stu-id="32934-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="32934-113">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="32934-113">Additional resources</span></span>

-   <span data-ttu-id="32934-114">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="32934-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="32934-115">**Visual Studio を使用した ASP.NET Core と Entity Framework Core の概要**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="32934-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="32934-116">**DbContext クラス**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="32934-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="32934-117">**EF Core と EF6.x を比較する**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="32934-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="32934-118">DDD の観点から見た Entity Framework Core のインフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="32934-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="32934-119">DDD の観点から見ると、EF の重要な機能は、POCO ドメイン エンティティを使用できることです。EF 用語では、*POCO Code First エンティティ*と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="32934-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="32934-120">POCO ドメイン エンティティを使用する場合、ドメイン モデル クラスは永続性無視になります。[永続化の無視 (Persistence Ignorance)](http://deviq.com/persistence-ignorance/) の原則と[インフラストラクチャの無視 (Infrastructure Ignorance)](https://ayende.com/blog/3137/infrastructure-ignorance) の原則に従います。</span><span class="sxs-lookup"><span data-stu-id="32934-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="32934-121">DDD パターンごとに、エンティティ クラス自体の中にドメインの動作とルールをカプセル化してください。そうすることで、エンティティ クラス自体でコレクションにアクセスするとき、インバリアント、検証、ルールを制御できます。</span><span class="sxs-lookup"><span data-stu-id="32934-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="32934-122">そのため、子エンティティや値オブジェクトのコレクションにパブリック アクセスを許可することは、DDD ではお勧めされません。</span><span class="sxs-lookup"><span data-stu-id="32934-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="32934-123">それよりも、フィールドとプロパティのコレクションを更新する方法とタイミング、更新時のビヘイビアーとアクションを制御するメソッドを公開することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="32934-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="32934-124">EF Core 1.1 以降、このような DDD 要件を満たすために、パブリック プロパティの代わりに、エンティティにプレーン フィールドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="32934-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="32934-125">エンティティ フィールドに外部からアクセスできるようにする場合、プロパティの代わりに、属性やフィールドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="32934-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="32934-126">プライベート プロパティの設定機能を利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="32934-126">You can also use private property setters.</span></span>

<span data-ttu-id="32934-127">同様に、`IReadOnlyCollection<T>` として型指定されたパブリック プロパティを利用することで、コレクションに読み取り専用アクセスできるようになりました。この機能をサポートするのがエンティティのコレクションのプライベート フィールド メンバーです (`List<T>` など)。このメンバーは永続性を EF に依存します。</span><span class="sxs-lookup"><span data-stu-id="32934-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="32934-128">以前のバージョンの Entity Framework では、コレクション プロパティで `ICollection<T>` をサポートする必要がありました。つまり、開発者が親エンティティ クラスを利用するとき、そのプロパティ コレクションから項目を追加したり、削除したりできました。</span><span class="sxs-lookup"><span data-stu-id="32934-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="32934-129">その機能は DDD の推奨パターンに反する可能性がありました。</span><span class="sxs-lookup"><span data-stu-id="32934-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="32934-130">読み取り専用 `IReadOnlyCollection<T>` オブジェクトを公開するとき、プライベート コレクションを使用できます。次のコード例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32934-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems; 
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

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

        var orderItem = new OrderItem(productId, productName, 
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="32934-131">`OrderItems` プロパティには `IReadOnlyCollection<OrderItem>` を利用して読み取り専用アクセスのみが可能となることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32934-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="32934-132">この型は読み取り専用であり、定期的な外部更新から守られます。</span><span class="sxs-lookup"><span data-stu-id="32934-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="32934-133">EF Core では、ドメイン モデルを "汚染する" ことなく物理データベースにマッピングできます。</span><span class="sxs-lookup"><span data-stu-id="32934-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="32934-134">マッピング アクションは永続レイヤーで行われるため、純粋な .NET POCO コードになります。</span><span class="sxs-lookup"><span data-stu-id="32934-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="32934-135">そのマッピング アクションでは、フィールドとデータベースのマッピングを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32934-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="32934-136">次の OnModelCreating メソッド例で強調表示されているコードは、そのフィールドを介して OrderItems プロパティにアクセスするように EF Core に伝えます。</span><span class="sxs-lookup"><span data-stu-id="32934-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation = 
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="32934-137">プロパティの代わりにフィールドを使用するとき、List&lt;OrderItem&gt; プロパティが与えられているかのように OrderItem エンティティが永続化されます。</span><span class="sxs-lookup"><span data-stu-id="32934-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="32934-138">ただし、アクセサーが 1 つ公開されます。新しい項目を注文に追加する `AddOrderItem` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="32934-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="32934-139">結果として、ビヘイビアーとデータが結び付けられ、ドメイン モデルを使用するアプリケーション コード全体で一貫性が与えられます。</span><span class="sxs-lookup"><span data-stu-id="32934-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="32934-140">Entity Framework Core でカスタム リポジトリを実装する</span><span class="sxs-lookup"><span data-stu-id="32934-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="32934-141">実装レベルでは、リポジトリは、更新の実行時に作業単位 (EF Core の DBContext) で調整されるデータ永続化コードを持つクラスです。次のクラスをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32934-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity; 
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="32934-142">IBuyerRepository インターフェイスは、コントラクトとしてのドメイン モデル レイヤーから取得されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32934-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="32934-143">ただし、リポジトリ実装は永続化とインフラストラクチャのレイヤーで行われます。</span><span class="sxs-lookup"><span data-stu-id="32934-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="32934-144">EF DbContext は、依存関係の挿入により、コンストラクター経由で取得されます。</span><span class="sxs-lookup"><span data-stu-id="32934-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="32934-145">IoC コンテナー (services.AddDbContext&lt;&gt; で明示的に設定することもできます) にある既定の有効期間 (ServiceLifetime.Scoped) に起因し、同じ HTTP 要求範囲内の複数のリポジトリ間で強要されます。</span><span class="sxs-lookup"><span data-stu-id="32934-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="32934-146">リポジトリで実装するためのメソッド (更新またはトランザクションとクエリ)</span><span class="sxs-lookup"><span data-stu-id="32934-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="32934-147">各リポジトリ クラス内に、関連集計に含まれるエンティティの状態を更新する永続性メソッドを置いてください。</span><span class="sxs-lookup"><span data-stu-id="32934-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="32934-148">集計とその関連リポジトリの間には一対一の関係があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32934-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="32934-149">集計ルート エンティティ オブジェクトがその EF グラフ内に子エンティティを埋め込んでいる可能性を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="32934-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="32934-150">たとえば、購入者には、関連する子エンティティとして複数の支払方法が与えられている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32934-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="32934-151">eShopOnContainers でマイクロサービスを注文する手法も CQS/CQRS に基づいているため、クエリの多くはカスタム リポジトリで実装されません。</span><span class="sxs-lookup"><span data-stu-id="32934-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="32934-152">集計、集計別のカスタム リポジトリ、一般的な DDD によって課される制約なしで、開発者はプレゼンテーション レイヤーに必要なクエリや結合を自由に作成できます。</span><span class="sxs-lookup"><span data-stu-id="32934-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="32934-153">本ガイドで提案するカスタム リポジトリの多くには更新メソッドとトランザクション メソッドがいくつかあるが、更新するデータの取得に必要なクエリ メソッドに限られます。</span><span class="sxs-lookup"><span data-stu-id="32934-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="32934-154">たとえば、BuyerRepository リポジトリは FindAsync メソッドを実装します。アプリケーションでは、注文に関連する新しい購入者を作成する前に、特定の購入者が存在するかどうかを認識する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="32934-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="32934-155">ただし、前述のように、Dapper を利用するフレキシブル クエリに基づく CQRS クエリで、プレゼンテーション レイヤーまたはクライアント アプリに送信するデータを取得する真のクエリ メソッドが実装されます。</span><span class="sxs-lookup"><span data-stu-id="32934-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="32934-156">カスタム リポジトリの使用と EF DbContext の直接使用の違い</span><span class="sxs-lookup"><span data-stu-id="32934-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="32934-157">Entity Framework DbContext クラスは Unit of Work と Repository のパターンに基づきます。ASP.NET Core MVC コントローラーなど、コードから直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="32934-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="32934-158">これで、eShopOnContainers の CRUD カタログ マイクロサービスのように、最も単純なコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="32934-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="32934-159">できるだけ単純なコードが必要であれば、DbContext クラスを直接使用することをお勧めします。多くの開発者がそうしています。</span><span class="sxs-lookup"><span data-stu-id="32934-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="32934-160">ただし、カスタム リポジトリを実装するのであれば、より複雑なマイクロサービスやアプリケーションを実装するとき、いくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="32934-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="32934-161">Unit of Work と Repository のパターンは、インフラストラクチャの永続レイヤーのカプセル化を意図しています。アプリケーションとドメイン モデルのレイヤーから切り離されます。</span><span class="sxs-lookup"><span data-stu-id="32934-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="32934-162">これらのパターンを実装すると、データベースへのアクセスをシミュレートするモック リポジトリの使用が容易になります。</span><span class="sxs-lookup"><span data-stu-id="32934-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="32934-163">図 9-18 では、リポジトリを使用しない (EF DbContext を直接使用する) 場合とリポジトリのモック (疑似) を簡単にするリポジトリを使用する場合の違いを確認できます。</span><span class="sxs-lookup"><span data-stu-id="32934-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="32934-164">**図 9-18**.</span><span class="sxs-lookup"><span data-stu-id="32934-164">**Figure 9-18**.</span></span> <span data-ttu-id="32934-165">カスタム リポジトリとプレーンな DbContext の使用の違い</span><span class="sxs-lookup"><span data-stu-id="32934-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="32934-166">モックにはさまざまな代替手法があります。</span><span class="sxs-lookup"><span data-stu-id="32934-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="32934-167">リポジトリだけをモックしたり、作業単位全体をモックしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="32934-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="32934-168">通常、リポジトリだけをモックする手法で十分です。作業単位全体を抽出し、モックする複雑な作業は通常は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="32934-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="32934-169">この後、アプリケーション レイヤーについて取り上げるとき、依存関係の挿入が ASP.NET Core でどのように機能するか、リポジトリを使用するとき、それがどのように実装されるか説明します。</span><span class="sxs-lookup"><span data-stu-id="32934-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="32934-170">手短に言えば、カスタム リポジトリでは、データ層の状態の影響を受けない単体テストを利用し、より簡単にコードをテストできます。</span><span class="sxs-lookup"><span data-stu-id="32934-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="32934-171">Entity Framework 経由で実際のデータベースにもアクセスするテストを実行する場合、単体テストではなく統合テストになり、大幅に遅くなります。</span><span class="sxs-lookup"><span data-stu-id="32934-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="32934-172">DbContext を直接使用した場合、唯一の選択肢として与えられるのは、メモリ内 SQL Server と単体テスト用の予測可能データを使用して単体テストを実行することです。</span><span class="sxs-lookup"><span data-stu-id="32934-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="32934-173">リポジトリ レベルで、モック オブジェクトと偽データを同じように制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="32934-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="32934-174">もちろん、MVC コント ローラーはいつでもテストできます。</span><span class="sxs-lookup"><span data-stu-id="32934-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="32934-175">IoC コンテナーの EF DbContext と IUnitOfWork のインスタンス有効期間</span><span class="sxs-lookup"><span data-stu-id="32934-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="32934-176">DbContext object (IUnitOfWork オブジェクトとして公開) は、場合によっては、同じ HTTP 要求範囲内にある複数のリポジトリ間で共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32934-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="32934-177">たとえば、実行する操作に複数の集計が伴うときに共有が必要になります。あるいは、複数のリポジトリ インスタンスを利用していると理由で共有が必要になります。</span><span class="sxs-lookup"><span data-stu-id="32934-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="32934-178">IUnitOfWork インターフェイスが EF Core タイプではなく、ドメイン レイヤーに含まれるということも重要です。</span><span class="sxs-lookup"><span data-stu-id="32934-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="32934-179">そのためには、DbContext オブジェクトのインスタンスのサービス有効期間を ServiceLifetime.Scoped に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32934-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="32934-180">これは、ASP.NET Core Web API プロジェクトの Startup.cs ファイルの ConfigureServices メソッドから IoC コンテナーの services.AddDbContext に DbContext を登録したときの既定の有効期間です。</span><span class="sxs-lookup"><span data-stu-id="32934-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="32934-181">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="32934-181">The following code illustrates this.</span></span>

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
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="32934-182">DbContext インスタンス化モードは ServiceLifetime.Transient または ServiceLifetime.Singleton に設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="32934-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="32934-183">IoC コンテナーのリポジトリ インスタンスの有効期間</span><span class="sxs-lookup"><span data-stu-id="32934-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="32934-184">同様に、リポジトリの有効期間は通常、範囲として設定してください (InstancePerLifetimeScope in Autofac)。</span><span class="sxs-lookup"><span data-stu-id="32934-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="32934-185">一時的として設定することもできますが、範囲が指定された有効期間のほうがサービスのメモリが効率的になります。</span><span class="sxs-lookup"><span data-stu-id="32934-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="32934-186">DbContext の有効期間が範囲 (InstancePerLifetimeScope) として設定されているとき (DBContext の既定の有効期間)、リポジトリに単一の有効期間を使用すると、同時実行関連で重大な問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32934-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="32934-187">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="32934-187">Additional resources</span></span>

-   <span data-ttu-id="32934-188">**ASP.NET MVC アプリケーションでの Repository および Unit of Work パターンの実装**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="32934-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="32934-189">**Jonathan Allen。Entity Framework、Dapper、Chain を使用する Repository パターンの実装方法**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="32934-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="32934-190">**Cesar de la Torre。ASP.NET Core IoC コンテナー サービスの有効期間と Autofac IoC コンテナー インスタンスの範囲の比較**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="32934-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="32934-191">テーブル マッピング</span><span class="sxs-lookup"><span data-stu-id="32934-191">Table mapping</span></span>

<span data-ttu-id="32934-192">テーブル マッピングでは、データベースに問い合わせたり、保存したりするテーブル データが識別されます。</span><span class="sxs-lookup"><span data-stu-id="32934-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="32934-193">先に、ドメイン エンティティ (製品や注文のドメインなど) を利用し、関連データベース スキーマを生成する方法を確認しました。</span><span class="sxs-lookup"><span data-stu-id="32934-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="32934-194">EF は、*規則*という概念を中心に作られています。</span><span class="sxs-lookup"><span data-stu-id="32934-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="32934-195">規則は “テーブルの名前は何になるのか?”</span><span class="sxs-lookup"><span data-stu-id="32934-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="32934-196">または “主キーはどのようなプロパティか?” のような質問に対処するものです。</span><span class="sxs-lookup"><span data-stu-id="32934-196">or “What property is the primary key?”</span></span> <span data-ttu-id="32934-197">規則は通常、慣例的な名前に基づきます。たとえば、主キーであれば、ID で終わるプロパティが一般的に与えられます。</span><span class="sxs-lookup"><span data-stu-id="32934-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="32934-198">規則では、派生コンテキストでエンティティを公開する DbSet&lt;TEntity&gt; プロパティと同じ名前を持つテーブルにマッピングされるように各エンティティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="32934-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="32934-199">所与のエンティティに DbSet&lt;TEntity&gt; 値が指定されない場合、クラス名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="32934-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="32934-200">データの注釈と Fluent API の違い</span><span class="sxs-lookup"><span data-stu-id="32934-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="32934-201">付加的な EF Core 規則がたくさん存在します。そのほとんどは、OnModelCreating メソッド内に実装されるデータの注釈か Fluent API を利用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="32934-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="32934-202">データの注釈はエンティティ モデル クラス自体で使用する必要があります。DDD の観点からは、侵入性が高い方法となります。</span><span class="sxs-lookup"><span data-stu-id="32934-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="32934-203">これはインフラストラクチャ データベースに関連するデータ注釈によってモデルに悪影響を及ぼしているためです。</span><span class="sxs-lookup"><span data-stu-id="32934-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="32934-204">一方、Fluent API は、データ永続性インフラストラクチャ レイヤー内でほとんどの規則やマッピングを変更するときに便利な方法となります。エンティティ モデルは汚染されず、永続性インフラストラクチャから切り離されます。</span><span class="sxs-lookup"><span data-stu-id="32934-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="32934-205">Fluent API と OnModelCreating メソッド</span><span class="sxs-lookup"><span data-stu-id="32934-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="32934-206">前述のように、規則やマッピングを変更するために、DbContext クラスで OnModelCreating メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="32934-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="32934-207">eShopOnContainers の注文マイクロサービスでは、必要に応じて、明示的なマッピングと構成が実装されます。次のコードをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32934-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
            
            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

<span data-ttu-id="32934-208">同じ OnModelCreating メソッド内ですべての Fluent API マッピングを設定できますが、そのコードを区切り、エンティティあたり 1 つで複数の構成クラスを与えることをお勧めします。例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32934-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="32934-209">大規模なモデルでは特に、個別の構成クラスを与え、異なる種類のエンティティを構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="32934-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="32934-210">例のコードでは、明示的な宣言とマッピングをいくつか確認できます。</span><span class="sxs-lookup"><span data-stu-id="32934-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="32934-211">ただし、EF Core の規則では、これらのマッピングの多くが自動的に行われます。そのため、実際に必要になるコードはより小さくなります。</span><span class="sxs-lookup"><span data-stu-id="32934-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="32934-212">EF Core の Hi/Lo アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="32934-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="32934-213">先の例のコードで興味深いところは、キーの生成方法として [Hi/Lo アルゴリズム](https://vladmihalcea.com/the-hilo-algorithm/)が使用されていることです。</span><span class="sxs-lookup"><span data-stu-id="32934-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="32934-214">Hi/Lo アルゴリズムは一意のキーが必要なときに便利です。</span><span class="sxs-lookup"><span data-stu-id="32934-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="32934-215">手短に言えば、Hi/Lo アルゴリズムでは、一意の識別子がテーブル行に割り当てられます。データベースにすぐに行を格納することには依存しません。</span><span class="sxs-lookup"><span data-stu-id="32934-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="32934-216">連続する通常のデータベース ID と同様に、識別子の使用をすぐに開始できます。</span><span class="sxs-lookup"><span data-stu-id="32934-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="32934-217">Hi/Lo アルゴリズムは、データベースではなく、クライアント側で安全な ID を生成するメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="32934-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="32934-218">ここでの*安全*とは競合がないという意味です。</span><span class="sxs-lookup"><span data-stu-id="32934-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="32934-219">このアルゴリズムは次の理由から興味深いものになっています。</span><span class="sxs-lookup"><span data-stu-id="32934-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="32934-220">Unit of Work パターンを壊しません。</span><span class="sxs-lookup"><span data-stu-id="32934-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="32934-221">その他の DBMS でシーケンス ジェネレーターが行うようなラウンド トリップが必要ありません。</span><span class="sxs-lookup"><span data-stu-id="32934-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="32934-222">GUID を利用する手法とは異なり、人間にわかりやすい識別子が生成されます。</span><span class="sxs-lookup"><span data-stu-id="32934-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="32934-223">EF Core は ForSqlServerUseSequenceHiLo メソッドで [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) に対応しています。先の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32934-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="32934-224">プロパティの代わりにフィールドをマッピングする</span><span class="sxs-lookup"><span data-stu-id="32934-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="32934-225">EF Core 1.1 以降で利用可能になったこの機能では、列をフィールドに直接マッピングできます。</span><span class="sxs-lookup"><span data-stu-id="32934-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="32934-226">エンティティ クラスのプロパティを使用せず、テーブルからフィールドに列をマッピングできます。</span><span class="sxs-lookup"><span data-stu-id="32934-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="32934-227">この方法の一般的な使用例に、エンティティの外部からアクセスする必要のない、内部状態用のプライベート フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="32934-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="32934-228">1 つのフィールドにマッピングすることも、`List<>` フィールドなど、コレクションにマッピングすることもできます。</span><span class="sxs-lookup"><span data-stu-id="32934-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="32934-229">この点については、ドメイン モデル クラスのモデリングについて説明したときにお伝えしました。ここでは、先のコードで強調表示されていた `PropertyAccessMode.Field` 構成でそのマッピングが実行されるしくみを確認できます。</span><span class="sxs-lookup"><span data-stu-id="32934-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="32934-230">インフラストラクチャ レベルでは非表示のシャドウ プロパティを EF Core で使用する</span><span class="sxs-lookup"><span data-stu-id="32934-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="32934-231">EF Core のシャドウ プロパティは、エンティティ クラス モデルに存在しないプロパティです。</span><span class="sxs-lookup"><span data-stu-id="32934-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="32934-232">これらのプロパティの値と状態は、インフラストラクチャ レベルの [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) で汚染されないように保守管理されます。</span><span class="sxs-lookup"><span data-stu-id="32934-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="32934-233">仕様パターンを実装する</span><span class="sxs-lookup"><span data-stu-id="32934-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="32934-234">先にデザイン セクションで紹介したように、仕様パターン (フルネームは Query-仕様パターン) は、任意の並べ替え/ページング ロジックと共にクエリの定義を置く場所として作られる Domain-Driven Design パターンです。</span><span class="sxs-lookup"><span data-stu-id="32934-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="32934-235">仕様パターンによって、オブジェクトのクエリが定義されます。</span><span class="sxs-lookup"><span data-stu-id="32934-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="32934-236">たとえば、製品を検索するページ クエリをカプセル化するために、必要な入力パラメーター (pageNumber、pageSize、filter など) を受け取る PagedProduct 仕様を作成できます。</span><span class="sxs-lookup"><span data-stu-id="32934-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="32934-237">その後、Repository のメソッド (usually a List() overload) は ISpecification を受け取り、その仕様に基づき、予想されるクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="32934-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="32934-238">一般的な仕様インターフェイスの例として、[eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb) から抜粋した次のコードをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32934-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb 

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="32934-239">一般的な仕様の基底クラスの実装は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="32934-239">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb
 
public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } = 
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();
 
    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }
    
    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="32934-240">次の仕様では、買い物かごの ID か買い物かごが属する購入者の ID が指定されると、買い物かごエンティティが 1 つ読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="32934-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="32934-241">買い物かごの項目コレクションを[一括で読み込み](https://docs.microsoft.com/en-us/ef/core/querying/related-data)ます。</span><span class="sxs-lookup"><span data-stu-id="32934-241">It will [eager load](https://docs.microsoft.com/en-us/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="32934-242">最後になりますが、一般的 EF リポジトリでこのような仕様を利用し、指定されたエンティティ型 T に関連するデータにフィルターを適用し、一括で読み込むしくみを下の画像で確認してください。</span><span class="sxs-lookup"><span data-stu-id="32934-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));
 
    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));
 
    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```
<span data-ttu-id="32934-243">この仕様はフィルタリング ロジックをカプセル化するだけでなく、データを入力するプロパティなど、返すデータのシェイプも指定できます。</span><span class="sxs-lookup"><span data-stu-id="32934-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="32934-244">リポジトリから IQueryable を返すことはお勧めされませんが、リポジトリ内で使用し、結果の集まりを作ることには何の問題もありません。</span><span class="sxs-lookup"><span data-stu-id="32934-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="32934-245">上の List メソッドでこの手法を確認できます。中間の IQueryable 式を利用してクエリのインクルード リストを作成し、それから最後の行にある仕様の基準に合わせてクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="32934-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="32934-246">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="32934-246">Additional resources</span></span>

-   <span data-ttu-id="32934-247">**テーブル マッピング**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="32934-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="32934-248">**HiLo を使用して Entity Framework Core でキーを生成する**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="32934-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="32934-249">**バッキング フィールド**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="32934-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="32934-250">**Steve Smith。Entity Framework Core のカプセル化されたコレクション**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="32934-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="32934-251">**シャドウ プロパティ**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="32934-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="32934-252">**仕様パターン**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="32934-252">**The Specification pattern**
[*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="32934-253">[前] (infrastructure-persistence-layer-design.md) [次] (nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="32934-253">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>

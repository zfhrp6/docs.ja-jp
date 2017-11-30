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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Entity Framework のコア インフラストラクチャの永続性レイヤーの実装

SQL Server、Oracle、または PostgreSQL などのリレーショナル データベースを使用する場合、推奨される方法は、Entity Framework (EF) に基づく、永続性レイヤーを実装するがします。 EF は、LINQ をサポートしているし、モデルでは、できるだけでなく、データベースに簡略化された永続化する厳密に型指定されたオブジェクトを提供します。

Entity Framework では、.NET Framework の一部として長い歴史があります。 .NET Core を使用する場合も、.NET Core と同じ方法で Windows または Linux で実行するため、Entity Framework Core を使用してください。 EF Core とは、Entity Framework、フット プリントがはるかに小さいとパフォーマンスで重要な機能強化を使用して実装の完全な書き直しです。

## <a name="introduction-to-entity-framework-core"></a>Entity Framework Core の概要

Entity Framework (EF) のコアは軽量で拡張性があると、クロスプラット フォームのバージョンの人気のある Entity Framework データ アクセス テクノロジです。 これは、.NET Core の 2016 中旬で導入されました。

EF Core の概要については、Microsoft のドキュメントで使用可能なは既に、ためここで単に提供されていますその情報へのリンク。

#### <a name="additional-resources"></a>その他の技術情報

-   **Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **ASP.NET Core と Visual Studio を使用して Entity Framework Core の概要**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **DbContext クラス**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **EF コア & EF6.x 比較**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>DDD の観点からエンティティ フレームワークのコア インフラストラクチャ

DDD の観点から EF の重要な機能は、EF 用語では POCO とも呼ばれます、POCO ドメイン エンティティを使用する機能*コード優先エンティティ*です。 POCO ドメイン エンティティを使用する場合、ドメイン モデル クラスは永続化非依存、次の[持続性の無視が適用](http://deviq.com/persistence-ignorance/)と[インフラストラクチャの無視が適用](https://ayende.com/blog/3137/infrastructure-ignorance)原則です。

DDD パターンごとは任意のコレクションにアクセスするとき、検証、およびルールは不変制御できるようにドメインの動作とルール自体、エンティティ クラス内でカプセル化します。 したがって、ddd でエンティティまたはオブジェクトの値は、子のコレクションへのパブリック アクセスを許可することはお勧めできません。 代わりに、その場合に制御する方法とタイミング、フィールドやプロパティ コレクションを更新できるメソッドとどのような動作と操作を実行するを公開します。

DDD 要件を満たすために EF コア 1.1 でにパブリックおよびプライベートの setter のプロパティではなく、エンティティ内プレーンなフィールドを持つことができます。 外部からアクセスできるようにエンティティ フィールドしたくない場合は、属性またはプロパティではなくフィールドだけ作成できます。 クリーナーこうしたい場合は、プライベート set アクセス操作子を使用する必要はありません。

同様の方法で保持できますコレクションへのアクセスの読み取り専用 IEnumerable として型指定されたパブリック プロパティを使用して&lt;T&gt;、コレクションのプライベート フィールドのメンバーで補助されている (リストと同様に&lt;&gt;) で、永続化の EF に依存するエンティティ。 Entity Framework の以前のバージョンには、ICollection をサポートするコレクションのプロパティが必要な&lt;T&gt;、親エンティティ クラスを使用してすべての開発者が追加またはそのプロパティのコレクションから項目を削除できなかったことです。 DDD で推奨されたパターンに対してその可能性になります。

次のコード例に示すように、読み取り専用の IEnumerable オブジェクトを公開する際プライベート コレクションを使用することができます。

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

読み取り専用としてリストを使用して OrderItems プロパティにアクセスするだけことに注意してください&lt;&gt;です。AsReadOnly() です。 このメソッドは、外部データの更新に対して保護されているように、プライベートの一覧をラップする読み取り専用のラッパーを作成します。 新しいコレクションのすべてのアイテムのコピー先があるないため ToList メソッドを使用するよりもはるかに低コストでは、します。代わりに、ラッパーのインスタンスの 1 つのヒープ割り当て操作を実行します。

EF コアは、ドメイン モデルを行うことがなく、ドメイン モデルを物理データベースにマップする方法を提供します。 永続レイヤー、マップされた操作が実装されているために、純粋な .NET POCO、コードを勧めします。 そのマッピング操作では、データベースへのフィールド マッピングを構成する必要があります。 OnModelCreating メソッドの次の例では、強調表示されたコードは、そのフィールドを介して OrderItems プロパティにアクセスする EF コアを示します。

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

リストがあった場合と同様に、OrderItem エンティティが永続化プロパティの代わりにフィールドを使用するときに&lt;OrderItem&gt;プロパティです。 ただし、注文に新しい項目を追加するため、1 つのアクセサー (AddOrderItem メソッド) を公開します。 その結果、動作とデータが一緒に扱わし、ドメイン モデルを使用するアプリケーション コード全体に適用されます。

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Entity Framework のコアでカスタムのリポジトリを実装します。

実装レベルでは、リポジトリは単なるクラス (EF コアで DBContext) の作業単位によってコーディネートされたデータ永続化のコードでクラスを次に示すように、更新プログラムを実行するとき。

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

ドメイン モデル層から IBuyerRepository インターフェイスを取得することを注意してください。 ただし、リポジトリの実装は、永続化とインフラストラクチャ レイヤーで行われます。

EF DbContext は、依存関係の挿入をコンス トラクターでは取得されます。 複数のリポジトリ、同じ HTTP 要求のスコープ内で、その既定の有効期間 (ServiceLifetime.Scoped) (これも明示的に設定できますサービス IoC コンテナーにご協力に感謝間で共有されます。AddDbContext&lt;&gt;)。

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>(更新プログラムまたはクエリではなくトランザクション) リポジトリに実装するメソッド

各リポジトリ クラス内では、その関連する集計が含まれるエンティティの状態を更新する永続化メソッドを配置する必要があります。 集計と、関連するリポジトリの間の一対一のリレーションシップがある注意してください。 集計ルート エンティティ オブジェクトが埋め込まれている、EF グラフ内の子エンティティを考慮します。 たとえば、購入者は、関連する子エンティティとして複数の支払方法があります。

EShopOnContainers で順序付けマイクロ サービスの実行方法については、CQS/CQRS に基づいても、ので、ほとんどのクエリでは、カスタム リポジトリで実装されていません。 開発者では、クエリと集計、集計、および DDD ごとのカスタムのリポジトリで一般に課せられる制限なしのプレゼンテーション層に必要な結合を作成する自由があります。 このガイドで提案されたカスタムのリポジトリのほとんどにいくつかの更新やトランザクション メソッドですが、クエリ メソッドだけを更新するデータを取得するために必要です。 たとえば、アプリケーションは、注文に関連する新しい buyer を作成する前に、特定の購入者が存在するかどうか知っておく必要があるために、BuyerRepository リポジトリは、FindAsync メソッドを実装します。

ただし、プレゼンテーション層またはクライアント アプリに送信するデータを取得する実際のクエリ メソッドが実装されて Dapper を使用して、柔軟なクエリに基づく CQRS クエリで、説明したようにします。

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>EF DbContext を直接使用するとカスタム リポジトリを使用します。

Entity Framework DbContext クラスは、作業単位とリポジトリ パターンに基づいて、およびとして使用できます、コードから直接など、ASP.NET Core MVC コント ローラーからです。 つまり方法 eShopOnContainers で CRUD カタログ マイクロ サービスのように、最も単純なコードを作成することができます。 必要がある場合、最も単純なコード可能な場合 DbContext クラスを直接使用する多くの開発者と同様です。

ただし、カスタムのリポジトリを実装する複数の利点より複雑な microservices またはアプリケーションを実装する場合。 作業単位とリポジトリ パターンは、アプリケーション層とドメイン モデル層から切り離され、インフラストラクチャの永続性レイヤーをカプセル化するものです。 これらのパターンを実装すると、データベースへのアクセスをシミュレートするモック リポジトリの使用を容易にするためです。

図 9-18 でそのリポジトリのモック作成を簡単にするためのリポジトリを使用すると (EF DbContext を使用して直接) リポジトリを使用していない間の相違点を確認できます。

![](./media/image19.png)

**図 9 18**です。 プレーンな DbContext ではなくカスタムのリポジトリを使用します。

モックする場合は、複数の代替にはあります。 だけでリポジトリを模擬表示でしたか、全体の作業単位を模擬表示する可能性があります。 通常モック リポジトリだけであっても、および複雑さを抽象化し、全体の作業単位を模擬表示通常は必要ありません。

その後、アプリケーション層の説明とは、ASP.NET Core での依存関係の挿入のしくみし、リポジトリを使用する場合の実装方法がわかります。

つまり、カスタム リポジトリを使用すると、データ層の状態の影響を受けない単体テストのコードをより簡単にテストできます。 また、Entity Framework で実際のデータベースにアクセスするテストを実行する場合はありません単体テストは統合テストがとても遅くなります。

DbContext を直接を使用していた場合単体テストの予測可能なデータをメモリ内の SQL Server を使用して単体テストを実行する必要があります唯一の選択肢になります。 リポジトリ レベルと同様に、モック オブジェクトと偽のデータを制御することはできません。 もちろん、MVC コント ローラーを常にテストする可能性があります。

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>EF DbContext および IUnitOfWork インスタンスの有効期間、IoC コンテナー内

(IUnitOfWork オブジェクトとして公開される) DbContext オブジェクトは、HTTP 要求のスコープ内の複数のリポジトリの間で共有する必要があります。 たとえば、これは、true の場合実行されている操作は複数の集計、または単に対処する必要がある複数のリポジトリを使用しているためです。 IUnitOfWork インターフェイスが EF 型ではなく、ドメインの一部であることは言うまでも重要です。

これを実行するためには、DbContext オブジェクトのインスタンスに、そのサービスの有効期間を ServiceLifetime.Scoped に設定が必要です。 これは、サービスに DbContext を登録するときに既定の有効期間です。ASP.NET Core Web API プロジェクトに Startup.cs ファイルの ConfigureServices メソッドから IoC コンテナーで AddDbContext です。 次に例を示します。

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

DbContext インスタンス化モードは、ServiceLifetime.Transient または ServiceLifetime.Singleton として構成する必要がありますされません。

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>IoC コンテナーでリポジトリ インスタンスの有効期間

同様の方法でリポジトリの有効期間が通常 (InstancePerLifetimeScope Autofac で) スコープとして設定する必要があります。 ある可能性もスコープを指定した有効期間を使用する場合に、サービスが一時的な (Autofac で InstancePerDependency) がにおいてはメモリ内で効率的であります。

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

原因となる、リポジトリのシングルトン有効期間を使用する重大な同時実行の問題、DbContext に設定されているときに注意 (InstancePerLifetimeScope) 有効期間 (DBContext の既定の有効期間) のスコープ設定されます。

#### <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET MVC アプリケーションのリポジトリと作業パターンの単位を実装する**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen です。リポジトリの実装方法が口ひげ、Entity Framework でのパターンし、チェーン**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesar de la Torre。Autofac IoC コンテナー インスタンスのスコープを持つ ASP.NET Core IoC コンテナー サービスの有効期間を比較する**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>テーブルのマッピング

テーブル マッピングからクエリを実行するテーブルのデータを識別し、データベースに保存します。 以前ドメイン エンティティ (たとえば、製品または順序ドメイン) を使用して、関連するデータベース スキーマを生成する方法を説明します。 EF は強くという概念に設計された*規則*です。 「どのようなテーブルの名前になりますか。」のような規則アドレス質問 「どのようなプロパティは、主キー」または 規則は、従来の名前に基づく通常 — たとえばが、一般に、主キー id を持つ最後のプロパティ

慣例により、各エンティティ設定されます、DbSet と同じ名前のテーブルにマップする&lt;TEntity&gt;派生のコンテキストにエンティティを公開するプロパティです。 場合ありません DbSet&lt;TEntity&gt;値が指定されたエンティティのクラス名を使用します。

### <a name="data-annotations-versus-fluent-api"></a>Fluent API ではなくデータ注釈

その他の多くの EF コア規則があり、それらのほとんどは、データ注釈または Fluent API、OnModelCreating メソッド内に実装を使用して変更できます。

データ注釈は DDD の観点からより侵入的な方法は、これ自体、エンティティ モデルのクラスに使用する必要があります。 これは、インフラストラクチャのデータベースに関連するデータ注釈を使用したモデルを行うがあるためです。 その一方で、Fluent API は、完全であり、永続化インフラストラクチャから切り離されたエンティティ モデルが表示されるように、ほとんどの規則と、データの永続化インフラストラクチャ レイヤー内のマッピングを変更する便利な方法です。

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API と OnModelCreating メソッド

前述のように、規則とのマッピングを変更するために使用できます OnModelCreating メソッドで DbContext クラス。 次の例では、方法を使う eShopOnContainers で順序付けマイクロ サービスを示します。

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

同じ OnModelCreating メソッド内のすべての Fluent API マッピングを設定する可能性がありますが、そのコードをパーティション分割を用意し、エンティティごとに 1 つ、複数の submethods ことをお勧めの例で示すようにします。 特に大規模なモデルは、指定してもかまいません別のエンティティの種類を構成する別のソース ファイル (静的クラス) を持つことをお勧めします。

コードの例では、明示的なです。 ただし、EF コア規則ので、同じことを実現するために作成することも、実際のコードが大幅に小さくなりますのほとんどは、自動的には。

### <a name="the-hilo-algorithm-in-ef-core"></a>EF コアでやあ/Lo アルゴリズム

上記の例のコードでの特徴を使用する、[やあ/Lo アルゴリズム](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/)キーの生成方法として。

やあ/Lo アルゴリズムは、一意なキーが必要な場合に便利です。 概要、としては、やあ-Lo アルゴリズムは、中にないによっては、データベースに行を格納すると、すぐに、テーブルの行に一意の識別子を割り当てます。 これにより、正規シーケンシャル データベース Id とが発生するとすぐに、識別子の使用を開始できます。

やあ/Lo アルゴリズムでは、データベースではなく、クライアント側での安全な Id を生成するためのメカニズムについて説明します。 *安全な*このコンテキストでの競合なしことを意味します。 このアルゴリズムは、これらの理由から興味深い。

-   作業単位のパターンは中断されません。

-   その他の Dbms で操作を行う方法のシーケンス ジェネレーターのラウンド トリップは不要です。

-   Guid を使用する手法とは異なりの人間が判読できる id を生成します。

EF コアをサポートしている[HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo メソッドで、前の例で示すようにします。

### <a name="mapping-fields-instead-of-properties"></a>プロパティではなくフィールドのマッピング

フィールドを列にマップする EF コア 1.1 の機能を使用可能であればエンティティ クラスの任意のプロパティを使用しないと、フィールドをテーブルから列をマップするだけです。 そのための一般的な用途を内部状態のプライベート フィールドをエンティティの外部からアクセスする必要がないとなります。

EF 1.1 には、データベース内の列に関連するプロパティを持たないフィールドをマップする方法がサポートされています。 これを行う 1 つのフィールドを持つかコレクションでは、リストのようにも&lt;&gt;フィールドです。 このポイントが前述ドメイン モデル クラスをモデリングについて説明しましたが、前のコードで強調表示されている PropertyAccessMode.Field 構成でそのマッピングを実行する方法を確認できます。

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>インフラストラクチャ レベルで非表示の Id の値のオブジェクトでシャドウ プロパティの使用

EF Core でシャドウ プロパティは、エンティティ クラス モデルに存在しないプロパティです。 値とこれらのプロパティの状態が純粋に保持されます、 [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker)インフラストラクチャ レベルでのクラスです。

DDD の観点からは、シャドウ プロパティは、シャドウ プロパティの主キーと ID を非表示にして値オブジェクトを実装する便利な方法です。 これは、値オブジェクトの id のないため、重要な (少なくとも、する必要はありません ID ドメイン モデル レイヤーにおいて値オブジェクトを整形するときに)。 ここでのポイントは EF コアの現在のバージョンの時点で EF コアがないとして値オブジェクトを実装する方法[複合型](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx)EF で利用できるように、6.x です。 現在シャドウ プロパティとして設定隠し ID (主キー) を持つエンティティとして値オブジェクトを実装する必要があるためにです。

わかるように、[アドレス値オブジェクト](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)eShopOnContainers でアドレス モデルに表示されない、ID:

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

背後でを行う必要が EF コアが、データベース テーブルには、このデータを永続化できるように、ID を入力します。 作業を行うことの ConfigureAddress メソッド内で、 [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) EF インフラストラクチャ コードを使用してドメイン モデルを汚染おはないため、インフラストラクチャ レベルでのクラスです。

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

#### <a name="additional-resources"></a>その他の技術情報

-   **テーブル マッピング**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **HiLo を使用して Entity Framework のコアを使用してキーを生成する**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **バッキング フィールド**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith です。Entity Framework のコア内のコレクションをカプセル化された**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **プロパティをシャドウ**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[前](インフラストラクチャ-永続化のレイヤー-design.md) [次へ] (nosql-データベースの永続化-infrastructure.md)

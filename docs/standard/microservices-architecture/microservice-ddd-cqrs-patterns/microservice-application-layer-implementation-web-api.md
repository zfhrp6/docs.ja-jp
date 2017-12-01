---
title: "Web API を使用してマイクロ サービスのアプリケーション レイヤーの実装"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Web API を使用してマイクロ サービスのアプリケーション レイヤーの実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>Web API を使用してマイクロ サービスのアプリケーション レイヤーの実装

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>依存関係の挿入を使用して、アプリケーション層にインフラストラクチャ オブジェクトを挿入するには

前述のように、アプリケーション層は、アイテムを作成するなど、Web API プロジェクトまたは MVC web アプリケーション プロジェクト内の一部として実装できます。 ASP.NET Core でビルドされたマイクロ サービスの場合、アプリケーション レイヤー場合、通常は、Web API ライブラリです。 今後の ASP.NET Core (のインフラストラクチャと、コント ローラー) から、カスタムのアプリケーション層コードから分離する場合は、別のクラス ライブラリで、アプリケーション層を配置することもできませんが、省略可能。

たとえば、順序マイクロ サービスのアプリケーション層のコードは、の一部として実装されて直接、 **Ordering.API**プロジェクト (ASP.NET Core Web API プロジェクト) に示す図 9 19 として。

![](./media/image20.png)

**図 9-19**です。 Ordering.API ASP.NET Core Web API プロジェクトで、アプリケーション層

ASP.NET Core を含む、単純な[組み込み IoC コンテナー](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)既定では、コンス トラクターの挿入をサポートする (IServiceProvider インターフェイスによって表される) と ASP.NET により、特定のサービスが DI を介して使用できます。 ASP.NET Core という用語を使用して*サービス*の DI から挿入されるを登録する型。 ConfigureServices クラス メソッドのアプリケーションの起動時には、組み込みのコンテナーのサービスを構成します。 依存関係は、型が必要なサービスで実装されます。

通常、インフラストラクチャ オブジェクトを実装する依存関係を挿入します。 挿入する非常に一般的な依存関係は、リポジトリです。 他のインフラストラクチャの依存関係がある場合を挿入することできます。 単純な実装は、挿入することでした直接作業単位パターン オブジェクト (EF DbContext オブジェクト) の場合は、DBContext は、インフラストラクチャの持続性のオブジェクトの実装でもあるため。

次の例では、.NET Core は、コンス トラクターによって必要なリポジトリ オブジェクトを挿入する方法がわかります。 クラスは、次のセクションで取り上げるコマンドです。

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

クラスは、トランザクションを実行し、状態の変更を保持する挿入されたリポジトリを使用します。 またはそのクラスが ASP.NET Core Web API コント ローラー メソッドでは、コマンド ハンドラーであるかどうかは関係ありません[DDD アプリケーション サービス](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)です。 最終的には、コマンド ハンドラーのような方法でリポジトリ、ドメイン エンティティ、およびその他のアプリケーションの調整を使用する単純なクラスです。 依存関係インジェクション動作が、同じクラスに対してはすべて、説明したように、DI を使用する例のようにに基づいて、コンス トラクターです。

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>依存関係の実装の種類とのインターフェイスまたは抽象化を登録します。

コンス トラクターで挿入されたオブジェクトを使用する前に、インターフェイス、および DI を通じて、アプリケーション クラスに挿入されたオブジェクトを生成するクラスを登録する場所を知る必要があります。 (DI のようにに基づいて、コンス トラクターは、上記のようにします)。

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>ASP.NET Core によって提供される組み込み IoC コンテナーの使用

ASP.NET Core によって提供される組み込み IoC コンテナーを使用する場合は、ConfigureServices メソッドを次のコードのように、Startup.cs ファイルに挿入するかの種類を登録します。

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

最も一般的なパターンの種類を IoC コンテナーに登録することは、型のペアを登録するときに、インターフェイスとその関連実装クラス。 任意のコンス トラクターを介して IoC コンテナーからオブジェクトを要求する場合は、インターフェイスの特定の型のオブジェクトを要求します。 たとえば、前の例では、最後の行を示す IMyCustomRepository (インターフェイスまたは抽象型) に依存関係、コンス トラクターのいずれかの場合は、IoC コンテナーは MyCustomSQLServerRepository 実装のインスタンスを挿入するが、クラス。

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>種類の自動登録の Scrutor ライブラリの使用

DI を .NET Core を使用する場合は、アセンブリをスキャンし、規約によって自動的にその型を登録することにする可能性があります。 この機能では、ASP.NET Core で現在使用できません。 ただし、使用することができます、 [Scrutor](https://github.com/khellang/Scrutor)ライブラリです。 この方法は、重複除去は、IoC コンテナーに登録する必要がある型がある場合に便利です。

#### <a name="additional-resources"></a>その他の技術情報

-   **Matthew キングです。Scrutor をサービスに登録する**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang です。Scrutor です。** GitHub のリポジトリ。
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>IoC コンテナーとして Autofac を使用します。

また追加 IoC コンテナーを使用してし、を使用して eShopOnContainers で順序付けマイクロ サービスと同様に、ASP.NET Core パイプラインに差し込みます[Autofac](https://autofac.org/)です。 Autofac を使用する場合は、ここで、型では、複数のクラス ライブラリに分散アプリケーションの種類を割り当てることもに応じて複数のファイルの登録の種類を分割することは、モジュールを使用して型通常登録します。

たとえば、次は、 [Autofac アプリケーション モジュール](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)の[Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API)を挿入する種類のプロジェクトです。

```csharp
public class ApplicationModule
    :Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

登録プロセスおよび概念により、組み込みの ASP.NET Core iOS コンテナーの種類を登録する方法とよく似ていますが、構文 Autofac を使用する場合は少し異なります。

コード例では、実装クラス OrderRepository と共に IOrderRepository の抽象型が登録されます。 これは、コンス トラクターが IOrderRepository 抽象またはインターフェイスの依存関係を宣言しているときに IoC コンテナーは OrderRepository クラスのインスタンスを挿入するがあることを意味します。

インスタンスのスコープの種類は、同じサービスまたは依存関係に対する要求間でインスタンスを共有する方法を決定します。 依存関係の要求が行われると、IoC コンテナーは、次を返すことができます。

-   有効期間の範囲ごとに 1 つのインスタンス (として ASP.NET Core IoC コンテナーで参照される*スコープ*)。

-   依存関係ごとに新しいインスタンス (として ASP.NET Core IoC コンテナーで参照される*一時的な*)。

-   IoC コンテナーを使用してすべてのオブジェクト間で共有される 1 つのインスタンス (として ASP.NET Core IoC コンテナーで参照される*シングルトン*)。

#### <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Core の依存関係の挿入の概要**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac です。** 正式なドキュメントです。
    [*http://docs.autofac.org/en/latest/*](http://docs.autofac.org/en/latest/)

-   **Cesar de la Torre。Autofac IoC コンテナー インスタンスのスコープを持つ ASP.NET Core IoC コンテナー サービスの有効期間を比較する**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>コマンドとコマンド ハンドラーのパターンを実装します。

例では、DI を通じてコンス トラクター、前のセクションに示すように、IoC コンテナーがクラスでコンス トラクターでリポジトリを挿入することができます。 しかし、正確に場所が、挿入されたか。 単純な Web API (たとえば、eShopOnContainers で、カタログ マイクロ サービス) で挿入することに MVC コント ローラー レベルのコント ローラーのコンス トラクター内で。 ただし、このセクションの最初のコードで (、 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) eShopOnContainers Ordering.API サービスからのクラス)、特定のコマンドのコンス トラクターは、操作には依存関係の挿入ハンドラー。 説明お知らせ、どのようなコマンド ハンドラーは、それを使用します。

コマンドのパターンは本質的に、このガイドの前半で導入された CQRS のパターンに関連します。 CQRS には、2 つの辺があります。 最初の領域が簡略化されたクエリを使用して、クエリ、 [Dapper](https://github.com/StackExchange/dapper-dot-net)が先に説明したマイクロ ORM です。 2 番目の領域は、トランザクションの開始点と、入力チャネルからサービスの外部のコマンドです。

図 9-20 を示すように、パターンに基づきますがクライアント側からのコマンドを受け付けて処理ルールに基づく、ドメイン モデル、および最後にトランザクションの状態を保持します。

![](./media/image21.png)

**図 9-20**です。 コマンドまたは CQRS パターンの「トランザクション側」の概要を表示

### <a name="the-command-class"></a>コマンド クラス

コマンドは、システムの状態を変更するアクションを実行するシステムの要求です。 コマンドは、命令型、1 回だけ処理する必要があります。

コマンドが課題であるためは通常 (「作成」または「更新」など) の命令型気分に動詞を使用して名前付きおよび CreateOrderCommand など、集計の種類があります。 イベントとは異なり、コマンドはできません。 過去のファクト要求だけをそのため、拒否される可能性があります。

コマンドは、プロセス マネージャーが操作を実行する集計を指定する場合、要求を開始したユーザーの結果として、UI とは、プロセス マネージャーから取得できます。

コマンドの重要な特性は、それを処理する 1 回だけを単一の受信者によってです。 これは、コマンドが単一のアクションまたはアプリケーションで実行するトランザクションであるためです。 など、同じ順序の作成コマンド必要があります処理できませんも複数回です。 これは、コマンドとイベントの重要な違いです。 多くのシステムや microservices 興味を持つイベントのために、イベントが複数回を処理できません可能性があります。

さらに、コマンドが、コマンドは、べき等ではない場合に、1 回だけに処理する重要なです。 コマンドでは、べき等が実行されることが複数回、コマンドの性質があるため、またはシステムが、コマンドを処理する方法のため、結果を変更することがなく場合です。

コマンドをすることをお勧めし、ドメインのビジネス ルールおよび不変条件の下の方が良い場合に、べき等を更新します。 たとえば、使用するには同じ例では、何らかの理由 (再試行ロジックやハッキングなど)、同じ CreateOrder コマンドに達した場合、システム複数回できますを識別し、複数の注文を作成しないことを確認してください。 そのためには、いくつかの種類の操作の id をアタッチし、コマンドまたは更新プログラムは既に処理されているかどうかを識別する必要があります。

単一の受信者にコマンドを送信します。コマンドを発行しません。 発行は、ファクトを状態統合イベント-問題が発生した可能性がありますなることのイベント レシーバーの興味深いです。 イベントの場合は、パブリッシャーにはレシーバー取得イベントか、どのように行うかについての問題はありません。 統合イベントは前のセクションで既に導入話は別です。

コマンドは、データ フィールドまたはコマンドを実行するために必要なすべての情報を含むコレクションを含むクラスに実装されます。 コマンドは、特別な種類のデータ転送オブジェクト (DTO) を変更またはトランザクションを要求に使用される具体的には 1 つです。 コマンド自体は、正確に、必要な情報をコマンド、および何詳細を処理するために基づきます。

次の例では、簡略化された CreateOrderCommand クラスを示します。 これは eShopOnContainers で順序付けマイクロ サービスで使用されている変更できないコマンドです。

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

基本的には、コマンド クラスには、ドメイン モデル オブジェクトを使用してビジネス トランザクションの実行に必要なすべてのデータが含まれています。 したがって、コマンドは、読み取り専用のデータと動作はありませんが含まれているデータ構造だけです。 コマンドの名前では、その目的を示します。 C のような多くの言語で\#コマンドは、クラスとして表されますが、実際のオブジェクト指向という意味では true。 クラスではありません。

その他の特徴として予想される使用率が、ドメイン モデルによって直接処理されるためコマンドは、変更できません。 投影の有効期間中に変更する必要はありません。 C で\#クラス、不変性は、set アクセス操作子またはその他の内部状態を変更する方法をなくすことによって実現できます。

たとえば、注文を作成するためのコマンド クラス可能性がありますは似ていますがデータの観点から注文を作成するのに可能性があります、同じ属性必要ありません。 インスタンスの順序はまだ作成されていないために、CreateOrderCommand には、注文 ID はありません。

多くのコマンド クラスを単純な場合、変更する必要があるいくつかの状態に関するいくつかのフィールドのみを必要とすることができます。 大文字と小文字"のプロセスから"注文の状態を変更する場合は「支払い」または「出荷」には、次のようなコマンドを使用してになります。

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

その UI 要求オブジェクトになります、コマンド dtos の使用とは別の一部の開発者が、基本設定だけで済みます。 それほど多くありません付加価値と面倒に分離して、オブジェクトが同じ図形とほぼ同様です。 たとえば、eShopOnContainers、コマンドをクライアント側から直接取得します。

### <a name="the-command-handler-class"></a>コマンド ハンドラー クラス

各コマンドの特定のコマンド ハンドラー クラスを実装する必要があります。 パターンのしくみがあり、コマンド オブジェクト、ドメイン オブジェクトおよびインフラストラクチャのリポジトリ オブジェクトを使用します。 コマンド ハンドラーは、CQRS と DDD の観点から、アプリケーション レイヤーの中心となる実際には。 ただし、ドメイン クラス内ですべてのドメイン ロジックを含める必要があります: 集計ルート (ルート エンティティ) 内で子エンティティまたは[ドメイン サービス](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)、コマンド ハンドラー内ではなく、アプリケーションからのクラスであるが、レイヤーです。

コマンド ハンドラーでは、コマンドを受信し、使用される集計結果を取得します。 結果はのコマンドを正常に実行または例外のいずれかにする必要があります。 例外の場合は、システム状態を変更されず必要があります。

コマンド ハンドラーは、次の手順に通常を受け取ります。

-   DTO と同様に、コマンド オブジェクトを受け取ります (から、[媒介](https://en.wikipedia.org/wiki/Mediator_pattern)または他のインフラストラクチャ オブジェクト)。

-   コマンドが (媒介によって認められていない) 場合は、有効であることを検証します。

-   現在のコマンドの対象となっている集計ルート インスタンスがインスタンス化します。

-   集計のルート インスタンスで、コマンドから、必要なデータを取得するメソッドを実行します。

-   これには、集計、関連するデータベースへの新しい状態が永続化します。 この最後の操作は、実際のトランザクションです。

通常、コマンド ハンドラーは、その集計ルート (ルート エンティティ) によって、1 つの集計について説明します。 複数の集計は、1 つのコマンドの受信の影響を受ける必要があります、複数の集計の状態またはアクションに伝達するのにドメインのイベントを使用できます。

ここでの重要なポイントは、コマンドの処理中は、すべてのドメイン ロジックが、ドメイン モデル (集計) の場合、完全にカプセル化された単体テストの準備が整って内する必要があります。 コマンド ハンドラーは、ドメイン モデルをデータベースから取得する方法とは、最後の手順としてへの変更を保持する、モデルが変更されたときに、インフラストラクチャ レイヤー (リポジトリ) の通知にだけ機能します。 このアプローチの利点は、アプリケーションまたはインフラストラクチャ レイヤーは、組み込みレベル (コマンド ハンドラーを Web API は、コードを変更することがなく、分離、完全にカプセル化された、機能豊富な動作上のドメイン モデル内のドメイン ロジックをリファクタリングすることができます。リポジトリなど)。

コマンド ハンドラーが多すぎるロジックで、複雑な場合、コードの匂いをすることができます。 それらを確認し、ドメイン ロジックを検索する場合は、ドメイン オブジェクト (集計ルートと子エンティティ) のメソッドにそのドメインの動作を移動するコードをリファクタリングします。

コマンド ハンドラー クラスの例は、としては、次のコードは、この章の先頭に表示される同じ CreateOrderCommandHandler クラスを示します。 ここで処理する Handle メソッドとドメイン モデル オブジェクト/集計を使用して操作を強調表示されているおです。

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

追加の手順のコマンド ハンドラーを次に示します。

-   集計ルートのメソッドおよび動作を操作するには、コマンドのデータを使用します。

-   内部的にドメイン オブジェクト内でイベントを発生させるドメイン、トランザクションを実行すると、ですが、コマンド ハンドラーの観点からは透過的です。

-   集計の操作の結果が成功した場合、トランザクションの完了後に、統合イベント コマンド ハンドラーを生成します。 (これらがまた生成されるリポジトリなどのインフラストラクチャ クラスによって。)

#### <a name="additional-resources"></a>その他の技術情報

-   **マーク Seemann です。境界、アプリケーションがオブジェクトではなく指向**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries、ApplicationsareNotObject 指向/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **コマンドとイベント**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **コマンド ハンドラー何か。** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard。ドメイン コマンド パターン – ハンドラー**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard。ドメイン コマンド パターン – 検証**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>コマンド処理パイプライン コマンドのハンドラーをトリガーする方法。

次の質問は、コマンド ハンドラーを呼び出す方法を示します。 ASP.NET Core の関連する各コント ローラーから手動で呼び出す可能性があります。 ただし、ことがある方法も組み合わせると、理想的ではありません。

その他の 2 つ主なオプションは、推奨されるオプションですが、次のとおりです。

-   インメモリ媒介パターン成果物です。

-   コント ローラーとハンドラー間の非同期メッセージ キューです。

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>コマンド パイプラインに媒介パターン (メモリ内) を使用します。

図 9-21 で示すように、CQRS アプローチを使用するインテリジェント媒介で、これは、コマンドまたは受信される DTO の種類に基づいて、right コマンド ハンドラーにリダイレクトするほど、メモリ内バスに似ています。 コンポーネント間で 1 つの黒い矢印は、その関連する相互作用と (DI で挿入された多くの場合) 内のオブジェクト間の依存関係を表します。

![](./media/image22.png)

**図 9-21**です。 1 つの CQRS マイクロ サービスでのプロセスで媒介パターンを使用します。

媒介パターンを使用する意味は、エンタープライズ アプリケーションで処理要求取得できることに複雑です。 ログ記録、検証、監査、およびセキュリティのような横断的関心事の開いている数を追加できるようにするには。 このような場合は、媒介パイプラインに依存することができます (を参照してください[媒介パターン](https://en.wikipedia.org/wiki/Mediator_pattern)) これらの余分な動作や横断的関心事の手段を提供します。

仲介者は、このプロセスの「方法」をカプセル化するオブジェクト: 状態に基づいて実行を調整、方法、コマンド ハンドラーが呼び出され、またはハンドラーに提供するペイロード。 媒介コンポーネントを適用できます横断的関心事集中かつ透過的な方法でデコレーターを適用することで (または[動作のパイプライン](https://github.com/jbogard/MediatR/wiki/Behaviors)媒介 v3 以降)。 (詳細については、次を参照してください、[デコレータ パターン](https://en.wikipedia.org/wiki/Decorator_pattern)。)。

デコレーターと動作に似ています[アスペクト指向プログラミング (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)、媒介コンポーネントによって管理される特定のプロセス パイプラインに適用されるのみです。 横断的関心事を実装する AOP の側面がに基づいて適用されます*縦横 weaver:*オブジェクト呼び出しの途中受信に基づくまたはコンパイル時に挿入します。 両方の典型的な AOP アプローチもいいます"マジック、"のように動作する AOP がその作業をどのように表示する簡単ではないためです。 深刻な問題やバグを扱う場合、AOP はデバッグが困難にすることができます。 その一方で、これらデコレーター/動作は明示的なして適用すると、媒介のコンテキストのみでデバッグがはるかに簡単に予測可能なためです。

2 つのサンプル デコレーターを実装しましたマイクロ サービスを順序付け eShopOnContainers でなど、 [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)クラスおよび[ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)クラスです。 デコレーターの実装は、次のセクションで説明します。 今後のバージョンでに eShopOnContainers が移行されますに注意してください[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)に移動する[動作](https://github.com/jbogard/MediatR/wiki/Behaviors)デコレーターを使用する代わりにします。

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>コマンドのパイプラインでメッセージ キュー (アウト プロセス) を使用します。

他の選択肢では、図 9-22 を示すように、また仲買担当者またはメッセージ キュー、に基づいて非同期のメッセージを使用します。 そのオプションは、コマンド ハンドラーの前に右媒介コンポーネントと組み合わせることも可能性があります。

![](./media/image23.png)

**図 9-22**です。 メッセージ キュー (外のプロセスおよびプロセス間通信) を使って CQRS コマンド

2 つのプロセスにパイプラインを分割する必要がありますので、コマンドをさらにそのまま使用するためのキューには、コマンドのパイプラインが複雑になるメッセージを使用して、外部メッセージ キュー経由で接続します。 それでも、スケーラビリティと非同期メッセージングに基づいて、パフォーマンスが向上する必要がある場合、このを使用する必要があります。 図 9-22 の場合は、コント ローラーだけコマンド メッセージをキューにポストし、返すことを検討してください。 コマンド ハンドラーは、自分のペースでメッセージを処理します。 キューの非常に大きな利点は、ハイパー スケーラビリティが必要な株式やその他のシナリオで大量の受信データの場合のようには場合、メッセージ キューがの場合、バッファーとして利用できます。

ただし、メッセージ キューの非同期の性質があるため、コマンドの処理の成否について、クライアント アプリケーションと通信する方法を理解する必要があります。 原則として、「ファイア アンド忘れた」コマンドを使用する必要がありますしないでください。 すべてのビジネス アプリケーションは、かどうか、コマンドは正常に処理または少なくとも確認され、受け入れを知っている必要があります。

したがって、非同期のキューに送信されたコマンドのメッセージを検証した後、クライアントに応答することと、トランザクションを実行した後、操作の結果を返す、インプロセス コマンド プロセスと比較して、システムに複雑さを追加します。 キューを使用して、追加のコンポーネントおよびカスタム通信を必要とは、システムで他の操作結果メッセージを介してコマンドの処理の結果を返す必要があります。

さらに、多くの場合は不要な Burtsev Alexey と Greg Young 内の次の興味深い exchange で説明するようになる一方向のコマンドは、非同期コマンド、[オンラインでの会話](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\]大量のコードの検索を使用して非同期コマンドの処理、または何らかの理由がこれを行うことがなくメッセージング方法の 1 つのコマンド (一部の長い操作を行っていない、外部の非同期コードを実行していないが、アプリケーションをでも交差しません境界をメッセージ バスを使用している)。 この不要な複雑さを導入理由 実際には、今のところコマンド ハンドラーをこれまで、ブロックと CQRS のコード例も、ほとんどの場合でうまく機能します。

\[Greg Young\] \[しています.\]非同期コマンドが存在しません。 実際には別のイベントはします。 送信 me をそのまま使用し、同意する場合は、イベントを発生させる必要がありますに場合は不要になったと処理を行うメッセージが表示します。 これは、何かがなされたメッセージが表示します。 これには最初、わずかに異なるように見えますが、多くの影響があります。

非同期コマンドでは、エラーを示す簡単な方法がないために、システムでは、複雑さが大幅に増加します。 そのため、非同期コマンドは推奨されません以外のスケーリング要件が必要な場合に、または特殊なケースで内部 microservices メッセージングを介して通信するとき。 ような場合、エラーの個別のレポートと回復のシステムを設計する必要があります。

EShopOnContainers の初期のバージョンで、HTTP 要求から開始され、媒介パターンによって、同期コマンドの処理を使用することにしました。 簡単にすることができるように、処理の成否を返す、 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)実装します。

いずれの場合は、アプリケーションのまたはマイクロ サービスのビジネス要件に基づいた意思決定はずです。

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>媒介パターン (MediatR) を持つコマンドのプロセス パイプラインを実装します。

サンプルの実装としては、このガイドは、ドライブ コマンド取り込みに媒介パターンに基づいており、メモリ、right コマンド ハンドラーにルーティングする、プロセスにパイプラインを使用してを提案します。 デコレーターを適用することにも提示ガイドまたは[動作](https://github.com/jbogard/MediatR/wiki/Behaviors)横断的関心事を区別するためにします。

.NET Core での実装の複数オープン ソース ライブラリが使用可能な媒介パターンを実装します。 このガイドで使用するライブラリは、 [MediatR](https://github.com/jbogard/MediatR) (Jimmy Bogard によって作成される)、オープン ソース ライブラリですが、別のアプローチを使用できます。 MediatR では、小規模で単純なのライブラリで、デコレーターまたは動作を適用中に、コマンドと同様に、インメモリ メッセージを処理することができます。

媒介パターンを使用することができますを結合を小さくし、その作業を実行するハンドラーを自動的に接続中に、要求された作業が関係する問題を分離する — コマンド ハンドラーをここでは、します。

このガイドを確認するとき、Jimmy Bogard によって媒介パターンを使用して別の理由が説明されて。

ここでのテストに留意だと考えられます: システムの動作に一貫性のあるウィンドウを提供と思われます。 要求で、応答アウトします。わかりましたその縦横ビルドのテストを一貫した動作で非常に有益です。

最初に、お知らせ見てコント ローラーのコードを実際に使用する媒介オブジェクト。 媒介オブジェクトを使用していなかった場合は、すべての依存関係、コント ローラーのロガー オブジェクトやその他のユーザーなどを挿入する必要があります。 そのため、コンス トラクターはかなり複雑になります。 その一方で、媒介オブジェクトを使用する場合、コント ローラーのコンス トラクターは次の例のように、横断的操作ごとに 1 つがあった場合に数多くの依存関係ではなく、いくつかの依存関係を持つ、はるかに簡単で指定できます。

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

媒介がすっきりとリーン Web API コント ローラー コンス トラクターを提供することを確認できます。 さらに、コント ローラーのメソッド内で媒介オブジェクトにコマンドを送信するコードでは、ほぼ 1 行には。

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

MediatR コマンド ハンドラーのクラスを認識するためには媒介クラスとコマンド ハンドラーのクラスを IoC コンテナーに登録する必要があります。 既定では、MediatR IoC コンテナーとして Autofac を使用しますが、組み込みの ASP.NET Core IoC コンテナーまたは MediatR でサポートされている他のコンテナーを使用することもできます。

次のコードでは、Autofac モジュールを使用する場合に、媒介の種類とコマンドを登録する方法を示します。

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

各コマンド ハンドラーには汎用 IAsyncRequestHandler のインターフェイスが実装されているため&lt;T&gt; RegisteredAssemblyTypes を検査してオブジェクトのために、ハンドラーがそのコマンド ハンドラーにより各コマンドを関連付けたりすることをリレーションシップは、次の例のように、CommandHandler クラスに記載されています。

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

これは、との関連付けを行うコマンド コマンド ハンドラー コードです。 ハンドラーは、単純なクラスだけですが、サーバクラスから継承&lt;T&gt;、MediatR ので、正しいペイロードで起動されるを取得します。

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>媒介とデコレーターのパターンを使用するコマンドを処理するときに、横断的関心事を適用します。

もう 1 つがある: 媒介パイプラインを横断的関心事を適用することです。 表示することも、Autofac 登録モジュールのコードの最後にデコレータに登録する方法を具体的には、カスタム LogDecorator クラスを入力します。

EShopOnContainers の将来のバージョンには移行ことに注意して[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)に移動する[動作](https://github.com/jbogard/MediatR/wiki/Behaviors)デコレーターを使用する代わりにします。

ある[LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)クラスは、次のコードは、実行されているコマンド ハンドラーとが成功したかどうかどうかに関する情報を記録として実装することができます。

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

このデコレータ クラスを実装するだけでしてパイプラインを修飾することによって、MediatR を通して処理されたすべてのコマンドには、実行に関する情報がログインします。

マイクロ サービスでも、2 番目のデコレータの基本的な検証は、順序付け eShopOnContainers、 [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)クラスに依存している、 [FluentValidation](https://github.com/JeremySkinner/FluentValidation)ライブラリのように、次のコード:

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

その後、に基づいて、 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) CreateOrderCommand、と共に、次のコードのように渡されるデータの検証を作成したライブラリ。

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}
```

追加の検証を作成できます。 これは、コマンド、検証を実装する非常にクリーンで簡潔な方法です。

同様の方法で追加の側面または横断的関心事にそれらを処理するときに、コマンドに適用するには、その他のデコレーターを実装する可能性があります。

#### <a name="additional-resources"></a>その他の技術情報

##### <a name="the-mediator-pattern"></a>媒介パターン

-   **媒介パターン**
    [*https://en.wikipedia.org/wiki/Mediator\_パターン*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>デコレータ パターン

-   **デコレータ パターン**
    [*https://en.wikipedia.org/wiki/Decorator\_パターン*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR です。** GitHub のリポジトリ。
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **MediatR と AutoMapper CQRS**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **コント ローラーをダイエットに入れます: 投稿とコマンド。** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **媒介パイプラインを持つ横断的関心事に取り組む**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS および REST: 完全に一致する**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **MediatR パイプライン例**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **MediatR および ASP.NET Core の縦方向のスライス テスト フィクスチャ**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **リリースされる Microsoft の依存関係の挿入の MediatR 拡張子**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Fluent 検証

-   **Jeremy スキニングです。FluentValidation です。** GitHub のリポジトリ。
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[前](microservice-application-layer-web-api-design.md) [次へ] (../implement-resilient-applications/index.md)

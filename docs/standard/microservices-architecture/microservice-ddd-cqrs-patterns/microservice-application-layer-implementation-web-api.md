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
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="b8e54-104">Web API を使用してマイクロ サービスのアプリケーション レイヤーの実装</span><span class="sxs-lookup"><span data-stu-id="b8e54-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="b8e54-105">依存関係の挿入を使用して、アプリケーション層にインフラストラクチャ オブジェクトを挿入するには</span><span class="sxs-lookup"><span data-stu-id="b8e54-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="b8e54-106">前述のように、アプリケーション層は、アイテムを作成するなど、Web API プロジェクトまたは MVC web アプリケーション プロジェクト内の一部として実装できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="b8e54-107">ASP.NET Core でビルドされたマイクロ サービスの場合、アプリケーション レイヤー場合、通常は、Web API ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="b8e54-108">今後の ASP.NET Core (のインフラストラクチャと、コント ローラー) から、カスタムのアプリケーション層コードから分離する場合は、別のクラス ライブラリで、アプリケーション層を配置することもできませんが、省略可能。</span><span class="sxs-lookup"><span data-stu-id="b8e54-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="b8e54-109">たとえば、順序マイクロ サービスのアプリケーション層のコードは、の一部として実装されて直接、 **Ordering.API**プロジェクト (ASP.NET Core Web API プロジェクト) に示す図 9 19 として。</span><span class="sxs-lookup"><span data-stu-id="b8e54-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="b8e54-110">**図 9-19**です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-110">**Figure 9-19**.</span></span> <span data-ttu-id="b8e54-111">Ordering.API ASP.NET Core Web API プロジェクトで、アプリケーション層</span><span class="sxs-lookup"><span data-stu-id="b8e54-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="b8e54-112">ASP.NET Core を含む、単純な[組み込み IoC コンテナー](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)既定では、コンス トラクターの挿入をサポートする (IServiceProvider インターフェイスによって表される) と ASP.NET により、特定のサービスが DI を介して使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="b8e54-113">ASP.NET Core という用語を使用して*サービス*の DI から挿入されるを登録する型。</span><span class="sxs-lookup"><span data-stu-id="b8e54-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="b8e54-114">ConfigureServices クラス メソッドのアプリケーションの起動時には、組み込みのコンテナーのサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="b8e54-115">依存関係は、型が必要なサービスで実装されます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="b8e54-116">通常、インフラストラクチャ オブジェクトを実装する依存関係を挿入します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="b8e54-117">挿入する非常に一般的な依存関係は、リポジトリです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="b8e54-118">他のインフラストラクチャの依存関係がある場合を挿入することできます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="b8e54-119">単純な実装は、挿入することでした直接作業単位パターン オブジェクト (EF DbContext オブジェクト) の場合は、DBContext は、インフラストラクチャの持続性のオブジェクトの実装でもあるため。</span><span class="sxs-lookup"><span data-stu-id="b8e54-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="b8e54-120">次の例では、.NET Core は、コンス トラクターによって必要なリポジトリ オブジェクトを挿入する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="b8e54-121">クラスは、次のセクションで取り上げるコマンドです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-121">The class is a command handler, which we will cover in the next section.</span></span>

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

<span data-ttu-id="b8e54-122">クラスは、トランザクションを実行し、状態の変更を保持する挿入されたリポジトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="b8e54-123">またはそのクラスが ASP.NET Core Web API コント ローラー メソッドでは、コマンド ハンドラーであるかどうかは関係ありません[DDD アプリケーション サービス](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="b8e54-124">最終的には、コマンド ハンドラーのような方法でリポジトリ、ドメイン エンティティ、およびその他のアプリケーションの調整を使用する単純なクラスです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="b8e54-125">依存関係インジェクション動作が、同じクラスに対してはすべて、説明したように、DI を使用する例のようにに基づいて、コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="b8e54-126">依存関係の実装の種類とのインターフェイスまたは抽象化を登録します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="b8e54-127">コンス トラクターで挿入されたオブジェクトを使用する前に、インターフェイス、および DI を通じて、アプリケーション クラスに挿入されたオブジェクトを生成するクラスを登録する場所を知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="b8e54-128">(DI のようにに基づいて、コンス トラクターは、上記のようにします)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="b8e54-129">ASP.NET Core によって提供される組み込み IoC コンテナーの使用</span><span class="sxs-lookup"><span data-stu-id="b8e54-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="b8e54-130">ASP.NET Core によって提供される組み込み IoC コンテナーを使用する場合は、ConfigureServices メソッドを次のコードのように、Startup.cs ファイルに挿入するかの種類を登録します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

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

<span data-ttu-id="b8e54-131">最も一般的なパターンの種類を IoC コンテナーに登録することは、型のペアを登録するときに、インターフェイスとその関連実装クラス。</span><span class="sxs-lookup"><span data-stu-id="b8e54-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="b8e54-132">任意のコンス トラクターを介して IoC コンテナーからオブジェクトを要求する場合は、インターフェイスの特定の型のオブジェクトを要求します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="b8e54-133">たとえば、前の例では、最後の行を示す IMyCustomRepository (インターフェイスまたは抽象型) に依存関係、コンス トラクターのいずれかの場合は、IoC コンテナーは MyCustomSQLServerRepository 実装のインスタンスを挿入するが、クラス。</span><span class="sxs-lookup"><span data-stu-id="b8e54-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="b8e54-134">種類の自動登録の Scrutor ライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="b8e54-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="b8e54-135">DI を .NET Core を使用する場合は、アセンブリをスキャンし、規約によって自動的にその型を登録することにする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="b8e54-136">この機能では、ASP.NET Core で現在使用できません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="b8e54-137">ただし、使用することができます、 [Scrutor](https://github.com/khellang/Scrutor)ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="b8e54-138">この方法は、重複除去は、IoC コンテナーに登録する必要がある型がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b8e54-139">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="b8e54-139">Additional resources</span></span>

-   <span data-ttu-id="b8e54-140">**Matthew キングです。Scrutor をサービスに登録する**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="b8e54-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="b8e54-141">**Kristian Hellang です。Scrutor です。**</span><span class="sxs-lookup"><span data-stu-id="b8e54-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="b8e54-142">GitHub のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="b8e54-142">GitHub repo.</span></span>
    [<span data-ttu-id="b8e54-143">*https://github.com/khellang/Scrutor*</span><span class="sxs-lookup"><span data-stu-id="b8e54-143">*https://github.com/khellang/Scrutor*</span></span>](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="b8e54-144">IoC コンテナーとして Autofac を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-144">Using Autofac as an IoC container</span></span>

<span data-ttu-id="b8e54-145">また追加 IoC コンテナーを使用してし、を使用して eShopOnContainers で順序付けマイクロ サービスと同様に、ASP.NET Core パイプラインに差し込みます[Autofac](https://autofac.org/)です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="b8e54-146">Autofac を使用する場合は、ここで、型では、複数のクラス ライブラリに分散アプリケーションの種類を割り当てることもに応じて複数のファイルの登録の種類を分割することは、モジュールを使用して型通常登録します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="b8e54-147">たとえば、次は、 [Autofac アプリケーション モジュール](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)の[Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API)を挿入する種類のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

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

<span data-ttu-id="b8e54-148">登録プロセスおよび概念により、組み込みの ASP.NET Core iOS コンテナーの種類を登録する方法とよく似ていますが、構文 Autofac を使用する場合は少し異なります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="b8e54-149">コード例では、実装クラス OrderRepository と共に IOrderRepository の抽象型が登録されます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="b8e54-150">これは、コンス トラクターが IOrderRepository 抽象またはインターフェイスの依存関係を宣言しているときに IoC コンテナーは OrderRepository クラスのインスタンスを挿入するがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="b8e54-151">インスタンスのスコープの種類は、同じサービスまたは依存関係に対する要求間でインスタンスを共有する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="b8e54-152">依存関係の要求が行われると、IoC コンテナーは、次を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="b8e54-153">有効期間の範囲ごとに 1 つのインスタンス (として ASP.NET Core IoC コンテナーで参照される*スコープ*)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="b8e54-154">依存関係ごとに新しいインスタンス (として ASP.NET Core IoC コンテナーで参照される*一時的な*)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="b8e54-155">IoC コンテナーを使用してすべてのオブジェクト間で共有される 1 つのインスタンス (として ASP.NET Core IoC コンテナーで参照される*シングルトン*)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b8e54-156">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="b8e54-156">Additional resources</span></span>

-   <span data-ttu-id="b8e54-157">**ASP.NET Core の依存関係の挿入の概要**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="b8e54-157">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="b8e54-158">**Autofac です。**</span><span class="sxs-lookup"><span data-stu-id="b8e54-158">**Autofac.**</span></span> <span data-ttu-id="b8e54-159">正式なドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-159">Official documentation.</span></span>
    [<span data-ttu-id="b8e54-160">*http://docs.autofac.org/en/latest/*</span><span class="sxs-lookup"><span data-stu-id="b8e54-160">*http://docs.autofac.org/en/latest/*</span></span>](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="b8e54-161">**Cesar de la Torre。Autofac IoC コンテナー インスタンスのスコープを持つ ASP.NET Core IoC コンテナー サービスの有効期間を比較する**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-161">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="b8e54-162">コマンドとコマンド ハンドラーのパターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-162">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="b8e54-163">例では、DI を通じてコンス トラクター、前のセクションに示すように、IoC コンテナーがクラスでコンス トラクターでリポジトリを挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="b8e54-164">しかし、正確に場所が、挿入されたか。</span><span class="sxs-lookup"><span data-stu-id="b8e54-164">But exactly where were they injected?</span></span> <span data-ttu-id="b8e54-165">単純な Web API (たとえば、eShopOnContainers で、カタログ マイクロ サービス) で挿入することに MVC コント ローラー レベルのコント ローラーのコンス トラクター内で。</span><span class="sxs-lookup"><span data-stu-id="b8e54-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="b8e54-166">ただし、このセクションの最初のコードで (、 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) eShopOnContainers Ordering.API サービスからのクラス)、特定のコマンドのコンス トラクターは、操作には依存関係の挿入ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="b8e54-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="b8e54-167">説明お知らせ、どのようなコマンド ハンドラーは、それを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="b8e54-168">コマンドのパターンは本質的に、このガイドの前半で導入された CQRS のパターンに関連します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="b8e54-169">CQRS には、2 つの辺があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-169">CQRS has two sides.</span></span> <span data-ttu-id="b8e54-170">最初の領域が簡略化されたクエリを使用して、クエリ、 [Dapper](https://github.com/StackExchange/dapper-dot-net)が先に説明したマイクロ ORM です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="b8e54-171">2 番目の領域は、トランザクションの開始点と、入力チャネルからサービスの外部のコマンドです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="b8e54-172">図 9-20 を示すように、パターンに基づきますがクライアント側からのコマンドを受け付けて処理ルールに基づく、ドメイン モデル、および最後にトランザクションの状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-172">As shown in Figure 9-20, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="b8e54-173">**図 9-20**です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-173">**Figure 9-20**.</span></span> <span data-ttu-id="b8e54-174">コマンドまたは CQRS パターンの「トランザクション側」の概要を表示</span><span class="sxs-lookup"><span data-stu-id="b8e54-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="b8e54-175">コマンド クラス</span><span class="sxs-lookup"><span data-stu-id="b8e54-175">The command class</span></span>

<span data-ttu-id="b8e54-176">コマンドは、システムの状態を変更するアクションを実行するシステムの要求です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="b8e54-177">コマンドは、命令型、1 回だけ処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="b8e54-178">コマンドが課題であるためは通常 (「作成」または「更新」など) の命令型気分に動詞を使用して名前付きおよび CreateOrderCommand など、集計の種類があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="b8e54-179">イベントとは異なり、コマンドはできません。 過去のファクト要求だけをそのため、拒否される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="b8e54-180">コマンドは、プロセス マネージャーが操作を実行する集計を指定する場合、要求を開始したユーザーの結果として、UI とは、プロセス マネージャーから取得できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="b8e54-181">コマンドの重要な特性は、それを処理する 1 回だけを単一の受信者によってです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="b8e54-182">これは、コマンドが単一のアクションまたはアプリケーションで実行するトランザクションであるためです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="b8e54-183">など、同じ順序の作成コマンド必要があります処理できませんも複数回です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="b8e54-184">これは、コマンドとイベントの重要な違いです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="b8e54-185">多くのシステムや microservices 興味を持つイベントのために、イベントが複数回を処理できません可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="b8e54-186">さらに、コマンドが、コマンドは、べき等ではない場合に、1 回だけに処理する重要なです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="b8e54-187">コマンドでは、べき等が実行されることが複数回、コマンドの性質があるため、またはシステムが、コマンドを処理する方法のため、結果を変更することがなく場合です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="b8e54-188">コマンドをすることをお勧めし、ドメインのビジネス ルールおよび不変条件の下の方が良い場合に、べき等を更新します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="b8e54-189">たとえば、使用するには同じ例では、何らかの理由 (再試行ロジックやハッキングなど)、同じ CreateOrder コマンドに達した場合、システム複数回できますを識別し、複数の注文を作成しないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b8e54-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="b8e54-190">そのためには、いくつかの種類の操作の id をアタッチし、コマンドまたは更新プログラムは既に処理されているかどうかを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="b8e54-191">単一の受信者にコマンドを送信します。コマンドを発行しません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="b8e54-192">発行は、ファクトを状態統合イベント-問題が発生した可能性がありますなることのイベント レシーバーの興味深いです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-192">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="b8e54-193">イベントの場合は、パブリッシャーにはレシーバー取得イベントか、どのように行うかについての問題はありません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="b8e54-194">統合イベントは前のセクションで既に導入話は別です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-194">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="b8e54-195">コマンドは、データ フィールドまたはコマンドを実行するために必要なすべての情報を含むコレクションを含むクラスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="b8e54-196">コマンドは、特別な種類のデータ転送オブジェクト (DTO) を変更またはトランザクションを要求に使用される具体的には 1 つです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="b8e54-197">コマンド自体は、正確に、必要な情報をコマンド、および何詳細を処理するために基づきます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="b8e54-198">次の例では、簡略化された CreateOrderCommand クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="b8e54-199">これは eShopOnContainers で順序付けマイクロ サービスで使用されている変更できないコマンドです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

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

<span data-ttu-id="b8e54-200">基本的には、コマンド クラスには、ドメイン モデル オブジェクトを使用してビジネス トランザクションの実行に必要なすべてのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b8e54-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="b8e54-201">したがって、コマンドは、読み取り専用のデータと動作はありませんが含まれているデータ構造だけです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="b8e54-202">コマンドの名前では、その目的を示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="b8e54-203">C のような多くの言語で\#コマンドは、クラスとして表されますが、実際のオブジェクト指向という意味では true。 クラスではありません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="b8e54-204">その他の特徴として予想される使用率が、ドメイン モデルによって直接処理されるためコマンドは、変更できません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="b8e54-205">投影の有効期間中に変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="b8e54-206">C で\#クラス、不変性は、set アクセス操作子またはその他の内部状態を変更する方法をなくすことによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="b8e54-207">たとえば、注文を作成するためのコマンド クラス可能性がありますは似ていますがデータの観点から注文を作成するのに可能性があります、同じ属性必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-207">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="b8e54-208">インスタンスの順序はまだ作成されていないために、CreateOrderCommand には、注文 ID はありません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-208">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="b8e54-209">多くのコマンド クラスを単純な場合、変更する必要があるいくつかの状態に関するいくつかのフィールドのみを必要とすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-209">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="b8e54-210">大文字と小文字"のプロセスから"注文の状態を変更する場合は「支払い」または「出荷」には、次のようなコマンドを使用してになります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-210">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="b8e54-211">その UI 要求オブジェクトになります、コマンド dtos の使用とは別の一部の開発者が、基本設定だけで済みます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-211">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="b8e54-212">それほど多くありません付加価値と面倒に分離して、オブジェクトが同じ図形とほぼ同様です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-212">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="b8e54-213">たとえば、eShopOnContainers、コマンドをクライアント側から直接取得します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-213">For instance, in eShopOnContainers, the commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="b8e54-214">コマンド ハンドラー クラス</span><span class="sxs-lookup"><span data-stu-id="b8e54-214">The Command Handler class</span></span>

<span data-ttu-id="b8e54-215">各コマンドの特定のコマンド ハンドラー クラスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-215">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="b8e54-216">パターンのしくみがあり、コマンド オブジェクト、ドメイン オブジェクトおよびインフラストラクチャのリポジトリ オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-216">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="b8e54-217">コマンド ハンドラーは、CQRS と DDD の観点から、アプリケーション レイヤーの中心となる実際には。</span><span class="sxs-lookup"><span data-stu-id="b8e54-217">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="b8e54-218">ただし、ドメイン クラス内ですべてのドメイン ロジックを含める必要があります: 集計ルート (ルート エンティティ) 内で子エンティティまたは[ドメイン サービス](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)、コマンド ハンドラー内ではなく、アプリケーションからのクラスであるが、レイヤーです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-218">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="b8e54-219">コマンド ハンドラーでは、コマンドを受信し、使用される集計結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-219">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="b8e54-220">結果はのコマンドを正常に実行または例外のいずれかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-220">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="b8e54-221">例外の場合は、システム状態を変更されず必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-221">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="b8e54-222">コマンド ハンドラーは、次の手順に通常を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-222">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="b8e54-223">DTO と同様に、コマンド オブジェクトを受け取ります (から、[媒介](https://en.wikipedia.org/wiki/Mediator_pattern)または他のインフラストラクチャ オブジェクト)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-223">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="b8e54-224">コマンドが (媒介によって認められていない) 場合は、有効であることを検証します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-224">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="b8e54-225">現在のコマンドの対象となっている集計ルート インスタンスがインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-225">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="b8e54-226">集計のルート インスタンスで、コマンドから、必要なデータを取得するメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-226">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="b8e54-227">これには、集計、関連するデータベースへの新しい状態が永続化します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-227">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="b8e54-228">この最後の操作は、実際のトランザクションです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-228">This last operation is the actual transaction.</span></span>

<span data-ttu-id="b8e54-229">通常、コマンド ハンドラーは、その集計ルート (ルート エンティティ) によって、1 つの集計について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-229">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="b8e54-230">複数の集計は、1 つのコマンドの受信の影響を受ける必要があります、複数の集計の状態またはアクションに伝達するのにドメインのイベントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-230">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates</span></span>

<span data-ttu-id="b8e54-231">ここでの重要なポイントは、コマンドの処理中は、すべてのドメイン ロジックが、ドメイン モデル (集計) の場合、完全にカプセル化された単体テストの準備が整って内する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-231">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="b8e54-232">コマンド ハンドラーは、ドメイン モデルをデータベースから取得する方法とは、最後の手順としてへの変更を保持する、モデルが変更されたときに、インフラストラクチャ レイヤー (リポジトリ) の通知にだけ機能します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-232">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="b8e54-233">このアプローチの利点は、アプリケーションまたはインフラストラクチャ レイヤーは、組み込みレベル (コマンド ハンドラーを Web API は、コードを変更することがなく、分離、完全にカプセル化された、機能豊富な動作上のドメイン モデル内のドメイン ロジックをリファクタリングすることができます。リポジトリなど)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-233">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="b8e54-234">コマンド ハンドラーが多すぎるロジックで、複雑な場合、コードの匂いをすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-234">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="b8e54-235">それらを確認し、ドメイン ロジックを検索する場合は、ドメイン オブジェクト (集計ルートと子エンティティ) のメソッドにそのドメインの動作を移動するコードをリファクタリングします。</span><span class="sxs-lookup"><span data-stu-id="b8e54-235">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="b8e54-236">コマンド ハンドラー クラスの例は、としては、次のコードは、この章の先頭に表示される同じ CreateOrderCommandHandler クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-236">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="b8e54-237">ここで処理する Handle メソッドとドメイン モデル オブジェクト/集計を使用して操作を強調表示されているおです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-237">In this case we have highlighted the Handle method and the operations with the domain model objects/aggregates.</span></span>

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

<span data-ttu-id="b8e54-238">追加の手順のコマンド ハンドラーを次に示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-238">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="b8e54-239">集計ルートのメソッドおよび動作を操作するには、コマンドのデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-239">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="b8e54-240">内部的にドメイン オブジェクト内でイベントを発生させるドメイン、トランザクションを実行すると、ですが、コマンド ハンドラーの観点からは透過的です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-240">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="b8e54-241">集計の操作の結果が成功した場合、トランザクションの完了後に、統合イベント コマンド ハンドラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-241">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="b8e54-242">(これらがまた生成されるリポジトリなどのインフラストラクチャ クラスによって。)</span><span class="sxs-lookup"><span data-stu-id="b8e54-242">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b8e54-243">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="b8e54-243">Additional resources</span></span>

-   <span data-ttu-id="b8e54-244">**マーク Seemann です。境界、アプリケーションがオブジェクトではなく指向**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries、ApplicationsareNotObject 指向/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-244">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="b8e54-245">**コマンドとイベント**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="b8e54-245">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="b8e54-246">**コマンド ハンドラー何か。** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="b8e54-246">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="b8e54-247">**Jimmy Bogard。ドメイン コマンド パターン – ハンドラー**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-247">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="b8e54-248">**Jimmy Bogard。ドメイン コマンド パターン – 検証**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-248">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="b8e54-249">コマンド処理パイプライン コマンドのハンドラーをトリガーする方法。</span><span class="sxs-lookup"><span data-stu-id="b8e54-249">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="b8e54-250">次の質問は、コマンド ハンドラーを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-250">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="b8e54-251">ASP.NET Core の関連する各コント ローラーから手動で呼び出す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-251">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="b8e54-252">ただし、ことがある方法も組み合わせると、理想的ではありません。</span><span class="sxs-lookup"><span data-stu-id="b8e54-252">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="b8e54-253">その他の 2 つ主なオプションは、推奨されるオプションですが、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-253">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="b8e54-254">インメモリ媒介パターン成果物です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-254">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="b8e54-255">コント ローラーとハンドラー間の非同期メッセージ キューです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-255">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="b8e54-256">コマンド パイプラインに媒介パターン (メモリ内) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-256">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="b8e54-257">図 9-21 で示すように、CQRS アプローチを使用するインテリジェント媒介で、これは、コマンドまたは受信される DTO の種類に基づいて、right コマンド ハンドラーにリダイレクトするほど、メモリ内バスに似ています。</span><span class="sxs-lookup"><span data-stu-id="b8e54-257">As shown in Figure 9-21, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="b8e54-258">コンポーネント間で 1 つの黒い矢印は、その関連する相互作用と (DI で挿入された多くの場合) 内のオブジェクト間の依存関係を表します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-258">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="b8e54-259">**図 9-21**です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-259">**Figure 9-21**.</span></span> <span data-ttu-id="b8e54-260">1 つの CQRS マイクロ サービスでのプロセスで媒介パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-260">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="b8e54-261">媒介パターンを使用する意味は、エンタープライズ アプリケーションで処理要求取得できることに複雑です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-261">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="b8e54-262">ログ記録、検証、監査、およびセキュリティのような横断的関心事の開いている数を追加できるようにするには。</span><span class="sxs-lookup"><span data-stu-id="b8e54-262">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="b8e54-263">このような場合は、媒介パイプラインに依存することができます (を参照してください[媒介パターン](https://en.wikipedia.org/wiki/Mediator_pattern)) これらの余分な動作や横断的関心事の手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-263">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="b8e54-264">仲介者は、このプロセスの「方法」をカプセル化するオブジェクト: 状態に基づいて実行を調整、方法、コマンド ハンドラーが呼び出され、またはハンドラーに提供するペイロード。</span><span class="sxs-lookup"><span data-stu-id="b8e54-264">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="b8e54-265">媒介コンポーネントを適用できます横断的関心事集中かつ透過的な方法でデコレーターを適用することで (または[動作のパイプライン](https://github.com/jbogard/MediatR/wiki/Behaviors)媒介 v3 以降)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-265">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since Mediator v3).</span></span> <span data-ttu-id="b8e54-266">(詳細については、次を参照してください、[デコレータ パターン](https://en.wikipedia.org/wiki/Decorator_pattern)。)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-266">(For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).)</span></span>

<span data-ttu-id="b8e54-267">デコレーターと動作に似ています[アスペクト指向プログラミング (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)、媒介コンポーネントによって管理される特定のプロセス パイプラインに適用されるのみです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-267">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="b8e54-268">横断的関心事を実装する AOP の側面がに基づいて適用されます*縦横 weaver:*オブジェクト呼び出しの途中受信に基づくまたはコンパイル時に挿入します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-268">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="b8e54-269">両方の典型的な AOP アプローチもいいます"マジック、"のように動作する AOP がその作業をどのように表示する簡単ではないためです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-269">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="b8e54-270">深刻な問題やバグを扱う場合、AOP はデバッグが困難にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-270">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="b8e54-271">その一方で、これらデコレーター/動作は明示的なして適用すると、媒介のコンテキストのみでデバッグがはるかに簡単に予測可能なためです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-271">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="b8e54-272">2 つのサンプル デコレーターを実装しましたマイクロ サービスを順序付け eShopOnContainers でなど、 [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)クラスおよび[ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)クラスです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-272">For example, in the eShopOnContainers ordering microservice, we implemented two sample decorators, a [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class and a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class.</span></span> <span data-ttu-id="b8e54-273">デコレーターの実装は、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-273">The decorator’s implementation is explained in the next section.</span></span> <span data-ttu-id="b8e54-274">今後のバージョンでに eShopOnContainers が移行されますに注意してください[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)に移動する[動作](https://github.com/jbogard/MediatR/wiki/Behaviors)デコレーターを使用する代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b8e54-274">Note that in a future version, eShopOnContainers will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="b8e54-275">コマンドのパイプラインでメッセージ キュー (アウト プロセス) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-275">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="b8e54-276">他の選択肢では、図 9-22 を示すように、また仲買担当者またはメッセージ キュー、に基づいて非同期のメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-276">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-22.</span></span> <span data-ttu-id="b8e54-277">そのオプションは、コマンド ハンドラーの前に右媒介コンポーネントと組み合わせることも可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-277">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="b8e54-278">**図 9-22**です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-278">**Figure 9-22**.</span></span> <span data-ttu-id="b8e54-279">メッセージ キュー (外のプロセスおよびプロセス間通信) を使って CQRS コマンド</span><span class="sxs-lookup"><span data-stu-id="b8e54-279">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="b8e54-280">2 つのプロセスにパイプラインを分割する必要がありますので、コマンドをさらにそのまま使用するためのキューには、コマンドのパイプラインが複雑になるメッセージを使用して、外部メッセージ キュー経由で接続します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-280">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="b8e54-281">それでも、スケーラビリティと非同期メッセージングに基づいて、パフォーマンスが向上する必要がある場合、このを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-281">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="b8e54-282">図 9-22 の場合は、コント ローラーだけコマンド メッセージをキューにポストし、返すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b8e54-282">Consider that in the case of Figure 9-22, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="b8e54-283">コマンド ハンドラーは、自分のペースでメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-283">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="b8e54-284">キューの非常に大きな利点は、ハイパー スケーラビリティが必要な株式やその他のシナリオで大量の受信データの場合のようには場合、メッセージ キューがの場合、バッファーとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-284">That is a great benefit of queues—the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="b8e54-285">ただし、メッセージ キューの非同期の性質があるため、コマンドの処理の成否について、クライアント アプリケーションと通信する方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-285">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="b8e54-286">原則として、「ファイア アンド忘れた」コマンドを使用する必要がありますしないでください。</span><span class="sxs-lookup"><span data-stu-id="b8e54-286">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="b8e54-287">すべてのビジネス アプリケーションは、かどうか、コマンドは正常に処理または少なくとも確認され、受け入れを知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-287">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="b8e54-288">したがって、非同期のキューに送信されたコマンドのメッセージを検証した後、クライアントに応答することと、トランザクションを実行した後、操作の結果を返す、インプロセス コマンド プロセスと比較して、システムに複雑さを追加します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-288">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="b8e54-289">キューを使用して、追加のコンポーネントおよびカスタム通信を必要とは、システムで他の操作結果メッセージを介してコマンドの処理の結果を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-289">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="b8e54-290">さらに、多くの場合は不要な Burtsev Alexey と Greg Young 内の次の興味深い exchange で説明するようになる一方向のコマンドは、非同期コマンド、[オンラインでの会話](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="b8e54-290">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="b8e54-291">\[Burtsev Alexey\]大量のコードの検索を使用して非同期コマンドの処理、または何らかの理由がこれを行うことがなくメッセージング方法の 1 つのコマンド (一部の長い操作を行っていない、外部の非同期コードを実行していないが、アプリケーションをでも交差しません境界をメッセージ バスを使用している)。</span><span class="sxs-lookup"><span data-stu-id="b8e54-291">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="b8e54-292">この不要な複雑さを導入理由</span><span class="sxs-lookup"><span data-stu-id="b8e54-292">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="b8e54-293">実際には、今のところコマンド ハンドラーをこれまで、ブロックと CQRS のコード例も、ほとんどの場合でうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-293">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="b8e54-294">\[Greg Young\] \[しています.\]非同期コマンドが存在しません。 実際には別のイベントはします。</span><span class="sxs-lookup"><span data-stu-id="b8e54-294">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="b8e54-295">送信 me をそのまま使用し、同意する場合は、イベントを発生させる必要がありますに場合は不要になったと処理を行うメッセージが表示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-295">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="b8e54-296">これは、何かがなされたメッセージが表示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-296">It's you telling me something has been done.</span></span> <span data-ttu-id="b8e54-297">これには最初、わずかに異なるように見えますが、多くの影響があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-297">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="b8e54-298">非同期コマンドでは、エラーを示す簡単な方法がないために、システムでは、複雑さが大幅に増加します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-298">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="b8e54-299">そのため、非同期コマンドは推奨されません以外のスケーリング要件が必要な場合に、または特殊なケースで内部 microservices メッセージングを介して通信するとき。</span><span class="sxs-lookup"><span data-stu-id="b8e54-299">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="b8e54-300">ような場合、エラーの個別のレポートと回復のシステムを設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-300">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="b8e54-301">EShopOnContainers の初期のバージョンで、HTTP 要求から開始され、媒介パターンによって、同期コマンドの処理を使用することにしました。</span><span class="sxs-lookup"><span data-stu-id="b8e54-301">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="b8e54-302">簡単にすることができるように、処理の成否を返す、 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)実装します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-302">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="b8e54-303">いずれの場合は、アプリケーションのまたはマイクロ サービスのビジネス要件に基づいた意思決定はずです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-303">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="b8e54-304">媒介パターン (MediatR) を持つコマンドのプロセス パイプラインを実装します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-304">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="b8e54-305">サンプルの実装としては、このガイドは、ドライブ コマンド取り込みに媒介パターンに基づいており、メモリ、right コマンド ハンドラーにルーティングする、プロセスにパイプラインを使用してを提案します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-305">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and routing them, in memory, to the right command handlers.</span></span> <span data-ttu-id="b8e54-306">デコレーターを適用することにも提示ガイドまたは[動作](https://github.com/jbogard/MediatR/wiki/Behaviors)横断的関心事を区別するためにします。</span><span class="sxs-lookup"><span data-stu-id="b8e54-306">The guide also proposes applying decorators or [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="b8e54-307">.NET Core での実装の複数オープン ソース ライブラリが使用可能な媒介パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-307">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="b8e54-308">このガイドで使用するライブラリは、 [MediatR](https://github.com/jbogard/MediatR) (Jimmy Bogard によって作成される)、オープン ソース ライブラリですが、別のアプローチを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-308">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="b8e54-309">MediatR では、小規模で単純なのライブラリで、デコレーターまたは動作を適用中に、コマンドと同様に、インメモリ メッセージを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-309">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="b8e54-310">媒介パターンを使用することができますを結合を小さくし、その作業を実行するハンドラーを自動的に接続中に、要求された作業が関係する問題を分離する — コマンド ハンドラーをここでは、します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-310">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="b8e54-311">このガイドを確認するとき、Jimmy Bogard によって媒介パターンを使用して別の理由が説明されて。</span><span class="sxs-lookup"><span data-stu-id="b8e54-311">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="b8e54-312">ここでのテストに留意だと考えられます: システムの動作に一貫性のあるウィンドウを提供と思われます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-312">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="b8e54-313">要求で、応答アウトします。わかりましたその縦横ビルドのテストを一貫した動作で非常に有益です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-313">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="b8e54-314">最初に、お知らせ見てコント ローラーのコードを実際に使用する媒介オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b8e54-314">First, let us take a look to the controller code where you actually would use the mediator object.</span></span> <span data-ttu-id="b8e54-315">媒介オブジェクトを使用していなかった場合は、すべての依存関係、コント ローラーのロガー オブジェクトやその他のユーザーなどを挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-315">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="b8e54-316">そのため、コンス トラクターはかなり複雑になります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-316">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="b8e54-317">その一方で、媒介オブジェクトを使用する場合、コント ローラーのコンス トラクターは次の例のように、横断的操作ごとに 1 つがあった場合に数多くの依存関係ではなく、いくつかの依存関係を持つ、はるかに簡単で指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-317">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies that you would have if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

<span data-ttu-id="b8e54-318">媒介がすっきりとリーン Web API コント ローラー コンス トラクターを提供することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-318">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="b8e54-319">さらに、コント ローラーのメソッド内で媒介オブジェクトにコマンドを送信するコードでは、ほぼ 1 行には。</span><span class="sxs-lookup"><span data-stu-id="b8e54-319">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

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

<span data-ttu-id="b8e54-320">MediatR コマンド ハンドラーのクラスを認識するためには媒介クラスとコマンド ハンドラーのクラスを IoC コンテナーに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-320">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="b8e54-321">既定では、MediatR IoC コンテナーとして Autofac を使用しますが、組み込みの ASP.NET Core IoC コンテナーまたは MediatR でサポートされている他のコンテナーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-321">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="b8e54-322">次のコードでは、Autofac モジュールを使用する場合に、媒介の種類とコマンドを登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-322">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

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

<span data-ttu-id="b8e54-323">各コマンド ハンドラーには汎用 IAsyncRequestHandler のインターフェイスが実装されているため&lt;T&gt; RegisteredAssemblyTypes を検査してオブジェクトのために、ハンドラーがそのコマンド ハンドラーにより各コマンドを関連付けたりすることをリレーションシップは、次の例のように、CommandHandler クラスに記載されています。</span><span class="sxs-lookup"><span data-stu-id="b8e54-323">Because each command handler implements the interface with generic IAsyncRequestHandler&lt;T&gt; and then inspects the RegisteredAssemblyTypes object, the handler is able to relate each command with its command handler, because that relationship is stated in the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="b8e54-324">これは、との関連付けを行うコマンド コマンド ハンドラー コードです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-324">This is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="b8e54-325">ハンドラーは、単純なクラスだけですが、サーバクラスから継承&lt;T&gt;、MediatR ので、正しいペイロードで起動されるを取得します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-325">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it gets invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a><span data-ttu-id="b8e54-326">媒介とデコレーターのパターンを使用するコマンドを処理するときに、横断的関心事を適用します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-326">Applying cross-cutting concerns when processing commands with the Mediator and Decorator patterns</span></span>

<span data-ttu-id="b8e54-327">もう 1 つがある: 媒介パイプラインを横断的関心事を適用することです。</span><span class="sxs-lookup"><span data-stu-id="b8e54-327">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="b8e54-328">表示することも、Autofac 登録モジュールのコードの最後にデコレータに登録する方法を具体的には、カスタム LogDecorator クラスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b8e54-328">You can also see at the end of the Autofac registration module code how it is registering a decorator type, specifically, a custom LogDecorator class.</span></span>

<span data-ttu-id="b8e54-329">EShopOnContainers の将来のバージョンには移行ことに注意して[MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)に移動する[動作](https://github.com/jbogard/MediatR/wiki/Behaviors)デコレーターを使用する代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b8e54-329">Again, note that a future version of eShopOnContainers it will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

<span data-ttu-id="b8e54-330">ある[LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs)クラスは、次のコードは、実行されているコマンド ハンドラーとが成功したかどうかどうかに関する情報を記録として実装することができます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-330">That [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

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

<span data-ttu-id="b8e54-331">このデコレータ クラスを実装するだけでしてパイプラインを修飾することによって、MediatR を通して処理されたすべてのコマンドには、実行に関する情報がログインします。</span><span class="sxs-lookup"><span data-stu-id="b8e54-331">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="b8e54-332">マイクロ サービスでも、2 番目のデコレータの基本的な検証は、順序付け eShopOnContainers、 [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs)クラスに依存している、 [FluentValidation](https://github.com/JeremySkinner/FluentValidation)ライブラリのように、次のコード:</span><span class="sxs-lookup"><span data-stu-id="b8e54-332">The eShopOnContainers ordering microservice also applies a second decorator for basic validations, the [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="b8e54-333">その後、に基づいて、 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) CreateOrderCommand、と共に、次のコードのように渡されるデータの検証を作成したライブラリ。</span><span class="sxs-lookup"><span data-stu-id="b8e54-333">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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

<span data-ttu-id="b8e54-334">追加の検証を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8e54-334">You could create additional validations.</span></span> <span data-ttu-id="b8e54-335">これは、コマンド、検証を実装する非常にクリーンで簡潔な方法です。</span><span class="sxs-lookup"><span data-stu-id="b8e54-335">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="b8e54-336">同様の方法で追加の側面または横断的関心事にそれらを処理するときに、コマンドに適用するには、その他のデコレーターを実装する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e54-336">In a similar way, you could implement other decorators for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b8e54-337">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="b8e54-337">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="b8e54-338">媒介パターン</span><span class="sxs-lookup"><span data-stu-id="b8e54-338">The mediator pattern</span></span>

-   <span data-ttu-id="b8e54-339">**媒介パターン**
    [*https://en.wikipedia.org/wiki/Mediator\_パターン*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="b8e54-339">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="b8e54-340">デコレータ パターン</span><span class="sxs-lookup"><span data-stu-id="b8e54-340">The decorator pattern</span></span>

-   <span data-ttu-id="b8e54-341">**デコレータ パターン**
    [*https://en.wikipedia.org/wiki/Decorator\_パターン*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="b8e54-341">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="b8e54-342">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="b8e54-342">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="b8e54-343">**MediatR です。**</span><span class="sxs-lookup"><span data-stu-id="b8e54-343">**MediatR.**</span></span> <span data-ttu-id="b8e54-344">GitHub のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="b8e54-344">GitHub repo.</span></span>
    [<span data-ttu-id="b8e54-345">*https://github.com/jbogard/MediatR*</span><span class="sxs-lookup"><span data-stu-id="b8e54-345">*https://github.com/jbogard/MediatR*</span></span>](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="b8e54-346">**MediatR と AutoMapper CQRS**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-346">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="b8e54-347">**コント ローラーをダイエットに入れます: 投稿とコマンド。** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-347">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="b8e54-348">**媒介パイプラインを持つ横断的関心事に取り組む**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-348">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="b8e54-349">**CQRS および REST: 完全に一致する**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-349">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="b8e54-350">**MediatR パイプライン例**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-350">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="b8e54-351">**MediatR および ASP.NET Core の縦方向のスライス テスト フィクスチャ**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*</span><span class="sxs-lookup"><span data-stu-id="b8e54-351">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="b8e54-352">**リリースされる Microsoft の依存関係の挿入の MediatR 拡張子**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="b8e54-352">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="b8e54-353">Fluent 検証</span><span class="sxs-lookup"><span data-stu-id="b8e54-353">Fluent validation</span></span>

-   <span data-ttu-id="b8e54-354">**Jeremy スキニングです。FluentValidation です。**</span><span class="sxs-lookup"><span data-stu-id="b8e54-354">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="b8e54-355">GitHub のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="b8e54-355">GitHub repo.</span></span>
    [<span data-ttu-id="b8e54-356">*https://github.com/JeremySkinner/FluentValidation*</span><span class="sxs-lookup"><span data-stu-id="b8e54-356">*https://github.com/JeremySkinner/FluentValidation*</span></span>](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="b8e54-357">[前](microservice-application-layer-web-api-design.md) [次へ] (../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="b8e54-357">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>

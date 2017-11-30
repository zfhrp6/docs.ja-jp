---
title: "イベントにサブスクライブします。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |イベントにサブスクライブします。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: fe17b53a39ff2964cd60183e291e2936d3ba28df
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="subscribing-to-events"></a><span data-ttu-id="81069-104">イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="81069-104">Subscribing to events</span></span>

<span data-ttu-id="81069-105">イベント バスを使用するための最初の手順では、microservices を受信するイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="81069-105">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="81069-106">受信者 microservices で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-106">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="81069-107">次の単純なコードを実装するサービスの開始時に必要な各受信者マイクロ サービスを示しています (つまり、スタートアップ クラス) ため、そのイベントをサブスクライブすることが必要です。</span><span class="sxs-lookup"><span data-stu-id="81069-107">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the Startup class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="81069-108">たとえば、basket.api マイクロ サービスを ProductPriceChangedIntegrationEvent メッセージをサブスクライブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-108">For instance, the basket.api microservice needs to subscribe to ProductPriceChangedIntegrationEvent messages.</span></span> <span data-ttu-id="81069-109">これは製品の価格をマイクロ サービスをすべての変更を認識され、その製品がユーザーのバスケットの場合の変更についてユーザーに警告します。</span><span class="sxs-lookup"><span data-stu-id="81069-109">This makes the microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

<span data-ttu-id="81069-110">このコードを実行した後、サブスクライバー マイクロ サービスは RabbitMQ チャネルを通じて、リッスンしています。</span><span class="sxs-lookup"><span data-stu-id="81069-110">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="81069-111">ProductPriceChangedIntegrationEvent の種類のすべてのメッセージが到着すると、コードは、それに渡され、イベントを処理するイベント ハンドラーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="81069-111">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="81069-112">イベント バスを介してイベントの発行</span><span class="sxs-lookup"><span data-stu-id="81069-112">Publishing events through the event bus</span></span>

<span data-ttu-id="81069-113">最後に、メッセージの送信者 (原点マイクロ サービス) は、次の例のようなコードとの統合イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="81069-113">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="81069-114">(これは、簡単な例を考慮原子性を受け取らないです)。同様のコードを実装することで、複数 microservices、通常のデータまたは原点マイクロ サービスからのトランザクションのコミット直後にイベントを反映する必要があるたびになります。</span><span class="sxs-lookup"><span data-stu-id="81069-114">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="81069-115">最初に、イベント バスの実装オブジェクト (RabbitMQ に基づいてまたは service bus に基づく) を挿入して、次のコードのように、コント ローラーのコンス トラクターには。</span><span class="sxs-lookup"><span data-stu-id="81069-115">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="81069-116">コント ローラーのメソッドからのようなメソッドで使用する、UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="81069-116">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("update")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="81069-117">この場合、原点マイクロ サービスが単純な CRUD マイクロ サービスのため、そのコードは直後に配置される Web API コント ローラーにします。</span><span class="sxs-lookup"><span data-stu-id="81069-117">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> <span data-ttu-id="81069-118">高度な microservices でそのでしたクラスで実装する、CommandHandler、右がコミットされると、元のデータ。</span><span class="sxs-lookup"><span data-stu-id="81069-118">In more advanced microservices, it could be implemented in the CommandHandler class, right after the original data is committed.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="81069-119">イベント バスに発行するときに、原子性と回復性の設計</span><span class="sxs-lookup"><span data-stu-id="81069-119">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="81069-120">分散メッセージングを通じて統合イベントを発行するときにシステムなどのイベント バスがアトミックに元のデータベースを更新し、イベントの発行の問題です。</span><span class="sxs-lookup"><span data-stu-id="81069-120">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="81069-121">インスタンスの例では、簡略化された前に示した、コードは、データベースにコミット データと製品の価格が変更された ProductPriceChangedIntegrationEvent メッセージを公開します。</span><span class="sxs-lookup"><span data-stu-id="81069-121">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="81069-122">最初に、これら 2 つの操作が自動的に実行される重要なことになります。</span><span class="sxs-lookup"><span data-stu-id="81069-122">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="81069-123">ただし、関連する分散トランザクションを使用している場合、データベースと、メッセージ ブローカーと同様に、以前のシステムの場合と[Microsoft メッセージ キュー (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)、が示す理由により推奨されてはいません[CAP 定理](https://www.quora.com/What-Is-CAP-Theorem-1)です。</span><span class="sxs-lookup"><span data-stu-id="81069-123">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="81069-124">基本的には、拡張性と可用性の高いシステムを構築する microservices を使用します。</span><span class="sxs-lookup"><span data-stu-id="81069-124">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="81069-125">キャップの定理という多少を簡略化することは、データベース (またはそのモデルを所有しているマイクロ サービス) をビルドすることはできません継続的に利用可能な強い一貫性のある*と*任意のパーティションに対する許容度がします。</span><span class="sxs-lookup"><span data-stu-id="81069-125">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="81069-126">これら 3 つのプロパティの 2 つを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-126">You must choose two of these three properties.</span></span>

<span data-ttu-id="81069-127">Microservices ベースのアーキテクチャでは、可用性と許容範囲を選択する必要がありますで強力な一貫性を乗算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-127">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="81069-128">そのため、最近のほとんどのマイクロ サービス ベースのアプリケーションで通常たくないメッセージング、分散トランザクションを使用するように実装する場合に、実行[分散トランザクション](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c)Windows 分散トランザクションに基づくコーディネーター (DTC) と[MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)です。</span><span class="sxs-lookup"><span data-stu-id="81069-128">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="81069-129">初期の問題とその例に確認しましょう。</span><span class="sxs-lookup"><span data-stu-id="81069-129">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="81069-130">データベースを更新した後、サービスがクラッシュした場合 (この場合、使用してコードの行の後に右\_コンテキスト。SaveChangesAsync()) が、統合イベントを公開すると、前に、全体的なシステム不整合が発生します。</span><span class="sxs-lookup"><span data-stu-id="81069-130">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="81069-131">これにより、発生している特定のビジネス操作に応じて、重要なビジネス可能性があります。</span><span class="sxs-lookup"><span data-stu-id="81069-131">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="81069-132">前述のアーキテクチャ」で、この問題に対処するためのいくつかのアプローチを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="81069-132">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="81069-133">完全な[イベント基になるパターン](https://msdn.microsoft.com/en-us/library/dn589792.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="81069-133">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="81069-134">使用して[トランザクション ログ マイニング](http://www.scoop.it/t/sql-server-transaction-log-mining)です。</span><span class="sxs-lookup"><span data-stu-id="81069-134">Using [transaction log mining](http://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="81069-135">使用して、[送信トレイ パターン](http://gistlabs.com/2014/05/the-outbox/)です。</span><span class="sxs-lookup"><span data-stu-id="81069-135">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="81069-136">これは、トランザクション (ローカル トランザクションを拡張する) 統合イベントを格納するテーブルです。</span><span class="sxs-lookup"><span data-stu-id="81069-136">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="81069-137">このシナリオでは、フル イベントの基になる (ES) パターンを使用して、最善の方法のいずれかの以外の場合*、*ベストです。</span><span class="sxs-lookup"><span data-stu-id="81069-137">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="81069-138">ただし、多くのアプリケーション シナリオでできない完全 ES システムを実装します。</span><span class="sxs-lookup"><span data-stu-id="81069-138">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="81069-139">ES では、現在の状態データを保管する代わりに、トランザクションのデータベース内のドメインのイベントのみを格納することを意味します。</span><span class="sxs-lookup"><span data-stu-id="81069-139">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="81069-140">ドメインのイベントのみを格納すると、使用可能なシステムの履歴され、過去の時点で、システムの状態を決定できるなどの大きなメリットことができます。</span><span class="sxs-lookup"><span data-stu-id="81069-140">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="81069-141">ただし、完全な ES システムを実装する、システムの大部分を再構築する必要があり、その他の多くの複雑さや要件を紹介します。</span><span class="sxs-lookup"><span data-stu-id="81069-141">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="81069-142">具体的にはに対するイベントの基になるなどのデータベースを使用するなど、[イベント ストア](https://geteventstore.com/)、または Azure Cosmos DB、MongoDB、Cassandra、CouchDB、RavenDB など、ドキュメント指向のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="81069-142">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="81069-143">ES は、イベントのソースとして使い慣れている場合を除き、この問題が最も簡単なソリューションではなくの優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="81069-143">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="81069-144">トランザクション ログが最初にマイニングを使用するオプションは、透過的な非常に検索します。</span><span class="sxs-lookup"><span data-stu-id="81069-144">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="81069-145">ただし、このアプローチを使用するのには、SQL Server トランザクション ログなど、RDBMS トランザクション ログと連結されるように、マイクロ サービスがあります。</span><span class="sxs-lookup"><span data-stu-id="81069-145">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="81069-146">これが望ましくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="81069-146">This is probably not desirable.</span></span> <span data-ttu-id="81069-147">別の欠点は、低レベルの更新トランザクション ログに記録できないことがあります、高度な統合イベントと同じレベルにします。</span><span class="sxs-lookup"><span data-stu-id="81069-147">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="81069-148">場合は、リバース エンジニア リングのプロセス、トランザクション ログの処理困難になります。</span><span class="sxs-lookup"><span data-stu-id="81069-148">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="81069-149">バランスの取れた手法は、トランザクションのデータベース テーブルおよび簡略化された ES パターンの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="81069-149">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="81069-150">「準備完了のイベントを公開する」統合イベント テーブルにコミットする場合は、元のイベントで設定するなどの状態を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="81069-150">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="81069-151">イベントをイベント バスに発行しようとするとします。</span><span class="sxs-lookup"><span data-stu-id="81069-151">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="81069-152">Origin サービスで別のトランザクションを開始して、状態を「、イベントを公開する準備完了」から「イベントが既にパブリッシュされている」に移動発行イベントのアクションが成功すると、</span><span class="sxs-lookup"><span data-stu-id="81069-152">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="81069-153">発行イベントのアクションでは、失敗、イベント バス、データがなります原点マイクロ サービス内で一貫性のない-これは、引き続き可能としてマーク"、イベントを公開する"とに関して、残りのサービスでは、それが最終的に一致します。</span><span class="sxs-lookup"><span data-stu-id="81069-153">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="81069-154">常にバック グラウンド ジョブをトランザクションまたは統合イベントの状態を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="81069-154">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="81069-155">ジョブには、「イベントを発行する準備完了」状態のイベントが検出されるは、そのイベントをイベント バスの再発行を試行できます。</span><span class="sxs-lookup"><span data-stu-id="81069-155">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="81069-156">この方法で永続化する各オリジン マイクロ サービスの統合イベントのみが、および他の microservices または外部システムと通信するイベントのみに注意してください。</span><span class="sxs-lookup"><span data-stu-id="81069-156">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="81069-157">これに対し、ES システムの完全には、すべてのドメイン イベントもを格納します。</span><span class="sxs-lookup"><span data-stu-id="81069-157">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="81069-158">そのため、このバランスの取れた手法は、簡略化された ES システムです。</span><span class="sxs-lookup"><span data-stu-id="81069-158">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="81069-159">現在の状態との統合イベントの一覧を作成する必要があります (「準備ができてを公開する」と「パブリッシュ」) です。</span><span class="sxs-lookup"><span data-stu-id="81069-159">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="81069-160">のみ統合イベントのこれらの状態を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-160">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="81069-161">この方法でする必要はありません、トランザクションのデータベース内のイベントとして、すべてのドメイン データを格納する、完全な ES システムの場合とします。</span><span class="sxs-lookup"><span data-stu-id="81069-161">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="81069-162">既にリレーショナル データベースを使用する場合は、統合イベントを格納するトランザクション テーブルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="81069-162">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="81069-163">アプリケーションで原子性を実現するには、ローカル トランザクションに基づく 2 段階のプロセスを使用します。</span><span class="sxs-lookup"><span data-stu-id="81069-163">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="81069-164">基本的には、テーブルがある場合、IntegrationEvent ドメイン エンティティがある、同じデータベースにします。</span><span class="sxs-lookup"><span data-stu-id="81069-164">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="81069-165">そのテーブルは、含めるができるように、原子性を実現するための保険会社では、ドメインのデータがコミットされる同じトランザクションに統合イベントが永続化とは動作します。</span><span class="sxs-lookup"><span data-stu-id="81069-165">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="81069-166">プロセスが次のようになったステップ バイ ステップ: アプリケーションがローカルのデータベース トランザクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="81069-166">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="81069-167">ドメイン エンティティの状態を更新し、イベントを統合イベントのテーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="81069-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="81069-168">最後に、トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="81069-168">Finally, it commits the transaction.</span></span> <span data-ttu-id="81069-169">目的の原子性が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81069-169">You get the desired atomicity.</span></span>

<span data-ttu-id="81069-170">イベントを公開する次の手順を実装する場合は、これらの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="81069-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="81069-171">トランザクションのコミット直後に、統合イベントを発行し、別のローカル トランザクションを使用してパブリッシュされると、テーブル内のイベントをマークします。</span><span class="sxs-lookup"><span data-stu-id="81069-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="81069-172">成果物と同様にテーブルを使用して、リモートの microservices で問題が発生した場合、統合イベントを追跡し、ストアド統合イベントに基づくな補正アクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="81069-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="81069-173">キューの種類として、テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="81069-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="81069-174">独立したアプリケーションのスレッドまたはプロセスは、統合イベント テーブルを照会し、イベントをイベント バスに発行、ローカル トランザクションを使用して、発行されると、イベントをマークします。</span><span class="sxs-lookup"><span data-stu-id="81069-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="81069-175">図 8-22 は、これらの方法のうちの最初のアーキテクチャを示します。</span><span class="sxs-lookup"><span data-stu-id="81069-175">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="81069-176">**図 8-22**です。</span><span class="sxs-lookup"><span data-stu-id="81069-176">**Figure 8-22**.</span></span> <span data-ttu-id="81069-177">イベントをイベント バスに発行するときの原子性</span><span class="sxs-lookup"><span data-stu-id="81069-177">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="81069-178">図 8-22 を示すアプローチには、担当のチェックと、パブリッシュされた統合イベントの成功を確認する追加の作業者マイクロ サービスがありません。</span><span class="sxs-lookup"><span data-stu-id="81069-178">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="81069-179">障害の発生、その追加チェッカー ワーカー マイクロ サービスは、テーブルからイベントを読み取るし、それらを再パブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="81069-179">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="81069-180">2 番目の方法について: キューとしてイベント ログ テーブルを使用して、常に、メッセージを公開するワーカー マイクロ サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="81069-180">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="81069-181">その場合は、プロセスにはそのような図 8-23 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="81069-181">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="81069-182">これにより、表示、追加のマイクロ サービスと、イベントを発行するときに、テーブルが 1 つのソース。</span><span class="sxs-lookup"><span data-stu-id="81069-182">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="81069-183">**図 8-23**です。</span><span class="sxs-lookup"><span data-stu-id="81069-183">**Figure 8-23**.</span></span> <span data-ttu-id="81069-184">イベントをワーカー マイクロ サービスを持つイベント バスに発行するときの原子性</span><span class="sxs-lookup"><span data-stu-id="81069-184">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="81069-185">わかりやすくするためは、eShopOnContainers サンプルは、さらに、イベント バス (なし、その他のプロセスまたはチェッカー microservices) の最初の方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="81069-185">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="81069-186">ただし、eShopOnContainers は、すべての可能な失敗した場合は処理されていません。</span><span class="sxs-lookup"><span data-stu-id="81069-186">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="81069-187">クラウドに展開されている実際のアプリケーションで確認し、ロジックを再送信するファクト最終的には、問題が発生し、実装する必要がありますを採用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-187">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="81069-188">キューとして、テーブルを使用できる最初の方法よりも効果的イベント バスを介して公開するときのイベントの 1 つのソースとしてそのテーブルがある場合。</span><span class="sxs-lookup"><span data-stu-id="81069-188">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="81069-189">イベント バスを通じて統合イベントを発行するときに、原子性を実装します。</span><span class="sxs-lookup"><span data-stu-id="81069-189">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="81069-190">次のコードは、複数の DbContext オブジェクトを含む 1 つのトランザクションを作成する方法を示しています。 — 元のデータの更新に関連する 1 つのコンテキストと IntegrationEventLog テーブルに関連する 2 つ目のコンテキスト。</span><span class="sxs-lookup"><span data-stu-id="81069-190">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="81069-191">次のサンプル コードでのトランザクションに含まれない回復力のあるコードが実行されている時に、データベースへの接続に問題が発生する場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="81069-191">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="81069-192">これは、Azure SQL DB サーバー間でデータベースを移動する可能性がありますと同様に、クラウド ベースのシステムで発生することができます。</span><span class="sxs-lookup"><span data-stu-id="81069-192">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="81069-193">回復力のあるトランザクションを実装する、複数のコンテキストにわたってを参照してください、[回復力のある Entity Framework の主要な SQL 接続の実装](#implementing_resilient_EFCore_SQL_conns)このガイドの後半の「します。</span><span class="sxs-lookup"><span data-stu-id="81069-193">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="81069-194">わかりやすくするためは、次の例は、コードの 1 つのプロセス全体を示します。</span><span class="sxs-lookup"><span data-stu-id="81069-194">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="81069-195">ただし、eShopOnContainers 実装では、実際にリファクターされてし、管理が容易であるために、複数のクラスにこのロジックを分割します。</span><span class="sxs-lookup"><span data-stu-id="81069-195">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult>
    UpdateProduct([FromBody]CatalogItem productToUpdate)
{
    var catalogItem = await _catalogContext.CatalogItems
        .SingleOrDefaultAsync(i => i.Id == productToUpdate.Id);

    if (catalogItem == null) return NotFound();

    bool raiseProductPriceChangedEvent = false;

    IntegrationEvent priceChangedEvent = null;

    if (catalogItem.Price != productToUpdate.Price)
        raiseProductPriceChangedEvent = true;

    if (raiseProductPriceChangedEvent) // Create event if price has changed
    {
        var oldPrice = catalogItem.Price;
        priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
            productToUpdate.Price,
            oldPrice);
    }

    // Update current product
    catalogItem = productToUpdate;
    // Achieving atomicity between original DB and the IntegrationEventLog
    // with a local transaction

    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);

        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if(raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
   }

   // Publish to event bus only if product price changed

   if (raiseProductPriceChangedEvent)
   {
       _eventBus.Publish(priceChangedEvent);
       integrationEventLogService.MarkEventAsPublishedAsync(
           priceChangedEvent);
   }

   return Ok();
}
```

<span data-ttu-id="81069-196">ProductPriceChangedIntegrationEvent 統合イベントの作成後、元のドメイン操作 (更新、カタログ アイテム) を格納するトランザクションにより、永続性イベントのイベント ログ テーブルにも含まれます。</span><span class="sxs-lookup"><span data-stu-id="81069-196">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="81069-197">これにより、1 つのトランザクションでは、常にしてイベント メッセージが送信されたかどうかを確認できません。</span><span class="sxs-lookup"><span data-stu-id="81069-197">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="81069-198">イベント ログ テーブルは、同じデータベースに対してローカル トランザクションを使用して、元のデータベース操作でアトミックに更新されます。</span><span class="sxs-lookup"><span data-stu-id="81069-198">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="81069-199">任意の操作が失敗した場合は、例外がスローされ、トランザクションはドメインの操作と送信されるイベント メッセージの間の整合性を維持するため、完了した操作をロールバックします。</span><span class="sxs-lookup"><span data-stu-id="81069-199">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="81069-200">サブスクリプションからメッセージを受信します受信者 microservices 内のイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="81069-200">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="81069-201">イベント サブスクリプション ロジックだけでなく、統合イベントのハンドラー (コールバック メソッド) の内部のコードを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-201">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="81069-202">イベント ハンドラーは、特定の種類のイベント メッセージを受信および処理される場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="81069-202">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="81069-203">まず、イベント ハンドラーは、イベント バスからイベント インスタンスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="81069-203">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="81069-204">伝達および受信者マイクロ サービスの状態の変更として、イベントを保持する、その統合イベントに関連する処理するコンポーネントが検出されます。</span><span class="sxs-lookup"><span data-stu-id="81069-204">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="81069-205">たとえば、カタログ マイクロ サービスで ProductPriceChanged イベントを生成する場合、バスケット マイクロ サービスで処理され、次のコードに示すように、この受信者バスケット マイクロ サービスで状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="81069-205">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="81069-206">イベント ハンドラーは、商品がバスケット インスタンスのいずれかに存在するかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-206">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="81069-207">また、関連バスケット品目ごとの品目の価格を更新します。</span><span class="sxs-lookup"><span data-stu-id="81069-207">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="81069-208">最後に、図 8-24 ように、価格の変更についてユーザーに表示するアラートを作成します。</span><span class="sxs-lookup"><span data-stu-id="81069-208">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="81069-209">**図 8-24**です。</span><span class="sxs-lookup"><span data-stu-id="81069-209">**Figure 8-24**.</span></span> <span data-ttu-id="81069-210">統合イベントによって受け渡されるをバスケットで項目の価格変更の表示</span><span class="sxs-lookup"><span data-stu-id="81069-210">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="81069-211">更新メッセージ イベントにべき等</span><span class="sxs-lookup"><span data-stu-id="81069-211">Idempotency in update message events</span></span>

<span data-ttu-id="81069-212">更新メッセージ イベントの重要な側面は、任意の時点、通信エラーは、再試行するメッセージで発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-212">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="81069-213">それ以外の場合、バック グラウンド タスクは既にパブリッシュされている、競合状態を作成するイベントを発行しよう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="81069-213">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="81069-214">必要とする、更新プログラムがべき等か、重複を検出できることを確認するための十分な情報を提供することを確認する破棄して、バックアップ 1 つのみの応答を送信します。</span><span class="sxs-lookup"><span data-stu-id="81069-214">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="81069-215">前述のように、べき等はこと操作は複数回結果を変更することがなくを意味します。</span><span class="sxs-lookup"><span data-stu-id="81069-215">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="81069-216">環境では、メッセージが格納されるイベントを通信するときにイベントべき等受信者マイクロ サービスの結果を変更することがなく複数回に納品される場合。</span><span class="sxs-lookup"><span data-stu-id="81069-216">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="81069-217">これが必要なイベント自体の性質か方法により、システム イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="81069-217">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="81069-218">メッセージべき等では、メッセージングを使用するアプリケーション内だけでなく、イベント バスのパターンを実装するアプリケーションに重要です。</span><span class="sxs-lookup"><span data-stu-id="81069-218">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="81069-219">べき等操作の例では、そのデータが既にテーブルにない場合にのみ、テーブルにデータを挿入する SQL ステートメントを示します。</span><span class="sxs-lookup"><span data-stu-id="81069-219">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="81069-220">何回か実行する SQL ステートメントを挿入する必要はありません。結果は同じになります:、テーブルには、そのデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="81069-220">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="81069-221">次のように、べき等することも必要に応じて、メッセージを送信した可能性がある場合にメッセージを処理するときに 1 回以上したがって処理します。</span><span class="sxs-lookup"><span data-stu-id="81069-221">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="81069-222">たとえば、再試行ロジックを正確に同じメッセージを複数回送信の送信者が発生する場合は、べき等であるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-222">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="81069-223">べき等メッセージのデザインを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="81069-223">It is possible to design idempotent messages.</span></span> <span data-ttu-id="81069-224">たとえばと表示されているイベントを作成することができます"に製品の価格を設定\$25"の代わりに"追加\$製品の価格を 5"。</span><span class="sxs-lookup"><span data-stu-id="81069-224">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="81069-225">でした安全に処理する最初のメッセージ回数を超えると、結果は同じになります。</span><span class="sxs-lookup"><span data-stu-id="81069-225">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="81069-226">2 番目のメッセージの場合は true です。</span><span class="sxs-lookup"><span data-stu-id="81069-226">That is not true for the second message.</span></span> <span data-ttu-id="81069-227">最初の場合でもたくないシステム送信できることも、新しい価格変化イベントと、新しい価格を上書きするようために、最初のイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="81069-227">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="81069-228">別の例は、複数のサブスクライバーに反映されている注文完了イベントにあります。</span><span class="sxs-lookup"><span data-stu-id="81069-228">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="81069-229">場合でも、同じ注文完了イベントのイベントは重複するメッセージが重要に注文情報が他のシステムで 1 回だけ更新されます。</span><span class="sxs-lookup"><span data-stu-id="81069-229">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="81069-230">各イベントを受信機あたり 1 回だけ処理を強制するロジックを作成するように、いくつかの種類のイベントごとの id を作成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="81069-230">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="81069-231">一部のメッセージ処理は、べき等では本質的にです。</span><span class="sxs-lookup"><span data-stu-id="81069-231">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="81069-232">たとえば、システムでは、サムネイル画像を生成する場合、可能性がありますいない関係生成したサムネイルに関するメッセージが処理された回数結果は、サムネイルが生成されるたびにそれらが同じです。</span><span class="sxs-lookup"><span data-stu-id="81069-232">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="81069-233">その一方で、クレジット_カードの請求の支払いゲートウェイを呼び出すなどの操作では、べき等なのでがまったく化できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="81069-233">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="81069-234">このような場合は、複数回のメッセージの処理に影響することであることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-234">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="81069-235">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="81069-235">Additional resources</span></span>

-   <span data-ttu-id="81069-236">**メッセージべき等に従う**(このページの小見出し) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="81069-236">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="81069-237">統合イベントのメッセージの重複除去</span><span class="sxs-lookup"><span data-stu-id="81069-237">Deduplicating integration event messages</span></span>

<span data-ttu-id="81069-238">メッセージ イベントが送信され、さまざまなレベルでサブスクライバーごとに 1 回だけ処理されることを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="81069-238">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="81069-239">1 つの方法を使用するメッセージング インフラストラクチャによって提供される重複除去機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="81069-239">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="81069-240">別は、移行先のマイクロ サービスにカスタム ロジックを実装することです。</span><span class="sxs-lookup"><span data-stu-id="81069-240">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="81069-241">検証、トランスポート レベルと、アプリケーション レベルの両方にあることが最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="81069-241">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="81069-242">イベント ハンドラーのレベルでメッセージ イベントの重複除去</span><span class="sxs-lookup"><span data-stu-id="81069-242">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="81069-243">すべての受信側で 1 回だけイベントを処理するかどうかを確認する方法の 1 つでは、イベント ハンドラーでメッセージ イベントを処理するときに、特定のロジックを実装することによってです。</span><span class="sxs-lookup"><span data-stu-id="81069-243">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="81069-244">。 たとえば、が eShopOnContainers アプリケーションで使用するアプローチでわかるように、[ソース コード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs)OrdersController クラス CreateOrderCommand コマンドを受信したときのです。</span><span class="sxs-lookup"><span data-stu-id="81069-244">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="81069-245">(ここではコマンドを使用、HTTP 要求、メッセージに基づくコマンドではなくがコマンドのメッセージに基づくべき等する必要がある論理と似ています)。</span><span class="sxs-lookup"><span data-stu-id="81069-245">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="81069-246">RabbitMQ を使用する場合は、メッセージを重複除去</span><span class="sxs-lookup"><span data-stu-id="81069-246">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="81069-247">断続的なネットワークの問題が発生してメッセージを複製することができます、メッセージの受信者はこれらの重複するメッセージを処理する準備完了である必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-247">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="81069-248">可能であれば、受信側では、べき等方法は、明示的にそれらを重複除去で処理するよりもをお勧めでメッセージを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-248">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="81069-249">よると、 [RabbitMQ ドキュメント](https://www.rabbitmq.com/reliability.html#consumer)、"メッセージがコンシューマーに配信し、キュー (たとえばコンシューマー接続が切断される前に未確認) のために再登録しと RabbitMQ に再配信フラグが設定されますときに (するかどうか、同じコンシューマーまたは別の) もう一度配布します。</span><span class="sxs-lookup"><span data-stu-id="81069-249">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="81069-250">「再配信」フラグが設定されている場合、受信側必要がありますを考慮するメッセージが既に処理されたためです。</span><span class="sxs-lookup"><span data-stu-id="81069-250">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="81069-251">ことが保証はありません。メッセージは、可能性がありますに到達しません、受信側離れた後、メッセージ ブローカーでは、おそらくネットワークの問題があるためです。</span><span class="sxs-lookup"><span data-stu-id="81069-251">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="81069-252">その一方で、「再配信」フラグが設定されていない場合は保証するメッセージが送信されていない 2 回以上。</span><span class="sxs-lookup"><span data-stu-id="81069-252">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="81069-253">そのため、受信側は、メッセージで、「再配信」フラグが設定されている場合にのみ、メッセージや、べき等方法でメッセージの処理を重複除去する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81069-253">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="81069-254">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="81069-254">Additional resources</span></span>

-   <span data-ttu-id="81069-255">**イベント ドリブン メッセージング**
    [*http://soapatterns.org/design\_パターン/イベント\_ドリブン\_メッセージング*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="81069-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="81069-256">**Jimmy Bogard。に対する回復力のリファクタリング: 結合の評価**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="81069-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="81069-257">**公開/定期受信チャネル**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="81069-257">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="81069-258">**コンテキスト間の通信範囲指定された**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="81069-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="81069-259">**最終的整合性**
    [*https://en.wikipedia.org/wiki/Eventual\_整合性*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="81069-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="81069-260">**Philip Brown です。コンテキストに制限を統合するための戦略**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="81069-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="81069-261">**Chris Richardson です。開発の集計、イベント ソース、CQRS - パート 2 を使用してトランザクション Microservices**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="81069-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="81069-262">**Chris Richardson です。イベント ソーシング パターン**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="81069-262">**Chris Richardson. Event Sourcing pattern**
[*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="81069-263">**イベント ソースの概要**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="81069-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="81069-264">**イベント ストア データベース**です。</span><span class="sxs-lookup"><span data-stu-id="81069-264">**Event Store database**.</span></span> <span data-ttu-id="81069-265">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="81069-265">Official site.</span></span>
    [<span data-ttu-id="81069-266">*https://geteventstore.com/*</span><span class="sxs-lookup"><span data-stu-id="81069-266">*https://geteventstore.com/*</span></span>](https://geteventstore.com/)

-   <span data-ttu-id="81069-267">**Patrick Nommensen です。イベント ドリブンのデータ管理 Microservices を**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*</span><span class="sxs-lookup"><span data-stu-id="81069-267">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="81069-268">**キャップの定理**
    [*https://en.wikipedia.org/wiki/CAP\_定理*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="81069-268">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="81069-269">**キャップの定理とは何ですか。** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="81069-269">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="81069-270">**データ整合性の入門**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="81069-270">**Data Consistency Primer**
[*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="81069-271">**Rick Saling です。キャップの定理: ため「すべてのものが異なる」クラウドやインターネット**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="81069-271">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="81069-272">**Eric 醸造会社です。CAP 12 年後:「ルール」が変更された方法**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="81069-272">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="81069-273">**外部 (DTC) トランザクションに参加している**(MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="81069-273">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="81069-274">**Azure Service Bus。仲介型メッセージング: 重複データ検出**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="81069-274">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="81069-275">**信頼性ガイド**(RabbitMQ ドキュメント) [ *https://www.rabbitmq.com/reliability.html\#コンシューマー*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="81069-275">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="81069-276">[前](rabbitmq-event-bus-development-test-environment.md) [次へ] (test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="81069-276">[Previous] (rabbitmq-event-bus-development-test-environment.md) [Next] (test-aspnet-core-services-web-apps.md)</span></span>

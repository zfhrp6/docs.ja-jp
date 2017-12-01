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
# <a name="subscribing-to-events"></a>イベントにサブスクライブします。

イベント バスを使用するための最初の手順では、microservices を受信するイベントをサブスクライブします。 受信者 microservices で行う必要があります。

次の単純なコードを実装するサービスの開始時に必要な各受信者マイクロ サービスを示しています (つまり、スタートアップ クラス) ため、そのイベントをサブスクライブすることが必要です。 たとえば、basket.api マイクロ サービスを ProductPriceChangedIntegrationEvent メッセージをサブスクライブする必要があります。 これは製品の価格をマイクロ サービスをすべての変更を認識され、その製品がユーザーのバスケットの場合の変更についてユーザーに警告します。

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

このコードを実行した後、サブスクライバー マイクロ サービスは RabbitMQ チャネルを通じて、リッスンしています。 ProductPriceChangedIntegrationEvent の種類のすべてのメッセージが到着すると、コードは、それに渡され、イベントを処理するイベント ハンドラーを呼び出します。

## <a name="publishing-events-through-the-event-bus"></a>イベント バスを介してイベントの発行

最後に、メッセージの送信者 (原点マイクロ サービス) は、次の例のようなコードとの統合イベントを公開します。 (これは、簡単な例を考慮原子性を受け取らないです)。同様のコードを実装することで、複数 microservices、通常のデータまたは原点マイクロ サービスからのトランザクションのコミット直後にイベントを反映する必要があるたびになります。

最初に、イベント バスの実装オブジェクト (RabbitMQ に基づいてまたは service bus に基づく) を挿入して、次のコードのように、コント ローラーのコンス トラクターには。

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

コント ローラーのメソッドからのようなメソッドで使用する、UpdateProduct:

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

この場合、原点マイクロ サービスが単純な CRUD マイクロ サービスのため、そのコードは直後に配置される Web API コント ローラーにします。 高度な microservices でそのでしたクラスで実装する、CommandHandler、右がコミットされると、元のデータ。

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>イベント バスに発行するときに、原子性と回復性の設計

分散メッセージングを通じて統合イベントを発行するときにシステムなどのイベント バスがアトミックに元のデータベースを更新し、イベントの発行の問題です。 インスタンスの例では、簡略化された前に示した、コードは、データベースにコミット データと製品の価格が変更された ProductPriceChangedIntegrationEvent メッセージを公開します。 最初に、これら 2 つの操作が自動的に実行される重要なことになります。 ただし、関連する分散トランザクションを使用している場合、データベースと、メッセージ ブローカーと同様に、以前のシステムの場合と[Microsoft メッセージ キュー (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)、が示す理由により推奨されてはいません[CAP 定理](https://www.quora.com/What-Is-CAP-Theorem-1)です。

基本的には、拡張性と可用性の高いシステムを構築する microservices を使用します。 キャップの定理という多少を簡略化することは、データベース (またはそのモデルを所有しているマイクロ サービス) をビルドすることはできません継続的に利用可能な強い一貫性のある*と*任意のパーティションに対する許容度がします。 これら 3 つのプロパティの 2 つを選択する必要があります。

Microservices ベースのアーキテクチャでは、可用性と許容範囲を選択する必要がありますで強力な一貫性を乗算する必要があります。 そのため、最近のほとんどのマイクロ サービス ベースのアプリケーションで通常たくないメッセージング、分散トランザクションを使用するように実装する場合に、実行[分散トランザクション](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c)Windows 分散トランザクションに基づくコーディネーター (DTC) と[MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx)です。

初期の問題とその例に確認しましょう。 データベースを更新した後、サービスがクラッシュした場合 (この場合、使用してコードの行の後に右\_コンテキスト。SaveChangesAsync()) が、統合イベントを公開すると、前に、全体的なシステム不整合が発生します。 これにより、発生している特定のビジネス操作に応じて、重要なビジネス可能性があります。

前述のアーキテクチャ」で、この問題に対処するためのいくつかのアプローチを持つことができます。

-   完全な[イベント基になるパターン](https://msdn.microsoft.com/en-us/library/dn589792.aspx)です。

-   使用して[トランザクション ログ マイニング](http://www.scoop.it/t/sql-server-transaction-log-mining)です。

-   使用して、[送信トレイ パターン](http://gistlabs.com/2014/05/the-outbox/)です。 これは、トランザクション (ローカル トランザクションを拡張する) 統合イベントを格納するテーブルです。

このシナリオでは、フル イベントの基になる (ES) パターンを使用して、最善の方法のいずれかの以外の場合*、*ベストです。 ただし、多くのアプリケーション シナリオでできない完全 ES システムを実装します。 ES では、現在の状態データを保管する代わりに、トランザクションのデータベース内のドメインのイベントのみを格納することを意味します。 ドメインのイベントのみを格納すると、使用可能なシステムの履歴され、過去の時点で、システムの状態を決定できるなどの大きなメリットことができます。 ただし、完全な ES システムを実装する、システムの大部分を再構築する必要があり、その他の多くの複雑さや要件を紹介します。 具体的にはに対するイベントの基になるなどのデータベースを使用するなど、[イベント ストア](https://geteventstore.com/)、または Azure Cosmos DB、MongoDB、Cassandra、CouchDB、RavenDB など、ドキュメント指向のデータベースです。 ES は、イベントのソースとして使い慣れている場合を除き、この問題が最も簡単なソリューションではなくの優れた方法です。

トランザクション ログが最初にマイニングを使用するオプションは、透過的な非常に検索します。 ただし、このアプローチを使用するのには、SQL Server トランザクション ログなど、RDBMS トランザクション ログと連結されるように、マイクロ サービスがあります。 これが望ましくない可能性があります。 別の欠点は、低レベルの更新トランザクション ログに記録できないことがあります、高度な統合イベントと同じレベルにします。 場合は、リバース エンジニア リングのプロセス、トランザクション ログの処理困難になります。

バランスの取れた手法は、トランザクションのデータベース テーブルおよび簡略化された ES パターンの組み合わせです。 「準備完了のイベントを公開する」統合イベント テーブルにコミットする場合は、元のイベントで設定するなどの状態を使用することができます。 イベントをイベント バスに発行しようとするとします。 Origin サービスで別のトランザクションを開始して、状態を「、イベントを公開する準備完了」から「イベントが既にパブリッシュされている」に移動発行イベントのアクションが成功すると、

発行イベントのアクションでは、失敗、イベント バス、データがなります原点マイクロ サービス内で一貫性のない-これは、引き続き可能としてマーク"、イベントを公開する"とに関して、残りのサービスでは、それが最終的に一致します。 常にバック グラウンド ジョブをトランザクションまたは統合イベントの状態を確認することができます。 ジョブには、「イベントを発行する準備完了」状態のイベントが検出されるは、そのイベントをイベント バスの再発行を試行できます。

この方法で永続化する各オリジン マイクロ サービスの統合イベントのみが、および他の microservices または外部システムと通信するイベントのみに注意してください。 これに対し、ES システムの完全には、すべてのドメイン イベントもを格納します。

そのため、このバランスの取れた手法は、簡略化された ES システムです。 現在の状態との統合イベントの一覧を作成する必要があります (「準備ができてを公開する」と「パブリッシュ」) です。 のみ統合イベントのこれらの状態を実装する必要があります。 この方法でする必要はありません、トランザクションのデータベース内のイベントとして、すべてのドメイン データを格納する、完全な ES システムの場合とします。

既にリレーショナル データベースを使用する場合は、統合イベントを格納するトランザクション テーブルを使用できます。 アプリケーションで原子性を実現するには、ローカル トランザクションに基づく 2 段階のプロセスを使用します。 基本的には、テーブルがある場合、IntegrationEvent ドメイン エンティティがある、同じデータベースにします。 そのテーブルは、含めるができるように、原子性を実現するための保険会社では、ドメインのデータがコミットされる同じトランザクションに統合イベントが永続化とは動作します。

プロセスが次のようになったステップ バイ ステップ: アプリケーションがローカルのデータベース トランザクションを開始します。 ドメイン エンティティの状態を更新し、イベントを統合イベントのテーブルに挿入します。 最後に、トランザクションをコミットします。 目的の原子性が表示されます。

イベントを公開する次の手順を実装する場合は、これらの選択肢があります。

-   トランザクションのコミット直後に、統合イベントを発行し、別のローカル トランザクションを使用してパブリッシュされると、テーブル内のイベントをマークします。 成果物と同様にテーブルを使用して、リモートの microservices で問題が発生した場合、統合イベントを追跡し、ストアド統合イベントに基づくな補正アクションを実行します。

-   キューの種類として、テーブルを使用します。 独立したアプリケーションのスレッドまたはプロセスは、統合イベント テーブルを照会し、イベントをイベント バスに発行、ローカル トランザクションを使用して、発行されると、イベントをマークします。

図 8-22 は、これらの方法のうちの最初のアーキテクチャを示します。

![](./media/image23.png)

**図 8-22**です。 イベントをイベント バスに発行するときの原子性

図 8-22 を示すアプローチには、担当のチェックと、パブリッシュされた統合イベントの成功を確認する追加の作業者マイクロ サービスがありません。 障害の発生、その追加チェッカー ワーカー マイクロ サービスは、テーブルからイベントを読み取るし、それらを再パブリッシュできます。

2 番目の方法について: キューとしてイベント ログ テーブルを使用して、常に、メッセージを公開するワーカー マイクロ サービスを使用します。 その場合は、プロセスにはそのような図 8-23 が表示されます。 これにより、表示、追加のマイクロ サービスと、イベントを発行するときに、テーブルが 1 つのソース。

![](./media/image24.png)

**図 8-23**です。 イベントをワーカー マイクロ サービスを持つイベント バスに発行するときの原子性

わかりやすくするためは、eShopOnContainers サンプルは、さらに、イベント バス (なし、その他のプロセスまたはチェッカー microservices) の最初の方法を使用します。 ただし、eShopOnContainers は、すべての可能な失敗した場合は処理されていません。 クラウドに展開されている実際のアプリケーションで確認し、ロジックを再送信するファクト最終的には、問題が発生し、実装する必要がありますを採用する必要があります。 キューとして、テーブルを使用できる最初の方法よりも効果的イベント バスを介して公開するときのイベントの 1 つのソースとしてそのテーブルがある場合。

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>イベント バスを通じて統合イベントを発行するときに、原子性を実装します。

次のコードは、複数の DbContext オブジェクトを含む 1 つのトランザクションを作成する方法を示しています。 — 元のデータの更新に関連する 1 つのコンテキストと IntegrationEventLog テーブルに関連する 2 つ目のコンテキスト。

次のサンプル コードでのトランザクションに含まれない回復力のあるコードが実行されている時に、データベースへの接続に問題が発生する場合に注意してください。 これは、Azure SQL DB サーバー間でデータベースを移動する可能性がありますと同様に、クラウド ベースのシステムで発生することができます。 回復力のあるトランザクションを実装する、複数のコンテキストにわたってを参照してください、[回復力のある Entity Framework の主要な SQL 接続の実装](#implementing_resilient_EFCore_SQL_conns)このガイドの後半の「します。

わかりやすくするためは、次の例は、コードの 1 つのプロセス全体を示します。 ただし、eShopOnContainers 実装では、実際にリファクターされてし、管理が容易であるために、複数のクラスにこのロジックを分割します。

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

ProductPriceChangedIntegrationEvent 統合イベントの作成後、元のドメイン操作 (更新、カタログ アイテム) を格納するトランザクションにより、永続性イベントのイベント ログ テーブルにも含まれます。 これにより、1 つのトランザクションでは、常にしてイベント メッセージが送信されたかどうかを確認できません。

イベント ログ テーブルは、同じデータベースに対してローカル トランザクションを使用して、元のデータベース操作でアトミックに更新されます。 任意の操作が失敗した場合は、例外がスローされ、トランザクションはドメインの操作と送信されるイベント メッセージの間の整合性を維持するため、完了した操作をロールバックします。

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>サブスクリプションからメッセージを受信します受信者 microservices 内のイベント ハンドラー。

イベント サブスクリプション ロジックだけでなく、統合イベントのハンドラー (コールバック メソッド) の内部のコードを実装する必要があります。 イベント ハンドラーは、特定の種類のイベント メッセージを受信および処理される場所を指定します。

まず、イベント ハンドラーは、イベント バスからイベント インスタンスを受け取ります。 伝達および受信者マイクロ サービスの状態の変更として、イベントを保持する、その統合イベントに関連する処理するコンポーネントが検出されます。 たとえば、カタログ マイクロ サービスで ProductPriceChanged イベントを生成する場合、バスケット マイクロ サービスで処理され、次のコードに示すように、この受信者バスケット マイクロ サービスで状態を変更します。

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

イベント ハンドラーは、商品がバスケット インスタンスのいずれかに存在するかどうかを確認する必要があります。 また、関連バスケット品目ごとの品目の価格を更新します。 最後に、図 8-24 ように、価格の変更についてユーザーに表示するアラートを作成します。

![](./media/image25.png)

**図 8-24**です。 統合イベントによって受け渡されるをバスケットで項目の価格変更の表示

## <a name="idempotency-in-update-message-events"></a>更新メッセージ イベントにべき等

更新メッセージ イベントの重要な側面は、任意の時点、通信エラーは、再試行するメッセージで発生する必要があります。 それ以外の場合、バック グラウンド タスクは既にパブリッシュされている、競合状態を作成するイベントを発行しよう可能性があります。 必要とする、更新プログラムがべき等か、重複を検出できることを確認するための十分な情報を提供することを確認する破棄して、バックアップ 1 つのみの応答を送信します。

前述のように、べき等はこと操作は複数回結果を変更することがなくを意味します。 環境では、メッセージが格納されるイベントを通信するときにイベントべき等受信者マイクロ サービスの結果を変更することがなく複数回に納品される場合。 これが必要なイベント自体の性質か方法により、システム イベントを処理します。 メッセージべき等では、メッセージングを使用するアプリケーション内だけでなく、イベント バスのパターンを実装するアプリケーションに重要です。

べき等操作の例では、そのデータが既にテーブルにない場合にのみ、テーブルにデータを挿入する SQL ステートメントを示します。 何回か実行する SQL ステートメントを挿入する必要はありません。結果は同じになります:、テーブルには、そのデータが含まれています。 次のように、べき等することも必要に応じて、メッセージを送信した可能性がある場合にメッセージを処理するときに 1 回以上したがって処理します。 たとえば、再試行ロジックを正確に同じメッセージを複数回送信の送信者が発生する場合は、べき等であるかどうかを確認する必要があります。

べき等メッセージのデザインを行うことができます。 たとえばと表示されているイベントを作成することができます"に製品の価格を設定\$25"の代わりに"追加\$製品の価格を 5"。 でした安全に処理する最初のメッセージ回数を超えると、結果は同じになります。 2 番目のメッセージの場合は true です。 最初の場合でもたくないシステム送信できることも、新しい価格変化イベントと、新しい価格を上書きするようために、最初のイベントを処理します。

別の例は、複数のサブスクライバーに反映されている注文完了イベントにあります。 場合でも、同じ注文完了イベントのイベントは重複するメッセージが重要に注文情報が他のシステムで 1 回だけ更新されます。

各イベントを受信機あたり 1 回だけ処理を強制するロジックを作成するように、いくつかの種類のイベントごとの id を作成すると便利です。

一部のメッセージ処理は、べき等では本質的にです。 たとえば、システムでは、サムネイル画像を生成する場合、可能性がありますいない関係生成したサムネイルに関するメッセージが処理された回数結果は、サムネイルが生成されるたびにそれらが同じです。 その一方で、クレジット_カードの請求の支払いゲートウェイを呼び出すなどの操作では、べき等なのでがまったく化できない可能性があります。 このような場合は、複数回のメッセージの処理に影響することであることを確認する必要があります。

### <a name="additional-resources"></a>その他の技術情報

-   **メッセージべき等に従う**(このページの小見出し) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>統合イベントのメッセージの重複除去

メッセージ イベントが送信され、さまざまなレベルでサブスクライバーごとに 1 回だけ処理されることを確認することができます。 1 つの方法を使用するメッセージング インフラストラクチャによって提供される重複除去機能を使用します。 別は、移行先のマイクロ サービスにカスタム ロジックを実装することです。 検証、トランスポート レベルと、アプリケーション レベルの両方にあることが最善の方法です。

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>イベント ハンドラーのレベルでメッセージ イベントの重複除去

すべての受信側で 1 回だけイベントを処理するかどうかを確認する方法の 1 つでは、イベント ハンドラーでメッセージ イベントを処理するときに、特定のロジックを実装することによってです。 。 たとえば、が eShopOnContainers アプリケーションで使用するアプローチでわかるように、[ソース コード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs)OrdersController クラス CreateOrderCommand コマンドを受信したときのです。 (ここではコマンドを使用、HTTP 要求、メッセージに基づくコマンドではなくがコマンドのメッセージに基づくべき等する必要がある論理と似ています)。

### <a name="deduplicating-messages-when-using-rabbitmq"></a>RabbitMQ を使用する場合は、メッセージを重複除去

断続的なネットワークの問題が発生してメッセージを複製することができます、メッセージの受信者はこれらの重複するメッセージを処理する準備完了である必要があります。 可能であれば、受信側では、べき等方法は、明示的にそれらを重複除去で処理するよりもをお勧めでメッセージを処理する必要があります。

よると、 [RabbitMQ ドキュメント](https://www.rabbitmq.com/reliability.html#consumer)、"メッセージがコンシューマーに配信し、キュー (たとえばコンシューマー接続が切断される前に未確認) のために再登録しと RabbitMQ に再配信フラグが設定されますときに (するかどうか、同じコンシューマーまたは別の) もう一度配布します。

「再配信」フラグが設定されている場合、受信側必要がありますを考慮するメッセージが既に処理されたためです。 ことが保証はありません。メッセージは、可能性がありますに到達しません、受信側離れた後、メッセージ ブローカーでは、おそらくネットワークの問題があるためです。 その一方で、「再配信」フラグが設定されていない場合は保証するメッセージが送信されていない 2 回以上。 そのため、受信側は、メッセージで、「再配信」フラグが設定されている場合にのみ、メッセージや、べき等方法でメッセージの処理を重複除去する必要があります。

### <a name="additional-resources"></a>その他の技術情報

-   **イベント ドリブン メッセージング**
    [*http://soapatterns.org/design\_パターン/イベント\_ドリブン\_メッセージング*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard。に対する回復力のリファクタリング: 結合の評価**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **公開/定期受信チャネル**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **コンテキスト間の通信範囲指定された**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)

-   **最終的整合性**
    [*https://en.wikipedia.org/wiki/Eventual\_整合性*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip Brown です。コンテキストに制限を統合するための戦略**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Richardson です。開発の集計、イベント ソース、CQRS - パート 2 を使用してトランザクション Microservices**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Richardson です。イベント ソーシング パターン**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)

-   **イベント ソースの概要**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)

-   **イベント ストア データベース**です。 公式サイト。
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen です。イベント ドリブンのデータ管理 Microservices を**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*

-   **キャップの定理**
    [*https://en.wikipedia.org/wiki/CAP\_定理*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **キャップの定理とは何ですか。** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **データ整合性の入門**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)

-   **Rick Saling です。キャップの定理: ため「すべてのものが異なる」クラウドやインターネット**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric 醸造会社です。CAP 12 年後:「ルール」が変更された方法**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **外部 (DTC) トランザクションに参加している**(MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure Service Bus。仲介型メッセージング: 重複データ検出**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **信頼性ガイド**(RabbitMQ ドキュメント) [ *https://www.rabbitmq.com/reliability.html\#コンシューマー*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[前](rabbitmq-event-bus-development-test-environment.md) [次へ] (test-aspnet-core-services-web-apps.md)

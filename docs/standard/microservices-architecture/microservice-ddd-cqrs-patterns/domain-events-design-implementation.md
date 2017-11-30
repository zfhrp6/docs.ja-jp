---
title: "ドメインのイベントです。 設計と実装"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |ドメインのイベント、設計と実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2d98b302be4ee72d8225526944fc3e41cbadcb5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="domain-events-design-and-implementation"></a>ドメインのイベント: 設計と実装

ドメイン内で変更の副作用を明示的に実装するのにには、ドメインのイベントを使用します。 その他の語と DDD 用語を使用して、複数の集計の間での副作用を明示的に実装するのにドメイン イベントを使用します。 必要に応じて、スケーラビリティが向上し、データベースのロックの影響を軽減は、同じドメイン内の集計の間で最終的整合性を使用します。

## <a name="what-is-a-domain-event"></a>ドメインのイベントとは何ですか。

イベントは、過去に発生したものです。 ドメインのイベントは、論理的には、特定のドメインで発生した、同じドメイン (インプロセス) を認識し、潜在的に対応するための他の部分を何かたいとします。

ドメインのイベントの重要な利点は、暗黙的にではなく副作用後、ドメインに問題が発生しましたを明示的に表現することができます。 効果必要があります一貫性のある、すべての操作、ビジネス タスクに関連する発生する可能性がそれらの側かのいずれかにします。 さらに、ドメインのイベントには、同じドメイン内のクラス間で問題の分離を強化しが有効にします。

たとえば、ユース ケースによって生じる副作用である必要がある場合にだけ、Entity Framework とエンティティまたは偶数の集計だけを使用する場合、ものとして実装されます、結合されたコードでの暗黙的な概念後、問題が発生しました。 ただし、のみが表示コードをわからない場合があります (副作用) そのコードがメインの操作の一部である場合、または副作用ですか。 その一方で、ドメインのイベントを使用して、概念明示的なとユビキタス言語の一部。 たとえば、eShopOnContainers アプリケーションで注文を作成するはほぼ順序です。更新またはユーザーにないため、購入者に注文があるまで、元のユーザーに基づく buyer の集計を作成します。 ドメインのイベントを使用する場合は、ドメインの専門家によって提供されるユビキタス言語に基づく、ドメイン ルールを明示的に表現できます。

ドメイン イベントは、1 つの重要な相違点のメッセージング スタイルのイベントに似ています。 実際のメッセージング、メッセージ キュー、メッセージ ブローカーまたは AMPQ を使用して、サービス バス、メッセージは常に非同期的に送信し、プロセスとマシンの間で通信します。 これは、複数のコンテキストの境界を付けられた、microservices、または別のアプリケーションを統合するために役立ちます。 ただし、ドメインのイベント、現在実行しているドメイン操作からイベントを発生するが、同じドメイン内に発生するすべての副作用をします。

ドメインのイベントとその副作用 (実行されたアクション後のイベント ハンドラーで管理されている) をほぼ即座に実行する通常のプロセス、および同じドメイン内で。 したがって、ドメインのイベントは、同期または非同期可能性があります。 統合イベント、ただしは常に非同期です。

## <a name="domain-events-versus-integration-events"></a>統合イベントではなくドメイン イベント

ドメインとの統合のイベントは、同じことを意味します。 だけ発生した問題に関する通知。 ただし、その実装は異なる必要があります。 ドメインのイベントは、IoC コンテナーまたはその他のメソッドに基づくメモリの媒介として実装される可能性がありますドメインのイベント ディスパッチャーにプッシュされただけのメッセージです。

その一方で、統合イベントの目的は、や他の microservices、範囲指定されたコンテキストでも外部アプリケーションでかどうかにコミットされたトランザクションとその他のサブシステムへの更新が反映されるまでです。 それらを実行するため、エンティティが正常に保存されている場合から多くのシナリオでこれが失敗した場合は、操作全体効果的がなかったかのみです。

説明したように、統合とさらに、イベントを複数の microservices (他の境界を付けられたコンテキスト) またはも外部システムとアプリケーション間の非同期通信に基づいている必要があります。 したがって、イベント バス インターフェイスには、プロセス間では、可能性のあるリモート サービスの間の通信を分散するインフラストラクチャの一部が必要があります。 商用サービス バス、キュー、メールボックスとして使用される共有データベースまたはその他の分散に基づくことができ、理想的にはベースのメッセージング システムをプッシュします。

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>同じドメイン内の複数の集計の間での副作用をトリガーする方法をお勧めとしてドメイン イベント

集計インスタンスには、1 つまたは複数の他の集計で実行する追加のドメイン ルールが必要です。 いずれかに関連するコマンドを実行している場合は、設計およびドメインのイベントによってトリガーされるこれらの副作用を実装する必要があります。 図 9-14 に示すように、最も重要なの 1 つとしてユース ケース、ドメイン イベントは、同じドメイン モデル内の複数の集計の状態の変更を伝達するために使用する必要があります。

![](./media/image15.png)

**図 9-14**です。 同じドメイン内の複数の集計の間の整合性のためにドメイン イベント

図では、ユーザーは、注文を開始したときに、OrderStarted ドメイン イベントは情報と共に、CreateOrder コマンドで identity マイクロ サービスから元のユーザー情報に基づく順序マイクロ サービスの購入者オブジェクトの作成をトリガーします。 ドメインのイベントは、最初の場所の作成時に、順序集計によって生成されます。

代わりに、その集計 (子エンティティ) のメンバーによって発生するイベントを定期受信されている集計ルートを持つことができます。 たとえば、各 OrderItem 子エンティティは、品目の価格は、特定の容量を超えた場合、または製品品目の量が高すぎるとに、イベントを発生させることができます。 集計のルートは、これらのイベントを受信し、グローバルの計算または集計を実行します。

このイベント ベースの通信が; 集計内で直接実装していないことを理解することが重要ドメインのイベント ハンドラーを実装する必要があります。 イベントを処理するドメインは、アプリケーション問題です。 ドメイン モデル レイヤーが、ドメイン ロジックに専念する必要がありますのみ — ドメインの専門家が理解できるようにすること、ハンドラーおよびリポジトリを使用して、副作用が永続性アクションなど、アプリケーション インフラストラクチャされません。 したがって、アプリケーション層のレベルは、ドメインのイベントが発生したときにアクションをトリガーするドメインのイベント ハンドラーを持つ必要があります。

ドメインのイベントは、任意の数のアプリケーションのアクションをトリガーするも使用できより重要な数を増やすにその後で、分離された方法で開く必要があります。 たとえば、順序が開始されると、ことができますをその他の集計には、その情報を伝達する、または通知のようにアプリケーションのアクションを発生させる場合にもドメイン イベントを公開します。

重要な点は、ドメインのイベントが発生したときに実行されるアクションの開いている数です。 最終的には、アクションと、ドメインおよびアプリケーション内のルールが大きくなります。 複雑さや問題が起こったときに副作用がアクションの数が増大、コードが「グルー」を伴う場合は (つまり、C では、new キーワードを持つオブジェクトをインスタンス化だけ\#)、たびに、新しいアクションを追加する必要とする必要があります。元のコードを変更します。 これは、結果、新しいバグは、各新しい要件が必要になる元のコードのフロー方向を変更します。 これには、に対して、[開く/解決済みの原則](https://en.wikipedia.org/wiki/Open/closed_principle)から[ソリッド](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))です。 それだけでなく、操作を対象に調整された元のクラスは拡張し、拡大、に対してに出向いて、[単一責任原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)です。

その一方で、ドメインのイベントを使用する場合は、このアプローチを使用する責任を隔離することによって粒度の細かいと分離の実装を作成することができます。

1.  コマンド (たとえば、CreateOrder) を送信します。
2.  コマンド ハンドラーで、コマンドを受信します。
    -   1 つの集計のトランザクションを実行します。
    -   (省略可能)副作用 (たとえば、OrderStartedDomainDvent) のドメインのイベントを発生させます。
1.  ハンドル ドメイン (現在のプロセス) 内のイベント thast は複数の集計またはアプリケーションのアクションの副作用のオープンの数を実行します。 例:
    -   確認するか、購入者および支払方法を作成します。
    -   作成し、購入者に電子メールを送信するように microservices またはトリガーの外部アクション間で状態を反映する、イベント バスに関連する統合イベントを送信します。
    -   その他の副作用を処理します。

図 9-15 を示すように、同じドメインのイベントから開始処理すること、ドメインまたは統合イベントおよびイベント バスに接続する microservices 全体を実行する必要があります。 追加のアプリケーション操作には、その他の集計に関連する複数のアクション。

![](./media/image16.png)

**図 9-15**です。 ドメインごとの複数のアクションの処理

イベント ハンドラーは通常、アプリケーション レイヤーでマイクロ サービスの動作のリポジトリまたはアプリケーションの API などのインフラストラクチャ オブジェクトを使用するためです。 その意味で、イベント ハンドラーは、どちらも、アプリケーション層の一部であるためコマンド ハンドラーに似ています。 重要な相違点は、コマンドを 1 回だけ処理する必要があります。 ドメイン イベント可能性がありますゼロを処理または *n* ためにがタイムアウトと場合、によって複数の受信器または各ハンドラーに対して別の目的でイベント ハンドラーを受信することができます。

数が開いている各ドメインのイベント ハンドラーの可能性には、現在コードに影響を与えずに多くのドメイン ルールを追加することができます。 たとえば、右側に発生するイベントの後に次のビジネス ルールを実装するが、いくつかのイベント ハンドラー (または 1 つのみでも) を追加することと同じくらい簡単可能性があります。

任意の数、注文の間で、ストアで顧客が購入合計金額が $6,000 を超える場合は、割引は 10% をすべて新しい注文に適用され、そのに割引された料金未来の注文に関する電子メールを顧客に通知します。

## <a name="implementing-domain-events"></a>ドメインのイベントを実装します。

C# の場合は、ドメイン イベントだけで、データを保持構造体またはクラスでは、次の例で示すように、ドメインでの発生に関連するすべての情報を DTO と同様に。

```csharp
public class OrderStartedDomainEvent : IAsyncNotification
{
    public int CardTypeId { get; private set; }
    public string CardNumber { get; private set; }
    public string CardSecurityNumber { get; private set; }
    public string CardHolderName { get; private set; }
    public DateTime CardExpiration { get; private set; }
    public Order Order { get; private set; }

    public OrderStartedDomainEvent(Order order,
        int cardTypeId, string cardNumber,
        string cardSecurityNumber, string cardHolderName,
        DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

これは、本質的に OrderStarted イベントに関連するすべてのデータを保持するクラスです。

ドメインの場所を問わず、言語の観点から イベントは、以前は、発生したため、イベントのクラス名は、OrderStartedDomainEvent OrderShippedDomainEvent などの過去形動詞として表さ必要があります。 EShopOnContainers で順序付けマイクロ サービスでドメインのイベントを実装する方法です。

触れましたが、イベントの重要な特性をイベントとは、変更しないでください、過去に発生したためです。 したがって、変更できないクラスである必要があります。 プロパティは読み取り専用からオブジェクトの外部で上記のコードで確認できます。 オブジェクトを更新する唯一の方法は、イベント オブジェクトを作成するときに、コンス トラクターです。

### <a name="raising-domain-events"></a>ドメインのイベントを発生させる

次の質問は、その関連するイベント ハンドラーに到達するためにドメイン イベントを発生させる方法を示します。 複数の方法を使用することができます。

Udi Dahan が最初に提案された (など、複数の関連する投稿など[イベントのドメインを 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) を管理して、イベントを発生させるため、静的クラスを使用します。 静的という名前のクラスがイベントを発生させるドメイン、呼び出された場合にすぐに DomainEvents DomainEvents.Raise (イベント myEvent) のような構文を使用してこのことがあります。 Jimmy Bogard 書いたブログ投稿 ([、ドメインの強化: ドメイン イベント](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/))、同様のアプローチすることをお勧めします。

ただし、ドメインのイベント クラスの静的な場合にもディスパッチ ハンドラーにすぐにします。 これにより、テストおよびデバッグが難しく、副作用のロジックを持つイベント ハンドラーは、イベントが発生した後すぐに実行されるためです。 フォーカスとだけ何が起こっているか、現在の集計クラスでするテスト、デバッグしているときに突然にリダイレクトするその他の集計またはアプリケーション ロジックに関連する副作用の他のイベント ハンドラーはしません。 これによっては他のアプローチが進化に伴い、理由は、次のセクションで説明したようです。

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>遅延を発生させると、イベントのディスパッチのアプローチ

ドメインのイベント ハンドラーにすぐにディスパッチなどではなくより適切な方法がイベントを追加する、ドメインのコレクションには、そのドメインのこれらのイベントをディスパッチするために*直前*または*右* *後*(EF に SaveChanges) と同様に、トランザクションをコミットします。 (このアプローチは、この投稿の Jimmy Bogard によって説明された[向上ドメインのイベント パターン](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/))。

ドメインのイベントを送信するかどうかを決定するトランザクションをコミットした後に右の前に、または右は重要ですが、または別のトランザクションで同じトランザクションの一部として、副作用を含めるかどうかを決定するためです。 後者の場合、複数の集計で最終的整合性に対処する必要があります。 このトピックは、次のセクションで説明しています。

遅延のアプローチは、どのような eShopOnContainers 使用です。 最初に、コレクションまたはエンティティごとのイベントの一覧に、エンティティで行われているイベントを追加します。 その一覧には、次の例のように、エンティティ オブジェクトの一部またはさらに、基本エンティティ クラスの一部をする必要があります。

```csharp
public abstract class Entity
{
    private List<IAsyncNotification> _domainEvents;

    public List<IAsyncNotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(IAsyncNotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<IAsyncNotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(IAsyncNotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

イベントを発生させる場合は、単に追加するコードを次に示すように、集計 entity メソッド内に配置するイベントの収集。

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
    cardTypeId,
    cardNumber,
    cardSecurityNumber,
    cardHolderName,
    cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

AddDomainEvent メソッドを行っていることだけが一覧に、イベントを追加することに注意してください。 イベントは生成されませんまだ、およびイベント ハンドラーは呼び出されませんまだです。

実際にするデータベースへのトランザクションをコミットする場合、後で、イベントをディスパッチします。 Entity Framework のコアを使用している場合は、次のコードと同様に、EF DbContext の SaveChanges メソッドでします。

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<int> SaveEntitiesAsync()
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);
        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

このコードでは、それぞれのそれぞれのイベント ハンドラーにエンティティのイベントをディスパッチします。

全体の結果は、ことが分離 (単純なリストに追加のメモリに) ドメインのイベントの発生からイベント ハンドラーにディスパッチします。 さらに、ディスパッチャーの種類を使用することによって、同期または非同期でイベントをディスパッチでしたします。

重要になっているトランザクションの境界をここで再生ことに注意してください。 作業時間とトランザクションの場合は、単位は、複数の集計をまたがることができる場合 (として EF コアおよびリレーショナル データベースを使用する場合)、うまくいかないことができます。 一貫性を実現するために追加の手順を実装するためにする場合は、トランザクションは、Azure DocumentDB のような NoSQL データベースを使用する場合などの集計をまたぐことはできません。 これは、永続性の無視がユニバーサル; 別の理由使用する記憶域システムによって異なります。

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>集計の集計で最終的整合性との間で 1 つのトランザクション

意見の分かれる最終的整合性の証明書利用者の間でのそれらの集計と集計の間で 1 つのトランザクションを実行するかどうかの質問はあります。 多くの DDD 作成者 Eric Evans と Vaughn カバー推奨規則を 1 つのトランザクションと同じように = 1 つの集計と集計の間で最終的整合性のためと主張します。 たとえば、著書で*ドメイン デザイン*は、Eric Evans:

集計にわたるすべてのルールは、常に最新の状態にする必要ありません。 イベント処理、バッチ処理、またはその他の更新メカニズム、を介して他の依存関係できます内に解決する特定の時刻。 (pg です。 128)

Vaughn カバーでは、次の質問[効果的な集計のデザインします。パート II: 行う集計作業まとめて](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

したがって、集計インスタンスは、1 つまたは複数の集計に関するその他のビジネス ルールを実行する必要がありますいずれかのコマンドを実行している場合を使用して最終的整合性\[しています.\]DDD モデルで最終的整合性をサポートするために実用的な方法があります。 集計メソッドは、1 つまたは複数の非同期サブスクライバーに配信された時間内にあるドメインのイベントを公開します。

この論理的根拠は、多くの集計またはエンティティにまたがるトランザクションではなく詳細なトランザクションの採用に基づいています。 考え方としては、2 番目のケースでは、データベース ロックの数がかなり大きくなる場合高い拡張性のニーズを持つ大規模なアプリケーションで。 拡張性の高いアプリケーションでは、複数の集計の間のインスタントのトランザクションの一貫性があるない必要があるという事実を採用で最終的整合性の概念を受け入れることができます。 アトミックの変更がビジネスで必要な多くの場合であり、どのような場合に特定の操作にアトミック トランザクションが必要があるかどうかどうかと、ドメインの専門家の責任です。 常に、操作は、複数の集計の間でアトミックのトランザクションを必要とする場合は、集計が大規模なを指定するか、正しく意図していないかどうかを依頼する場合があります。

ただし、他の開発者と Jimmy Bogard のように設計者は、単一のトランザクションにまたがる複数の集計の要件を満たして — のみとその他の集計に関連する同じ元のコマンドの副作用がします。 たとえば、[向上ドメインのイベント パターン](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)Bogard では。

通常、ドメイン、同じ論理トランザクション内では必ずしもドメイン イベントを発生させるの同じスコープ内で発生するイベントの副作用したい\[しています.\]トランザクションをコミットする前にこのハンドラーにイベントをそれぞれをディスパッチします。

右側のドメインのイベントをディスパッチする場合*する前に*元のトランザクションをコミットは、同じトランザクションに含まれるこれらのイベントの副作用をするためです。 たとえば、EF DbContext SaveChanges メソッドが失敗した場合、トランザクションがロールバック関連ドメインのイベント ハンドラーによって実装されているすべての副作用操作の結果を含む、すべての変更。 これは、DbContext ライフ スコープは、既定でとして定義されているため「スコープ設定されます。」 したがって、DbContext オブジェクトは、同じスコープまたはオブジェクト グラフ内でインスタンス化されている複数のリポジトリ オブジェクト間で共有されます。 これにより、Web API または MVC アプリケーションを開発するときに、HttpRequest スコープと一致します。

実際には、(1 つのアトミック トランザクションと最終的整合性) の両方の方法を適切に指定できます。 これは、ドメインまたはビジネス要件と、どのドメインの専門家がわかります本当に依存します。 スケーラブルなどのようにする必要があるにはサービスによっても異なります (より詳細なトランザクションは、データベースのロックに関して以下の影響を与える)。 どの程度投資をしてもよい最終的整合性は、集計およびな補正アクションを実装する必要性の可能性のある不一致が検出するためにより複雑なコードを必要とするために、コードで行ったによって異なります。 元の集計およびその後、イベントがディスパッチされるときに変更をコミットする場合がある問題を考慮し、イベント ハンドラーは、副作用をコミットできません、不一致を集計する必要があります。

な補正アクションを許可する方法は、元のトランザクションの一部ができるように、ドメインのイベントをその他のデータベース テーブルに保存することです。 その後、バッチ処理の不整合を検出して、集計の現在の状態を持つイベントの一覧を比較することによってな補正アクションを実行することができます。 な補正アクションから、側では、ビジネス ユーザー、ドメインの専門家と説明が含まれています。 詳細な分析に必要な複雑なトピックの一部です。

いずれの場合は、必要があるアプローチを選択できます。 初期遅延アプローチしますが、-1 つのトランザクションを使用するように、コミットする前に、イベントを発生させる — EF コアやリレーショナル データベースを使用する最も簡単な方法は、します。 簡単に実装して多くのビジネス ケースでは有効であります。 EShopOnContainers で順序付けマイクロ サービスで使用するアプローチです。

しかし、方法は実際にディスパッチするそれぞれのそれぞれのイベント ハンドラーにこれらのイベントか。 新機能、\_前の例を参照してください媒介オブジェクトしますか? 持つ手法および成果物のイベントとそのイベント ハンドラーの間でマップを使用することができます。

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>ドメインのイベント ディスパッチャー: イベントからイベント ハンドラーへのマッピング

ディスパッチまたはイベントを発行することが、ある種の成果物ごとの関連するハンドラーを取得でき、プロセスの副作用は、そのイベントに基づくように、イベントを発行する必要があります。

1 つの方法は、実際のメッセージング システムであっても、イベント バス、メモリ内のイベントではなく、サービス バスに基づく可能性があります。 ただし、最初のケースでは、実際のメッセージになりますだけ同一プロセス内のこれらのイベントを処理する必要があるために、ドメインのイベントを処理するための過剰 (つまり、同じドメインおよびアプリケーション レイヤー内)。

複数のイベント ハンドラーにイベントをマップする別の方法は、イベントをディスパッチする場所を動的に推論できるように、IoC コンテナー内の型の登録を使用して、です。 つまり、特定のイベントを取得する必要がイベント ハンドラーあるを把握する必要があります。 図 9 ~ 16 を簡略化した方法を示しています。

![](./media/image17.png)

**図 9 ~ 16**です。 IoC を使用してドメイン イベント ディスパッチャー

すべての組み込みおよびを自分でアプローチを実装する成果物をビルドすることができます。 ただし、使用可能なライブラリと同様に使用も[MediatR](https://github.com/jbogard/MediatR)、IoT コンテナー背後を使用します。 したがって直接使用できます、定義済みのインターフェイスと媒介オブジェクトのパブリッシュ/ディスパッチ メソッド。

コードでは、まず、IoC コンテナーで、種類のイベント ハンドラーを登録する次の例で示すように。

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement
        // IAsyncNotificationHandler<>) in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(
            typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
            .GetTypeInfo().Assembly)
            .Where(t => t.IsClosedTypeOf(typeof(IAsyncNotificationHandler<>)))
            .AsImplementedInterfaces();
        // Other registrations ...
    }
}
```

コードは、まずアセンブリを指定します、ハンドラーのいずれかを保持するアセンブリを配置することにより、ドメインのイベント ハンドラーが含まれています (typeof(ValidateOrAddBuyerAggregateWhenXxxx)、ですが、使用することが選択したアセンブリを検索するその他のイベント ハンドラー)。 すべてのイベント ハンドラーは、IAsyncNotificationHandler インターフェイスを実装しては、型次のものだけを検索し、すべてのイベント ハンドラーを登録します。

### <a name="how-to-subscribe-to-domain-events"></a>ドメインのイベントをサブスクライブする方法

MediatR を使用する場合、各イベント ハンドラーでは、次のコードでわかるように IAsyncNotificationHandler インターフェイスのジェネリック パラメーターで提供されているイベントの種類に使用します。

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

イベントと見なすことができます、サブスクリプション、イベント ハンドラー間のリレーションシップに基づく MediatR 成果物は各イベントのすべてのイベント ハンドラーを検出し、これらのイベント ハンドラーの各をトリガーします。

### <a name="how-to-handle-domain-events"></a>ドメインのイベントを処理する方法

最後に、イベント ハンドラーでは、通常インフラストラクチャのリポジトリを使用して、必要なその他の集計を取得し、副作用としてドメイン ロジックを実行するアプリケーション層のコードを実装します。 次のコードは一例を示しています。

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
    : IAsyncNotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;
    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // Parameter validations
        //...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ?
            orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;
        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }
        buyer.VerifyOrAddPaymentMethod(cardTypeId,
            $"Payment Method on {DateTime.UtcNow}",
            orderStartedEvent.CardNumber,
            orderStartedEvent.CardSecurityNumber,
            orderStartedEvent.CardHolderName,
            orderStartedEvent.CardExpiration,
            orderStartedEvent.Order.Id);
        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) :
        _buyerRepository.Add(buyer);
        await _buyerRepository.UnitOfWork.SaveEntitiesAsync();
        // Logging code using buyerUpdated info, etc.
    }
}
```

このイベント ハンドラーのコードがコードと見なされますアプリケーション レイヤー、インフラストラクチャのリポジトリを使用しているためインフラストラクチャ永続性レイヤーで、次のセクションで説明したようです。 イベント ハンドラーは、他のインフラストラクチャ コンポーネントを使用することもできます。

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>ドメインのイベントがマイクロ サービス境界の外部で発行する統合イベントを生成できます。

最後が複数 microservices のイベントに伝達するたい場合がありますは言うまでも重要です。 統合イベントの発生と見なされます、特定のドメインのイベント ハンドラーから、イベント バスを介して発行できました。

## <a name="conclusions-on-domain-events"></a>ドメインのイベントのまとめ 

説明したように、ドメイン内で変更の副作用を明示的に実装するのにドメインのイベントを使用します。 DDD 用語を使用するのには、1 つまたは複数の集計の間での副作用を明示的に実装するのにドメインのイベントを使用します。 さらに、およびスケーラビリティの向上とデータベースのロックの影響を軽減は、同じドメイン内の集計の間で最終的整合性を使用します。

#### <a name="additional-resources"></a>その他の技術情報

-   **Greg Young です。ドメインのイベントとは何ですか。** 
     [ *http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **年 1 月 Stenberg です。ドメインのイベントと最終的整合性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard。優れたドメインのイベント パターン**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon。効果的な集計デザイン パート II: 行う作業を一緒に集計**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_記事/カバー\_2011\_2. pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard。ドメインの強化: ドメイン イベント**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>*

-   **Tony Truong です。ドメインのイベント パターン例**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan です。ドメイン モデルが完全に作成する方法にカプセル化された**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan です。イベントのドメインを 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan です。ドメインのイベントの救済**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **年 1 月 Kronquist です。ドメインのイベントを公開表示しないで、それらが戻ります。** 
     [ *https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesar de la Torre。ドメインのイベントとします。DDD および microservices アーキテクチャに統合イベント**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[前](クライアント-側-validation.md) [次へ] (インフラストラクチャ-永続化のレイヤー-design.md)

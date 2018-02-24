---
title: "サーキット ブレーカー パターンの実装"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | サーキット ブレーカー パターンの実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d7db6899068f84f9165022cfbf17767a75e7db9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a>サーキット ブレーカー パターンの実装

前述のように、リモート サービスやリソースに接続を試行する際に発生し得る、復旧にどのくらい時間がかかるかわからない障害を処理する必要があります。 この種類の障害を処理することにより、アプリケーションの安定性と回復性が向上します。

分散環境において、リモート リソースとサービスの呼び出しは、低速なネットワーク接続やタイムアウト、あるいはリソースが低速であったり、一時的に利用不可能であったりなどの、一時的な障害が原因で失敗することがあります。 このような障害は通常しばらくすると自動的に修正されます。堅牢なクラウド アプリケーションなら再試行パターンなどの方法でそうした障害を処理する備えができているはずです。

ただし、予期しないイベントが原因で、障害の修正に非常に長い時間がかかる状況もあり得ます。 このような障害の重大度は、部分的な接続の損失からサービスの完全な不具合まで多岐にわたります。 このような状況では、アプリケーションが成功の見込みの薄い操作を再試行し続けることは無駄かもしれません。 代わりに、アプリケーションが操作の失敗を受け入れ、失敗を処理するようにコードを書く必要があります。

サーキット ブレーカー パターンの目的は、再試行パターンとは異なります。 再試行パターンでは、操作が最終的には成功するとの見込みをもってアプリケーションに操作を再試行させます。 サーキット ブレーカー パターンは、失敗する可能性の高い操作をアプリケーションが実行しないようにします。 アプリケーションは、サーキット ブレーカーを介して操作を呼び出す再試行パターンを使用すれば、これら 2 つのパターンを結合できます。 しかし、再試行のロジックはサーキット ブレーカーが返す例外に対応できる必要があり、障害が一時的ではないことをサーキット ブレーカーが示す場合、再試行を中止する必要があります。

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>Polly によるサーキット ブレーカー パターンの実装

再試行の実装と同じように、サーキット ブレーカーの推奨されるアプローチは、Polly など実績のある .NET ライブラリを活用することです。

eShopOnContainers アプリケーションは、HTTP 再試行の実装に Polly サーキット ブレーカー ポリシーを使用しています。 実際、このアプリケーションは両方のポリシーを ResilientHttpClient ユーティリティ クラスに適用しています。 HTTP 要求に (eShopOnContainers から) ResilientHttpClient 型のオブジェクトを使用する場合、これら両方のポリシーを適用することになりますが、さらにポリシーを追加することもできます。

HTTP 呼び出しの再試行に使用されるコードに追加する必要があるのは、次のコードの最後の部分で示されているように、使用するポリシーのリストにサーキット ブレーカー ポリシーを加えるコードだけです。

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
            // number of retries
            6,
            // exponential backofff
            retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
            // on retry
            (exception, timeSpan, retryCount, context) =>
            {
                var msg = $"Retry {retryCount} implemented with Polly RetryPolicy " +
                    $"of {context.PolicyKey} " +
                    $"at {context.ExecutionKey}, " +
                    $"due to: {exception}.";
                _logger.LogWarning(msg);
                _logger.LogDebug(msg);
            }),
            Policy.Handle<HttpRequestException>()
                .CircuitBreakerAsync(
                    // number of exceptions before breaking circuit
                    5,
                    // time circuit opened before retry
                    TimeSpan.FromMinutes(1),
                    (exception, duration) =>
                    {
                        // on circuit opened
                        _logger.LogTrace("Circuit breaker opened");
                    },
                    () =>
                    {
                        // on circuit closed
                        _logger.LogTrace("Circuit breaker reset");
                    })
    };
}
```

このコードは、ポリシーを HTTP ラッパーに追加します。 このポリシーは、exceptionsAllowedBeforeBreaking パラメーターで渡される指定された回数 (この例では 5 回) の連続する例外をコードが検出するとオープン状態になるサーキット ブレーカーを定義します。 サーキットがオープン状態の場合、HTTP 要求は機能せず、例外が発生します。

サーキット ブレーカーは、HTTP 呼び出しを実行しているクライアント アプリケーションまたはサービスとは別の環境に展開されている特定のリソースに問題がある場合に、要求をフォールバック インフラストラクチャにリダイレクトするために使用する必要もあります。 こうすれば、バックエンドのマイクロサービスのみに影響を与え、クライアント アプリケーションには影響を与えないデータセンターの停止が生じた場合に、クライアント アプリケーションはフォールバック サービスにリダイレクトできます。 Polly では、この[フェールオーバー ポリシー](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) シナリオを自動化するための新しいポリシーが計画されています。

もちろん、これらすべての機能は、位置を意識することなく Azure に自動的にフェールオーバーを管理させるのとは対照的に、フェールオーバーを .NET コード内から管理する場合のためのものです。

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>eShopOnContainers から ResilientHttpClient ユーティリティ クラスを使用する

ResilientHttpClient ユーティリティ クラスは、.NET HttpClient クラスを使用するのと同じような方法で使用します。 eShopOnContainers MVC Web アプリからの次の例では (OrderController に使用される OrderingService エージェント クラス)、ResilientHttpClient オブジェクトはコンストラクターの httpClient パラメーターにより挿入されます。 その後オブジェクトは HTTP 要求を実行するために使用されます。

```csharp
public class OrderingService : IOrderingService
{
    private IHttpClient _apiClient;
    private readonly string _remoteServiceBaseUrl;
    private readonly IOptionsSnapshot<AppSettings> _settings;
    private readonly IHttpContextAccessor _httpContextAccesor;

    public OrderingService(IOptionsSnapshot<AppSettings> settings,
        IHttpContextAccessor httpContextAccesor,
        IHttpClient httpClient)
    {
        _remoteServiceBaseUrl = $"{settings.Value.OrderingUrl}/api/v1/orders";
        _settings = settings;
        _httpContextAccesor = httpContextAccesor;
        _apiClient = httpClient;
    }

    async public Task<List<Order>> GetMyOrders(ApplicationUser user)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        var ordersUrl = _remoteServiceBaseUrl;
        var dataString = await _apiClient.GetStringAsync(ordersUrl);
        var response = JsonConvert.DeserializeObject<List<Order>>(dataString);
        return response;
    }

    // Other methods ...
    async public Task CreateOrder(Order order)
    {
        var context = _httpContextAccesor.HttpContext;
        var token = await context.Authentication.GetTokenAsync("access_token");
        _apiClient.Inst.DefaultRequestHeaders.Authorization = new
            System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", token);
        _apiClient.Inst.DefaultRequestHeaders.Add("x-requestid",
            order.RequestId.ToString());
        var ordersUrl = $"{_remoteServiceBaseUrl}/new";
        order.CardTypeId = 1;
        order.CardExpirationApiFormat();
        SetFakeIdToProducts(order);
        var response = await _apiClient.PostAsync(ordersUrl, order);
        response.EnsureSuccessStatusCode();
    }
}
```

\_apiClient メンバー オブジェクトが使用される場合はいつでも、このオブジェクトは内部的にラッパー クラスを Polly ポリシーと共に使用します。このポリシーには、再試行ポリシー、サーキット ブレーカー ポリシーと、Polly ポリシー コレクションからの適用したい任意の他のポリシーが含まれます。

## <a name="testing-retries-in-eshoponcontainers"></a>eShopOnContainers で再試行をテストする

Docker ホスト内で eShopOnContainers ソリューションを起動する場合、このソリューションは複数のコンテナーを起動する必要があります。 SQL Server コンテナーなど、一部のコンテナーは起動と初期化が低速です。 eShopOnContainers アプリケーションを Docker に初めて展開する場合は、イメージとデータベースを設定する必要があるため、特にそうです。 一部のコンテナーは他のコンテナーより起動が低速だという事実により、以前のセクションで説明したように docker-compose レベルでコンテナー間の依存関係を設定している場合であっても、残りのサービスによる初期化時の HTTP 例外のスローが引き起こされる可能性があります。 コンテナー間の docker-compose 依存関係は、プロセス レベルだけのものです。 コンテナーのエントリ ポイント プロセスは起動されても、SQL Server はクエリに対して準備ができていないことがあります。 結果としてエラーの連鎖が生じ、アプリケーションがその特定のコンテナーを利用しようとするときに例外が発生することがあります。

また、起動時のこのタイプのエラーは、アプリケーションをクラウドに展開する際に生じることもあります。 その場合、オーケストレーターは、クラスターのノード全体でコンテナーの数を分散させる際に、コンテナーを 1 つのノードまたは VM から別の場所に移動することがあります (つまり、新しいインスタンスを起動する)。

eShopOnContainers は、すでに説明した再試行パターンを使用してこの問題を解決します。 これは、ソリューションを起動した際に次のようなログ トレースや警告が発生する理由でもあります。

> "**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request. ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>eShopOnContainers でサーキット ブレーカーをテストする

サーキットをオープン状態にして eShopOnContainers でテストするには、いくつかの方法があります。

1 つの方法は、サーキット ブレーカー ポリシーで許可する再試行の数を 1 まで減らし、ソリューション全体を Docker に再展開することです。 再試行を 1 回にすることで、展開中に HTTP 要求が失敗し、サーキット ブレーカーがオープン状態になって、エラーが発生する可能性が高くなります。

もう 1 つの方法は、`Basket` マイクロサービスで実装されているカスタムのミドルウェアを使用することです。 このミドルウェアが有効な場合、すべての HTTP 要求を捕捉し、状態コード 500 を返します。 次のように、"failing" URI に GET 要求を実行してミドルウェアを有効にできます。

-   GET /failing

この要求は、ミドルウェアの現在の状態を返します。 ミドルウェアが有効な場合、要求は状態コード 500 を返します。 ミドルウェアが無効の場合、応答はありません。

-   GET /failing?enable

この要求はミドルウェアを有効にします。

-   GET /failing?disable

この要求はミドルウェアを無効にします。

たとえば、アプリケーションが実行されたら、任意のブラウザーで次の URI を使用して要求を実行することにより、ミドルウェアを有効にできます。 注文マイクロサービスにはポート 5103 を使用することにご注意ください。

http://localhost:5103/failing?enable

その後、図 10-4 に示されているように、URI [http://localhost:5103/failing](http://localhost:5103/failing) を使用して状態を確認できます。

![](./media/image4.png)

**図 10-4**. "failing" ASP.NET ミドルウェアの状態を確認している。この場合は無効。 

この時点で Basket マイクロサービスは、呼び出すたびに状態コード 500 を返します。

ミドルウェアを実行したら、MVC Web アプリから注文してみることができます。 要求は失敗するため、サーキットがオープン状態になります。

次の例では、MVC Web アプリが、注文のためのロジック内に catch ブロックを含んでいることがわかります。 コードがサーキット オープンの例外を捕捉すると、ユーザーに待機を促すメッセージを表示します。

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            //… Other code
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode                 
            HandleBrokenCircuitException();
        }
        return View();
    }       

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

まとめます。 再試行ポリシーは、HTTP 要求の実行を数回試行し、HTTP エラーが発生します。 試行回数がサーキット ブレーカー ポリシーに設定された最大回数に達すると (この場合は 5 回)、アプリケーションは BrokenCircuitException をスローします。 結果として、図 10-5 に示されているようなメッセージが表示されます。

![](./media/image5.png)

**図 10-5**. サーキット ブレーカーが UI にエラーを返している

サーキットをいつオープン状態にするかに関して、別のロジックを実装することもできます。 または、フォールバック データセンターか冗長バックエンド システムがある場合、他のバックエンド マイクロサービスに対して HTTP 要求を試行することができます。

最後に、CircuitBreakerPolicy の別の可能性として、Isolate (サーキットを強制的にオープン状態にし、オープン状態を維持する) と Reset (もう一度クローズド状態にする) を使用する方法があります。 これらは、ポリシーに対して Isolate と Reset を直接呼び出すユーティリティ HTTP エンドポイントを構築するために使用できます。 このような HTTP エンドポイントは、アップグレードしたい場合など、ダウンストリーム システムを一時的に分離するために運用環境で適切な安全性を保つために使用することもできます。 または、障害が発生する恐れがあるダウンストリーム システムを保護するために手動でサーキットを切断することもできます。

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>再試行ポリシーにジッタ方式を追加する

通常の再試行ポリシーは、同時実行性やスケーラビリティが高い場合や、高競合状態下でシステムに影響を及ぼすことがあります。 部分的な停止の場合に多くのクライアントから来る同様の再試行のピークを乗り越えるための賢い回避策は、ジッタ方式を再試行アルゴリズムまたはポリシーに追加することです。 これにより、急増するバックオフにランダム性を加えることで、エンドツーエンド システム全体のパフォーマンスを向上できます。 こうすれば、問題が発生した際のスパイクを分散できます。 Polly を使用する場合、ジッタを実装するコードは次の例のようになります。

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a>その他の技術情報

-   **再試行パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)

-   **接続の回復** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Polly** (.NET の復元および一時的な障害処理ライブラリ) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **サーキット ブレーカー パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker.ジッタ: ランダム性を使って状況を改善する** https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[前へ] (implement-http-call-retries-exponential-backoff-polly.md) [次へ] (monitor-app-health.md)

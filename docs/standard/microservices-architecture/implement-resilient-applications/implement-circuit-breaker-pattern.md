---
title: "遮断器パターンを実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |遮断器パターンを実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2a629e25a7565aaba156f68cf06d9a24b6c2b8b0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-circuit-breaker-pattern"></a>遮断器パターンを実装します。

前述のように、変数から、リモート サービスまたはリソースに接続しようとしたときに発生する可能性がありますとを回復する時間がかかる可能性がありますエラーを処理する必要があります。 この種類のエラーの処理では、安定性とアプリケーションの回復性を向上できます。

分散環境でリモート リソースとサービスを呼び出すことができます低速ネットワーク接続のタイムアウト、およびなどの一時的なエラーによって失敗するまたはリソースがされている場合速度の遅いが一時的にご利用いただけません。 このようなエラー通常修正自体短期間のうち、しに処理する再試行パターンのような方法を使用した、堅牢なクラウド アプリケーションを準備する必要があります。

ただしはもありますエラーを修正するかなり長くかかる可能性がありますの予期しない出来事によりがという状況です。 このようなエラーは、サービスの完全な障害に接続の部分的な損失からの重大度の範囲です。 これらの状況では、継続的に成功する可能性がある操作を再試行するアプリケーションの無意味な場合があります。 代わりに、操作が失敗したことに同意し、それに応じてエラーを処理するアプリケーションをコーディングする必要があります。

遮断器のパターンは、再試行パターンは、異なる目的がします。 再試行パターンにより、アプリケーションを操作が成功最終的にする期待の操作を再試行してください。 遮断器パターンにより、アプリケーションが失敗する可能性がある操作を実行します。 アプリケーションでは、遮断器で操作を再試行パターンを使用して、これら 2 つのパターンを組み合わせることができます。 ただし、再試行ロジックは、遮断器によって返されるすべての例外を区別する必要があります、遮断器は、エラーが一時的なものではないことを示している場合の再試行回数を破棄にする必要があります。

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a>ポリーを遮断器のパターンを実装します。

再試行を実装する場合としては、ポリーのような実証済みの .NET ライブラリを活用するためにサーキット ブレーカーの方法をお勧めします。

EShopOnContainers アプリケーションは、HTTP 再試行を実装する場合に、ポリー遮断器のポリシーを使用します。 実際には、アプリケーションでは、両方のポリシーが ResilientHttpClient ユーティリティ クラスに適用されます。 (EShopOnContainers) からの HTTP 要求 ResilientHttpClient の型のオブジェクトを使用すると、これら両方のポリシーを適用するけれども、すぎる追加のポリシーを追加することが

唯一の追加は、ここの HTTP 呼び出しの再試行に使用するコードを使用するにはポリシーの一覧に遮断器のポリシーを追加する場所、次のコードの最後に示すようにコードに示します。

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

コードは、HTTP ラッパーにポリシーを追加します。 ポリシーとしてコードが指定された数の連続する例外 (行での例外) を検出したときに表示される、遮断器を定義することは、exceptionsAllowedBeforeBreaking パラメーター (この場合の 5) に渡されます。 回路が開いているときは、HTTP 要求が機能しないが、例外が発生します。

サーキット ブレーカーは、クライアントのアプリケーションよりも、別の環境にデプロイされている特定のリソースまたは HTTP 呼び出しを実行しているサービスに問題がある場合、フォールバック インフラストラクチャに要求をリダイレクトするためも使用してください。 このように、バックエンド microservices のみがクライアント アプリケーション、影響を及ぼすデータ センターで障害があるクライアント アプリケーションが代替のサービスにリダイレクトできます。 これを自動化する新しいポリシーを計画しているポリー[フェールオーバー ポリシー](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)シナリオです。

もちろん、これらすべての機能は、によって自動的に管理するため、Azure の場所の透過性がなく、.NET コード内でのフェールオーバーを管理している場合です。

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a>EShopOnContainers から ResilientHttpClient ユーティリティ クラスを使用します。

.NET HttpClient クラスを使用する方法と同様の方法で ResilientHttpClient ユーティリティ クラスを使用するとします。 EShopOnContainers MVC web アプリケーション (、OrderingService エージェントによって使用されるクラス OrderController) から次の例で、コンス トラクターの httpClient パラメーターを通じて ResilientHttpClient オブジェクトが挿入されます。 HTTP 要求を実行するオブジェクトを使用しています。

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

ときに、 \_apiClient メンバー オブジェクトを使用して、内部的にポリー policiesؙ のラッパー クラスを使用: 再試行ポリシー、遮断器ポリシーおよびポリー ポリシーのコレクションから適用するその他のポリシー。

## <a name="testing-retries-in-eshoponcontainers"></a>EShopOnContainers での再試行回数のテスト

Docker ホストに eShopOnContainers ソリューションを起動するたびに複数のコンテナーを開始する必要があります。 コンテナーの一部を起動し、SQL Server のコンテナーと同様に、初期化に時間がかかります。 これは特に、Docker に eShopOnContainers アプリケーションを配置するときに最初のイメージと、データベースを設定する必要があるためです。 コンテナーをいくつかの開始よりも他のユーザーが最初に HTTP 例外をスローするサービスの残りの部分でコンテナー間の依存関係を設定した場合でも、時間がかかること、docker の構成レベルでは、前のセクションで説明したようです。 Docker の構成コンテナー間の依存関係は、プロセス レベルでのみです。 コンテナーのエントリ ポイント プロセスが開始される場合が、SQL Server がクエリの準備ができていない場合があります。 結果は、連鎖的に、エラー、その特定のコンテナーを使用しようとするときに、アプリケーションが例外を取得できます。

この種類のエラーの起動時にアプリケーションがクラウドに展開する場合。 その場合は、orchestrators 可能性があるコンテナーから 1 つのノードまたは VM へ移動 (つまり、新しいインスタンスを開始) 別、クラスターのノード間でコンテナーの数のバランスをとる場合。

この問題は解決 eShopOnContainers 方法は、上記で説明したお再試行パターンを使用してです。 なぜ、ソリューションを開始するときに発生する可能性ログ トレースまたは次のような警告がまたです。

> "**ポリーの RetryPolicy で実装される再試行 1**、原因: System.Net.Http.HttpRequestException: 要求の送信中にエラーが発生しました。 ---&gt;System.Net.Http.CurlException: がサーバーに接続できませんでした\\System.Net.Http.CurlHandler.ThrowIfCURLEError (CURLcode エラー) にある n\\に n\[しています.\].

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a>EShopOnContainers で遮断器のテスト

回線を開いて eShopOnContainers 併用をテストして、いくつかの方法があります。

1 つのオプションには、1、遮断器ポリシーに再試行の最大数を削減し、Docker にソリューション全体を再展開します。 1 回の再試行は配置時に HTTP 要求に失敗する可能性が高く、遮断器が開き、およびエラーが発生しました。

順序付けのマイクロ サービスで実装されているカスタムのミドルウェアを使用することもできます。 このミドルウェアを有効にすると、すべての HTTP 要求をキャッチし、ステータス コード 500 を返します。 GET 要求を失敗にすることにより、ミドルウェアを有効にすることができます、次のように、URI:

-   取得/失敗

この要求では、ミドルウェアの現在の状態を返します。 ミドルウェアが有効になっている場合、要求はステータス コード 500 を返します。 ミドルウェアが無効になっている場合、応答がありません。

-   取得/失敗しているかを有効にします。

この要求は、ミドルウェアを使用できます。

-   取得/失敗しているか無効にします。

この要求には、ミドルウェアが無効にします。

たとえば、アプリケーションが実行されている任意のブラウザーで次の URI を使用して、要求をすることで、ミドルウェアを有効にできます。 順序付けのマイクロ サービスはポート 5102 を使用することに注意してください。

http://localhost:5102 失敗/? を有効にします。

URI を使用して状態を確認することができますし、 [http://localhost:5102 失敗/](http://localhost:5100/failing)図 10-4 に示すように、します。

![](./media/image4.png)

**図 10-4**です。 ASP.NET のミドルウェアの障害をシミュレートします。

この時点で、順序付けマイクロ サービスが応答状態コード 500 を呼び出すたびにでは呼び出すことです。

ミドルウェアが実行されていると、MVC web アプリケーションから注文を作成しようとすることができます。 要求が失敗したため、回線が開きます。

次の例では、MVC web アプリケーションが catch を持つことを確認できますで注文を発行するためのロジックをブロックします。 コードでは、開いている回線例外をキャッチ、表示、ユーザーが手短にわかりやすいメッセージが待機されます。

```csharp
[HttpPost]
public async Task<IActionResult> Create(Order model, string action)
{
    try
    {
        if (ModelState.IsValid)
        {
            var user = _appUserParser.Parse(HttpContext.User);
            await _orderSvc.CreateOrder(model);
            //Redirect to historic list.
            return RedirectToAction("Index");
        }
    }
    catch(BrokenCircuitException ex)
    {
        ModelState.AddModelError("Error",
            "It was not possible to create a new order, please try later on");
    }
    return View(model);
}
```

次に概要を示します。 再試行ポリシーでは、何回かに、HTTP 要求および HTTP エラーを取得しようとします。 試行回数には、(ここでは、5)、遮断器ポリシーの最大数のセットに達すると、アプリケーションは、BrokenCircuitException をスローします。 図 10-5 に示すように、わかりやすいメッセージになります。

![](./media/image5.png)

**図 10-5**です。 遮断器が UI にエラーを返す

回線を開くときに別のロジックを実装することができます。 または、代替データ センターまたは冗長のバックエンド システムがある場合、異なるバックエンド マイクロ サービスに対する HTTP 要求を試みることができます。

最後に、他の方法として、CircuitBreakerPolicy は (を強制的に開いていると、開いている回路を保持して) 分離と (をもう一度閉じる) のリセットを使用します。 これらは、ポリシーを特定し、直接のリセットを起動するユーティリティ HTTP エンドポイントの作成に使用する可能性があります。 このような HTTP エンドポイントも使用できます、一時的にアップグレードする場合などの下流システムを分離するためには、実稼働環境で、適切に保護します。 または、エラーが発生すると思われる下流システムを保護するために手動で回線を作動する可能性があります。

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a>再試行ポリシーにジッター戦略を追加します。

正規の再試行ポリシーとの競合 高い同時実行性とスケーラビリティの場合、システムに影響を与えることができます。 部分的な障害が発生した場合、多くのクライアントからのものと同様の再試行のピークをなくすためは、適切な回避策は、再試行アルゴリズム/ポリシー ジッター戦略を追加します。 これにより、指数バックオフに乱数を追加することで、エンド ツー エンド システムの全体的なパフォーマンスが向上ことができます。 これによって、問題が発生したときに、急増によってが分散されます。 ポリーを使用すると、ジッターを実装するコードは次の例のようになります。

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

-   **接続の回復**(Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **ポリー** (.NET からの復元力と一時的なエラー処理ライブラリ) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)

-   **遮断器パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

-   **Marc Brooker です。ジッター: を行うものよりランダム**https://brooker.co.za/blog/2015/03/21/backoff.html


>[!div class="step-by-step"]
[前](implement-http-call-retries-exponential-backoff-polly.md) [次へ] (モニター-アプリ-health.md)

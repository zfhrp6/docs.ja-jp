---
title: サーキット ブレーカー パターンの実装
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | サーキット ブレーカー パターンの実装'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/12/2017
ms.openlocfilehash: 2c89992c4c60ca7f1085050e6fed4922ecd4d8cc
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106131"
---
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="f0267-103">サーキット ブレーカー パターンの実装</span><span class="sxs-lookup"><span data-stu-id="f0267-103">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="f0267-104">前述のように、リモート サービスやリソースに接続を試行する際に発生し得る、復旧にどのくらい時間がかかるかわからない障害を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-104">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="f0267-105">この種類の障害を処理することにより、アプリケーションの安定性と回復性が向上します。</span><span class="sxs-lookup"><span data-stu-id="f0267-105">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="f0267-106">分散環境において、リモート リソースとサービスの呼び出しは、低速なネットワーク接続やタイムアウト、あるいはリソースが低速であったり、一時的に利用不可能であったりなどの、一時的な障害が原因で失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-106">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="f0267-107">このような障害は通常しばらくすると自動的に修正されます。堅牢なクラウド アプリケーションなら再試行パターンなどの方法でそうした障害を処理する備えができているはずです。</span><span class="sxs-lookup"><span data-stu-id="f0267-107">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="f0267-108">ただし、予期しないイベントが原因で、障害の修正に非常に長い時間がかかる状況もあり得ます。</span><span class="sxs-lookup"><span data-stu-id="f0267-108">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="f0267-109">このような障害の重大度は、部分的な接続の損失からサービスの完全な不具合まで多岐にわたります。</span><span class="sxs-lookup"><span data-stu-id="f0267-109">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="f0267-110">このような状況では、アプリケーションが成功の見込みの薄い操作を再試行し続けることは無駄かもしれません。</span><span class="sxs-lookup"><span data-stu-id="f0267-110">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="f0267-111">代わりに、アプリケーションが操作の失敗を受け入れ、失敗を処理するようにコードを書く必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-111">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="f0267-112">サーキット ブレーカー パターンの目的は、再試行パターンとは異なります。</span><span class="sxs-lookup"><span data-stu-id="f0267-112">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="f0267-113">再試行パターンでは、操作が最終的には成功するとの見込みをもってアプリケーションに操作を再試行させます。</span><span class="sxs-lookup"><span data-stu-id="f0267-113">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="f0267-114">サーキット ブレーカー パターンは、失敗する可能性の高い操作をアプリケーションが実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="f0267-114">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="f0267-115">アプリケーションは、サーキット ブレーカーを介して操作を呼び出す再試行パターンを使用すれば、これら 2 つのパターンを結合できます。</span><span class="sxs-lookup"><span data-stu-id="f0267-115">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="f0267-116">しかし、再試行のロジックはサーキット ブレーカーが返す例外に対応できる必要があり、障害が一時的ではないことをサーキット ブレーカーが示す場合、再試行を中止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-116">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="f0267-117">Polly によるサーキット ブレーカー パターンの実装</span><span class="sxs-lookup"><span data-stu-id="f0267-117">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="f0267-118">再試行の実装と同じように、サーキット ブレーカーの推奨されるアプローチは、Polly など実績のある .NET ライブラリを活用することです。</span><span class="sxs-lookup"><span data-stu-id="f0267-118">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="f0267-119">eShopOnContainers アプリケーションは、HTTP 再試行の実装に Polly サーキット ブレーカー ポリシーを使用しています。</span><span class="sxs-lookup"><span data-stu-id="f0267-119">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="f0267-120">実際、このアプリケーションは両方のポリシーを ResilientHttpClient ユーティリティ クラスに適用しています。</span><span class="sxs-lookup"><span data-stu-id="f0267-120">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="f0267-121">HTTP 要求に (eShopOnContainers から) ResilientHttpClient 型のオブジェクトを使用する場合、これら両方のポリシーを適用することになりますが、さらにポリシーを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-121">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="f0267-122">HTTP 呼び出しの再試行に使用されるコードに追加する必要があるのは、次のコードの最後の部分で示されているように、使用するポリシーのリストにサーキット ブレーカー ポリシーを加えるコードだけです。</span><span class="sxs-lookup"><span data-stu-id="f0267-122">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

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

<span data-ttu-id="f0267-123">このコードは、ポリシーを HTTP ラッパーに追加します。</span><span class="sxs-lookup"><span data-stu-id="f0267-123">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="f0267-124">このポリシーは、exceptionsAllowedBeforeBreaking パラメーターで渡される指定された回数 (この例では 5 回) の連続する例外をコードが検出するとオープン状態になるサーキット ブレーカーを定義します。</span><span class="sxs-lookup"><span data-stu-id="f0267-124">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="f0267-125">サーキットがオープン状態の場合、HTTP 要求は機能せず、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="f0267-125">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="f0267-126">サーキット ブレーカーは、HTTP 呼び出しを実行しているクライアント アプリケーションまたはサービスとは別の環境に展開されている特定のリソースに問題がある場合に、要求をフォールバック インフラストラクチャにリダイレクトするために使用する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-126">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="f0267-127">こうすれば、バックエンドのマイクロサービスのみに影響を与え、クライアント アプリケーションには影響を与えないデータセンターの停止が生じた場合に、クライアント アプリケーションはフォールバック サービスにリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-127">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="f0267-128">Polly では、この[フェールオーバー ポリシー](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) シナリオを自動化するための新しいポリシーが計画されています。</span><span class="sxs-lookup"><span data-stu-id="f0267-128">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="f0267-129">もちろん、これらすべての機能は、位置を意識することなく Azure に自動的にフェールオーバーを管理させるのとは対照的に、フェールオーバーを .NET コード内から管理する場合のためのものです。</span><span class="sxs-lookup"><span data-stu-id="f0267-129">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="f0267-130">eShopOnContainers から ResilientHttpClient ユーティリティ クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="f0267-130">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="f0267-131">ResilientHttpClient ユーティリティ クラスは、.NET HttpClient クラスを使用するのと同じような方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="f0267-131">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="f0267-132">eShopOnContainers MVC Web アプリからの次の例では (OrderController に使用される OrderingService エージェント クラス)、ResilientHttpClient オブジェクトはコンストラクターの httpClient パラメーターにより挿入されます。</span><span class="sxs-lookup"><span data-stu-id="f0267-132">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="f0267-133">その後オブジェクトは HTTP 要求を実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0267-133">Then the object is used to perform HTTP requests.</span></span>

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

<span data-ttu-id="f0267-134">\_apiClient メンバー オブジェクトが使用される場合はいつでも、このオブジェクトは内部的にラッパー クラスを Polly ポリシーと共に使用します。このポリシーには、再試行ポリシー、サーキット ブレーカー ポリシーと、Polly ポリシー コレクションからの適用したい任意の他のポリシーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0267-134">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="f0267-135">eShopOnContainers で再試行をテストする</span><span class="sxs-lookup"><span data-stu-id="f0267-135">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="f0267-136">Docker ホスト内で eShopOnContainers ソリューションを起動する場合、このソリューションは複数のコンテナーを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-136">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="f0267-137">SQL Server コンテナーなど、一部のコンテナーは起動と初期化が低速です。</span><span class="sxs-lookup"><span data-stu-id="f0267-137">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="f0267-138">eShopOnContainers アプリケーションを Docker に初めて展開する場合は、イメージとデータベースを設定する必要があるため、特にそうです。</span><span class="sxs-lookup"><span data-stu-id="f0267-138">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="f0267-139">一部のコンテナーは他のコンテナーより起動が低速だという事実により、以前のセクションで説明したように docker-compose レベルでコンテナー間の依存関係を設定している場合であっても、残りのサービスによる初期化時の HTTP 例外のスローが引き起こされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-139">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="f0267-140">コンテナー間の docker-compose 依存関係は、プロセス レベルだけのものです。</span><span class="sxs-lookup"><span data-stu-id="f0267-140">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="f0267-141">コンテナーのエントリ ポイント プロセスは起動されても、SQL Server はクエリに対して準備ができていないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-141">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="f0267-142">結果としてエラーの連鎖が生じ、アプリケーションがその特定のコンテナーを利用しようとするときに例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-142">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="f0267-143">また、起動時のこのタイプのエラーは、アプリケーションをクラウドに展開する際に生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-143">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="f0267-144">その場合、オーケストレーターは、クラスターのノード全体でコンテナーの数を分散させる際に、コンテナーを 1 つのノードまたは VM から別の場所に移動することがあります (つまり、新しいインスタンスを起動する)。</span><span class="sxs-lookup"><span data-stu-id="f0267-144">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="f0267-145">eShopOnContainers は、すでに説明した再試行パターンを使用してこの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="f0267-145">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="f0267-146">これは、ソリューションを起動した際に次のようなログ トレースや警告が発生する理由でもあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-146">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="f0267-147">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span><span class="sxs-lookup"><span data-stu-id="f0267-147">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="f0267-148"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span><span class="sxs-lookup"><span data-stu-id="f0267-148"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="f0267-149">eShopOnContainers でサーキット ブレーカーをテストする</span><span class="sxs-lookup"><span data-stu-id="f0267-149">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="f0267-150">サーキットをオープン状態にして eShopOnContainers でテストするには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-150">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="f0267-151">1 つの方法は、サーキット ブレーカー ポリシーで許可する再試行の数を 1 まで減らし、ソリューション全体を Docker に再展開することです。</span><span class="sxs-lookup"><span data-stu-id="f0267-151">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="f0267-152">再試行を 1 回にすることで、展開中に HTTP 要求が失敗し、サーキット ブレーカーがオープン状態になって、エラーが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="f0267-152">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="f0267-153">もう 1 つの方法は、`Basket` マイクロサービスで実装されているカスタムのミドルウェアを使用することです。</span><span class="sxs-lookup"><span data-stu-id="f0267-153">Another option is to use custom middleware that is implemented in the `Basket` microservice.</span></span> <span data-ttu-id="f0267-154">このミドルウェアが有効な場合、すべての HTTP 要求を捕捉し、状態コード 500 を返します。</span><span class="sxs-lookup"><span data-stu-id="f0267-154">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="f0267-155">次のように、"failing" URI に GET 要求を実行してミドルウェアを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-155">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="f0267-156">GET /failing</span><span class="sxs-lookup"><span data-stu-id="f0267-156">GET /failing</span></span>

<span data-ttu-id="f0267-157">この要求は、ミドルウェアの現在の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="f0267-157">This request returns the current state of the middleware.</span></span> <span data-ttu-id="f0267-158">ミドルウェアが有効な場合、要求は状態コード 500 を返します。</span><span class="sxs-lookup"><span data-stu-id="f0267-158">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="f0267-159">ミドルウェアが無効の場合、応答はありません。</span><span class="sxs-lookup"><span data-stu-id="f0267-159">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="f0267-160">GET /failing?enable</span><span class="sxs-lookup"><span data-stu-id="f0267-160">GET /failing?enable</span></span>

<span data-ttu-id="f0267-161">この要求はミドルウェアを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f0267-161">This request enables the middleware.</span></span>

-   <span data-ttu-id="f0267-162">GET /failing?disable</span><span class="sxs-lookup"><span data-stu-id="f0267-162">GET /failing?disable</span></span>

<span data-ttu-id="f0267-163">この要求はミドルウェアを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f0267-163">This request disables the middleware.</span></span>

<span data-ttu-id="f0267-164">たとえば、アプリケーションが実行されたら、任意のブラウザーで次の URI を使用して要求を実行することにより、ミドルウェアを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-164">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="f0267-165">注文マイクロサービスにはポート 5103 を使用することにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="f0267-165">Note that the ordering microservice uses port 5103.</span></span>

http://localhost:5103/failing?enable

<span data-ttu-id="f0267-166">その後、図 10-4 に示されているように、URI [http://localhost:5103/failing](http://localhost:5103/failing) を使用して状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="f0267-166">You can then check the status using the URI [http://localhost:5103/failing](http://localhost:5103/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="f0267-167">**図 10-4**.</span><span class="sxs-lookup"><span data-stu-id="f0267-167">**Figure 10-4**.</span></span> <span data-ttu-id="f0267-168">"failing" ASP.NET ミドルウェアの状態を確認している。この場合は無効。</span><span class="sxs-lookup"><span data-stu-id="f0267-168">Checking the state of the “Failing” ASP.NET middleware – In this case, disabled.</span></span> 

<span data-ttu-id="f0267-169">この時点で Basket マイクロサービスは、呼び出すたびに状態コード 500 を返します。</span><span class="sxs-lookup"><span data-stu-id="f0267-169">At this point, the Basket microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="f0267-170">ミドルウェアを実行したら、MVC Web アプリから注文してみることができます。</span><span class="sxs-lookup"><span data-stu-id="f0267-170">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="f0267-171">要求は失敗するため、サーキットがオープン状態になります。</span><span class="sxs-lookup"><span data-stu-id="f0267-171">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="f0267-172">次の例では、MVC Web アプリが、注文のためのロジック内に catch ブロックを含んでいることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f0267-172">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="f0267-173">コードがサーキット オープンの例外を捕捉すると、ユーザーに待機を促すメッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="f0267-173">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="f0267-174">まとめます。</span><span class="sxs-lookup"><span data-stu-id="f0267-174">Here’s a summary.</span></span> <span data-ttu-id="f0267-175">再試行ポリシーは、HTTP 要求の実行を数回試行し、HTTP エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f0267-175">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="f0267-176">試行回数がサーキット ブレーカー ポリシーに設定された最大回数に達すると (この場合は 5 回)、アプリケーションは BrokenCircuitException をスローします。</span><span class="sxs-lookup"><span data-stu-id="f0267-176">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="f0267-177">結果として、図 10-5 に示されているようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0267-177">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="f0267-178">**図 10-5**.</span><span class="sxs-lookup"><span data-stu-id="f0267-178">**Figure 10-5**.</span></span> <span data-ttu-id="f0267-179">サーキット ブレーカーが UI にエラーを返している</span><span class="sxs-lookup"><span data-stu-id="f0267-179">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="f0267-180">サーキットをいつオープン状態にするかに関して、別のロジックを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-180">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="f0267-181">または、フォールバック データセンターか冗長バックエンド システムがある場合、他のバックエンド マイクロサービスに対して HTTP 要求を試行することができます。</span><span class="sxs-lookup"><span data-stu-id="f0267-181">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="f0267-182">最後に、CircuitBreakerPolicy の別の可能性として、Isolate (サーキットを強制的にオープン状態にし、オープン状態を維持する) と Reset (もう一度クローズド状態にする) を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="f0267-182">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="f0267-183">これらは、ポリシーに対して Isolate と Reset を直接呼び出すユーティリティ HTTP エンドポイントを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0267-183">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="f0267-184">このような HTTP エンドポイントは、アップグレードしたい場合など、ダウンストリーム システムを一時的に分離するために運用環境で適切な安全性を保つために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-184">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="f0267-185">または、障害が発生する恐れがあるダウンストリーム システムを保護するために手動でサーキットを切断することもできます。</span><span class="sxs-lookup"><span data-stu-id="f0267-185">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="f0267-186">再試行ポリシーにジッタ方式を追加する</span><span class="sxs-lookup"><span data-stu-id="f0267-186">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="f0267-187">通常の再試行ポリシーは、同時実行性やスケーラビリティが高い場合や、高競合状態下でシステムに影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="f0267-187">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="f0267-188">部分的な停止の場合に多くのクライアントから来る同様の再試行のピークを乗り越えるための賢い回避策は、ジッタ方式を再試行アルゴリズムまたはポリシーに追加することです。</span><span class="sxs-lookup"><span data-stu-id="f0267-188">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="f0267-189">これにより、急増するバックオフにランダム性を加えることで、エンドツーエンド システム全体のパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="f0267-189">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="f0267-190">こうすれば、問題が発生した際のスパイクを分散できます。</span><span class="sxs-lookup"><span data-stu-id="f0267-190">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="f0267-191">Polly を使用する場合、ジッタを実装するコードは次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="f0267-191">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="f0267-192">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="f0267-192">Additional resources</span></span>

-   <span data-ttu-id="f0267-193">**再試行パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="f0267-193">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="f0267-194">**接続の回復性** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="f0267-194">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="f0267-195">**Polly** (.NET の復元および一時的な障害処理ライブラリ) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="f0267-195">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="f0267-196">**サーキット ブレーカー パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="f0267-196">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="f0267-197">**Marc Brooker.ジッタ: ランダム性を使って状況を改善する** https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="f0267-197">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f0267-198">[前へ](implement-http-call-retries-exponential-backoff-polly.md)
[次へ](monitor-app-health.md)</span><span class="sxs-lookup"><span data-stu-id="f0267-198">[Previous](implement-http-call-retries-exponential-backoff-polly.md)
[Next](monitor-app-health.md)</span></span>

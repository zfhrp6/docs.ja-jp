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
# <a name="implementing-the-circuit-breaker-pattern"></a><span data-ttu-id="dd797-104">遮断器パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="dd797-104">Implementing the Circuit Breaker pattern</span></span>

<span data-ttu-id="dd797-105">前述のように、変数から、リモート サービスまたはリソースに接続しようとしたときに発生する可能性がありますとを回復する時間がかかる可能性がありますエラーを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-105">As noted earlier, you should handle faults that might take a variable amount of time to recover from, as might happen when you try to connect to a remote service or resource.</span></span> <span data-ttu-id="dd797-106">この種類のエラーの処理では、安定性とアプリケーションの回復性を向上できます。</span><span class="sxs-lookup"><span data-stu-id="dd797-106">Handling this type of fault can improve the stability and resiliency of an application.</span></span>

<span data-ttu-id="dd797-107">分散環境でリモート リソースとサービスを呼び出すことができます低速ネットワーク接続のタイムアウト、およびなどの一時的なエラーによって失敗するまたはリソースがされている場合速度の遅いが一時的にご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="dd797-107">In a distributed environment, calls to remote resources and services can fail due to transient faults, such as slow network connections and timeouts, or if resources are being slow or are temporarily unavailable.</span></span> <span data-ttu-id="dd797-108">このようなエラー通常修正自体短期間のうち、しに処理する再試行パターンのような方法を使用した、堅牢なクラウド アプリケーションを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-108">These faults typically correct themselves after a short time, and a robust cloud application should be prepared to handle them by using a strategy like the Retry pattern.</span></span>

<span data-ttu-id="dd797-109">ただしはもありますエラーを修正するかなり長くかかる可能性がありますの予期しない出来事によりがという状況です。</span><span class="sxs-lookup"><span data-stu-id="dd797-109">However, there can also be situations where faults are due to unanticipated events that might take much longer to fix.</span></span> <span data-ttu-id="dd797-110">このようなエラーは、サービスの完全な障害に接続の部分的な損失からの重大度の範囲です。</span><span class="sxs-lookup"><span data-stu-id="dd797-110">These faults can range in severity from a partial loss of connectivity to the complete failure of a service.</span></span> <span data-ttu-id="dd797-111">これらの状況では、継続的に成功する可能性がある操作を再試行するアプリケーションの無意味な場合があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-111">In these situations, it might be pointless for an application to continually retry an operation that is unlikely to succeed.</span></span> <span data-ttu-id="dd797-112">代わりに、操作が失敗したことに同意し、それに応じてエラーを処理するアプリケーションをコーディングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-112">Instead, the application should be coded to accept that the operation has failed and handle the failure accordingly.</span></span>

<span data-ttu-id="dd797-113">遮断器のパターンは、再試行パターンは、異なる目的がします。</span><span class="sxs-lookup"><span data-stu-id="dd797-113">The Circuit Breaker pattern has a different purpose than the Retry pattern.</span></span> <span data-ttu-id="dd797-114">再試行パターンにより、アプリケーションを操作が成功最終的にする期待の操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="dd797-114">The Retry pattern enables an application to retry an operation in the expectation that the operation will eventually succeed.</span></span> <span data-ttu-id="dd797-115">遮断器パターンにより、アプリケーションが失敗する可能性がある操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="dd797-115">The Circuit Breaker pattern prevents an application from performing an operation that is likely to fail.</span></span> <span data-ttu-id="dd797-116">アプリケーションでは、遮断器で操作を再試行パターンを使用して、これら 2 つのパターンを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="dd797-116">An application can combine these two patterns by using the Retry pattern to invoke an operation through a circuit breaker.</span></span> <span data-ttu-id="dd797-117">ただし、再試行ロジックは、遮断器によって返されるすべての例外を区別する必要があります、遮断器は、エラーが一時的なものではないことを示している場合の再試行回数を破棄にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-117">However, the retry logic should be sensitive to any exceptions returned by the circuit breaker, and it should abandon retry attempts if the circuit breaker indicates that a fault is not transient.</span></span>

## <a name="implementing-a-circuit-breaker-pattern-with-polly"></a><span data-ttu-id="dd797-118">ポリーを遮断器のパターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="dd797-118">Implementing a Circuit Breaker pattern with Polly</span></span>

<span data-ttu-id="dd797-119">再試行を実装する場合としては、ポリーのような実証済みの .NET ライブラリを活用するためにサーキット ブレーカーの方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dd797-119">As when implementing retries, the recommended approach for circuit breakers is to take advantage of proven .NET libraries like Polly.</span></span>

<span data-ttu-id="dd797-120">EShopOnContainers アプリケーションは、HTTP 再試行を実装する場合に、ポリー遮断器のポリシーを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd797-120">The eShopOnContainers application uses the Polly Circuit Breaker policy when implementing HTTP retries.</span></span> <span data-ttu-id="dd797-121">実際には、アプリケーションでは、両方のポリシーが ResilientHttpClient ユーティリティ クラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="dd797-121">In fact, the application applies both policies to the ResilientHttpClient utility class.</span></span> <span data-ttu-id="dd797-122">(EShopOnContainers) からの HTTP 要求 ResilientHttpClient の型のオブジェクトを使用すると、これら両方のポリシーを適用するけれども、すぎる追加のポリシーを追加することが</span><span class="sxs-lookup"><span data-stu-id="dd797-122">Whenever you use an object of type ResilientHttpClient for HTTP requests (from eShopOnContainers), you will be applying both those policies, but you could add additional policies, too.</span></span>

<span data-ttu-id="dd797-123">唯一の追加は、ここの HTTP 呼び出しの再試行に使用するコードを使用するにはポリシーの一覧に遮断器のポリシーを追加する場所、次のコードの最後に示すようにコードに示します。</span><span class="sxs-lookup"><span data-stu-id="dd797-123">The only addition here to the code used for HTTP call retries is the code where you add the Circuit Breaker policy to the list of policies to use, as shown at the end of the following code:</span></span>

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

<span data-ttu-id="dd797-124">コードは、HTTP ラッパーにポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="dd797-124">The code adds a policy to the HTTP wrapper.</span></span> <span data-ttu-id="dd797-125">ポリシーとしてコードが指定された数の連続する例外 (行での例外) を検出したときに表示される、遮断器を定義することは、exceptionsAllowedBeforeBreaking パラメーター (この場合の 5) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="dd797-125">That policy defines a circuit breaker that opens when the code detects the specified number of consecutive exceptions (exceptions in a row), as passed in the exceptionsAllowedBeforeBreaking parameter (5 in this case).</span></span> <span data-ttu-id="dd797-126">回路が開いているときは、HTTP 要求が機能しないが、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="dd797-126">When the circuit is open, HTTP requests do not work, but an exception is raised.</span></span>

<span data-ttu-id="dd797-127">サーキット ブレーカーは、クライアントのアプリケーションよりも、別の環境にデプロイされている特定のリソースまたは HTTP 呼び出しを実行しているサービスに問題がある場合、フォールバック インフラストラクチャに要求をリダイレクトするためも使用してください。</span><span class="sxs-lookup"><span data-stu-id="dd797-127">Circuit breakers should also be used to redirect requests to a fallback infrastructure if you might have issues in a particular resource that is deployed in a different environment than the client application or service that is performing the HTTP call.</span></span> <span data-ttu-id="dd797-128">このように、バックエンド microservices のみがクライアント アプリケーション、影響を及ぼすデータ センターで障害があるクライアント アプリケーションが代替のサービスにリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="dd797-128">That way, if there is an outage in the datacenter that impacts only your backend microservices but not your client applications, the client applications can redirect to the fallback services.</span></span> <span data-ttu-id="dd797-129">これを自動化する新しいポリシーを計画しているポリー[フェールオーバー ポリシー](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy)シナリオです。</span><span class="sxs-lookup"><span data-stu-id="dd797-129">Polly is planning a new policy to automate this [failover policy](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy) scenario.</span></span>

<span data-ttu-id="dd797-130">もちろん、これらすべての機能は、によって自動的に管理するため、Azure の場所の透過性がなく、.NET コード内でのフェールオーバーを管理している場合です。</span><span class="sxs-lookup"><span data-stu-id="dd797-130">Of course, all those features are for cases where you are managing the failover from within the .NET code, as opposed to having it managed automatically for you by Azure, with location transparency.</span></span>

## <a name="using-the-resilienthttpclient-utility-class-from-eshoponcontainers"></a><span data-ttu-id="dd797-131">EShopOnContainers から ResilientHttpClient ユーティリティ クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd797-131">Using the ResilientHttpClient utility class from eShopOnContainers</span></span>

<span data-ttu-id="dd797-132">.NET HttpClient クラスを使用する方法と同様の方法で ResilientHttpClient ユーティリティ クラスを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="dd797-132">You use the ResilientHttpClient utility class in a way similar to how you use the .NET HttpClient class.</span></span> <span data-ttu-id="dd797-133">EShopOnContainers MVC web アプリケーション (、OrderingService エージェントによって使用されるクラス OrderController) から次の例で、コンス トラクターの httpClient パラメーターを通じて ResilientHttpClient オブジェクトが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="dd797-133">In the following example from the eShopOnContainers MVC web application (the OrderingService agent class used by OrderController), the ResilientHttpClient object is injected through the httpClient parameter of the constructor.</span></span> <span data-ttu-id="dd797-134">HTTP 要求を実行するオブジェクトを使用しています。</span><span class="sxs-lookup"><span data-stu-id="dd797-134">Then the object is used to perform HTTP requests.</span></span>

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

<span data-ttu-id="dd797-135">ときに、 \_apiClient メンバー オブジェクトを使用して、内部的にポリー policiesؙ のラッパー クラスを使用: 再試行ポリシー、遮断器ポリシーおよびポリー ポリシーのコレクションから適用するその他のポリシー。</span><span class="sxs-lookup"><span data-stu-id="dd797-135">Whenever the \_apiClient member object is used, it internally uses the wrapper class with Polly policiesؙ—the Retry policy, the Circuit Breaker policy, and any other policy that you might want to apply from the Polly policies collection.</span></span>

## <a name="testing-retries-in-eshoponcontainers"></a><span data-ttu-id="dd797-136">EShopOnContainers での再試行回数のテスト</span><span class="sxs-lookup"><span data-stu-id="dd797-136">Testing retries in eShopOnContainers</span></span>

<span data-ttu-id="dd797-137">Docker ホストに eShopOnContainers ソリューションを起動するたびに複数のコンテナーを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-137">Whenever you start the eShopOnContainers solution in a Docker host, it needs to start multiple containers.</span></span> <span data-ttu-id="dd797-138">コンテナーの一部を起動し、SQL Server のコンテナーと同様に、初期化に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="dd797-138">Some of the containers are slower to start and initialize, like the SQL Server container.</span></span> <span data-ttu-id="dd797-139">これは特に、Docker に eShopOnContainers アプリケーションを配置するときに最初のイメージと、データベースを設定する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="dd797-139">This is especially true the first time you deploy the eShopOnContainers application into Docker, because it needs to set up the images and the database.</span></span> <span data-ttu-id="dd797-140">コンテナーをいくつかの開始よりも他のユーザーが最初に HTTP 例外をスローするサービスの残りの部分でコンテナー間の依存関係を設定した場合でも、時間がかかること、docker の構成レベルでは、前のセクションで説明したようです。</span><span class="sxs-lookup"><span data-stu-id="dd797-140">The fact that some containers start slower than others can cause the rest of the services to initially throw HTTP exceptions, even if you set dependencies between containers at the docker-compose level, as explained in previous sections.</span></span> <span data-ttu-id="dd797-141">Docker の構成コンテナー間の依存関係は、プロセス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="dd797-141">Those docker-compose dependencies between containers are just at the process level.</span></span> <span data-ttu-id="dd797-142">コンテナーのエントリ ポイント プロセスが開始される場合が、SQL Server がクエリの準備ができていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-142">The container’s entry point process might be started, but SQL Server might not be ready for queries.</span></span> <span data-ttu-id="dd797-143">結果は、連鎖的に、エラー、その特定のコンテナーを使用しようとするときに、アプリケーションが例外を取得できます。</span><span class="sxs-lookup"><span data-stu-id="dd797-143">The result can be a cascade of errors, and the application can get an exception when trying to consume that particular container.</span></span>

<span data-ttu-id="dd797-144">この種類のエラーの起動時にアプリケーションがクラウドに展開する場合。</span><span class="sxs-lookup"><span data-stu-id="dd797-144">You might also see this type of error on startup when the application is deploying to the cloud.</span></span> <span data-ttu-id="dd797-145">その場合は、orchestrators 可能性があるコンテナーから 1 つのノードまたは VM へ移動 (つまり、新しいインスタンスを開始) 別、クラスターのノード間でコンテナーの数のバランスをとる場合。</span><span class="sxs-lookup"><span data-stu-id="dd797-145">In that case, orchestrators might be moving containers from one node or VM to another (that is, starting new instances) when balancing the number of containers across the cluster’s nodes.</span></span>

<span data-ttu-id="dd797-146">この問題は解決 eShopOnContainers 方法は、上記で説明したお再試行パターンを使用してです。</span><span class="sxs-lookup"><span data-stu-id="dd797-146">The way eShopOnContainers solves this issue is by using the Retry pattern we illustrated earlier.</span></span> <span data-ttu-id="dd797-147">なぜ、ソリューションを開始するときに発生する可能性ログ トレースまたは次のような警告がまたです。</span><span class="sxs-lookup"><span data-stu-id="dd797-147">It is also why, when starting the solution, you might get log traces or warnings like the following:</span></span>

> <span data-ttu-id="dd797-148">"**ポリーの RetryPolicy で実装される再試行 1**、原因: System.Net.Http.HttpRequestException: 要求の送信中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dd797-148">"**Retry 1 implemented with Polly's RetryPolicy**, due to: System.Net.Http.HttpRequestException: An error occurred while sending the request.</span></span><span data-ttu-id="dd797-149"> ---&gt;System.Net.Http.CurlException: がサーバーに接続できませんでした\\System.Net.Http.CurlHandler.ThrowIfCURLEError (CURLcode エラー) にある n\\に n\[しています.\].</span><span class="sxs-lookup"><span data-stu-id="dd797-149"> ---&gt; System.Net.Http.CurlException: Couldn't connect to server\\n at System.Net.Http.CurlHandler.ThrowIfCURLEError(CURLcode error)\\n at \[...\].</span></span>

## <a name="testing-the-circuit-breaker-in-eshoponcontainers"></a><span data-ttu-id="dd797-150">EShopOnContainers で遮断器のテスト</span><span class="sxs-lookup"><span data-stu-id="dd797-150">Testing the circuit breaker in eShopOnContainers</span></span>

<span data-ttu-id="dd797-151">回線を開いて eShopOnContainers 併用をテストして、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-151">There are a few ways you can open the circuit and test it with eShopOnContainers.</span></span>

<span data-ttu-id="dd797-152">1 つのオプションには、1、遮断器ポリシーに再試行の最大数を削減し、Docker にソリューション全体を再展開します。</span><span class="sxs-lookup"><span data-stu-id="dd797-152">One option is to lower the allowed number of retries to 1 in the circuit breaker policy and redeploy the whole solution into Docker.</span></span> <span data-ttu-id="dd797-153">1 回の再試行は配置時に HTTP 要求に失敗する可能性が高く、遮断器が開き、およびエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="dd797-153">With a single retry, there is a good chance that an HTTP request will fail during deployment, the circuit breaker will open, and you get an error.</span></span>

<span data-ttu-id="dd797-154">順序付けのマイクロ サービスで実装されているカスタムのミドルウェアを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="dd797-154">Another option is to use custom middleware that is implemented in the ordering microservice.</span></span> <span data-ttu-id="dd797-155">このミドルウェアを有効にすると、すべての HTTP 要求をキャッチし、ステータス コード 500 を返します。</span><span class="sxs-lookup"><span data-stu-id="dd797-155">When this middleware is enabled, it catches all HTTP requests and returns status code 500.</span></span> <span data-ttu-id="dd797-156">GET 要求を失敗にすることにより、ミドルウェアを有効にすることができます、次のように、URI:</span><span class="sxs-lookup"><span data-stu-id="dd797-156">You can enable the middleware by making a GET request to the failing URI, like the following:</span></span>

-   <span data-ttu-id="dd797-157">取得/失敗</span><span class="sxs-lookup"><span data-stu-id="dd797-157">GET /failing</span></span>

<span data-ttu-id="dd797-158">この要求では、ミドルウェアの現在の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="dd797-158">This request returns the current state of the middleware.</span></span> <span data-ttu-id="dd797-159">ミドルウェアが有効になっている場合、要求はステータス コード 500 を返します。</span><span class="sxs-lookup"><span data-stu-id="dd797-159">If the middleware is enabled, the request return status code 500.</span></span> <span data-ttu-id="dd797-160">ミドルウェアが無効になっている場合、応答がありません。</span><span class="sxs-lookup"><span data-stu-id="dd797-160">If the middleware is disabled, there is no response.</span></span>

-   <span data-ttu-id="dd797-161">取得/失敗しているかを有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd797-161">GET /failing?enable</span></span>

<span data-ttu-id="dd797-162">この要求は、ミドルウェアを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd797-162">This request enables the middleware.</span></span>

-   <span data-ttu-id="dd797-163">取得/失敗しているか無効にします。</span><span class="sxs-lookup"><span data-stu-id="dd797-163">GET /failing?disable</span></span>

<span data-ttu-id="dd797-164">この要求には、ミドルウェアが無効にします。</span><span class="sxs-lookup"><span data-stu-id="dd797-164">This request disables the middleware.</span></span>

<span data-ttu-id="dd797-165">たとえば、アプリケーションが実行されている任意のブラウザーで次の URI を使用して、要求をすることで、ミドルウェアを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="dd797-165">For instance, once the application is running, you can enable the middleware by making a request using the following URI in any browser.</span></span> <span data-ttu-id="dd797-166">順序付けのマイクロ サービスはポート 5102 を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dd797-166">Note that the ordering microservice uses port 5102.</span></span>

<span data-ttu-id="dd797-167">http://localhost:5102 失敗/? を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dd797-167">http://localhost:5102/failing?enable</span></span>

<span data-ttu-id="dd797-168">URI を使用して状態を確認することができますし、 [http://localhost:5102 失敗/](http://localhost:5100/failing)図 10-4 に示すように、します。</span><span class="sxs-lookup"><span data-stu-id="dd797-168">You can then check the status using the URI [http://localhost:5102/failing](http://localhost:5100/failing), as shown in Figure 10-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="dd797-169">**図 10-4**です。</span><span class="sxs-lookup"><span data-stu-id="dd797-169">**Figure 10-4**.</span></span> <span data-ttu-id="dd797-170">ASP.NET のミドルウェアの障害をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="dd797-170">Simulating a failure with ASP.NET middleware</span></span>

<span data-ttu-id="dd797-171">この時点で、順序付けマイクロ サービスが応答状態コード 500 を呼び出すたびにでは呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="dd797-171">At this point, the ordering microservice responds with status code 500 whenever you call invoke it.</span></span>

<span data-ttu-id="dd797-172">ミドルウェアが実行されていると、MVC web アプリケーションから注文を作成しようとすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd797-172">Once the middleware is running, you can try making an order from the MVC web application.</span></span> <span data-ttu-id="dd797-173">要求が失敗したため、回線が開きます。</span><span class="sxs-lookup"><span data-stu-id="dd797-173">Because the requests fails, the circuit will open.</span></span>

<span data-ttu-id="dd797-174">次の例では、MVC web アプリケーションが catch を持つことを確認できますで注文を発行するためのロジックをブロックします。</span><span class="sxs-lookup"><span data-stu-id="dd797-174">In the following example, you can see that the MVC web application has a catch block in the logic for placing an order.</span></span> <span data-ttu-id="dd797-175">コードでは、開いている回線例外をキャッチ、表示、ユーザーが手短にわかりやすいメッセージが待機されます。</span><span class="sxs-lookup"><span data-stu-id="dd797-175">If the code catches an open-circuit exception, it shows the user a friendly message telling them to wait.</span></span>

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

<span data-ttu-id="dd797-176">次に概要を示します。</span><span class="sxs-lookup"><span data-stu-id="dd797-176">Here’s a summary.</span></span> <span data-ttu-id="dd797-177">再試行ポリシーでは、何回かに、HTTP 要求および HTTP エラーを取得しようとします。</span><span class="sxs-lookup"><span data-stu-id="dd797-177">The Retry policy tries several times to make the HTTP request and gets HTTP errors.</span></span> <span data-ttu-id="dd797-178">試行回数には、(ここでは、5)、遮断器ポリシーの最大数のセットに達すると、アプリケーションは、BrokenCircuitException をスローします。</span><span class="sxs-lookup"><span data-stu-id="dd797-178">When the number of tries reaches the maximum number set for the Circuit Breaker policy (in this case, 5), the application throws a BrokenCircuitException.</span></span> <span data-ttu-id="dd797-179">図 10-5 に示すように、わかりやすいメッセージになります。</span><span class="sxs-lookup"><span data-stu-id="dd797-179">The result is a friendly message, as shown in Figure 10-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="dd797-180">**図 10-5**です。</span><span class="sxs-lookup"><span data-stu-id="dd797-180">**Figure 10-5**.</span></span> <span data-ttu-id="dd797-181">遮断器が UI にエラーを返す</span><span class="sxs-lookup"><span data-stu-id="dd797-181">Circuit breaker returning an error to the UI</span></span>

<span data-ttu-id="dd797-182">回線を開くときに別のロジックを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="dd797-182">You can implement different logic for when to open the circuit.</span></span> <span data-ttu-id="dd797-183">または、代替データ センターまたは冗長のバックエンド システムがある場合、異なるバックエンド マイクロ サービスに対する HTTP 要求を試みることができます。</span><span class="sxs-lookup"><span data-stu-id="dd797-183">Or you can try an HTTP request against a different back-end microservice if there is a fallback datacenter or redundant back-end system.</span></span>

<span data-ttu-id="dd797-184">最後に、他の方法として、CircuitBreakerPolicy は (を強制的に開いていると、開いている回路を保持して) 分離と (をもう一度閉じる) のリセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="dd797-184">Finally, another possibility for the CircuitBreakerPolicy is to use Isolate (which forces open and holds open the circuit) and Reset (which closes it again).</span></span> <span data-ttu-id="dd797-185">これらは、ポリシーを特定し、直接のリセットを起動するユーティリティ HTTP エンドポイントの作成に使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-185">These could be used to build a utility HTTP endpoint that invokes Isolate and Reset directly on the policy.</span></span> <span data-ttu-id="dd797-186">このような HTTP エンドポイントも使用できます、一時的にアップグレードする場合などの下流システムを分離するためには、実稼働環境で、適切に保護します。</span><span class="sxs-lookup"><span data-stu-id="dd797-186">Such an HTTP endpoint could also be used, suitably secured, in production for temporarily isolating a downstream system, such as when you want to upgrade it.</span></span> <span data-ttu-id="dd797-187">または、エラーが発生すると思われる下流システムを保護するために手動で回線を作動する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dd797-187">Or it could trip the circuit manually to protect a downstream system you suspect to be faulting.</span></span>

## <a name="adding-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="dd797-188">再試行ポリシーにジッター戦略を追加します。</span><span class="sxs-lookup"><span data-stu-id="dd797-188">Adding a jitter strategy to the retry policy</span></span>

<span data-ttu-id="dd797-189">正規の再試行ポリシーとの競合 高い同時実行性とスケーラビリティの場合、システムに影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="dd797-189">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="dd797-190">部分的な障害が発生した場合、多くのクライアントからのものと同様の再試行のピークをなくすためは、適切な回避策は、再試行アルゴリズム/ポリシー ジッター戦略を追加します。</span><span class="sxs-lookup"><span data-stu-id="dd797-190">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="dd797-191">これにより、指数バックオフに乱数を追加することで、エンド ツー エンド システムの全体的なパフォーマンスが向上ことができます。</span><span class="sxs-lookup"><span data-stu-id="dd797-191">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="dd797-192">これによって、問題が発生したときに、急増によってが分散されます。</span><span class="sxs-lookup"><span data-stu-id="dd797-192">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="dd797-193">ポリーを使用すると、ジッターを実装するコードは次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="dd797-193">When you use Polly, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random();
Policy.Handle<HttpResponseException>() // etc
    .WaitAndRetry(5, // exponential back-off plus some jitter
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))
            + TimeSpan.FromMilliseconds(jitterer.Next(0, 100))
    );
```

## <a name="additional-resources"></a><span data-ttu-id="dd797-194">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="dd797-194">Additional resources</span></span>

-   <span data-ttu-id="dd797-195">**再試行パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="dd797-195">**Retry pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/retry*](https://docs.microsoft.com/azure/architecture/patterns/retry)</span></span>

-   <span data-ttu-id="dd797-196">**接続の回復**(Entity Framework Core) [ *https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="dd797-196">**Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="dd797-197">**ポリー** (.NET からの復元力と一時的なエラー処理ライブラリ) [ *https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span><span class="sxs-lookup"><span data-stu-id="dd797-197">**Polly** (.NET resilience and transient-fault-handling library) [*https://github.com/App-vNext/Polly*](https://github.com/App-vNext/Polly)</span></span>

-   <span data-ttu-id="dd797-198">**遮断器パターン**
    [*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span><span class="sxs-lookup"><span data-stu-id="dd797-198">**Circuit Breaker pattern**
[*https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker*](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)</span></span>

-   <span data-ttu-id="dd797-199">**Marc Brooker です。ジッター: を行うものよりランダム**https://brooker.co.za/blog/2015/03/21/backoff.html</span><span class="sxs-lookup"><span data-stu-id="dd797-199">**Marc Brooker. Jitter: Making Things Better With Randomness** https://brooker.co.za/blog/2015/03/21/backoff.html</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="dd797-200">[前](implement-http-call-retries-exponential-backoff-polly.md) [次へ] (モニター-アプリ-health.md)</span><span class="sxs-lookup"><span data-stu-id="dd797-200">[Previous] (implement-http-call-retries-exponential-backoff-polly.md) [Next] (monitor-app-health.md)</span></span>

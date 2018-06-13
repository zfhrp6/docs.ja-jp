---
title: Polly で指数のバックオフを含む HTTP 呼び出しの再試行を実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Polly で指数のバックオフを含む HTTP 呼び出しの再試行を実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 66ac57fc824e01f96d6584ab86bb95ba1b0174a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576982"
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="b34e3-103">Polly で指数のバックオフを含む HTTP 呼び出しの再試行を実装する</span><span class="sxs-lookup"><span data-stu-id="b34e3-103">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="b34e3-104">指数のバックオフでの再試行のためのアプローチとしては、オープン ソースである [Polly](https://github.com/App-vNext/Polly) ライブラリのような高度な .NET ライブラリを利用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b34e3-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="b34e3-105">Polly とは、回復機能と一時的な障害処理の機能を提供する .NET ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="b34e3-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="b34e3-106">このような機能は、再試行、遮断器、バルクヘッド分離、タイムアウト、フォールバックなどの Polly ポリシーを適用することで簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="b34e3-106">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="b34e3-107">Polly は .NET 4.x および .NET Standard バージョン 1.0 (.NET Core をサポート) を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="b34e3-107">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="b34e3-108">Polly の再試行ポリシーは、HTTP の再試行を実装する場合に eShopOnContainers で使用されるアプローチです。</span><span class="sxs-lookup"><span data-stu-id="b34e3-108">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="b34e3-109">使用する再試行ポリシーの構成に応じて、標準的な HttpClient 機能か、または Polly を使用した HttpClient の回復バージョンを挿入できるように、インターフェイスを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="b34e3-109">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="b34e3-110">次の例では、eShopOnContainers で実装されたインターフェイスを示します。</span><span class="sxs-lookup"><span data-stu-id="b34e3-110">The following example shows the interface implemented in eShopOnContainers.</span></span>

```csharp
public interface IHttpClient
{
    Task<string> GetStringAsync(string uri, string authorizationToken = null,
        string authorizationMethod = "Bearer");
        Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    Task<HttpResponseMessage> DeleteAsync(string uri,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer");

    // Other methods ...
}
```

<span data-ttu-id="b34e3-111">簡単なアプローチを開発またはテストするときのように、回復メカニズムを使用したくない場合は、標準の実装を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b34e3-111">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="b34e3-112">次のコードは、省略可能なケースとして認証トークンを使用した要求を許可する標準的な HttpClient 実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="b34e3-112">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

```csharp
public class StandardHttpClient : IHttpClient
{
    private HttpClient _client;
    private ILogger<StandardHttpClient> _logger;

    public StandardHttpClient(ILogger<StandardHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
    }

    public async Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
        if (authorizationToken != null)
        {
            requestMessage.Headers.Authorization =
                new AuthenticationHeaderValue(authorizationMethod, authorizationToken);
        }
        var response = await _client.SendAsync(requestMessage);
        return await response.Content.ReadAsStringAsync();
    }

    public async Task<HttpResponseMessage> PostAsync<T>(string uri, T item,
        string authorizationToken = null, string requestId = null,
        string authorizationMethod = "Bearer")
    {
        // Rest of the code and other Http methods ...
```

<span data-ttu-id="b34e3-113">興味深い実装は類似した別のクラスをコード化することですが、使用する回復メカニズム (次の例では、指数のバックオフでの再試行) を実装するには Polly を使用します。</span><span class="sxs-lookup"><span data-stu-id="b34e3-113">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

```csharp
public class ResilientHttpClient : IHttpClient
{
    private HttpClient _client;
    private PolicyWrap _policyWrapper;
    private ILogger<ResilientHttpClient> _logger;

    public ResilientHttpClient(Policy[] policies,
        ILogger<ResilientHttpClient> logger)
    {
        _client = new HttpClient();
        _logger = logger;
        // Add Policies to be applied
        _policyWrapper = Policy.WrapAsync(policies);
    }

    private Task<T> HttpInvoker<T>(Func<Task<T>> action)
    {
        // Executes the action applying all
        // the policies defined in the wrapper
        return _policyWrapper.ExecuteAsync(() => action());
    }

    public Task<string> GetStringAsync(string uri,
        string authorizationToken = null,
        string authorizationMethod = "Bearer")
    {
        return HttpInvoker(async () =>
        {
            var requestMessage = new HttpRequestMessage(HttpMethod.Get, uri);
            // The Token's related code eliminated for clarity in code snippet
            var response = await _client.SendAsync(requestMessage);
            return await response.Content.ReadAsStringAsync();
        });
    }
    // Other Http methods executed through HttpInvoker so it applies Polly policies
    // ...
}
```

<span data-ttu-id="b34e3-114">Polly では、再試行回数を指定した再試行ポリシー、指数のバックオフの構成、および HTTP 例外が発生した場合に実行するアクション (エラーの記録など) を定義します。</span><span class="sxs-lookup"><span data-stu-id="b34e3-114">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="b34e3-115">この場合は、IoC コンテナーでの種類の登録時に指定した回数が試行されるように、ポリシーを構成します。</span><span class="sxs-lookup"><span data-stu-id="b34e3-115">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="b34e3-116">指数のバックオフ構成であるために、コードは HttpRequest 例外を検出するたびに、ポリシーが構成されている方法に応じて指数関数的に増加する時間を待機してから Http 要求を再試行します。</span><span class="sxs-lookup"><span data-stu-id="b34e3-116">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="b34e3-117">重要なメソッドは HttpInvoker です。これは、このユーティリティ クラス全体にわたって HTTP 要求を行うメソッドです。</span><span class="sxs-lookup"><span data-stu-id="b34e3-117">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="b34e3-118">そのメソッドは、\_policyWrapper.ExecuteAsync が指定された HTTP 要求を内部で実行します。これにより再試行ポリシーが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="b34e3-118">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="b34e3-119">eShopOnContainers では、次に示した [MVC Web アプリの startup.cs クラス](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)のコードのように、IoC コンテナーで種類を登録するときに Polly ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b34e3-119">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

```csharp
// Startup.cs class
if (Configuration.GetValue<string>("UseResilientHttp") == bool.TrueString)
{
    services.AddTransient<IResilientHttpClientFactory,
        ResilientHttpClientFactory>();
    services.AddSingleton<IHttpClient,
        ResilientHttpClient>(sp =>
            sp.GetService<IResilientHttpClientFactory>().
            CreateResilientHttpClient());
}
else
{
    services.AddSingleton<IHttpClient, StandardHttpClient>();
}
```

<span data-ttu-id="b34e3-120">TCP 接続がサービスによって効率的に使用され、[ソケットでの問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)が発生しなくなるように、IHttpClient オブジェクトは一時的なものとしてではなく、シングルトンとしてインスタンス化されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b34e3-120">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="b34e3-121">ただし、回復性に関して重要な点は、次のコードに示すように、CreateResilientHttpClient メソッドの ResilientHttpClientFactory 内で Polly の WaitAndRetryAsync ポリシーを適用することです。</span><span class="sxs-lookup"><span data-stu-id="b34e3-121">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

```csharp
public ResilientHttpClient CreateResilientHttpClient()
    => new ResilientHttpClient(CreatePolicies(), _logger);

// Other code
private Policy[] CreatePolicies()
    => new Policy[]
    {
        Policy.Handle<HttpRequestException>()
            .WaitAndRetryAsync(
        // number of retries
        6,
        // exponential backoff
        retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)),
        // on retry
        (exception, timeSpan, retryCount, context) =>
        {
            var msg = $"Retry {retryCount} implemented with Pollys RetryPolicy " +
            $"of {context.PolicyKey} " +
            $"at {context.ExecutionKey}, " +
            $"due to: {exception}.";
            _logger.LogWarning(msg);
            _logger.LogDebug(msg);
        }),
    }
```


>[!div class="step-by-step"]
<span data-ttu-id="b34e3-122">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="b34e3-122">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>

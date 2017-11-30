---
title: "ポリーを指数バックオフによる HTTP 呼び出しの再試行を実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |ポリーを指数バックオフによる HTTP 呼び出しの再試行を実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1ed48142546403ea710f4c132e038521232c20ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a><span data-ttu-id="5ad6b-104">ポリーを指数バックオフによる HTTP 呼び出しの再試行を実装します。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-104">Implementing HTTP call retries with exponential backoff with Polly</span></span>

<span data-ttu-id="5ad6b-105">指数バックオフによる再試行をお勧め活用するために .NET ライブラリの高度なオープン ソースのような[ポリー](https://github.com/App-vNext/Polly)ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-105">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open source [Polly](https://github.com/App-vNext/Polly) library.</span></span>

<span data-ttu-id="5ad6b-106">ポリーは、回復力と一時的なエラー処理機能を提供する .NET ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-106">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="5ad6b-107">再試行、遮断器、バルクヘッド分離、タイムアウト、およびフォールバックなどポリー ポリシーを適用することで、それらの機能を簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-107">You can implement those capabilities easily by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="5ad6b-108">ポリー対象 .NET 4.x および .NET の標準のバージョン 1.0 (.NET Core をサポートしています)。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-108">Polly targets .NET 4.x and the .NET Standard version 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="5ad6b-109">ポリーの再試行ポリシーは、HTTP 再試行を実装する場合、eShopOnContainers で使用される方法です。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-109">The Retry policy in Polly is the approach used in eShopOnContainers when implementing HTTP retries.</span></span> <span data-ttu-id="5ad6b-110">HttpClient の標準的な機能または使用するどのような再試行ポリシーの構成に応じてポリーを使用する HttpClient の回復力のあるバージョンのいずれかを挿入できるように、インターフェイスを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-110">You can implement an interface so you can inject either standard HttpClient functionality or a resilient version of HttpClient using Polly, depending on what retry policy configuration you want to use.</span></span>

<span data-ttu-id="5ad6b-111">次の例では、eShopOnContainers で実装されたインターフェイスを示します。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-111">The following example shows the interface implemented in eShopOnContainers.</span></span>

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

<span data-ttu-id="5ad6b-112">開発または簡単な方法をテストするとき、として、回復力のあるメカニズムを使用したくない場合は、標準の実装を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-112">You can use the standard implementation if you do not want to use a resilient mechanism, as when you are developing or testing simpler approaches.</span></span> <span data-ttu-id="5ad6b-113">次のコードは、省略可能なケースとして、標準 HttpClient の実装できるようにする要求の認証トークンを使用を示します。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-113">The following code shows the standard HttpClient implementation allowing requests with authentication tokens as an optional case.</span></span>

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

<span data-ttu-id="5ad6b-114">同様、別のクラスが使用する回復力のあるメカニズムを実装するポリーを使用してコードを興味深い実装が、次の例では、指数バックオフによる再試行です。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-114">The interesting implementation is to code another, similar class, but using Polly to implement the resilient mechanisms you want to use—in the following example, retries with exponential backoff.</span></span>

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

<span data-ttu-id="5ad6b-115">ポリーでの再試行、指数バックオフ構成、およびエラーの記録など、HTTP 例外がある場合に実行されるアクションの数と再試行ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-115">With Polly, you define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there is an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="5ad6b-116">ここはしようとする、指定された回数、IoC コンテナー内の型を登録するときに、ポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-116">In this case, the policy is configured so it will try the number of times specified when registering the types in the IoC container.</span></span> <span data-ttu-id="5ad6b-117">指数バックオフ構成のため、コードが、HttpRequest 例外を検出するたびに、Http 要求を再試行ポリシーの構成方法によっては指数関数的に増加するまでの時間が待機した後にします。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-117">Because of the exponential backoff configuration, whenever the code detects an HttpRequest exception, it retries the Http request after waiting an amount of time that increases exponentially depending on how the policy was configured.</span></span>

<span data-ttu-id="5ad6b-118">重要なメソッドです HttpInvoker、ため、このユーティリティ クラス全体での HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-118">The important method is HttpInvoker, which is what makes HTTP requests throughout this utility class.</span></span> <span data-ttu-id="5ad6b-119">メソッドが HTTP 要求が内部でが実行される\_policyWrapper.ExecuteAsync で、再試行ポリシーを考慮します。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-119">That method internally executes the HTTP request with \_policyWrapper.ExecuteAsync, which takes into account the retry policy.</span></span>

<span data-ttu-id="5ad6b-120">EShopOnContainers でポリシーを指定するポリーから次のコードのように、IoC コンテナーの種類を登録するときに、 [MVC web アプリケーション、startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)クラスです。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-120">In eShopOnContainers you specify Polly policies when registering the types at the IoC container, as in the following code from the [MVC web app at the startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs) class.</span></span>

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

<span data-ttu-id="5ad6b-121">サービスでの TCP 接続を効率的に使用できるように、一時的なものとしての代わりにシングルトンとして IHttpClient オブジェクトがインスタンス化に注意してください、[ソケットを使用して問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)は行われません。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-121">Note that the IHttpClient objects are instantiated as singleton instead of as transient so that TCP connections are used efficiently by the service and [an issue with sockets](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) will not occur.</span></span>

<span data-ttu-id="5ad6b-122">回復性に関する重要な点が CreateResilientHttpClient メソッドで ResilientHttpClientFactory 内ポリー WaitAndRetryAsync ポリシーを適用すること、次のコードに示すように。</span><span class="sxs-lookup"><span data-stu-id="5ad6b-122">But the important point about resiliency is that you apply the Polly WaitAndRetryAsync policy within ResilientHttpClientFactory in the CreateResilientHttpClient method, as shown in the following code:</span></span>

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
<span data-ttu-id="5ad6b-123">[前](implement-custom-http-call-retries-exponential-backoff.md) [次へ] (実装の回線のブレーカー-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="5ad6b-123">[Previous] (implement-custom-http-call-retries-exponential-backoff.md) [Next] (implement-circuit-breaker-pattern.md)</span></span>

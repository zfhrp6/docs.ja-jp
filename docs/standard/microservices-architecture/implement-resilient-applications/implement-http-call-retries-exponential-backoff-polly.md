---
title: Polly で指数のバックオフを含む HTTP 呼び出しの再試行を実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Polly で指数のバックオフを含む HTTP 呼び出しの再試行を実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cce1392bb381859e7cad89c9f2518113241ae724
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106932"
---
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>Polly で指数のバックオフを含む HTTP 呼び出しの再試行を実装する

指数のバックオフでの再試行のためのアプローチとしては、オープン ソースである [Polly](https://github.com/App-vNext/Polly) ライブラリのような高度な .NET ライブラリを利用することをお勧めします。

Polly とは、回復機能と一時的な障害処理の機能を提供する .NET ライブラリです。 このような機能は、再試行、遮断器、バルクヘッド分離、タイムアウト、フォールバックなどの Polly ポリシーを適用することで簡単に実装できます。 Polly は .NET 4.x および .NET Standard バージョン 1.0 (.NET Core をサポート) を対象にしています。

Polly の再試行ポリシーは、HTTP の再試行を実装する場合に eShopOnContainers で使用されるアプローチです。 使用する再試行ポリシーの構成に応じて、標準的な HttpClient 機能か、または Polly を使用した HttpClient の回復バージョンを挿入できるように、インターフェイスを実装することができます。

次の例では、eShopOnContainers で実装されたインターフェイスを示します。

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

簡単なアプローチを開発またはテストするときのように、回復メカニズムを使用したくない場合は、標準の実装を使用することができます。 次のコードは、省略可能なケースとして認証トークンを使用した要求を許可する標準的な HttpClient 実装を示しています。

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

興味深い実装は類似した別のクラスをコード化することですが、使用する回復メカニズム (次の例では、指数のバックオフでの再試行) を実装するには Polly を使用します。

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

Polly では、再試行回数を指定した再試行ポリシー、指数のバックオフの構成、および HTTP 例外が発生した場合に実行するアクション (エラーの記録など) を定義します。 この場合は、IoC コンテナーでの種類の登録時に指定した回数が試行されるように、ポリシーを構成します。 指数のバックオフ構成であるために、コードは HttpRequest 例外を検出するたびに、ポリシーが構成されている方法に応じて指数関数的に増加する時間を待機してから Http 要求を再試行します。

重要なメソッドは HttpInvoker です。これは、このユーティリティ クラス全体にわたって HTTP 要求を行うメソッドです。 そのメソッドは、\_policyWrapper.ExecuteAsync が指定された HTTP 要求を内部で実行します。これにより再試行ポリシーが考慮されます。

eShopOnContainers では、次に示した [MVC Web アプリの startup.cs クラス](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)のコードのように、IoC コンテナーで種類を登録するときに Polly ポリシーを指定します。

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

TCP 接続がサービスによって効率的に使用され、[ソケットでの問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)が発生しなくなるように、IHttpClient オブジェクトは一時的なものとしてではなく、シングルトンとしてインスタンス化されることに注意してください。

ただし、回復性に関して重要な点は、次のコードに示すように、CreateResilientHttpClient メソッドの ResilientHttpClientFactory 内で Polly の WaitAndRetryAsync ポリシーを適用することです。

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
[前へ](implement-custom-http-call-retries-exponential-backoff.md)
[次へ](implement-circuit-breaker-pattern.md)

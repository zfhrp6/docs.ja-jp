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
# <a name="implementing-http-call-retries-with-exponential-backoff-with-polly"></a>ポリーを指数バックオフによる HTTP 呼び出しの再試行を実装します。

指数バックオフによる再試行をお勧め活用するために .NET ライブラリの高度なオープン ソースのような[ポリー](https://github.com/App-vNext/Polly)ライブラリです。

ポリーは、回復力と一時的なエラー処理機能を提供する .NET ライブラリです。 再試行、遮断器、バルクヘッド分離、タイムアウト、およびフォールバックなどポリー ポリシーを適用することで、それらの機能を簡単に実装できます。 ポリー対象 .NET 4.x および .NET の標準のバージョン 1.0 (.NET Core をサポートしています)。

ポリーの再試行ポリシーは、HTTP 再試行を実装する場合、eShopOnContainers で使用される方法です。 HttpClient の標準的な機能または使用するどのような再試行ポリシーの構成に応じてポリーを使用する HttpClient の回復力のあるバージョンのいずれかを挿入できるように、インターフェイスを実装することができます。

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

開発または簡単な方法をテストするとき、として、回復力のあるメカニズムを使用したくない場合は、標準の実装を使用することができます。 次のコードは、省略可能なケースとして、標準 HttpClient の実装できるようにする要求の認証トークンを使用を示します。

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

同様、別のクラスが使用する回復力のあるメカニズムを実装するポリーを使用してコードを興味深い実装が、次の例では、指数バックオフによる再試行です。

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

ポリーでの再試行、指数バックオフ構成、およびエラーの記録など、HTTP 例外がある場合に実行されるアクションの数と再試行ポリシーを定義します。 ここはしようとする、指定された回数、IoC コンテナー内の型を登録するときに、ポリシーを設定します。 指数バックオフ構成のため、コードが、HttpRequest 例外を検出するたびに、Http 要求を再試行ポリシーの構成方法によっては指数関数的に増加するまでの時間が待機した後にします。

重要なメソッドです HttpInvoker、ため、このユーティリティ クラス全体での HTTP 要求。 メソッドが HTTP 要求が内部でが実行される\_policyWrapper.ExecuteAsync で、再試行ポリシーを考慮します。

EShopOnContainers でポリシーを指定するポリーから次のコードのように、IoC コンテナーの種類を登録するときに、 [MVC web アプリケーション、startup.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Web/WebMVC/Startup.cs)クラスです。

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

サービスでの TCP 接続を効率的に使用できるように、一時的なものとしての代わりにシングルトンとして IHttpClient オブジェクトがインスタンス化に注意してください、[ソケットを使用して問題](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)は行われません。

回復性に関する重要な点が CreateResilientHttpClient メソッドで ResilientHttpClientFactory 内ポリー WaitAndRetryAsync ポリシーを適用すること、次のコードに示すように。

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
[前](implement-custom-http-call-retries-exponential-backoff.md) [次へ] (実装の回線のブレーカー-pattern.md)

---
title: 指数のバックオフを含むカスタムの HTTP 呼び出しの再試行を実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 指数のバックオフを含むカスタムの HTTP 呼び出しの再試行を実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 10751bb74ed648839fabec67ff7a71e458fb2a44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574947"
---
# <a name="implementing-custom-http-call-retries-with-exponential-backoff"></a><span data-ttu-id="f68f9-103">指数のバックオフを含むカスタムの HTTP 呼び出しの再試行を実装する</span><span class="sxs-lookup"><span data-stu-id="f68f9-103">Implementing custom HTTP call retries with exponential backoff</span></span>

<span data-ttu-id="f68f9-104">回復力のあるマイクロサービスを作成するには、考えられる HTTP 障害シナリオに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68f9-104">In order to create resilient microservices, you need to handle possible HTTP failure scenarios.</span></span> <span data-ttu-id="f68f9-105">そのために、指数バックオフによる再試行の実装を独自に作成することが可能です。</span><span class="sxs-lookup"><span data-stu-id="f68f9-105">For that purpose, you could create your own implementation of retries with exponential backoff.</span></span>

<span data-ttu-id="f68f9-106">指数バックオフでは、テンポラル リソースの非可用性を処理することに加えて、クラウド プロバイダーが使用状況のオーバー ロードを防ぐためにリソースの可用性を調整する場合があるということも考慮に入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68f9-106">In addition to handling temporal resource unavailability, the exponential backoff also needs to take into account that the cloud provider might throttle availability of resources to prevent usage overload.</span></span> <span data-ttu-id="f68f9-107">たとえば、過剰な接続要求を高い頻度で作成した場合、クラウド プロバイダーがこれをサービス拒否攻撃 ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) 攻撃と見なす場合があります。</span><span class="sxs-lookup"><span data-stu-id="f68f9-107">For example, creating too many connection requests very quickly might be viewed as a Denial of Service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) attack by the cloud provider.</span></span> <span data-ttu-id="f68f9-108">したがって、容量のしきい値に達した場合に接続要求を縮小するメカニズムを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f68f9-108">As a result, you need to provide a mechanism to scale back connection requests when a capacity threshold has been encountered.</span></span>

<span data-ttu-id="f68f9-109">最初の考察として、[RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260) にあるような指数バックオフ用のユーティリティ クラスを使用した独自のコードに加えて、次に示すようなコード ([GitHub リポジトリ](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)でも提供されています) を実装することも可能です。</span><span class="sxs-lookup"><span data-stu-id="f68f9-109">As an initial exploration, you could implement your own code with a utility class for exponential backoff as in [RetryWithExponentialBackoff.cs](https://gist.github.com/CESARDELATORRE/6d7f647b29e55fdc219ee1fd2babb260), plus code like the following (which is also available on a [GitHub repo](https://gist.github.com/CESARDELATORRE/d80c6423a1aebaffaf387469f5194f5b)).</span></span>

```csharp
public sealed class RetryWithExponentialBackoff
{
    private readonly int maxRetries, delayMilliseconds, maxDelayMilliseconds;

    public RetryWithExponentialBackoff(int maxRetries = 50,
        int delayMilliseconds = 200,
        int maxDelayMilliseconds = 2000)
    {
        this.maxRetries = maxRetries;
        this.delayMilliseconds = delayMilliseconds;
        this.maxDelayMilliseconds = maxDelayMilliseconds;
    }

    public async Task RunAsync(Func<Task> func)
    {
        ExponentialBackoff backoff = new ExponentialBackoff(this.maxRetries,
            this.delayMilliseconds,
            this.maxDelayMilliseconds);
        retry:
        try
        {
            await func();
        }
        catch (Exception ex) when (ex is TimeoutException ||
            ex is System.Net.Http.HttpRequestException)
        {
            Debug.WriteLine("Exception raised is: " +
                ex.GetType().ToString() +
                " –Message: " + ex.Message +
                " -- Inner Message: " +
                ex.InnerException.Message);
            await backoff.Delay();
            goto retry;
        }
    }
}

public struct ExponentialBackoff
{
    private readonly int m_maxRetries, m_delayMilliseconds, m_maxDelayMilliseconds;
    private int m_retries, m_pow;

    public ExponentialBackoff(int maxRetries, int delayMilliseconds,
        int maxDelayMilliseconds)
    {
        m_maxRetries = maxRetries;
        m_delayMilliseconds = delayMilliseconds;
        m_maxDelayMilliseconds = maxDelayMilliseconds;
        m_retries = 0;
        m_pow = 1;
    }

    public Task Delay()
    {
        if (m_retries == m_maxRetries)
        {
            throw new TimeoutException("Max retry attempts exceeded.");
        }
        ++m_retries;
        if (m_retries < 31)
        {
            m_pow = m_pow << 1; // m_pow = Pow(2, m_retries - 1)
        }
        int delay = Math.Min(m_delayMilliseconds * (m_pow - 1) / 2,
            m_maxDelayMilliseconds);
        return Task.Delay(delay);
    }
}
```

<span data-ttu-id="f68f9-110">クライアント C\# アプリケーション (別の Web API クライアント マイクロサービス、ASP.NET MVC アプリケーション、または C\# Xamarin アプリケーション) でこのコードを使用することは簡単です。</span><span class="sxs-lookup"><span data-stu-id="f68f9-110">Using this code in a client C\# application (another Web API client microservice, an ASP.NET MVC application, or even a C\# Xamarin application) is straightforward.</span></span> <span data-ttu-id="f68f9-111">次の例は、HttpClient クラスの使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="f68f9-111">The following example shows how, using the HttpClient class.</span></span>

```csharp
public async Task<Catalog> GetCatalogItems(int page,int take, int? brand, int? type)
{
    _apiClient = new HttpClient();
    var itemsQs = $"items?pageIndex={page}&pageSize={take}";
    var filterQs = "";
    var catalogUrl = $"{_remoteServiceBaseUrl}items{filterQs}?pageIndex={page}&pageSize={take}";
    var dataString = "";
    //
    // Using HttpClient with Retry and Exponential Backoff
    //
    var retry = new RetryWithExponentialBackoff();
    await retry.RunAsync(async () =>
    {
        // work with HttpClient call
        dataString = await _apiClient.GetStringAsync(catalogUrl);
    });
    return JsonConvert.DeserializeObject<Catalog>(dataString);
}
```

<span data-ttu-id="f68f9-112">ただし、このコードは概念の実証用にのみ使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f68f9-112">However, this code is suitable only as a proof of concept.</span></span> <span data-ttu-id="f68f9-113">次のトピックでは、より高度で実績のあるライブラリの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f68f9-113">The next topic explains how to use more sophisticated and proven libraries.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f68f9-114">[Previous] (implement-resilient-entity-framework-core-sql-connections.md) [Next] (implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="f68f9-114">[Previous] (implement-resilient-entity-framework-core-sql-connections.md) [Next] (implement-http-call-retries-exponential-backoff-polly.md)</span></span>

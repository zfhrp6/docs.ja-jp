---
title: "正常性の監視"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |正常性の監視"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a><span data-ttu-id="0e4ae-104">正常性の監視</span><span class="sxs-lookup"><span data-stu-id="0e4ae-104">Health monitoring</span></span>

<span data-ttu-id="0e4ae-105">正常性の監視と、ほぼリアルタイムのコンテナーと microservices 状態情報を許可できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="0e4ae-106">正常性監視と microservices の動作のさまざまな側面に重要な orchestrators が後で説明したようのフェーズで部分的なアプリケーションのアップグレードを実行時に、特に重要です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="0e4ae-107">Microservices ベースのアプリケーションがハートビートを多くの場合、使用または、パフォーマンス モニター、スケジューラ、および orchestrators、さまざまなサービスの追跡を有効にする正常性を確認します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="0e4ae-108">オンデマンドまたはスケジュールで、サービスは、「私はアライブ」信号のいくつかの並べ替えを送信できない場合、アプリケーションは、展開するときに更新プログラム、単に遅すぎます障害を検出し、障害が最終的に大規模な停止を連鎖を停止できませんか可能性がありますリスクに直面する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="0e4ae-109">モデルでは、通常、サービスが、その状態に関するレポートを送信し、その情報が集約され、アプリケーションの正常性の状態の全体的な表示をします。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="0e4ae-110">Orchestrator を使用している場合は、クラスターが適切に操作できるように、orchestrator のクラスターに正常性情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="0e4ae-111">アプリケーション用にカスタマイズされている高品質の正常性レポートに投資する場合は、検出しより簡単に実行中のアプリケーションの問題を修正できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="0e4ae-112">ASP.NET Core services での確認の正常性を実装します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="0e4ae-113">ASP.NET Core マイクロ サービスまたは web アプリケーションを開発する場合は、ASP.NET チームから HealthChecks をという名前のライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-113">When developing an ASP.NET Core microservice or web application, you can use a library named HealthChecks from the ASP.NET team.</span></span> <span data-ttu-id="0e4ae-114">(、2017 年 1 月の時点で、初期リリースは GitHub で利用可能) です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-114">(As of May 2017, an early release is available on GitHub).</span></span>

<span data-ttu-id="0e4ae-115">このライブラリは使いやすいあり機能 (SQL Server データベースやリモート API) など、アプリケーションに必要な特定の外部リソースが正常に機能していることを検証することができます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="0e4ae-116">このライブラリを使用する場合は、後で説明して、リソースが正常である意味も決定できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="0e4ae-117">このライブラリを使用するためには、まず、microservices でライブラリを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="0e4ae-118">次に、正常性レポートのクエリを実行するフロント エンド アプリケーションが必要です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="0e4ae-119">フロント エンド アプリケーションにはカスタムのレポート アプリケーションがあるか、それ自体を orchestrator それに対処できる可能性がありますを稼働状態にします。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="0e4ae-120">バック エンド ASP.NET microservices HealthChecks ライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="0e4ae-121">EShopOnContainers サンプル アプリケーションで HealthChecks ライブラリを使用する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="0e4ae-122">を開始するには、各マイクロ サービスの正常な状態の構成要素を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="0e4ae-123">サンプル アプリケーションでは、microservices はマイクロ サービス API が HTTP およびその関連する SQL Server データベースが使用可能なも使用してアクセスできる場合は正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="0e4ae-124">今後、NuGet パッケージとして HealthChecks ライブラリをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="0e4ae-125">このドキュメントの作成時点では、ダウンロードし、ソリューションの一部として、コードをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="0e4ae-126">Https://github.com/aspnet/HealthChecks で利用可能なコードを複製し、次のフォルダーをソリューションにコピーします。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-126">Clone the code available at https://github.com/aspnet/HealthChecks and copy the following folders to your solution.</span></span>

  - <span data-ttu-id="0e4ae-127">src/共通</span><span class="sxs-lookup"><span data-stu-id="0e4ae-127">src/common</span></span>
  - <span data-ttu-id="0e4ae-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="0e4ae-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="0e4ae-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="0e4ae-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="0e4ae-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="0e4ae-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="0e4ae-131">Azure (Microsoft.Extensions.HealthChecks.AzureStorage) が eShopOnContainers のこのバージョンでは、Azure では、すべての依存関係はありませんのでのような追加のチェックを使用することも、する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="0e4ae-132">EShopOnContainers は ASP.NET Core に基づいているために、ASP.NET の正常性チェックは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="0e4ae-133">図 10-6 は、Visual Studio で、任意 microservices を基盤として使用する準備ができて HealthChecks ライブラリを示します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="0e4ae-134">**図 10-6**です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-134">**Figure 10-6**.</span></span> <span data-ttu-id="0e4ae-135">Visual Studio ソリューションでは ASP.NET Core HealthChecks ライブラリのソース コード</span><span class="sxs-lookup"><span data-stu-id="0e4ae-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="0e4ae-136">以前導入際に、マイクロ サービスの各プロジェクトでは、まず次の 3 つの HealthChecks ライブラリへの参照を追加を開始します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="0e4ae-137">その後、そのマイクロ サービスで実行する正常性チェックのアクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="0e4ae-138">これらのアクションは、基本的に他の microservices (HttpUrlCheck) またはデータベースへの依存関係 (現在 SqlCheck\* SQL Server データベース用)。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="0e4ae-139">各 ASP.NET マイクロ サービスまたは ASP.NET web アプリケーションのスタートアップ クラス内でアクションを追加するとします。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="0e4ae-140">AddHealthCheck の 1 つの方法として、すべての HTTP またはデータベースの依存関係を追加することで、各サービスまたは web アプリケーションを構成してください。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="0e4ae-141">たとえば、eShopOnContainers から MVC web アプリケーションは、多くのサービスに依存、ために、正常性チェックに追加されたいくつかの AddCheck メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="0e4ae-142">たとえば、次のコードにカタログ マイクロ サービスが SQL Server データベースの依存関係を追加する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

<span data-ttu-id="0e4ae-143">ただし、eShopOnContainers の MVC web アプリケーションでは、microservices の残りの部分で複数の依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="0e4ae-144">そのため、各マイクロ サービスの 1 つの AddUrlCheck メソッドを呼び出す例を次に示すように。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

<span data-ttu-id="0e4ae-145">したがって、すべてのチェックがも異常な状態になるまで、マイクロ サービスは「正常」の状態を提供しません。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="0e4ae-146">場合は、マイクロ サービスがあるないと、依存関係サービスまたは SQL Server、Healthy("Ok") チェックを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="0e4ae-147">次のコードは eShopOnContainers basket.api マイクロ サービスです。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="0e4ae-148">(バスケット マイクロ サービスが Redis cache を使用しますが、ライブラリでは、Redis の正常性チェックのプロバイダーがまだ含まれません)。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="0e4ae-149">正常性チェックのエンドポイントを公開するサービスまたは web アプリケーションの場合、UseHealthChecks を有効にする必要がある (\[*url\_の\_ヘルス\_チェック*\]) 拡張機能メソッド。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="0e4ae-150">このメソッドが、ASP.NET Core サービスまたは web アプリケーションの直後に次のコードに示すように UseKestrel Program クラスのメイン メソッド内でレベル、WebHostBuilder には移動します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

<span data-ttu-id="0e4ae-151">プロセスの次のように動作します。 各マイクロ サービスを公開エンドポイント/hc です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="0e4ae-152">ASP.NET Core ミドルウェア HealthChecks ライブラリによっては、そのエンドポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="0e4ae-153">そのエンドポイントが呼び出されたときに、スタートアップ クラスで AddHealthChecks メソッドで構成されているすべての正常性チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="0e4ae-154">UseHealthChecks メソッドでは、ポートまたはパスが必要です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="0e4ae-155">ポートまたはパスを使用して、サービスのヘルス状態を確認するエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="0e4ae-156">たとえば、カタログ マイクロ サービスは、パス/hc を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="0e4ae-157">正常性チェック応答のキャッシュ</span><span class="sxs-lookup"><span data-stu-id="0e4ae-157">Caching health check responses</span></span>

<span data-ttu-id="0e4ae-158">サービスで、サービス拒否 (DoS) が発生しないか、単にたくないリソースをチェックして、サービスのパフォーマンスに影響するので頻度が高すぎる、制御を返すをキャッシュして各正常性チェックのキャッシュの存続期間を構成します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="0e4ae-159">既定では、キャッシュの存続期間が内部的には、5 分間に設定されているが、次のコードのように各正常性チェックでそのキャッシュの存続期間を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="0e4ae-160">正常性の状態に関するレポートを microservices のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="0e4ae-161">」の説明に従って、Docker で、マイクロ サービスが実行されている正常性チェックを構成すると正常な状態である場合、ブラウザーから直接確認することができます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="0e4ae-162">(これは必要 localhost、または外部の Docker ホスト IP を通じて、コンテナーにアクセスできるように Docker ホストからコンテナーのポートを発行することです。)図 10-7 では、対応する応答をブラウザーで要求を示します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="0e4ae-163">**図 10-7**です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-163">**Figure 10-7**.</span></span> <span data-ttu-id="0e4ae-164">ブラウザーから 1 つのサービスのヘルス状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="0e4ae-165">そのテストで確認できます (ポート 5101 で実行されている) catalog.api マイクロ サービスが正常である JSON 内の HTTP ステータス 200 およびステータス情報を返します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="0e4ae-166">内部的には、サービスもオンになっている、SQL Server データベースの依存関係の正常性と正常性チェックが正常であるとそれ自体に報告することも意味します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="0e4ae-167">取り組むを使用します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-167">Using watchdogs</span></span>

<span data-ttu-id="0e4ae-168">ウォッチドッグは、正常性を監視したり、以前に導入された HealthChecks ライブラリとクエリを実行してサービス、および、microservices について正常性のレポート間で負荷をできる個別のサービスです。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="0e4ae-169">これにより、1 つのサービスのビューに基づいたが検出されないエラーを防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="0e4ae-170">取り組むでは、ユーザーの介入なしの既知の条件の修復アクションを実行できるコードをホストするに適してもいます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="0e4ae-171">EShopOnContainers サンプルには、図 10-8 に示すようにサンプル正常性チェック レポートを表示する web ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="0e4ae-172">これは、割り当てることも、最も単純な監視はすべてが示される eShopOnContainers microservices と web アプリケーションの状態。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="0e4ae-173">通常、ウォッチドッグではもアクションを実行して、異常な状態を検出するとします。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="0e4ae-174">**図 10-8**です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-174">**Figure 10-8**.</span></span> <span data-ttu-id="0e4ae-175">EShopOnContainers でサンプルの正常性チェック レポート</span><span class="sxs-lookup"><span data-stu-id="0e4ae-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="0e4ae-176">要約するは、ASP.NET Core HealthChecks ライブラリの ASP.NET ミドルウェアは、各マイクロ サービスを 1 つの正常性チェックのエンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="0e4ae-177">内に定義されているすべての正常性チェックの実行、それらすべてのチェックによって全体的なヘルス状態を返します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="0e4ae-178">HealthChecks ライブラリは、今後の外部のリソースの新しい正常性チェックを使用して拡張です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="0e4ae-179">たとえば、後で、ライブラリを持つ Redis cache のおよびその他のデータベースの正常性チェックいく予定です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="0e4ae-180">ライブラリにより、複数のサービスまたはアプリケーションの依存で報告される正常性と、それらの正常性チェックに基づいた操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="0e4ae-181">Orchestrators を使用するときの正常性チェック</span><span class="sxs-lookup"><span data-stu-id="0e4ae-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="0e4ae-182">Microservices の可用性を監視するには、Docker Swarm、Kubernetes、Service Fabric など orchestrators は定期的に、microservices をテストする要求を送信することによって正常性チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="0e4ae-183">ときに、orchestrator では、サービス/コンテナーが異常で、そのインスタンスへの要求のルーティングを停止することを決定します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="0e4ae-184">通常、そのコンテナーの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="0e4ae-185">たとえば、ほとんど orchestrators はダウンタイムの展開を管理するのに正常性チェックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="0e4ae-186">正常な状態にサービス/コンテナーの変更の状態は場合にのみ、orchestrator は、サービス/コンテナー インスタンスにトラフィックのルーティングを開始します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="0e4ae-187">正常性の監視は、orchestrator は、アプリケーションのアップグレードを実行するときに特に重要です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="0e4ae-188">フェーズでサービスを更新する (Azure Service Fabric) のようないくつか orchestrators: 5 分ごとのアプリケーションのアップグレードのサーフェスをクラスターを更新したりなどです。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="0e4ae-189">同時にアップグレードされるノードのセットと呼びます、*アップグレード ドメイン*です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="0e4ae-190">各アップグレード ドメインは、アップグレードされており、ユーザーには後、アップグレード ドメインは、展開が次のアップグレード ドメインに移動する前に正常性チェックを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="0e4ae-191">サービスのヘルス状態の別の要素は、サービスからメトリックを報告しています。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="0e4ae-192">これは、Service Fabric のように、いくつかの orchestrators の正常性モデルの高度な機能です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="0e4ae-193">メトリックは、リソース使用率のバランスをとるに使用されるため、orchestrator を使用する場合に重要です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="0e4ae-194">メトリックは、システム正常性の指標も指定できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="0e4ae-195">たとえばを持つ多く microservices は、アプリケーションがある可能性があり、各インスタンスは、要求/秒 (RPS) メトリックを報告します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="0e4ae-196">1 つのサービスが別のサービスよりも多くのリソース (メモリやプロセッサなど) を使用している場合、orchestrator でした内を移動のサービス インスタンス クラスター リソースの使用率を維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="0e4ae-197">Azure Service Fabric を使用している場合、によって提供される独自[正常性の監視モデル](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)、単純な正常性チェックをより高度であります。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="0e4ae-198">先進的な監視: 視覚エフェクト、分析、およびアラート</span><span class="sxs-lookup"><span data-stu-id="0e4ae-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="0e4ae-199">監視の最後の部分には、レポート サービスのパフォーマンスの作成と、問題が検出されたとき、警告、イベント ストリームを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="0e4ae-200">監視のこの面のさまざまなソリューションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="0e4ae-201">サービスの状態を示す単純なカスタム アプリケーションを使用すると、カスタムのページのように紹介説明しました[ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks)です。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="0e4ae-202">または Azure Application Insights と Operations Management Suite などのより高度なツールを使用して、イベントのストリームに基づき、アラートを生成します。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="0e4ae-203">最後に、すべてのイベント ストリームを格納していた場合そのデータを視覚化する Microsoft Power BI または Kibana Splunk などのサード パーティのソリューションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e4ae-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0e4ae-204">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0e4ae-204">Additional resources</span></span>

-   <span data-ttu-id="0e4ae-205">**ASP.NET Core HealthChecks** (初期リリース) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="0e4ae-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="0e4ae-206">**Service Fabric の正常性の監視の概要**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="0e4ae-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="0e4ae-207">**Azure の Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="0e4ae-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="0e4ae-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="0e4ae-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0e4ae-209">[前](実装の回線のブレーカー-pattern.md) [次へ] (../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="0e4ae-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>

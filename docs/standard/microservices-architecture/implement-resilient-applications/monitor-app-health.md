---
title: "正常性の監視"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 正常性の監視"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76821e27613335609527b867a6b94dac551f6235
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="health-monitoring"></a><span data-ttu-id="2f8f8-104">正常性の監視</span><span class="sxs-lookup"><span data-stu-id="2f8f8-104">Health monitoring</span></span>

<span data-ttu-id="2f8f8-105">正常性を監視することで、コンテナーとマイクロサービスの状態に関する情報をほぼリアルタイムに得ることができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="2f8f8-106">正常性の監視はマイクロサービス運用の複数の側面において不可欠であり、オーケストレーターで段階的に部分的なアプリケーションのアップグレードを行う際に特に重要です。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="2f8f8-107">マイクロサービス ベースのアプリケーションでは、多くの場合、ハートビートまたは正常性チェックを使用して、パフォーマンス モニター、スケジューラー、およびオーケストレーターで多数のサービスを追跡できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="2f8f8-108">サービスが必要に応じて、またはスケジュールに従って、ある種の "アライブ" シグナルを送信できない場合、更新プログラムの展開時にアプリケーションがリスクに直面する可能性があります。あるいは、単に障害の検出が遅すぎたために障害の連鎖を防ぐことができず、最終的に大規模な停止が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="2f8f8-109">標準的なモデルでは、サービスは状態に関するレポートを送信し、その情報が集約され、アプリケーションの正常性状態の概要が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="2f8f8-110">オーケストレーターを使用する場合は、オーケストレーターのクラスターに正常性情報を提供することができるため、クラスターは適切に機能できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="2f8f8-111">アプリケーション用にカスタマイズされている高品質の正常性レポートに投資する場合、実行中のアプリケーションの問題をはるかに簡単に検出して修正することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="2f8f8-112">ASP.NET Core サービスでの正常性チェックの実装</span><span class="sxs-lookup"><span data-stu-id="2f8f8-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="2f8f8-113">ASP.NET Core マイクロサービスまたは Web アプリケーションを開発する場合、ASP.NET チームの `HealthChecks` という名前のライブラリを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-113">When developing an ASP.NET Core microservice or web application, you can use a library named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="2f8f8-114">早期リリースはこの [GitHub リポジトリ](https://github.com/dotnet-architecture/HealthChecks)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-114">Early release is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="2f8f8-115">このライブラリは使いやすく、アプリケーションに必要な特定の外部リソース (SQL Server データベースやリモート API など) が正しく動作していることを検証できる機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="2f8f8-116">このライブラリを使用すれば、リソースが正常であるかどうかを判断することもできます。これについては後で説明します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="2f8f8-117">このライブラリを使用するには、まず、マイクロサービスでライブラリを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="2f8f8-118">次に、正常性レポートのクエリを実行するフロント エンド アプリケーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="2f8f8-119">このフロント エンド アプリケーションはカスタム レポート アプリケーションである場合があります。また、正常性状態に応じて対応できるオーケストレーター自体である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="2f8f8-120">バック エンド ASP.NET マイクロサービスでの HealthChecks ライブラリの使用</span><span class="sxs-lookup"><span data-stu-id="2f8f8-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="2f8f8-121">EShopOnContainers サンプル アプリケーションでの HealthChecks ライブラリの使用方法を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="2f8f8-122">開始するには、各マイクロサービスの正常性状態の構成要素を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="2f8f8-123">サンプル アプリケーションでは、マイクロサービス API が HTTP 経由でアクセス可能である場合と、それに関連する SQL Server データベースも使用可能である場合、マイクロサービスは正常な状態です。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="2f8f8-124">将来的には、HealthChecks ライブラリを NuGet パッケージとしてインストールできるようになります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="2f8f8-125">ただし、このドキュメントの作成時点では、ソリューションの一部として、コードをダウンロードしてコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="2f8f8-126">https://github.com/dotnet-architecture/HealthChecks から入手可能なコードを複製し、次のフォルダーをソリューションにコピーします。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-126">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="2f8f8-127">src/common</span><span class="sxs-lookup"><span data-stu-id="2f8f8-127">src/common</span></span>
  - <span data-ttu-id="2f8f8-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="2f8f8-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="2f8f8-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="2f8f8-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="2f8f8-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="2f8f8-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="2f8f8-131">Azure の場合 (Microsoft.Extensions.HealthChecks.AzureStorage) のように追加チェックを使用することもできますが、このバージョンの eShopOnContainers には Azure に対する依存関係がないため、必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="2f8f8-132">EShopOnContainers は ASP.NET Core に基づいているため、ASP.NET の正常性チェックは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="2f8f8-133">図 10-6 には、マイクロサービスで構成要素として使用する準備ができている、Visual Studio の HealthChecks ライブラリが示されています。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="2f8f8-134">**図 10-6**. </span><span class="sxs-lookup"><span data-stu-id="2f8f8-134">**Figure 10-6**.</span></span> <span data-ttu-id="2f8f8-135">Visual Studio ソリューションの ASP.NET Core HealthChecks ライブラリ ソース コード</span><span class="sxs-lookup"><span data-stu-id="2f8f8-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="2f8f8-136">前述のとおり、各マイクロサービス プロジェクトでまず行うことは、3 つの HealthChecks ライブラリへの参照を追加することです。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="2f8f8-137">その後、そのマイクロサービスで実行する正常性チェックのアクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="2f8f8-138">これらのアクションは基本的に他のマイクロサービス (HttpUrlCheck) またはデータベース (現時点では SQL Server データベースの SqlCheck\*) に依存します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="2f8f8-139">各 ASP.NET マイクロサービスまたは ASP.NET Web アプリケーションのスタートアップ クラス内でアクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="2f8f8-140">各サービスまたは Web アプリケーションは、すべての HTTP またはデータベースの依存関係を 1 つの AddHealthCheck メソッドとして追加することで構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="2f8f8-141">たとえば、eShopOnContainers の MVC Web アプリケーションは多くのサービスに依存するため、正常性チェックにはいくつかの AddCheck メソッドが追加されています。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="2f8f8-142">たとえば、次のコードでは、カタログ マイクロサービスが SQL Server データベースに対する依存関係をどのように追加するかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="2f8f8-143">ただし、eShopOnContainers の MVC Web アプリケーションには、残りのマイクロサービスに対する複数の依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="2f8f8-144">そのため、次の例に示すように、マイクロサービスごとに 1 つの AddUrlCheck メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="2f8f8-145">したがって、そのすべてのチェックでも正常であると判断されるまで、マイクロサービスでは "正常" 状態と示されません。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="2f8f8-146">マイクロサービスにサービスまたは SQL Server に対する依存関係がない場合は、Healthy("Ok") チェックを追加するだけ済みます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="2f8f8-147">次のコードは eShopOnContainers basket.api マイクロサービスからのものです </span><span class="sxs-lookup"><span data-stu-id="2f8f8-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="2f8f8-148">(バスケット マイクロサービスでは Redis Cache を使用しますが、ライブラリにはまだ Redis 正常性チェック プロバイダーは含まれていません)。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="2f8f8-149">サービスまたは Web アプリケーションで正常性チェック エンドポイントを公開するには、UseHealthChecks(\[*url\_for\_health\_checks*\]) 拡張メソッドを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="2f8f8-150">このメソッドは、以下のコードに示すように、ASP.NET Core サービスまたは Web アプリケーションの Program クラスのメイン メソッドの WebHostBuilder レベルで UseKestrel の直後に配置されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="2f8f8-151">プロセスのしくみは次のとおりです。まず、各マイクロサービスがエンドポイント /hc を公開します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="2f8f8-152">そのエンドポイントは、HealthChecks ライブラリの ASP.NET Core ミドルウェアによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="2f8f8-153">そのエンドポイントが呼び出されたときに、スタートアップ クラスの AddHealthChecks メソッドで構成されているすべての正常性チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="2f8f8-154">UseHealthChecks メソッドにはポートまたはパスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="2f8f8-155">そのポートまたはパスはエンドポイントであり、サービスの正常性状態を確認するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="2f8f8-156">たとえば、カタログ マイクロサービスではパス /hc を使用します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="2f8f8-157">正常性チェック応答のキャッシュ</span><span class="sxs-lookup"><span data-stu-id="2f8f8-157">Caching health check responses</span></span>

<span data-ttu-id="2f8f8-158">サービスでサービス拒否攻撃 (DoS) が発生しないようにする場合や、リソースを頻繁に確認しすぎてサービスのパフォーマンスが影響を受けることのないようにするだけの場合は、戻り値をキャッシュし、各正常性チェックのキャッシュ期間を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="2f8f8-159">既定では、キャッシュ期間は内部的に 5 分に設定されますが、次のコードのように、各正常性チェックでそのキャッシュ期間を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="2f8f8-160">マイクロサービスでクエリを実行してその正常性状態についてレポートする</span><span class="sxs-lookup"><span data-stu-id="2f8f8-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="2f8f8-161">説明に従って正常性チェックを構成し、マイクロサービスを Docker で実行した後、正常かどうかをブラウザーから直接確認することができます </span><span class="sxs-lookup"><span data-stu-id="2f8f8-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="2f8f8-162">(そのためには、Docker ホスト外のコンテナー ポートを公開し、localhost または外部の Docker ホスト IP を通じてコンテナーにアクセスできるようにする必要があります)。図 10-7 には、ブラウザーでの要求とそれに対応する応答が示されています。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="2f8f8-163">**図 10-7**. </span><span class="sxs-lookup"><span data-stu-id="2f8f8-163">**Figure 10-7**.</span></span> <span data-ttu-id="2f8f8-164">ブラウザーからの単一サービスの正常性状態の確認</span><span class="sxs-lookup"><span data-stu-id="2f8f8-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="2f8f8-165">このテストでは、catalog.api マイクロサービス (ポート 5101 で実行されている) が正常であり、JSON で HTTP ステータス 200 とステータス情報が返されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="2f8f8-166">これは、内部的にサービスが SQL Server データベースの依存関係の正常性も確認し、その正常性チェック自体が正常とレポートされたことも意味します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="2f8f8-167">ウォッチドッグの使用</span><span class="sxs-lookup"><span data-stu-id="2f8f8-167">Using watchdogs</span></span>

<span data-ttu-id="2f8f8-168">ウォッチドッグは、サービス間の正常性と負荷を監視し、前述の HealthChecks ライブラリを使用してクエリを実行することでマイクロサービスに関する正常性をレポートできる別個のサービスです。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="2f8f8-169">これは、単一サービスのビューに基づいて検出されないエラーを防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="2f8f8-170">また、ウォッチドッグは、ユーザーの介入なしで既知の状態に応じて修復アクションを実行できるコードをホストする場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="2f8f8-171">eShopOnContainers サンプルには、図 10-8 に示すように、サンプルの正常性チェック レポートを表示する Web ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="2f8f8-172">これは、eShopOnContainers でマイクロサービスと Web アプリケーションの状態を表示するだけであるため、使用可能な最も単純なウォッチドッグです。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="2f8f8-173">通常、ウォッチドッグは異常状態の検出時にもアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="2f8f8-174">**図 10-8**. </span><span class="sxs-lookup"><span data-stu-id="2f8f8-174">**Figure 10-8**.</span></span> <span data-ttu-id="2f8f8-175">eShopOnContainers のサンプルの正常性チェック レポート</span><span class="sxs-lookup"><span data-stu-id="2f8f8-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="2f8f8-176">つまり、ASP.NET Core HealthChecks ライブラリの ASP.NET ミドルウェアでは、マイクロサービスごとに 1 つの正常性チェック エンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="2f8f8-177">これにより、定義されているすべての正常性チェックが実行され、これらすべてのチェックに応じて、全体的な正常性状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="2f8f8-178">HealthChecks ライブラリは、今後の外部リソースの新しい正常性チェックにより拡張可能です。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="2f8f8-179">たとえば、今後、ライブラリに Redis Cache や他のデータベースの正常性チェックが含まれることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="2f8f8-180">ライブラリでは複数のサービスまたはアプリケーションの依存関係での正常性レポートが可能であるため、これらの正常性チェックに基づいてアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="2f8f8-181">オーケストレーターを使用する場合の正常性チェック</span><span class="sxs-lookup"><span data-stu-id="2f8f8-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="2f8f8-182">マイクロサービスの可用性を監視するために、Docker Swarm、Kubernetes、Service Fabric などのオーケストレーターではマイクロサービスのテスト要求を送信して、定期的に正常性チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="2f8f8-183">オーケストレーターでサービス/コンテナーが異常であると判断された場合、そのインスタンスへの要求のルーティングが停止します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="2f8f8-184">通常は、そのコンテナーの新しいインスタンスも作成されます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="2f8f8-185">たとえば、ほとんどのオーケストレーターでは、ダウンタイムなしの展開を管理するために正常性チェックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="2f8f8-186">サービス/コンテナーの状態が正常に変わった場合にのみ、オーケストレーターはサービス/コンテナー インスタンスへのトラフィックのルーティングを開始します。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="2f8f8-187">正常性の監視は、オーケストレーターがアプリケーションのアップグレードを実行する場合に特に重要です。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="2f8f8-188">いくつかのオーケストレーター (Azure Service Fabric など) ではサービスを段階的に更新します。たとえば、アプリケーションのアップグレードごとに 5 分の 1 のクラスター サーフェスを更新する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="2f8f8-189">同時にアップグレードされるノード セットを*アップグレード ドメイン* といいます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="2f8f8-190">各アップグレード ドメインがアップグレードされ、ユーザーが使用できるようになったら、そのアップグレード ドメインは、展開が次のアップグレード ドメインに移る前に正常性チェックを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="2f8f8-191">サービスの正常性のもう 1 つの側面は、サービスからのメトリックのレポートです。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="2f8f8-192">これは、Service Fabric などの一部のオーケストレーターの正常性モデルの高度な機能です。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="2f8f8-193">メトリックは、リソース使用量のバランスをとるために使用されるため、オーケストレーターの使用時に重要になります。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="2f8f8-194">メトリックをシステム正常性のインジケーターにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="2f8f8-195">たとえば、アプリケーションに多くのマイクロサービスがあり、各インスタンスで要求/秒 (RPS) メトリックをレポートするとします。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="2f8f8-196">1 つのサービスが別のサービスより多くのリソース (メモリやプロセッサなど) を使用している場合、オーケストレーターはクラスター内でサービス インスタンスを移動して、リソース使用率を均一に保つことができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="2f8f8-197">Azure Service Fabric を使用している場合は、単純な正常性チェックより高度な独自の[正常性の監視モデル](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)が提供されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="2f8f8-198">高度な監視: 視覚化、分析、およびアラート</span><span class="sxs-lookup"><span data-stu-id="2f8f8-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="2f8f8-199">監視の最後の部分は、イベント ストリームの視覚化、サービス パフォーマンスのレポート、および問題の検出時のアラートです。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="2f8f8-200">監視のこの部分ではさまざまなソリューションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="2f8f8-201">[ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks) の説明の際に示したカスタム ページのように、サービス状態を示す単純なカスタム アプリケーションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="2f8f8-202">または Azure Application Insights や Operations Management Suite などのより高度なツールを使用して、イベントのストリームに基づき、アラートを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="2f8f8-203">最後に、すべてのイベント ストリームを格納していた場合、Microsoft Power BI、または Kibana や Splunk などのサードパーティのソリューションを使用して、データを視覚化することができます。</span><span class="sxs-lookup"><span data-stu-id="2f8f8-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2f8f8-204">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="2f8f8-204">Additional resources</span></span>

-   <span data-ttu-id="2f8f8-205">**ASP.NET Core HealthChecks** (初期リリース) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="2f8f8-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="2f8f8-206">**Service Fabric の正常性モニタリングの概要**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="2f8f8-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="2f8f8-207">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="2f8f8-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="2f8f8-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="2f8f8-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="2f8f8-209">[前へ] (implement-circuit-breaker-pattern.md) [次へ] (../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="2f8f8-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>

---
title: "ASP.NET Core サービスと web アプリのテスト"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |ASP.NET Core サービスと web アプリのテスト"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f756a679befee676db2bf6d402fd7e34b1621b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="e384a-104">ASP.NET Core サービスと web アプリのテスト</span><span class="sxs-lookup"><span data-stu-id="e384a-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="e384a-105">コント ローラーは、すべての ASP.NET Core API サービスと ASP.NET MVC Web アプリケーションの中央部分です。</span><span class="sxs-lookup"><span data-stu-id="e384a-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="e384a-106">そのため、アプリケーションの意図したとおりに動作する信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="e384a-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="e384a-107">自動テストは、この信頼を提供でき、実稼働環境に到達する前に、エラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="e384a-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="e384a-108">コント ローラーの有効または無効な入力に基づく動作をテストおよびテストの実行ビジネス操作の結果に基づいてコント ローラー応答する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e384a-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="e384a-109">ただし、microservices がこれらの種類のテストが必要です。</span><span class="sxs-lookup"><span data-stu-id="e384a-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="e384a-110">単体テストされます。</span><span class="sxs-lookup"><span data-stu-id="e384a-110">Unit tests.</span></span> <span data-ttu-id="e384a-111">これらは、アプリケーションの個々 のコンポーネントが期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="e384a-112">アサーションは、コンポーネントの API をテストします。</span><span class="sxs-lookup"><span data-stu-id="e384a-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="e384a-113">統合をテストします。</span><span class="sxs-lookup"><span data-stu-id="e384a-113">Integration tests.</span></span> <span data-ttu-id="e384a-114">これらは、コンポーネントの相互作用がデータベースと同様に外部成果物に対して期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="e384a-115">アサーションには、コンポーネントの API、UI、またはログ記録などのデータベースの I/O などの操作の副作用をテストできます。</span><span class="sxs-lookup"><span data-stu-id="e384a-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="e384a-116">各マイクロ サービス機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="e384a-116">Functional tests for each microservice.</span></span> <span data-ttu-id="e384a-117">これらは、ユーザーの観点から予想されるように、アプリケーションが動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="e384a-118">サービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="e384a-118">Service tests.</span></span> <span data-ttu-id="e384a-119">これらは、同時に複数のサービスのテストを含む、エンド ツー エンドのサービスのユース ケースがテストされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="e384a-120">この種類のテストでは、まず環境を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e384a-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="e384a-121">この場合、すること、サービスを開始します (たとえばを使用して docker-作成上)。</span><span class="sxs-lookup"><span data-stu-id="e384a-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="e384a-122">ASP.NET Core Web Api の実装の単体テスト</span><span class="sxs-lookup"><span data-stu-id="e384a-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="e384a-123">単体テストでは、そのインフラストラクチャとの依存関係から分離でのアプリケーションの一部のテストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e384a-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="e384a-124">ときに単体テストを行うコント ローラー ロジック、1 つのアクションのコンテンツだけメソッドをテスト、またはその依存関係や framework 自体の動作できません。</span><span class="sxs-lookup"><span data-stu-id="e384a-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="e384a-125">単体テストはコンポーネント間の対話で問題を検出できません-統合テストの目的はします。</span><span class="sxs-lookup"><span data-stu-id="e384a-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="e384a-126">ユニットとしてテスト コント ローラーのアクションをそれらの動作にのみ注目するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="e384a-127">コント ローラーの単体テストは、フィルター、ルーティング、またはモデル バインディングのようなものを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e384a-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="e384a-128">1 つだけのテストの重点を置いて、ため単体テストは一般に書き込む単純なおよび実行するクイックです。</span><span class="sxs-lookup"><span data-stu-id="e384a-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="e384a-129">多くのオーバーヘッドなし、適切に記述された一連の単体テストを頻繁に実行できます。</span><span class="sxs-lookup"><span data-stu-id="e384a-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="e384a-130">単体テストは、xUnit.net、MSTest、Moq、NUnit などのテスト フレームワークに基づく実装されます。</span><span class="sxs-lookup"><span data-stu-id="e384a-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="e384a-131">EShopOnContainers サンプル アプリケーションについては、XUnit を使用します。</span><span class="sxs-lookup"><span data-stu-id="e384a-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="e384a-132">C では、new キーワードを使用して直接、コント ローラー クラスのインスタンスを作成する Web API コント ローラーの単体テストを記述するときに\#テストはできる限り高速に実行するようにします。</span><span class="sxs-lookup"><span data-stu-id="e384a-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="e384a-133">次の例は、これを行う方法を使用する場合を示しています。 [XUnit](https://xunit.github.io/)テスト フレームワークとします。</span><span class="sxs-lookup"><span data-stu-id="e384a-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="e384a-134">統合と各マイクロ サービスの機能のテストを実装します。</span><span class="sxs-lookup"><span data-stu-id="e384a-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="e384a-135">前述のように、統合テストと機能のテストはさまざまな目的と目標があります。</span><span class="sxs-lookup"><span data-stu-id="e384a-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="e384a-136">ただし、ASP.NET Core コント ローラーをテストするときに両方を実装する方法と同様に、統合テストを重視してこのセクションの内容。</span><span class="sxs-lookup"><span data-stu-id="e384a-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="e384a-137">統合テスト組み立て時に、アプリケーションのコンポーネントが正しく動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="e384a-138">ASP.NET Core サポート統合が単体テスト フレームワークと、ネットワークのオーバーヘッドが要求を処理するために使用する組み込みのテストの web ホストを使用してテストします。</span><span class="sxs-lookup"><span data-stu-id="e384a-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="e384a-139">単体テストとは異なり統合テストには、データベース、ファイル システム、ネットワーク リソース、または web 要求と応答などのアプリケーションのインフラストラクチャの問題が頻繁に含まれます。</span><span class="sxs-lookup"><span data-stu-id="e384a-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="e384a-140">単体テストでは、fakes を使用してまたは、これらの問題についての代わりにオブジェクトを模擬表示します。</span><span class="sxs-lookup"><span data-stu-id="e384a-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="e384a-141">統合テストの目的は、システムの統合テストの fakes を使用したりしないオブジェクトを模擬表示するために、これらのシステムでは、期待どおりに動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="e384a-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="e384a-142">代わりに、他のサービスからのデータベース アクセスまたはサービス呼び出しのように、インフラストラクチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e384a-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="e384a-143">統合テストで単体テストより大きいコード セグメントを実行し、統合テストは、インフラストラクチャの要素に依存するので、多くの場合桁違い単体テストよりも遅くなります。</span><span class="sxs-lookup"><span data-stu-id="e384a-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="e384a-144">したがって、統合テストを記述して実行の数を制限することをお勧めを勧めします。</span><span class="sxs-lookup"><span data-stu-id="e384a-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="e384a-145">ASP.NET Core には、組み込みのテスト web ホスト、ネットワークのオーバーヘッドが、HTTP 要求を処理するために使用する実行できること、テスト高速実際の web ホストを使用するときに意味が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e384a-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="e384a-146">テスト web ホストは、Microsoft.AspNetCore.TestHost と NuGet コンポーネントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e384a-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="e384a-147">統合テスト プロジェクトに追加できるし、アプリケーションを ASP.NET Core をホストするために使用します。</span><span class="sxs-lookup"><span data-stu-id="e384a-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="e384a-148">わかるように、次のコードに、ASP.NET Core コント ローラーで統合テストを作成するときに、によるテスト ホスト コント ローラーがインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="e384a-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="e384a-149">これは、HTTP 要求に匹敵するが、高速に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e384a-149">This is comparable to an HTTP request, but it runs faster.</span></span>

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a><span data-ttu-id="e384a-150">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="e384a-150">Additional resources</span></span>

-   <span data-ttu-id="e384a-151">**Steve Smith です。テスト コント ローラー** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="e384a-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="e384a-152">**Steve Smith です。統合テスト**(ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="e384a-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="e384a-153">**Dotnet テストを使用して .NET Core での単体テスト**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span><span class="sxs-lookup"><span data-stu-id="e384a-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span></span>

-   <span data-ttu-id="e384a-154">**xUnit.net**です。</span><span class="sxs-lookup"><span data-stu-id="e384a-154">**xUnit.net**.</span></span> <span data-ttu-id="e384a-155">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="e384a-155">Official site.</span></span>
    [<span data-ttu-id="e384a-156">*https://xunit.github.io/*</span><span class="sxs-lookup"><span data-stu-id="e384a-156">*https://xunit.github.io/*</span></span>](https://xunit.github.io/)

-   <span data-ttu-id="e384a-157">**単体テストの基本。** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="e384a-157">**Unit Test Basics.**
[*https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="e384a-158">**Moq**です。</span><span class="sxs-lookup"><span data-stu-id="e384a-158">**Moq**.</span></span> <span data-ttu-id="e384a-159">GitHub のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="e384a-159">GitHub repo.</span></span>
    [<span data-ttu-id="e384a-160">*https://github.com/moq/moq*</span><span class="sxs-lookup"><span data-stu-id="e384a-160">*https://github.com/moq/moq*</span></span>](https://github.com/moq/moq)

-   <span data-ttu-id="e384a-161">**NUnit**です。</span><span class="sxs-lookup"><span data-stu-id="e384a-161">**NUnit**.</span></span> <span data-ttu-id="e384a-162">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="e384a-162">Official site.</span></span>
    [<span data-ttu-id="e384a-163">*https://www.nunit.org/*</span><span class="sxs-lookup"><span data-stu-id="e384a-163">*https://www.nunit.org/*</span></span>](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="e384a-164">複数のコンテナー アプリケーションのテストをサービスの実装</span><span class="sxs-lookup"><span data-stu-id="e384a-164">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="e384a-165">前述の複数のコンテナー アプリケーションをテストするときに、すべての microservices を Docker ホストまたはコンテナーのクラスター内で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e384a-165">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="e384a-166">エンド ツー エンドのサービスを含むテストをいくつかの microservices に関連する複数の操作では、展開、docker を実行して、Docker ホストでアプリケーション全体を開始する必要があります-作成して (または同等のメカニズム、orchestrator を使用している場合)。</span><span class="sxs-lookup"><span data-stu-id="e384a-166">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="e384a-167">アプリケーション全体とそのすべてのサービスが実行されると、エンド ツー エンドの統合と機能のテストを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e384a-167">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="e384a-168">使用できるいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e384a-168">There are a few approaches you can use.</span></span> <span data-ttu-id="e384a-169">アプリケーション (または docker compose.ci.build.yml と同様に、同様のもの) の展開に使用する docker compose.yml ファイルで、ソリューション レベルで展開すると、エントリ ポイントを使用する[dotnet テスト](https://docs.microsoft.com/dotnet/core/tools/dotnet-test)です。</span><span class="sxs-lookup"><span data-stu-id="e384a-169">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span></span> <span data-ttu-id="e384a-170">対象とするイメージで、テストの実行が別の構成ファイルを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e384a-170">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="e384a-171">Microservices とコンテナー上のデータベースを含む統合テストを別の構成ファイルを使用するには、テストを実行する前に、元の状態に、関連するデータを常にリセットすることを確認しての操作をすることができます。</span><span class="sxs-lookup"><span data-stu-id="e384a-171">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="e384a-172">作成するアプリケーションが立ち上がっており実行中であるとする利用できますブレークポイントと例外の Visual Studio を実行している場合。</span><span class="sxs-lookup"><span data-stu-id="e384a-172">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="e384a-173">または、統合テストは、Visual Studio Team Services または Docker コンテナーをサポートするその他のすべての CI/CD システムで CI パイプラインで自動的に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="e384a-173">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e384a-174">[前](サブスクライブ-events.md) [次へ] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="e384a-174">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>

---
title: "ASP.NET Core サービスと Web アプリのテスト"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | ASP.NET Core サービスと Web アプリのテスト"
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
ms.openlocfilehash: 596f588aae8c0814e5b40d29c4bf5723f944c5ac
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="1c14b-104">ASP.NET Core サービスと Web アプリのテスト</span><span class="sxs-lookup"><span data-stu-id="1c14b-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="1c14b-105">コントローラーは、すべての ASP.NET Core API サービスと ASP.NET MVC Web アプリケーションの中心になるものです。</span><span class="sxs-lookup"><span data-stu-id="1c14b-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="1c14b-106">そのため、アプリケーションが意図するとおりに動作するという信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="1c14b-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="1c14b-107">自動テストを行うと、この信頼が得られ、運用環境に提供する前にエラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="1c14b-108">有効または無効な入力に基づくコントローラーの動作、および実行するビジネス操作の結果に基づくコントローラーの応答をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="1c14b-109">ただし、マイクロサービスに対してこれらの種類のテストを実行すべきです。</span><span class="sxs-lookup"><span data-stu-id="1c14b-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="1c14b-110">単体テスト。</span><span class="sxs-lookup"><span data-stu-id="1c14b-110">Unit tests.</span></span> <span data-ttu-id="1c14b-111">これは、アプリケーションの個々のコンポーネントが期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="1c14b-112">アサーションは、コンポーネント API をテストします。</span><span class="sxs-lookup"><span data-stu-id="1c14b-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="1c14b-113">統合テスト。</span><span class="sxs-lookup"><span data-stu-id="1c14b-113">Integration tests.</span></span> <span data-ttu-id="1c14b-114">これは、コンポーネント間の相互作用が、データベースなどの外部成果物に対して期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="1c14b-115">アサーションは、コンポーネント API や UI をテストしたり、データベース I/O やログ記録などの操作の副作用をテストしたりできます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="1c14b-116">各マイクロサービスの機能テスト。</span><span class="sxs-lookup"><span data-stu-id="1c14b-116">Functional tests for each microservice.</span></span> <span data-ttu-id="1c14b-117">これは、ユーザーの観点から、アプリケーションが期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="1c14b-118">サービス テスト。</span><span class="sxs-lookup"><span data-stu-id="1c14b-118">Service tests.</span></span> <span data-ttu-id="1c14b-119">これは、複数のサービスを同時にテストするなど、エンド ツー エンドのサービスのユース ケースがテストされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="1c14b-120">この種類のテストでは、まず環境を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="1c14b-121">この場合、サービスを開始することを意味します (たとえば、docker-compose up を使用します)。</span><span class="sxs-lookup"><span data-stu-id="1c14b-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="1c14b-122">ASP.NET Core Web API の単体テストの実装</span><span class="sxs-lookup"><span data-stu-id="1c14b-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="1c14b-123">単体テストでは、アプリケーションの一部をインフラストラクチャや依存関係から切り離してテストします。</span><span class="sxs-lookup"><span data-stu-id="1c14b-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="1c14b-124">コントローラー ロジックの単体テストを行うときは、それが依存しているものやフレームワーク自体の動作ではなく、単一のアクションやメソッドの内容のみをテストします。</span><span class="sxs-lookup"><span data-stu-id="1c14b-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="1c14b-125">単体テストではコンポーネント間の相互作用の問題は検出しません。これは、統合テストの目的です。</span><span class="sxs-lookup"><span data-stu-id="1c14b-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="1c14b-126">コントローラーのアクションの単体テストでは、その動作にだけ注目するようにします。</span><span class="sxs-lookup"><span data-stu-id="1c14b-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="1c14b-127">コントローラーの単体テストからは、フィルター、ルーティング、モデル バインドなどに関することは除外します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="1c14b-128">1 つの事柄だけに注目してテストするため、一般に、単体テストは簡単に記述してすばやく実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="1c14b-129">適切に記述された一連の単体テストは、大きなオーバーヘッドなしに頻繁に実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="1c14b-130">単体テストは、xUnit.net、MSTest、Moq、NUnit などのテスト フレームワークに基づいて実装されます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="1c14b-131">eShopOnContainers サンプル アプリケーションでは、XUnit を使用します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="1c14b-132">Web API コントローラーの単体テストを記述する際には、C\# で new キーワードを直接使用してコントローラー クラスをインスタンス化することにより、できるだけ速くテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="1c14b-133">次の例では、[XUnit](https://xunit.github.io/) をテスト フレームワークとして使用し、これを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="1c14b-134">各マイクロサービスの統合テストと機能テストの実装</span><span class="sxs-lookup"><span data-stu-id="1c14b-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="1c14b-135">前述のように、統合テストと機能テストにはさまざまな目的と目標があります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="1c14b-136">しかし、ASP.NET Core コントローラーをテストするときにそれらのテストを実装する方法は似ているため、このセクションでは統合テストに注目します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="1c14b-137">統合テストは、アプリケーションのコンポーネントが、組み立てたときに正しく動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="1c14b-138">ASP.NET Core は、単体テスト フレームワークと組み込みのテスト Web ホストを使用した統合テストをサポートします。これは、ネットワークのオーバーヘッドなしで要求を処理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="1c14b-139">単体テストとは異なり、統合テストにはしばしば、データベース、ファイル システム、ネットワーク リソース、Web 要求と応答などのアプリケーション インフラストラクチャの問題があります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="1c14b-140">単体テストでは、これらの問題の代わりにフェイクやモック オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1c14b-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="1c14b-141">しかし、統合テストの目的は、対象のシステムがこれらの問題のシステムで期待どおりに動作することを確認することであるため、統合テストではフェイクやモック オブジェクトを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1c14b-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="1c14b-142">代わりに、データベース アクセスや他のサービスからのサービス呼び出しなどのインフラストラクチャを含めます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="1c14b-143">統合テストは、単体テストより大きなコード セグメントを実行し、インフラストラクチャ要素に依存するため、多くの場合、単体テストと比べて桁違いに低速になります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="1c14b-144">そのため、記述して実行する統合テストの数を制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1c14b-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="1c14b-145">ASP.NET Core には、ネットワークのオーバーヘッドなしで HTTP 要求を処理するために使用できる、組み込みのテスト Web ホストが含まれています。これは、実際の Web ホストを使用するときにはそれらのテストをより速く実行できるということです。</span><span class="sxs-lookup"><span data-stu-id="1c14b-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="1c14b-146">テスト Web ホストは、Microsoft.AspNetCore.TestHost として NuGet コンポーネントでご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="1c14b-147">これを統合テスト プロジェクトに追加して、ASP.NET Core アプリケーションをホストするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="1c14b-148">次のコードからわかるように、ASP.NET Core コントローラーの統合テストを作成すると、テスト ホストによってコントローラーがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="1c14b-149">これは、HTTP 要求に相当しますが、より速く実行されます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-149">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="1c14b-150">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="1c14b-150">Additional resources</span></span>

-   <span data-ttu-id="1c14b-151">**Steve Smith。コントローラーのテスト** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="1c14b-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="1c14b-152">**Steve Smith。統合テスト** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="1c14b-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="1c14b-153">**dotnet test を使用した .NET Core での単体テスト**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span><span class="sxs-lookup"><span data-stu-id="1c14b-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](../../../core/testing/unit-testing-with-dotnet-test.md)</span></span>

-   <span data-ttu-id="1c14b-154">**xUnit.net**。</span><span class="sxs-lookup"><span data-stu-id="1c14b-154">**xUnit.net**.</span></span> <span data-ttu-id="1c14b-155">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="1c14b-155">Official site.</span></span>
    [<span data-ttu-id="1c14b-156">*https://xunit.github.io/*</span><span class="sxs-lookup"><span data-stu-id="1c14b-156">*https://xunit.github.io/*</span></span>](https://xunit.github.io/)

-   <span data-ttu-id="1c14b-157">**単体テストの基本。**
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="1c14b-157">**Unit Test Basics.**
[*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="1c14b-158">**Moq**。</span><span class="sxs-lookup"><span data-stu-id="1c14b-158">**Moq**.</span></span> <span data-ttu-id="1c14b-159">GitHub リポジトリ。</span><span class="sxs-lookup"><span data-stu-id="1c14b-159">GitHub repo.</span></span>
    [<span data-ttu-id="1c14b-160">*https://github.com/moq/moq*</span><span class="sxs-lookup"><span data-stu-id="1c14b-160">*https://github.com/moq/moq*</span></span>](https://github.com/moq/moq)

-   <span data-ttu-id="1c14b-161">**NUnit**。</span><span class="sxs-lookup"><span data-stu-id="1c14b-161">**NUnit**.</span></span> <span data-ttu-id="1c14b-162">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="1c14b-162">Official site.</span></span>
    [<span data-ttu-id="1c14b-163">*https://www.nunit.org/*</span><span class="sxs-lookup"><span data-stu-id="1c14b-163">*https://www.nunit.org/*</span></span>](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="1c14b-164">マルチコンテナー アプリケーションでのサービス テストの実装</span><span class="sxs-lookup"><span data-stu-id="1c14b-164">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="1c14b-165">前述のとおり、マルチコンテナー アプリケーションをテストする際、すべてのマイクロサービスを Docker ホスト内やコンテナー クラスター内で実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-165">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="1c14b-166">いくつかのマイクロサービスが関係する複数の操作を含むエンド ツー エンドのサービス テストでは、docker-compose up (または、オーケストレーターを使用している場合は相当するメカニズム) を実行して、Docker ホストでアプリケーション全体を展開して起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-166">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="1c14b-167">アプリケーション全体とそのすべてのサービスが実行されると、エンド ツー エンドの統合テストと機能のテストを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-167">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="1c14b-168">使用できる方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="1c14b-168">There are a few approaches you can use.</span></span> <span data-ttu-id="1c14b-169">アプリケーションの展開に使用する docker-compose.yml ファイル (または、docker-compose.ci.build.yml などの同様のもの) では、ソリューション レベルで [dotnet test](../../../core/tools/dotnet-test.md) を使用してエントリ ポイントを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-169">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="1c14b-170">対象とするイメージで、テストを実行する別の Compose ファイルを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-170">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="1c14b-171">コンテナー上のマイクロサービスとデータベースを含む統合テストで別の Compose ファイルを使用すれば、テストを実行する前に、関連するデータが元の状態に常にリセットされることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-171">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="1c14b-172">Compose アプリケーションが起動し実行されると、Visual Studio を実行している場合はブレークポイントと例外を活用できます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-172">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="1c14b-173">または、Visual Studio Team Services の CI パイプラインや Docker コンテナーをサポートする他の CI/CD システムで、統合テストを自動的に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1c14b-173">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="1c14b-174">[前へ] (subscribe-events.md) [次へ] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="1c14b-174">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>

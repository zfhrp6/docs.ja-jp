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
# <a name="testing-aspnet-core-services-and-web-apps"></a>ASP.NET Core サービスと web アプリのテスト

コント ローラーは、すべての ASP.NET Core API サービスと ASP.NET MVC Web アプリケーションの中央部分です。 そのため、アプリケーションの意図したとおりに動作する信頼が必要です。 自動テストは、この信頼を提供でき、実稼働環境に到達する前に、エラーを検出できます。

コント ローラーの有効または無効な入力に基づく動作をテストおよびテストの実行ビジネス操作の結果に基づいてコント ローラー応答する必要があります。 ただし、microservices がこれらの種類のテストが必要です。

-   単体テストされます。 これらは、アプリケーションの個々 のコンポーネントが期待どおりに動作することを確認します。 アサーションは、コンポーネントの API をテストします。

-   統合をテストします。 これらは、コンポーネントの相互作用がデータベースと同様に外部成果物に対して期待どおりに動作することを確認します。 アサーションには、コンポーネントの API、UI、またはログ記録などのデータベースの I/O などの操作の副作用をテストできます。

-   各マイクロ サービス機能をテストします。 これらは、ユーザーの観点から予想されるように、アプリケーションが動作することを確認します。

-   サービスをテストします。 これらは、同時に複数のサービスのテストを含む、エンド ツー エンドのサービスのユース ケースがテストされることを確認します。 この種類のテストでは、まず環境を準備する必要があります。 この場合、すること、サービスを開始します (たとえばを使用して docker-作成上)。

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>ASP.NET Core Web Api の実装の単体テスト

単体テストでは、そのインフラストラクチャとの依存関係から分離でのアプリケーションの一部のテストが含まれます。 ときに単体テストを行うコント ローラー ロジック、1 つのアクションのコンテンツだけメソッドをテスト、またはその依存関係や framework 自体の動作できません。 単体テストはコンポーネント間の対話で問題を検出できません-統合テストの目的はします。

ユニットとしてテスト コント ローラーのアクションをそれらの動作にのみ注目するかどうかを確認します。 コント ローラーの単体テストは、フィルター、ルーティング、またはモデル バインディングのようなものを回避できます。 1 つだけのテストの重点を置いて、ため単体テストは一般に書き込む単純なおよび実行するクイックです。 多くのオーバーヘッドなし、適切に記述された一連の単体テストを頻繁に実行できます。

単体テストは、xUnit.net、MSTest、Moq、NUnit などのテスト フレームワークに基づく実装されます。 EShopOnContainers サンプル アプリケーションについては、XUnit を使用します。

C では、new キーワードを使用して直接、コント ローラー クラスのインスタンスを作成する Web API コント ローラーの単体テストを記述するときに\#テストはできる限り高速に実行するようにします。 次の例は、これを行う方法を使用する場合を示しています。 [XUnit](https://xunit.github.io/)テスト フレームワークとします。

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>統合と各マイクロ サービスの機能のテストを実装します。

前述のように、統合テストと機能のテストはさまざまな目的と目標があります。 ただし、ASP.NET Core コント ローラーをテストするときに両方を実装する方法と同様に、統合テストを重視してこのセクションの内容。

統合テスト組み立て時に、アプリケーションのコンポーネントが正しく動作することを確認します。 ASP.NET Core サポート統合が単体テスト フレームワークと、ネットワークのオーバーヘッドが要求を処理するために使用する組み込みのテストの web ホストを使用してテストします。

単体テストとは異なり統合テストには、データベース、ファイル システム、ネットワーク リソース、または web 要求と応答などのアプリケーションのインフラストラクチャの問題が頻繁に含まれます。 単体テストでは、fakes を使用してまたは、これらの問題についての代わりにオブジェクトを模擬表示します。 統合テストの目的は、システムの統合テストの fakes を使用したりしないオブジェクトを模擬表示するために、これらのシステムでは、期待どおりに動作を確認します。 代わりに、他のサービスからのデータベース アクセスまたはサービス呼び出しのように、インフラストラクチャが含まれます。

統合テストで単体テストより大きいコード セグメントを実行し、統合テストは、インフラストラクチャの要素に依存するので、多くの場合桁違い単体テストよりも遅くなります。 したがって、統合テストを記述して実行の数を制限することをお勧めを勧めします。

ASP.NET Core には、組み込みのテスト web ホスト、ネットワークのオーバーヘッドが、HTTP 要求を処理するために使用する実行できること、テスト高速実際の web ホストを使用するときに意味が含まれています。 テスト web ホストは、Microsoft.AspNetCore.TestHost と NuGet コンポーネントで使用できます。 統合テスト プロジェクトに追加できるし、アプリケーションを ASP.NET Core をホストするために使用します。

わかるように、次のコードに、ASP.NET Core コント ローラーで統合テストを作成するときに、によるテスト ホスト コント ローラーがインスタンス化します。 これは、HTTP 要求に匹敵するが、高速に実行されます。

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

#### <a name="additional-resources"></a>その他の技術情報

-   **Steve Smith です。テスト コント ローラー** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith です。統合テスト**(ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)

-   **Dotnet テストを使用して .NET Core での単体テスト**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**です。 公式サイト。
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **単体テストの基本。** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)

-   **Moq**です。 GitHub のリポジトリ。
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**です。 公式サイト。
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>複数のコンテナー アプリケーションのテストをサービスの実装 

前述の複数のコンテナー アプリケーションをテストするときに、すべての microservices を Docker ホストまたはコンテナーのクラスター内で実行されている必要があります。 エンド ツー エンドのサービスを含むテストをいくつかの microservices に関連する複数の操作では、展開、docker を実行して、Docker ホストでアプリケーション全体を開始する必要があります-作成して (または同等のメカニズム、orchestrator を使用している場合)。 アプリケーション全体とそのすべてのサービスが実行されると、エンド ツー エンドの統合と機能のテストを実行できます。

使用できるいくつかの方法があります。 アプリケーション (または docker compose.ci.build.yml と同様に、同様のもの) の展開に使用する docker compose.yml ファイルで、ソリューション レベルで展開すると、エントリ ポイントを使用する[dotnet テスト](https://docs.microsoft.com/dotnet/core/tools/dotnet-test)です。 対象とするイメージで、テストの実行が別の構成ファイルを使用することもできます。 Microservices とコンテナー上のデータベースを含む統合テストを別の構成ファイルを使用するには、テストを実行する前に、元の状態に、関連するデータを常にリセットすることを確認しての操作をすることができます。

作成するアプリケーションが立ち上がっており実行中であるとする利用できますブレークポイントと例外の Visual Studio を実行している場合。 または、統合テストは、Visual Studio Team Services または Docker コンテナーをサポートするその他のすべての CI/CD システムで CI パイプラインで自動的に実行することができます。

>[!div class="step-by-step"]
[前](サブスクライブ-events.md) [次へ] (../microservice-ddd-cqrs-patterns/index.md)

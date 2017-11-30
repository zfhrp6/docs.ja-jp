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
# <a name="health-monitoring"></a>正常性の監視

正常性の監視と、ほぼリアルタイムのコンテナーと microservices 状態情報を許可できます。 正常性監視と microservices の動作のさまざまな側面に重要な orchestrators が後で説明したようのフェーズで部分的なアプリケーションのアップグレードを実行時に、特に重要です。

Microservices ベースのアプリケーションがハートビートを多くの場合、使用または、パフォーマンス モニター、スケジューラ、および orchestrators、さまざまなサービスの追跡を有効にする正常性を確認します。 オンデマンドまたはスケジュールで、サービスは、「私はアライブ」信号のいくつかの並べ替えを送信できない場合、アプリケーションは、展開するときに更新プログラム、単に遅すぎます障害を検出し、障害が最終的に大規模な停止を連鎖を停止できませんか可能性がありますリスクに直面する可能性があります。

モデルでは、通常、サービスが、その状態に関するレポートを送信し、その情報が集約され、アプリケーションの正常性の状態の全体的な表示をします。 Orchestrator を使用している場合は、クラスターが適切に操作できるように、orchestrator のクラスターに正常性情報を提供できます。 アプリケーション用にカスタマイズされている高品質の正常性レポートに投資する場合は、検出しより簡単に実行中のアプリケーションの問題を修正できます。

## <a name="implementing-health-checks-in-aspnet-core-services"></a>ASP.NET Core services での確認の正常性を実装します。

ASP.NET Core マイクロ サービスまたは web アプリケーションを開発する場合は、ASP.NET チームから HealthChecks をという名前のライブラリを使用できます。 (、2017 年 1 月の時点で、初期リリースは GitHub で利用可能) です。

このライブラリは使いやすいあり機能 (SQL Server データベースやリモート API) など、アプリケーションに必要な特定の外部リソースが正常に機能していることを検証することができます。 このライブラリを使用する場合は、後で説明して、リソースが正常である意味も決定できます。

このライブラリを使用するためには、まず、microservices でライブラリを使用する必要があります。 次に、正常性レポートのクエリを実行するフロント エンド アプリケーションが必要です。 フロント エンド アプリケーションにはカスタムのレポート アプリケーションがあるか、それ自体を orchestrator それに対処できる可能性がありますを稼働状態にします。

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>バック エンド ASP.NET microservices HealthChecks ライブラリを使用します。

EShopOnContainers サンプル アプリケーションで HealthChecks ライブラリを使用する方法を確認できます。 を開始するには、各マイクロ サービスの正常な状態の構成要素を定義する必要があります。 サンプル アプリケーションでは、microservices はマイクロ サービス API が HTTP およびその関連する SQL Server データベースが使用可能なも使用してアクセスできる場合は正常な状態です。

今後、NuGet パッケージとして HealthChecks ライブラリをインストールすることができます。 このドキュメントの作成時点では、ダウンロードし、ソリューションの一部として、コードをコンパイルする必要があります。 Https://github.com/aspnet/HealthChecks で利用可能なコードを複製し、次のフォルダーをソリューションにコピーします。

  - src/共通
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Azure (Microsoft.Extensions.HealthChecks.AzureStorage) が eShopOnContainers のこのバージョンでは、Azure では、すべての依存関係はありませんのでのような追加のチェックを使用することも、する必要はありません。 EShopOnContainers は ASP.NET Core に基づいているために、ASP.NET の正常性チェックは必要ありません。

図 10-6 は、Visual Studio で、任意 microservices を基盤として使用する準備ができて HealthChecks ライブラリを示します。

![](./media/image6.png)

**図 10-6**です。 Visual Studio ソリューションでは ASP.NET Core HealthChecks ライブラリのソース コード

以前導入際に、マイクロ サービスの各プロジェクトでは、まず次の 3 つの HealthChecks ライブラリへの参照を追加を開始します。 その後、そのマイクロ サービスで実行する正常性チェックのアクションを追加します。 これらのアクションは、基本的に他の microservices (HttpUrlCheck) またはデータベースへの依存関係 (現在 SqlCheck\* SQL Server データベース用)。 各 ASP.NET マイクロ サービスまたは ASP.NET web アプリケーションのスタートアップ クラス内でアクションを追加するとします。

AddHealthCheck の 1 つの方法として、すべての HTTP またはデータベースの依存関係を追加することで、各サービスまたは web アプリケーションを構成してください。 たとえば、eShopOnContainers から MVC web アプリケーションは、多くのサービスに依存、ために、正常性チェックに追加されたいくつかの AddCheck メソッドです。

たとえば、次のコードにカタログ マイクロ サービスが SQL Server データベースの依存関係を追加する方法を確認できます。

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

ただし、eShopOnContainers の MVC web アプリケーションでは、microservices の残りの部分で複数の依存関係があります。 そのため、各マイクロ サービスの 1 つの AddUrlCheck メソッドを呼び出す例を次に示すように。

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

したがって、すべてのチェックがも異常な状態になるまで、マイクロ サービスは「正常」の状態を提供しません。

場合は、マイクロ サービスがあるないと、依存関係サービスまたは SQL Server、Healthy("Ok") チェックを追加する必要があります。 次のコードは eShopOnContainers basket.api マイクロ サービスです。 (バスケット マイクロ サービスが Redis cache を使用しますが、ライブラリでは、Redis の正常性チェックのプロバイダーがまだ含まれません)。

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

正常性チェックのエンドポイントを公開するサービスまたは web アプリケーションの場合、UseHealthChecks を有効にする必要がある (\[*url\_の\_ヘルス\_チェック*\]) 拡張機能メソッド。 このメソッドが、ASP.NET Core サービスまたは web アプリケーションの直後に次のコードに示すように UseKestrel Program クラスのメイン メソッド内でレベル、WebHostBuilder には移動します。

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

プロセスの次のように動作します。 各マイクロ サービスを公開エンドポイント/hc です。 ASP.NET Core ミドルウェア HealthChecks ライブラリによっては、そのエンドポイントが作成されます。 そのエンドポイントが呼び出されたときに、スタートアップ クラスで AddHealthChecks メソッドで構成されているすべての正常性チェックが実行されます。

UseHealthChecks メソッドでは、ポートまたはパスが必要です。 ポートまたはパスを使用して、サービスのヘルス状態を確認するエンドポイント。 たとえば、カタログ マイクロ サービスは、パス/hc を使用します。

### <a name="caching-health-check-responses"></a>正常性チェック応答のキャッシュ

サービスで、サービス拒否 (DoS) が発生しないか、単にたくないリソースをチェックして、サービスのパフォーマンスに影響するので頻度が高すぎる、制御を返すをキャッシュして各正常性チェックのキャッシュの存続期間を構成します。

既定では、キャッシュの存続期間が内部的には、5 分間に設定されているが、次のコードのように各正常性チェックでそのキャッシュの存続期間を変更することができます。

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>正常性の状態に関するレポートを microservices のクエリを実行します。

」の説明に従って、Docker で、マイクロ サービスが実行されている正常性チェックを構成すると正常な状態である場合、ブラウザーから直接確認することができます。 (これは必要 localhost、または外部の Docker ホスト IP を通じて、コンテナーにアクセスできるように Docker ホストからコンテナーのポートを発行することです。)図 10-7 では、対応する応答をブラウザーで要求を示します。

![](./media/image7.png)

**図 10-7**です。 ブラウザーから 1 つのサービスのヘルス状態を確認します。

そのテストで確認できます (ポート 5101 で実行されている) catalog.api マイクロ サービスが正常である JSON 内の HTTP ステータス 200 およびステータス情報を返します。 内部的には、サービスもオンになっている、SQL Server データベースの依存関係の正常性と正常性チェックが正常であるとそれ自体に報告することも意味します。

## <a name="using-watchdogs"></a>取り組むを使用します。

ウォッチドッグは、正常性を監視したり、以前に導入された HealthChecks ライブラリとクエリを実行してサービス、および、microservices について正常性のレポート間で負荷をできる個別のサービスです。 これにより、1 つのサービスのビューに基づいたが検出されないエラーを防ぐのに役立ちます。 取り組むでは、ユーザーの介入なしの既知の条件の修復アクションを実行できるコードをホストするに適してもいます。

EShopOnContainers サンプルには、図 10-8 に示すようにサンプル正常性チェック レポートを表示する web ページが含まれています。 これは、割り当てることも、最も単純な監視はすべてが示される eShopOnContainers microservices と web アプリケーションの状態。 通常、ウォッチドッグではもアクションを実行して、異常な状態を検出するとします。

![](./media/image8.png)

**図 10-8**です。 EShopOnContainers でサンプルの正常性チェック レポート

要約するは、ASP.NET Core HealthChecks ライブラリの ASP.NET ミドルウェアは、各マイクロ サービスを 1 つの正常性チェックのエンドポイントを提供します。 内に定義されているすべての正常性チェックの実行、それらすべてのチェックによって全体的なヘルス状態を返します。

HealthChecks ライブラリは、今後の外部のリソースの新しい正常性チェックを使用して拡張です。 たとえば、後で、ライブラリを持つ Redis cache のおよびその他のデータベースの正常性チェックいく予定です。 ライブラリにより、複数のサービスまたはアプリケーションの依存で報告される正常性と、それらの正常性チェックに基づいた操作を実行できます。

## <a name="health-checks-when-using-orchestrators"></a>Orchestrators を使用するときの正常性チェック

Microservices の可用性を監視するには、Docker Swarm、Kubernetes、Service Fabric など orchestrators は定期的に、microservices をテストする要求を送信することによって正常性チェックを実行します。 ときに、orchestrator では、サービス/コンテナーが異常で、そのインスタンスへの要求のルーティングを停止することを決定します。 通常、そのコンテナーの新しいインスタンスを作成します。

たとえば、ほとんど orchestrators はダウンタイムの展開を管理するのに正常性チェックを使用できます。 正常な状態にサービス/コンテナーの変更の状態は場合にのみ、orchestrator は、サービス/コンテナー インスタンスにトラフィックのルーティングを開始します。

正常性の監視は、orchestrator は、アプリケーションのアップグレードを実行するときに特に重要です。 フェーズでサービスを更新する (Azure Service Fabric) のようないくつか orchestrators: 5 分ごとのアプリケーションのアップグレードのサーフェスをクラスターを更新したりなどです。 同時にアップグレードされるノードのセットと呼びます、*アップグレード ドメイン*です。 各アップグレード ドメインは、アップグレードされており、ユーザーには後、アップグレード ドメインは、展開が次のアップグレード ドメインに移動する前に正常性チェックを渡す必要があります。

サービスのヘルス状態の別の要素は、サービスからメトリックを報告しています。 これは、Service Fabric のように、いくつかの orchestrators の正常性モデルの高度な機能です。 メトリックは、リソース使用率のバランスをとるに使用されるため、orchestrator を使用する場合に重要です。 メトリックは、システム正常性の指標も指定できます。 たとえばを持つ多く microservices は、アプリケーションがある可能性があり、各インスタンスは、要求/秒 (RPS) メトリックを報告します。 1 つのサービスが別のサービスよりも多くのリソース (メモリやプロセッサなど) を使用している場合、orchestrator でした内を移動のサービス インスタンス クラスター リソースの使用率を維持しようとします。

Azure Service Fabric を使用している場合、によって提供される独自[正常性の監視モデル](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)、単純な正常性チェックをより高度であります。

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>先進的な監視: 視覚エフェクト、分析、およびアラート

監視の最後の部分には、レポート サービスのパフォーマンスの作成と、問題が検出されたとき、警告、イベント ストリームを視覚化します。 監視のこの面のさまざまなソリューションを使用することができます。

サービスの状態を示す単純なカスタム アプリケーションを使用すると、カスタムのページのように紹介説明しました[ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks)です。 または Azure Application Insights と Operations Management Suite などのより高度なツールを使用して、イベントのストリームに基づき、アラートを生成します。

最後に、すべてのイベント ストリームを格納していた場合そのデータを視覚化する Microsoft Power BI または Kibana Splunk などのサード パーティのソリューションを使用できます。

## <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Core HealthChecks** (初期リリース) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Service Fabric の正常性の監視の概要**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure の Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[前](実装の回線のブレーカー-pattern.md) [次へ] (../secure-net-microservices-web-applications/index.md)

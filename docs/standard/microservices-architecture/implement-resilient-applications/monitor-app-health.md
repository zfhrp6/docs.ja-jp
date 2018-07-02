---
title: 正常性の監視
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 正常性の監視
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 62d4e9a26710a5c4b191287bf76192972f7e991b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106542"
---
# <a name="health-monitoring"></a>正常性の監視

正常性を監視することで、コンテナーとマイクロサービスの状態に関する情報をほぼリアルタイムに得ることができます。 正常性の監視はマイクロサービス運用の複数の側面において不可欠であり、オーケストレーターで段階的に部分的なアプリケーションのアップグレードを行う際に特に重要です。

マイクロサービス ベースのアプリケーションでは、多くの場合、ハートビートまたは正常性チェックを使用して、パフォーマンス モニター、スケジューラー、およびオーケストレーターで多数のサービスを追跡できるようにします。 サービスが必要に応じて、またはスケジュールに従って、ある種の "アライブ" シグナルを送信できない場合、更新プログラムの展開時にアプリケーションがリスクに直面する可能性があります。あるいは、単に障害の検出が遅すぎたために障害の連鎖を防ぐことができず、最終的に大規模な停止が発生する可能性があります。

標準的なモデルでは、サービスは状態に関するレポートを送信し、その情報が集約され、アプリケーションの正常性状態の概要が提供されます。 オーケストレーターを使用する場合は、オーケストレーターのクラスターに正常性情報を提供することができるため、クラスターは適切に機能できます。 アプリケーション用にカスタマイズされている高品質の正常性レポートに投資する場合、実行中のアプリケーションの問題をはるかに簡単に検出して修正することができます。

## <a name="implementing-health-checks-in-aspnet-core-services"></a>ASP.NET Core サービスでの正常性チェックの実装

ASP.NET Core マイクロサービスまたは Web アプリケーションを開発する場合、ASP.NET チームの `HealthChecks` という名前の帯域外ライブラリ (ASP.NETCore に正式には含まれません) を使用することができます。 これは、[GitHub リポジトリ](https://github.com/dotnet-architecture/HealthChecks)から入手できます。

このライブラリは使いやすく、アプリケーションに必要な特定の外部リソース (SQL Server データベースやリモート API など) が正しく動作していることを検証できる機能を提供します。 このライブラリを使用すれば、リソースが正常であるかどうかを判断することもできます。これについては後で説明します。

このライブラリを使用するには、まず、マイクロサービスでライブラリを使用する必要があります。 次に、正常性レポートのクエリを実行するフロント エンド アプリケーションが必要になります。 このフロント エンド アプリケーションはカスタム レポート アプリケーションである場合があります。また、正常性状態に応じて対応できるオーケストレーター自体である場合もあります。

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>バック エンド ASP.NET マイクロサービスでの HealthChecks ライブラリの使用

EShopOnContainers サンプル アプリケーションでの HealthChecks ライブラリの使用方法を確認することができます。 開始するには、各マイクロサービスの正常性状態の構成要素を定義する必要があります。 サンプル アプリケーションでは、マイクロサービス API が HTTP 経由でアクセス可能である場合と、それに関連する SQL Server データベースも使用可能である場合、マイクロサービスは正常な状態です。

将来的には、HealthChecks ライブラリを NuGet パッケージとしてインストールできるようになります。 ただし、このドキュメントの作成時点では、ソリューションの一部として、コードをダウンロードしてコンパイルする必要があります。 https://github.com/dotnet-architecture/HealthChecks にあるコードを複製し、次のフォルダーをソリューションにコピーします。

  - src/common
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Azure の場合 (Microsoft.Extensions.HealthChecks.AzureStorage) のように追加チェックを使用することもできますが、このバージョンの eShopOnContainers には Azure に対する依存関係がないため、必要ありません。 EShopOnContainers は ASP.NET Core に基づいているため、ASP.NET の正常性チェックは必要ありません。

図 10-6 には、マイクロサービスで構成要素として使用する準備ができている、Visual Studio の HealthChecks ライブラリが示されています。

![](./media/image6.png)

**図 10-6**.  Visual Studio ソリューションの ASP.NET Core HealthChecks ライブラリ ソース コード

前述のとおり、各マイクロサービス プロジェクトでまず行うことは、3 つの HealthChecks ライブラリへの参照を追加することです。 その後、そのマイクロサービスで実行する正常性チェックのアクションを追加します。 これらのアクションは基本的に他のマイクロサービス (HttpUrlCheck) またはデータベース (現時点では SQL Server データベースの SqlCheck\*) に依存します。 各 ASP.NET マイクロサービスまたは ASP.NET Web アプリケーションのスタートアップ クラス内でアクションを追加します。

各サービスまたは Web アプリケーションは、すべての HTTP またはデータベースの依存関係を 1 つの AddHealthCheck メソッドとして追加することで構成する必要があります。 たとえば、eShopOnContainers の MVC Web アプリケーションは多くのサービスに依存するため、正常性チェックにはいくつかの AddCheck メソッドが追加されています。

たとえば、次のコードでは、カタログ マイクロサービスが SQL Server データベースに対する依存関係をどのように追加するかを確認できます。

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

ただし、eShopOnContainers の MVC Web アプリケーションには、残りのマイクロサービスに対する複数の依存関係があります。 そのため、次の例に示すように、マイクロサービスごとに 1 つの AddUrlCheck メソッドが呼び出されます。

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

したがって、そのすべてのチェックでも正常であると判断されるまで、マイクロサービスでは "正常" 状態と示されません。

マイクロサービスにサービスまたは SQL Server に対する依存関係がない場合は、Healthy("Ok") チェックを追加するだけ済みます。 次のコードは eShopOnContainers basket.api マイクロサービスからのものです  (バスケット マイクロサービスでは Redis Cache を使用しますが、ライブラリにはまだ Redis 正常性チェック プロバイダーは含まれていません)。

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

サービスまたは Web アプリケーションで正常性チェック エンドポイントを公開するには、UseHealthChecks(\[*url\_for\_health\_checks*\]) 拡張メソッドを有効にする必要があります。 このメソッドは、以下のコードに示すように、ASP.NET Core サービスまたは Web アプリケーションの Program クラスのメイン メソッドの WebHostBuilder レベルで UseKestrel の直後に配置されます。

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

プロセスのしくみは次のとおりです。まず、各マイクロサービスがエンドポイント /hc を公開します。 そのエンドポイントは、HealthChecks ライブラリの ASP.NET Core ミドルウェアによって作成されます。 そのエンドポイントが呼び出されたときに、スタートアップ クラスの AddHealthChecks メソッドで構成されているすべての正常性チェックが実行されます。

UseHealthChecks メソッドにはポートまたはパスが必要です。 そのポートまたはパスはエンドポイントであり、サービスの正常性状態を確認するために使用します。 たとえば、カタログ マイクロサービスではパス /hc を使用します。

### <a name="caching-health-check-responses"></a>正常性チェック応答のキャッシュ

サービスでサービス拒否攻撃 (DoS) が発生しないようにする場合や、リソースを頻繁に確認しすぎてサービスのパフォーマンスが影響を受けることのないようにするだけの場合は、戻り値をキャッシュし、各正常性チェックのキャッシュ期間を構成することができます。

既定では、キャッシュ期間は内部的に 5 分に設定されますが、次のコードのように、各正常性チェックでそのキャッシュ期間を変更することができます。

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>マイクロサービスでクエリを実行してその正常性状態についてレポートする

説明に従って正常性チェックを構成し、マイクロサービスを Docker で実行した後、正常かどうかをブラウザーから直接確認することができます  (そのためには、Docker ホスト外のコンテナー ポートを公開し、localhost または外部の Docker ホスト IP を通じてコンテナーにアクセスできるようにする必要があります)。図 10-7 には、ブラウザーでの要求とそれに対応する応答が示されています。

![](./media/image7.png)

**図 10-7**.  ブラウザーからの単一サービスの正常性状態の確認

このテストでは、catalog.api マイクロサービス (ポート 5101 で実行されている) が正常であり、JSON で HTTP ステータス 200 とステータス情報が返されていることがわかります。 これは、内部的にサービスが SQL Server データベースの依存関係の正常性も確認し、その正常性チェック自体が正常とレポートされたことも意味します。

## <a name="using-watchdogs"></a>ウォッチドッグの使用

ウォッチドッグは、サービス間の正常性と負荷を監視し、前述の HealthChecks ライブラリを使用してクエリを実行することでマイクロサービスに関する正常性をレポートできる別個のサービスです。 これは、単一サービスのビューに基づいて検出されないエラーを防ぐのに役立ちます。 また、ウォッチドッグは、ユーザーの介入なしで既知の状態に応じて修復アクションを実行できるコードをホストする場合に適しています。

eShopOnContainers サンプルには、図 10-8 に示すように、サンプルの正常性チェック レポートを表示する Web ページが含まれています。 これは、eShopOnContainers でマイクロサービスと Web アプリケーションの状態を表示するだけであるため、使用可能な最も単純なウォッチドッグです。 通常、ウォッチドッグは異常状態の検出時にもアクションを実行します。

![](./media/image8.png)

**図 10-8**.  eShopOnContainers のサンプルの正常性チェック レポート

つまり、ASP.NET Core HealthChecks ライブラリの ASP.NET ミドルウェアでは、マイクロサービスごとに 1 つの正常性チェック エンドポイントを提供します。 これにより、定義されているすべての正常性チェックが実行され、これらすべてのチェックに応じて、全体的な正常性状態が返されます。

HealthChecks ライブラリは、今後の外部リソースの新しい正常性チェックにより拡張可能です。 たとえば、今後、ライブラリに Redis Cache や他のデータベースの正常性チェックが含まれることが予想されます。 ライブラリでは複数のサービスまたはアプリケーションの依存関係での正常性レポートが可能であるため、これらの正常性チェックに基づいてアクションを実行できます。

## <a name="health-checks-when-using-orchestrators"></a>オーケストレーターを使用する場合の正常性チェック

マイクロサービスの可用性を監視するために、Docker Swarm、Kubernetes、Service Fabric などのオーケストレーターではマイクロサービスのテスト要求を送信して、定期的に正常性チェックを実行します。 オーケストレーターでサービス/コンテナーが異常であると判断された場合、そのインスタンスへの要求のルーティングが停止します。 通常は、そのコンテナーの新しいインスタンスも作成されます。

たとえば、ほとんどのオーケストレーターでは、ダウンタイムなしの展開を管理するために正常性チェックを使用できます。 サービス/コンテナーの状態が正常に変わった場合にのみ、オーケストレーターはサービス/コンテナー インスタンスへのトラフィックのルーティングを開始します。

正常性の監視は、オーケストレーターがアプリケーションのアップグレードを実行する場合に特に重要です。 いくつかのオーケストレーター (Azure Service Fabric など) ではサービスを段階的に更新します。たとえば、アプリケーションのアップグレードごとに 5 分の 1 のクラスター サーフェスを更新する場合があります。 同時にアップグレードされるノード セットを*アップグレード ドメイン* といいます。 各アップグレード ドメインがアップグレードされ、ユーザーが使用できるようになったら、そのアップグレード ドメインは、展開が次のアップグレード ドメインに移る前に正常性チェックを渡す必要があります。

サービスの正常性のもう 1 つの側面は、サービスからのメトリックのレポートです。 これは、Service Fabric などの一部のオーケストレーターの正常性モデルの高度な機能です。 メトリックは、リソース使用量のバランスをとるために使用されるため、オーケストレーターの使用時に重要になります。 メトリックをシステム正常性のインジケーターにすることもできます。 たとえば、アプリケーションに多くのマイクロサービスがあり、各インスタンスで要求/秒 (RPS) メトリックをレポートするとします。 1 つのサービスが別のサービスより多くのリソース (メモリやプロセッサなど) を使用している場合、オーケストレーターはクラスター内でサービス インスタンスを移動して、リソース使用率を均一に保つことができます。

Azure Service Fabric を使用している場合は、単純な正常性チェックより高度な独自の[正常性の監視モデル](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)が提供されることに注意してください。

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>高度な監視: 視覚化、分析、およびアラート

監視の最後の部分は、イベント ストリームの視覚化、サービス パフォーマンスのレポート、および問題の検出時のアラートです。 監視のこの部分ではさまざまなソリューションを使用できます。

[ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks) の説明の際に示したカスタム ページのように、サービス状態を示す単純なカスタム アプリケーションを使用できます。 または Azure Application Insights や Operations Management Suite などのより高度なツールを使用して、イベントのストリームに基づき、アラートを生成することができます。

最後に、すべてのイベント ストリームを格納していた場合、Microsoft Power BI、または Kibana や Splunk などのサードパーティのソリューションを使用して、データを視覚化することができます。

## <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET Core HealthChecks** (早期リリース) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Service Fabric 正常性監視の概要**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[前へ](implement-circuit-breaker-pattern.md)
[次へ](../secure-net-microservices-web-applications/index.md)

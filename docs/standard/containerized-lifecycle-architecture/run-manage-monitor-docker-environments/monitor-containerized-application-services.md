---
title: コンテナー化アプリケーションのサービスを監視します。
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26854e9efc4d7e43d5896c30a1c5ce0801045f45
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="monitor-containerized-application-services"></a>コンテナー化アプリケーションのサービスを監視します。

監視して、アプリケーションの動作を分析する方法があるアプリケーションを複数のコンテナーと microservices に分割が重要です。

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)ライブ アプリケーションを監視する拡張可能な分析サービスです。 検出し、パフォーマンスの問題を診断し、ユーザーはどの機能実際にアプリを理解するために実行できます。 継続的にパフォーマンスを改善するのに役立つことを目的と使いやすさのサービスやアプリケーションの開発者に設計されています。 Application Insights は、web/サービスとスタンドアロンの両方で、さまざまなプラットフォームなど、.NET、Java、Node.js とその他の多くのプラットフォームでは、ホストの内部設置型またはクラウド上のアプリを使用できます。

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>QA を Application Insights を使用する環境でのアプリの Docker の分析

Docker に関連してライフ サイクル イベントおよび Application Insights での Docker コンテナーからパフォーマンス カウンターをグラフにできます。 だけを実行する必要があります、[アプリケーション Insights Docker イメージ](https://hub.docker.com/r/microsoft/applicationinsights/)コンテナー、ホストとそれには他の Docker images と同様にホストのパフォーマンス カウンターを表示します。 このアプリケーション Insights Docker イメージ (図 6-1) に役立つパフォーマンスおよびアクティビティの Docker ホスト (つまり、Linux Vm)、Docker コンテナーと実行中のアプリケーションに関する製品利用統計情報を収集して、コンテナー化アプリケーションを監視するには内にします。

![例](./media/image1.png)

図 6-1。 Application Insights の Docker ホストとコンテナーの監視

実行すると、[アプリケーション Insights Docker イメージ](https://hub.docker.com/r/microsoft/applicationinsights/)Docker ホスト上のメリットが以下。

-   ホストで実行されているすべてのコンテナーに関する製品利用統計情報のライフ サイクル-開始、停止、およびなどです。

-   すべてのコンテナーのパフォーマンス カウンター: CPU、メモリ、ネットワーク使用率などです。

-   インストールされている場合[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)アプリでは、コンテナーで実行されている、それらのアプリのすべてのテレメトリは、コンテナーとホスト マシンを識別するプロパティを追加します。 したがって、たとえば、複数のホストで実行されているアプリのインスタンスがあれば、簡単にされますホストによってアプリのテレメトリをフィルター処理すること。

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Application Insights を設定するアプリケーションの Docker と Docker ホストを監視するには

Application Insights リソースを作成するには、下記の一覧に表示される記事は、設定を指示します。 Azure ポータルを必要なスクリプトを作成します。

-   **Application Insights での Docker アプリケーションの監視:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Docker Hub、Github にあるアプリケーション Insights Docker イメージ:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) そして <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **ASP.NET の Application Insights を設定します。**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Web ページの application Insights:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](http://microsoft.com/oms)簡略化された IT 管理ソリューションをログ分析、automation、backup、およびサイトの回復を提供します。 基づく[クエリ](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/)Operations Management Suite に上げることができます[アラート](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts)経由で修復を設定および[Azure Automation](https://docs.microsoft.com/azure/automation/)です。 1 つのペインのガラスのビューを提供する、既存の管理ソリューションともシームレスに統合できます。 Operations Management Suite は、管理し、オンプレミスの保護およびインフラストラクチャをクラウドに役立ちます。

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](http://microsoft.com/oms) Docker のコンテナー ソリューション

自身で有益なサービスを提供することだけでなく、Operations Management Suite コンテナー ソリューション管理および監視できます Docker ホストとコンテナー、コンテナーとコンテナー ホストである、に関する情報を表示することによってコンテナーが実行されています。障害が発生した、または、Docker デーモンとコンテナーでのログに送信される*stdout*と*stderr*です。 また、CPU、メモリ、ネットワーク、コンテナーとホストのストレージなどのパフォーマンス メトリックを表示し、トラブルシューティングやノイズの多い近隣のコンテナーの検出に役立てることもできます。

![](./media/image2.png)

図 6-2: Operations Management Suite で示すように Docker コンテナーについて

Application Insights と Operations Management Suite 焦点をアクティビティの監視ただし、Application Insights 重点的により、アプリ内で実行されているその SDK によりアプリ自体を監視します。 ただし、Operations Management Suite 重点的により、ホストの周囲のインフラストラクチャとながら、非常に柔軟なデータ ドリブン/検索システム規模でログに詳細な分析を提供します。

Operations Management Suite がクラウド ベース サービスとして実装されているため素早くことができます、立ち上がっており実行中インフラストラクチャ サービスでの最小限の投資でします。 新機能では、保存する継続的なメンテナンスに、自動的に配信され、コストをアップグレードします。

Operations Management Suite コンテナー ソリューションでは、次の操作を行うことができます。

-   集中管理し、何百万ものスケールで Docker コンテナーからログを関連付ける

-   1 つの場所のすべてのコンテナー ホストに関する情報を参照してください。

-   対象のコンテナを実行しているし、実行しているどのようなイメージを実行します。

-   コンテナー ホスト上の問題を引き起こす可能性のある「ノイズの多い近隣」コンテナーをすばやく診断します。

-   コンテナーにおけるアクションの監査証跡を参照してください。

-   表示し、Docker ホストへのリモート処理なしでログを一元的な検索でのトラブルシューティングします。

-   「ノイズの多い近隣」と、ホスト上余分なリソースを消費になる可能性があるコンテナーを検索します。

-   一元的な CPU、メモリ、記憶域、およびコンテナーのネットワークの使用状況とパフォーマンス情報を表示します。

-   生成して、Docker コンテナーに Azure automation のテスト

型のようにクエリを実行するパフォーマンスの情報を表示する図 6-3 に示すように、パフォーマンスを = です。

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

Operations Management Suite で示すように Docker ホストのパフォーマンス メトリックを図 6-3:

Operations Management Suite での標準機能ではまたクエリを保存できると便利ですが増えるし、システム内の傾向を検出、クエリを保持します。

**詳細については** でコンテナー ソリューションをインストールして、Docker の構成に関する情報を検索する[Operations Management Suite](http://microsoft.com/oms)に進み、<https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>です。

>[!div class="step-by-step"]
[前] (管理、運用の docker-environments.md) [次へ] (../key-takeaways/index.md)

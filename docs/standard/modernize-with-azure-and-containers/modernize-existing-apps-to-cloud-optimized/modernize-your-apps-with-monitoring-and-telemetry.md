---
title: 監視と遠隔測定でアプリを最新化します。
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |監視と遠隔測定でアプリを最新化します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8f5f9bfebf46db7b98bedc4b5b8204d23357c72e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957972"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>監視と遠隔測定でアプリを最新化します。

実稼働環境でアプリケーションを実行するときに、アプリケーションの実行方法に関する詳細情報があることが重要です。 高レベルのパフォーマンス ユーザーが、エラーを取得するか、安定性と信頼性の高いアプリケーションは、ですか。 豊富なパフォーマンスの監視、強力なアラート、およびダッシュ ボード、アプリケーションが使用できると期待どおりに実行することを確認する必要があります。 問題があるかどうかをすばやく確認を顧客の数が、影響を受けるし、を見つけて、問題を修正する根本原因分析の実行を決定できる必要があります。

## <a name="monitor-your-application-with-application-insights"></a>Application Insights を使用してアプリケーションを監視します。

Application Insights は、複数のプラットフォームで作業を行う web 開発者の拡張可能なアプリケーション パフォーマンス管理 (APM) サービスです。 これを使用して、ライブ web アプリケーションを監視します。 Application Insights は、パフォーマンス上の問題を自動的に検出します。 ユーザーはどの機能実際にアプリを理解するため、問題の診断に役立つ強力な分析ツールが含まれています。 Application Insights はパフォーマンスと使いやすさを継続的に改善するために設計されています。 アプリのプラットフォームでは、.NET、Node.js、J2EE をするかどうかなどのさまざまなでうまく動作オンプレミスにホストまたはクラウドにします。 Application Insights は、DevOps プロセスと統合され、さまざまな開発ツールに接続ポイントを持ちます。

図 4-10 では、Application Insights でアプリを監視する方法と、ダッシュ ボードにこれらの分析の表示の例を示します。

![Application Insights の監視ダッシュ ボード](./media/image10.png)

> **図 4-10 です。** Application Insights の監視ダッシュ ボード

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>ログ分析とそのコンテナーの監視ソリューションを使用して Docker インフラストラクチャを監視します。

[Azure ログ分析](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)の一部である、[全体的な監視ソリューションの Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)です。 サービスに[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)です。 ログ分析クラウドを監視し、内部設置型環境 (内部設置型用の OMS) の可用性とパフォーマンスを維持するためにします。 リソースがクラウドとオンプレミスの環境で、複数のソースで分析を行うために他の監視ツールから生成されたデータを収集します。

Azure インフラストラクチャ ログとの関連ログ分析、Azure サービスとして取り込み、他の Azure サービスからのログとメトリック データ (を介して[Azure モニター](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))、Azure Vm、Docker コンテナー、および内部設置型またはその他のクラウド インフラストラクチャ。 ログ分析は、柔軟なログ検索とこのデータの上にボックス外の分析を提供します。 指定した条件に基づいて、豊富なことソース間でデータの分析に使用することができます、ツールにより、複雑なクエリ、すべてのログを事前にアラートが通知を提供します。 カスタム リポジトリにデータを中央ログ分析、クエリし、視覚的に表現できますも収集できます。 すぐに洞察を得る、セキュリティ ログ分析の組み込みのソリューションの利点と、インフラストラクチャの機能を実行することができますも。

ログ分析を OMS ポータルまたは任意のブラウザーで実行して、Azure ポータルを介してアクセスし、構成設定にアクセスして複数のツールを分析し、収集したデータの動作を提供できます。

[コンテナー監視ソリューション](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)ではログ分析、表示および 1 つの場所で、Docker と Windows コンテナー ホストを管理します。 ソリューションは、どのコンテナーを示しています。 実行して、どのようなコンテナー イメージを実行していると、コンテナーが実行されています。 コンテナーで使用されているコマンドを含む、詳細な監査情報を表示することができます。 また、コンテナーを表示し、Docker または Windows のホストをリモートで表示することがなく一元的なログを検索トラブルシューティングすることもできます。 ホスト上のノイズの多いと使用の余分なリソースがあるコンテナーを検索できます。 さらに、一元的な CPU、メモリ、記憶域、およびネットワーク使用率およびパフォーマンスについては、コンテナーを表示することができます。 Windows を実行するコンピューター上には、集中管理し、Windows Server からログを比較することができます、HYPER-V と Docker のコンテナーです。 ソリューションには、次のコンテナー orchestrators がサポートされています。

-   Docker Swarm

-   DC OS/

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

図 4-11 は、さまざまなコンテナー ホストのエージェントと OMS との間の関係を示しています。

![ログ分析コンテナー監視ソリューション](./media/image11.png)

> **図 4-11。** ログ分析コンテナー監視ソリューション

ログ分析のコンテナーの監視ソリューションを使用できます。

-   1 つの場所のすべてのコンテナー ホストに関する情報を参照してください。

-   対象のコンテナを実行しているどのようなイメージを実行して、実行しています。

-   コンテナーにおけるアクションの監査証跡を参照してください。

-   表示して、Docker ホストへのリモート ログインに関係なく一元的なログを検索してトラブルシューティングを行います。

-   「ノイズの多い近隣」場合があり、ホスト上余分なリソースを消費するコンテナーを検索します。

-   一元的な CPU、メモリ、記憶域、およびネットワーク使用率およびパフォーマンスについては、コンテナーを表示します。

### <a name="additional-resources"></a>その他の技術情報

-   **Microsoft Azure での監視の概要**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **Application Insights とは何ですか。**

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **ログ分析は何ですか。**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   **ログ分析でコンテナー監視ソリューション**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Azure のモニターの概要**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **Operations Management Suite (OMS) とは何ですか。**

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **OMS を使用して Service Fabric で Windows Server コンテナーの監視**

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[前へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[次へ](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)

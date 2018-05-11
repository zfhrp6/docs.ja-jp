---
title: クラウドに最適化されたアプリケーションで Microsoft のテクノロジ
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |クラウドに最適化されたアプリケーションで Microsoft のテクノロジ
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: ece366ee3918124bb60e367d3c7447c1d4555c72
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>クラウドに最適化されたアプリケーションで Microsoft のテクノロジ

次の一覧は、ツール、テクノロジ、およびはクラウドに最適化されたアプリの要件として認識されるソリューションについて説明します。 優先度の高いに応じて選択的にまたは段階的に、クラウドに最適化された要素を導入できます。

-   **クラウド インフラストラクチャ**: コンピューティング プラットフォーム、オペレーティング システム、ネットワーク、および記憶域を提供するインフラストラクチャ。 Microsoft Azure は、このレベルに配置されます。

-   **ランタイム**: この層は、アプリケーションを実行する環境を提供します。 コンテナーを使用している場合は、このレイヤー通常はに基づいて[Docker エンジン](https://docs.docker.com/engine/)、Linux ホスト上または Windows ホストで実行中です。 ([Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/) Windows Server 2016 以降ではサポートされています。 Windows コンテナーは Windows で実行される既存の .NET Framework アプリケーションに最適な選択肢です。)

-   **クラウドの管理**: 管理されたクラウド オプションを選択するときに、コストと複雑さを管理して、基になるインフラストラクチャ、Vm、OS パッチをサポートするネットワーク構成を回避できます。 IaaS を使用して、移行する場合は、これらすべてのタスク、および関連するコストを担当しています。 管理されたクラウド オプションでは、アプリケーションとサービスを開発のみを管理します。 通常、クラウド サービス プロバイダーでは、他のすべてを管理します。 Azure で管理されたクラウド サービスの例として、 [Azure SQL Database](https://azure.microsoft.com/services/sql-database)、 [Azure Redis Cache](https://azure.microsoft.com/services/cache/)、 [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)、 [Azure Storage](https://azure.microsoft.com/services/storage/)、[For MySQL データベースを azure](https://azure.microsoft.com/services/mysql/)、 [PostgreSQL の Azure データベース](https://azure.microsoft.com/services/postgresql/)、 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)のようなコンピューティング サービスを管理および[VM スケール設定](https://azure.microsoft.com/services/virtual-machine-scale-sets/)、 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)、 [Azure App Service](https://azure.microsoft.com/services/app-service/)、および[Azure Kubernetes サービス](https://azure.microsoft.com/services/container-service/)です。

-   **アプリケーションの開発**: コンテナーで実行されるアプリケーションをビルドするときに多くの言語から選択できます。 このガイドの焦点[.NET](https://www.microsoft.com/net)が、Node.js、Python、Spring/Java と同様に、他の言語を使用して、コンテナー ベースのアプリを開発したり、移動できます。

-   **製品利用統計情報ログ、および監査関連の監視、**: 監視および監査のアプリケーションとクラウドで実行されているコンテナーに機能は、クラウドに最適化されたアプリケーションにとって不可欠です。 [Azure の Application Insights](https://azure.microsoft.com/services/application-insights/)と[Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite)クラウドに向けて最適化されたアプリの監視、および監査を提供する Microsoft 製品の主なツールです。

-   **プロビジョニング**: オートメーション ツールのヘルプ、インフラストラクチャをプロビジョニングし、複数の環境 (運用、テスト、ステージング) にアプリケーションを展開します。 Chef、Puppet などのツールを使用して、アプリケーションの構成および環境を管理することができます。 このレイヤーも簡単かつ直接的なアプローチを使用して実装することができます。 たとえば、展開ツールで Azure コマンド ライン インターフェイス (Azure CLI) を使用して直接とし、継続的なデプロイを使用でき、リリース管理パイプラインに[Visual Studio Team Services](https://www.visualstudio.com/team-services/)です。

-   **アプリケーションのライフ サイクル**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/) Jenkins など、他のツールは、するのに役立つ組み込みのオートメーション サーバー実装 CI/CD パイプライン、リリース管理を含むとします。

この章で、関連のチュートリアルの次のセクションでは、ランタイム層 (Windows コンテナー) に関する詳細情報について重点的に説明します。 このガイダンスでは、Windows Server 2016 (とそれ以降のバージョン) で Windows コンテナーの Vm と Azure のコンテナー インスタンスを展開する方法について説明します。 Azure App Service などのより高度な PaaS プラットフォームおよび Azure Service Fabric および Azure Kubernetes サービスと同様に orchestrator についても説明します。

## <a name="monolithic-applications-can-be-cloud-optimized"></a>モノリシック アプリケーション*できます*するクラウドに最適化されました。

そのモノリシック アプリケーション (microservices に基づいていないこと) を強調表示することが重要*できます*クラウドに向けて最適化されたアプリケーションします。 構築し、コンテナー、継続的な配信、および DevOps の組み合わせを使用してモデルをコンピューティング クラウド利用モノリシックのアプリケーションを操作できます。 モノリシックな既存のアプリケーションがビジネスの目標の適切な場合は、その改革し、ようにクラウドに最適化されました。

同様に、モノリシック アプリケーションできますが、アプリケーションをクラウドに最適化された場合 N 層アプリケーションと同様に、他のより複雑なアーキテクチャことができますもする最新化されたアプリケーションをクラウドに最適化されたとします。

>[!div class="step-by-step"]
[前へ](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
[次へ](what-about-cloud-native-applications.md)

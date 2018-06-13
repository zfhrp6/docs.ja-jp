---
title: Microsoft ツールを使用した Docker アプリケーション devops ワークフロー
description: Microsoft プラットフォームでのコンテナー化された Docker アプリケーションのライフサイクルと Microsoft ツールでの Toolsdevops ワークフロー
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4a88725de78f59c62aac1bd33764db6b2e0887e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32768490"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft ツールを使用した Docker アプリケーション DevOps ワークフロー

Microsoft Visual Studio、Visual Studio Team Services、Team Foundation Server、および Application Insights は、開発および IT 操作の包括的なエコシステムを提供します。これにより、チームでは、プロジェクトを管理し、コンテナー化アプリケーションを迅速にビルド、テスト、および展開することができます。

クラウドの Visual Studio と Visual Studio Team Services と、オンプレミスの Team Foundation Server により、開発チームは、コンテナー化アプリケーションを、任意のプラットフォーム (Windows または Linux) で生産的に直接ビルド、テストおよびリリースできます。

Microsoft ツールは、Docker、.NET Core、または他のプラットフォームとのあらゆる組み合わせのコンテナー化アプリケーションの特定の実装の、グローバル ビルド、継続的インテグレーション (CI)、Visual Studio Team Services または Team Foundation Server でのテストから、Docker 環境 (開発、ステージング、実稼働) への継続的配置 (CD) と Application Insights を介した開発チームへのサービスに関する分析情報の転送のパイプラインを自動化できます。 すべてのコードのコミットでビルド (CI) を開始して、特定のコンテナー化された環境 (CD) に自動的にサービスを展開できます。

開発者およびテスト担当者は、Microsoft Azure のテンプレートを使用して、Docker に基づく運用環境のような開発とテストの環境を、簡単かつ迅速にプロビジョニングできます。

コンテナー化アプリケーションの開発は、ビジネスが複雑であり、拡張のニーズがあればあるほど、着実に複雑になります。 このよい例は、マイクロサービス アーキテクチャに基づいたアプリケーションです。 このような環境で成功するには、プロジェクトのライフ サイクル全体が自動化される必要があります。ビルドや展開のみでなく、製品利用統計情報のコレクションと共に、バージョンも管理される必要があります。 Visual Studio Team Services と Azure には、次の機能があります。

-   (Git または Team Foundation バージョン管理に基づく) Visual Studio Team Services と Team Foundation Server のソース コード管理、(アジャイル、スクラム、CMMI がサポートされている) アジャイル計画、CI、リリース管理およびアジャイル チーム用の他のツール。

-   Visual Studio Team Services と Team Foundation Server には、強力で増えていっているファースト パーティおよびサード パーティの拡張機能のエコシステムを含んでいます。これを使用すると、マイクロサービス用に、CI、ビルド、テスト、配信、リリース管理パイプラインを容易に構成できます。

-   Visual Studio Team Services でビルド パイプラインの一部として、自動テストを実行します。

-   Visual Studio Team Services では、実稼働環境用のみでなく、A/B 実験、[カナリヤ リリース](https://martinfowler.com/bliki/CanaryRelease.html)など、テスト用を含む複数の環境への配信により、DevOps のライフ サイクルを強化できます。

-   組織は、Azure Container Registry に格納されたプライベート イメージから Docker コンテナーを、Azure Resource Manager テンプレートと既に使い慣れているツールを使用して、(Data、PaaS などの) Azure コンポーネントの任意の依存関係と共に簡単にプロビジョニングできます。


>[!div class="step-by-step"]
[前へ] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [次へ] (docker-application-outer-loop-devops-workflow.md)

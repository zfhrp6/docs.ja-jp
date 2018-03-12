---
title: "CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 668c48b64cab964da65625ef5326fb75e133b3b9
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。

今日の企業は、marketplace に競合する迅速なペースで導入する必要があります。 高品質を提供するには、最新のアプリケーションには、DevOps ツールや技術革新の定数このサイクルの実装に不可欠なプロセスが必要です。 適切な DevOps ツールは、開発者は継続的なデプロイを効率化し、ユーザーの手に革新的なアプリケーションを迅速に取得します。

継続的な統合とデプロイのプラクティスは定評が、複数のコンテナー アプリケーションで作業するときに特にコンテナーの概要新しいの考慮事項について説明します。

Visual Studio Team Services には、継続的インテグレーションとさまざまな公式 Team Services の展開タスクを環境に複数のコンテナー アプリケーションの展開がサポートされています。

-   [スタンドアロンでの Docker ホストの VM 展開](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm)(Linux または Windows Server 2016 以降)

-   [Service Fabric に展開します。](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [Azure のコンテナー サービス – Kubernetes に展開します。](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

展開できますが、 [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)または DC/OS Team Services のスクリプトを使用したタスクを使用しています。

続けるには展開の機敏性を促進することは、これらのツールは、優れた開発用のテスト-運用デプロイのエクスペリエンスに開発および CI/CD ソリューションの選択肢を備えた、コンテナーのワークロードを提供します。

図 4-12 には、Azure コンテナー サービスで Kubernetes クラスターに展開する継続的なデプロイ パイプラインが表示されます。

![Visual Studio Team Services 継続的なデプロイのパイプライン、Kubernetes クラスターに展開します。](./media/image12.png)

> **図 4-12 です。** Visual Studio Team Services 継続的なデプロイのパイプライン、Kubernetes クラスターに展開します。

>[!div class="step-by-step"]
[前へ](modernize-your-apps-with-monitoring-and-telemetry.md)
[次へ](migrate-to-hybrid-cloud-scenarios.md)

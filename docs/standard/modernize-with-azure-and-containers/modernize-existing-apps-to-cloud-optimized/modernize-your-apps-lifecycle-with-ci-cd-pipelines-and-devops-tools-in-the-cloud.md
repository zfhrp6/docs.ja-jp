---
title: CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 63907a1911b4c95f0dbecb2af33964225cf3e7b1
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="346fa-103">CI/CD パイプラインや DevOps ツール、クラウドでアプリのライフ サイクルを最新化します。</span><span class="sxs-lookup"><span data-stu-id="346fa-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="346fa-104">今日の企業は、marketplace に競合する迅速なペースで導入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="346fa-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="346fa-105">高品質を提供するには、最新のアプリケーションには、DevOps ツールや技術革新の定数このサイクルの実装に不可欠なプロセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="346fa-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="346fa-106">適切な DevOps ツールは、開発者は継続的なデプロイを効率化し、ユーザーの手に革新的なアプリケーションを迅速に取得します。</span><span class="sxs-lookup"><span data-stu-id="346fa-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="346fa-107">継続的な統合とデプロイのプラクティスは定評が、複数のコンテナー アプリケーションで作業するときに特にコンテナーの概要新しいの考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="346fa-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="346fa-108">Visual Studio Team Services には、継続的インテグレーションとさまざまな公式 Team Services の展開タスクを環境に複数のコンテナー アプリケーションの展開がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="346fa-108">Visual Studio Team Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Team Services deployment tasks:</span></span>

-   <span data-ttu-id="346fa-109">[スタンドアロンでの Docker ホストの VM 展開](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm)(Linux または Windows Server 2016 以降)</span><span class="sxs-lookup"><span data-stu-id="346fa-109">[Deploy to standalone Docker Host VM](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-docker-windowsvm) (Linux or Windows Server 2016 or later)</span></span>

-   [<span data-ttu-id="346fa-110">Service Fabric に展開します。</span><span class="sxs-lookup"><span data-stu-id="346fa-110">Deploy to Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-tutorial-deploy-app-with-cicd-vsts)

-   [<span data-ttu-id="346fa-111">Azure のコンテナー サービス – Kubernetes に展開します。</span><span class="sxs-lookup"><span data-stu-id="346fa-111">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/vsts/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="346fa-112">展開できますが、 [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)または DC/OS Team Services のスクリプトを使用したタスクを使用しています。</span><span class="sxs-lookup"><span data-stu-id="346fa-112">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Team Services script-based tasks.</span></span>

<span data-ttu-id="346fa-113">続けるには展開の機敏性を促進することは、これらのツールは、優れた開発用のテスト-運用デプロイのエクスペリエンスに開発および CI/CD ソリューションの選択肢を備えた、コンテナーのワークロードを提供します。</span><span class="sxs-lookup"><span data-stu-id="346fa-113">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="346fa-114">図 4-12 には、Azure コンテナー サービスで Kubernetes クラスターに展開する継続的なデプロイ パイプラインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="346fa-114">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Visual Studio Team Services 継続的なデプロイのパイプライン、Kubernetes クラスターに展開します。](./media/image12.png)

> <span data-ttu-id="346fa-116">**図 4-12 です。**</span><span class="sxs-lookup"><span data-stu-id="346fa-116">**Figure 4-12.**</span></span> <span data-ttu-id="346fa-117">Visual Studio Team Services 継続的なデプロイのパイプライン、Kubernetes クラスターに展開します。</span><span class="sxs-lookup"><span data-stu-id="346fa-117">Visual Studio Team Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="346fa-118">[前へ](modernize-your-apps-with-monitoring-and-telemetry.md)
[次へ](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="346fa-118">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>

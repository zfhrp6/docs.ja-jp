---
title: Microsoft ツールを使用した Docker アプリケーション devops ワークフロー
description: Microsoft プラットフォームでのコンテナー化された Docker アプリケーションのライフサイクルと Microsoft ツールでの Toolsdevops ワークフロー
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4a88725de78f59c62aac1bd33764db6b2e0887e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a><span data-ttu-id="4bf49-103">Microsoft ツールを使用した Docker アプリケーション DevOps ワークフロー</span><span class="sxs-lookup"><span data-stu-id="4bf49-103">Docker application DevOps workflow with Microsoft tools</span></span>

<span data-ttu-id="4bf49-104">Microsoft Visual Studio、Visual Studio Team Services、Team Foundation Server、および Application Insights は、開発および IT 操作の包括的なエコシステムを提供します。これにより、チームでは、プロジェクトを管理し、コンテナー化アプリケーションを迅速にビルド、テスト、および展開することができます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-104">Microsoft Visual Studio, Visual Studio Team Services, Team Foundation Server, and Application Insights provide a comprehensive ecosystem for development and IT operations that give your team the tools to manage projects and rapidly build, test, and deploy containerized applications.</span></span>

<span data-ttu-id="4bf49-105">クラウドの Visual Studio と Visual Studio Team Services と、オンプレミスの Team Foundation Server により、開発チームは、コンテナー化アプリケーションを、任意のプラットフォーム (Windows または Linux) で生産的に直接ビルド、テストおよびリリースできます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-105">With Visual Studio and Visual Studio Team Services in the cloud, along with Team Foundation Server on-premises, development teams can productively build, test, and release containerized applications directed toward any platform (Windows or Linux).</span></span>

<span data-ttu-id="4bf49-106">Microsoft ツールは、Docker、.NET Core、または他のプラットフォームとのあらゆる組み合わせのコンテナー化アプリケーションの特定の実装の、グローバル ビルド、継続的インテグレーション (CI)、Visual Studio Team Services または Team Foundation Server でのテストから、Docker 環境 (開発、ステージング、実稼働) への継続的配置 (CD) と Application Insights を介した開発チームへのサービスに関する分析情報の転送のパイプラインを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-106">Microsoft tools can automate the pipeline for specific implementations of containerized applications—Docker, .NET Core, or any combination with other platforms—from global builds and Continuous Integration (CI) and tests with Visual Studio Team Services or Team Foundation Server, to Continuous Deployment (CD) to Docker environments (Development, Staging, Production), and to transmit analytics information about the services to the development team through Application Insights.</span></span> <span data-ttu-id="4bf49-107">すべてのコードのコミットでビルド (CI) を開始して、特定のコンテナー化された環境 (CD) に自動的にサービスを展開できます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-107">Every code commit can initiate a build (CI) and automatically deploy the services to specific containerized environments (CD).</span></span>

<span data-ttu-id="4bf49-108">開発者およびテスト担当者は、Microsoft Azure のテンプレートを使用して、Docker に基づく運用環境のような開発とテストの環境を、簡単かつ迅速にプロビジョニングできます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-108">Developers and testers can easily and quickly provision production-like development and test environments based on Docker by using templates in Microsoft Azure.</span></span>

<span data-ttu-id="4bf49-109">コンテナー化アプリケーションの開発は、ビジネスが複雑であり、拡張のニーズがあればあるほど、着実に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="4bf49-109">The complexity of containerized application development increases steadily depending on the business complexity and scalability needs.</span></span> <span data-ttu-id="4bf49-110">このよい例は、マイクロサービス アーキテクチャに基づいたアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="4bf49-110">A good example of this are applications based on microservices architectures.</span></span> <span data-ttu-id="4bf49-111">このような環境で成功するには、プロジェクトのライフ サイクル全体が自動化される必要があります。ビルドや展開のみでなく、製品利用統計情報のコレクションと共に、バージョンも管理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf49-111">To succeed in such an environment, your project must automate the entire life cycle—not only the build and deployment, but it also must manage versions along with the collection of telemetry.</span></span> <span data-ttu-id="4bf49-112">Visual Studio Team Services と Azure には、次の機能があります。</span><span class="sxs-lookup"><span data-stu-id="4bf49-112">Visual Studio Team Services and Azure offer the following capabilities:</span></span>

-   <span data-ttu-id="4bf49-113">(Git または Team Foundation バージョン管理に基づく) Visual Studio Team Services と Team Foundation Server のソース コード管理、(アジャイル、スクラム、CMMI がサポートされている) アジャイル計画、CI、リリース管理およびアジャイル チーム用の他のツール。</span><span class="sxs-lookup"><span data-stu-id="4bf49-113">Visual Studio Team Services/Team Foundation Server source code management (based on Git or Team Foundation Version Control), Agile planning (Agile, Scrum, and CMMI are supported), CI, release management, and other tools for Agile teams.</span></span>

-   <span data-ttu-id="4bf49-114">Visual Studio Team Services と Team Foundation Server には、強力で増えていっているファースト パーティおよびサード パーティの拡張機能のエコシステムを含んでいます。これを使用すると、マイクロサービス用に、CI、ビルド、テスト、配信、リリース管理パイプラインを容易に構成できます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-114">Visual Studio Team Services/Team Foundation Server include a powerful and growing ecosystem of first- and third-party extensions with which you easily can construct a CI, build, test, delivery, and release management pipeline for microservices.</span></span>

-   <span data-ttu-id="4bf49-115">Visual Studio Team Services でビルド パイプラインの一部として、自動テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bf49-115">Run automated tests as part of your build pipeline in Visual Studio Team Services.</span></span>

-   <span data-ttu-id="4bf49-116">Visual Studio Team Services では、実稼働環境用のみでなく、A/B 実験、[カナリヤ リリース](https://martinfowler.com/bliki/CanaryRelease.html)など、テスト用を含む複数の環境への配信により、DevOps のライフ サイクルを強化できます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-116">Visual Studio Team Services can tighten the DevOps life cycle with delivery to multiple environments, not just for production environments, but also for testing, including A/B experimentation, [canary releases](https://martinfowler.com/bliki/CanaryRelease.html), and so on.</span></span>

-   <span data-ttu-id="4bf49-117">組織は、Azure Container Registry に格納されたプライベート イメージから Docker コンテナーを、Azure Resource Manager テンプレートと既に使い慣れているツールを使用して、(Data、PaaS などの) Azure コンポーネントの任意の依存関係と共に簡単にプロビジョニングできます。</span><span class="sxs-lookup"><span data-stu-id="4bf49-117">Organizations easily can provision Docker containers from private images stored in Azure Container Registry along with any dependency on Azure components (Data, PaaS, etc.) using Azure Resource Manager templates with tools with which they are already comfortable working.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4bf49-118">[前へ] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [次へ] (docker-application-outer-loop-devops-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4bf49-118">[Previous] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [Next] (docker-application-outer-loop-devops-workflow.md)</span></span>

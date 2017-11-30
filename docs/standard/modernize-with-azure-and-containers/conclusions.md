---
title: "まとめ"
description: "Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 |結論"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 0bcc330a5970ab923b48d8790c4de93171283d94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="conclusions"></a><span data-ttu-id="d8891-103">まとめ</span><span class="sxs-lookup"><span data-stu-id="d8891-103">Conclusions</span></span>

-   <span data-ttu-id="d8891-104">最終的には、コンテナー ベースのソリューションには、コスト節約の利点があります。</span><span class="sxs-lookup"><span data-stu-id="d8891-104">Container-based solutions ultimately provide cost savings benefits.</span></span> <span data-ttu-id="d8891-105">コンテナーは、実稼働環境での依存関係が存在しない場合の原因となった摩擦を削除するために、展開に関する問題の解決策です。</span><span class="sxs-lookup"><span data-stu-id="d8891-105">Containers are a solution to deployment problems because they remove the friction caused by an absence of dependencies in production environments.</span></span> <span data-ttu-id="d8891-106">これらの問題を削除すると、その開発/テスト、DevOps および運用操作大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="d8891-106">By removing those issues, it improves Dev/Test, DevOps and production operations significantly.</span></span>

-   <span data-ttu-id="d8891-107">Docker コンテナーには、サーバー ベースのアプリケーションまたはサービスの配置の標準的な単位が高まっています。</span><span class="sxs-lookup"><span data-stu-id="d8891-107">A Docker container is becoming the standard unit of deployment for any server-based application or service.</span></span>

-   <span data-ttu-id="d8891-108">運用環境でのスケーラブルな Windows コンテナー ベースのアプリケーションをホストするオーケストレーター (Service Fabric Kubernetes など) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d8891-108">For production environments, you should use an orchestrator (like Service Fabric or Kubernetes) to host scalable Windows Containers­­–based applications.</span></span>

-   <span data-ttu-id="d8891-109">コンテナーをホストする azure Vm は、クラウドでの小規模な開発およびテスト環境の作成を高速で簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="d8891-109">Azure VMs hosting containers are a fast and simple way to create small Dev/Test environments in the cloud.</span></span>

-   <span data-ttu-id="d8891-110">Azure に既存のアプリケーションから、リレーショナル データベースを移行する場合、azure SQL データベースのマネージ インスタンスが既定で勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8891-110">Azure SQL Database Managed Instance is recommended by default when migrating your relational databases from existing applications to Azure.</span></span>

-   <span data-ttu-id="d8891-111">Visual Studio 2017 と Image2Docker は、Windows コンテナーで、既存の .NET アプリケーションを取得中に開始された学習を向上させることにより刷新を開始するための基本的なツールです。</span><span class="sxs-lookup"><span data-stu-id="d8891-111">Visual Studio 2017 and Image2Docker are basic tools for you to start modernizing your existing .NET applications with Windows Containers by accelerating the getting started learning curve.</span></span>

-   <span data-ttu-id="d8891-112">実稼働環境でコンテナー化アプリケーションを配置するときを常に作成または DevOps カルチャと Visual Studio Team Services や Jenkins などの CI/CD パイプライン DevOps ツールを導入します。</span><span class="sxs-lookup"><span data-stu-id="d8891-112">When placing containerized applications in production you will always create or adopt a DevOps culture and DevOps tools for CI/CD pipelines, like Visual Studio Team Services or Jenkins.</span></span>

-   <span data-ttu-id="d8891-113">Microsoft Azure では、Windows コンテナー、クラウド インフラストラクチャの PaaS サービスと、既存の .NET Framework アプリケーションを最新化するための最も包括的で完全な環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="d8891-113">Microsoft Azure provides the most comprehensive and complete environment to modernize your existing .NET Framework applications with Windows Containers, cloud infrastructure and PaaS services.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="d8891-114">前へ</span><span class="sxs-lookup"><span data-stu-id="d8891-114">Previous</span></span>](walkthroughs-technical-get-started-overview.md)
---
title: "監視と遠隔測定でアプリを最新化します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |監視と遠隔測定でアプリを最新化します。"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3caeb60cf0107aaf5413d935f3bde11863561c7d
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="05b52-103">監視と遠隔測定でアプリを最新化します。</span><span class="sxs-lookup"><span data-stu-id="05b52-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="05b52-104">実稼働環境でアプリケーションを実行するときに、アプリケーションの実行方法に関する詳細情報があることが重要です。</span><span class="sxs-lookup"><span data-stu-id="05b52-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="05b52-105">高レベルのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="05b52-105">Is it performing at a high level?</span></span> <span data-ttu-id="05b52-106">ユーザーが、エラーを取得するか、安定性と信頼性の高いアプリケーションは、ですか。</span><span class="sxs-lookup"><span data-stu-id="05b52-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="05b52-107">豊富なパフォーマンスの監視、強力なアラート、およびダッシュ ボード、アプリケーションが使用できると期待どおりに実行することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b52-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="05b52-108">問題があるかどうかをすばやく確認を顧客の数が、影響を受けるし、を見つけて、問題を修正する根本原因分析の実行を決定できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b52-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="05b52-109">Application Insights を使用してアプリケーションを監視します。</span><span class="sxs-lookup"><span data-stu-id="05b52-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="05b52-110">Application Insights は、複数のプラットフォームで作業を行う web 開発者の拡張可能なアプリケーション パフォーマンス管理 (APM) サービスです。</span><span class="sxs-lookup"><span data-stu-id="05b52-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="05b52-111">これを使用して、ライブ web アプリケーションを監視します。</span><span class="sxs-lookup"><span data-stu-id="05b52-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="05b52-112">Application Insights は、パフォーマンス上の問題を自動的に検出します。</span><span class="sxs-lookup"><span data-stu-id="05b52-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="05b52-113">ユーザーはどの機能実際にアプリを理解するため、問題の診断に役立つ強力な分析ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05b52-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="05b52-114">Application Insights はパフォーマンスと使いやすさを継続的に改善するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="05b52-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="05b52-115">アプリのプラットフォームでは、.NET、Node.js、J2EE をするかどうかなどのさまざまなでうまく動作オンプレミスにホストまたはクラウドにします。</span><span class="sxs-lookup"><span data-stu-id="05b52-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="05b52-116">Application Insights は、DevOps プロセスと統合され、さまざまな開発ツールに接続ポイントを持ちます。</span><span class="sxs-lookup"><span data-stu-id="05b52-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="05b52-117">図 4-10 では、Application Insights でアプリを監視する方法と、ダッシュ ボードにこれらの分析の表示の例を示します。</span><span class="sxs-lookup"><span data-stu-id="05b52-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights の監視ダッシュ ボード](./media/image10.png)

> <span data-ttu-id="05b52-119">**図 4-10 です。**</span><span class="sxs-lookup"><span data-stu-id="05b52-119">**Figure 4-10.**</span></span> <span data-ttu-id="05b52-120">Application Insights の監視ダッシュ ボード</span><span class="sxs-lookup"><span data-stu-id="05b52-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="05b52-121">ログ分析とそのコンテナーの監視ソリューションを使用して Docker インフラストラクチャを監視します。</span><span class="sxs-lookup"><span data-stu-id="05b52-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="05b52-122">[Azure ログ分析](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)の一部である、[全体的な監視ソリューションの Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)です。</span><span class="sxs-lookup"><span data-stu-id="05b52-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="05b52-123">サービスに[Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)です。</span><span class="sxs-lookup"><span data-stu-id="05b52-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="05b52-124">ログ分析クラウドを監視し、内部設置型環境 (内部設置型用の OMS) の可用性とパフォーマンスを維持するためにします。</span><span class="sxs-lookup"><span data-stu-id="05b52-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="05b52-125">リソースがクラウドとオンプレミスの環境で、複数のソースで分析を行うために他の監視ツールから生成されたデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="05b52-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="05b52-126">Azure インフラストラクチャ ログとの関連ログ分析、Azure サービスとして取り込み、他の Azure サービスからのログとメトリック データ (を介して[Azure モニター](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor))、Azure Vm、Docker コンテナー、および内部設置型またはその他のクラウド インフラストラクチャ。</span><span class="sxs-lookup"><span data-stu-id="05b52-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="05b52-127">ログ分析は、柔軟なログ検索とこのデータの上にボックス外の分析を提供します。</span><span class="sxs-lookup"><span data-stu-id="05b52-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="05b52-128">指定した条件に基づいて、豊富なことソース間でデータの分析に使用することができます、ツールにより、複雑なクエリ、すべてのログを事前にアラートが通知を提供します。</span><span class="sxs-lookup"><span data-stu-id="05b52-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="05b52-129">カスタム リポジトリにデータを中央ログ分析、クエリし、視覚的に表現できますも収集できます。</span><span class="sxs-lookup"><span data-stu-id="05b52-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="05b52-130">すぐに洞察を得る、セキュリティ ログ分析の組み込みのソリューションの利点と、インフラストラクチャの機能を実行することができますも。</span><span class="sxs-lookup"><span data-stu-id="05b52-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="05b52-131">ログ分析を OMS ポータルまたは任意のブラウザーで実行して、Azure ポータルを介してアクセスし、構成設定にアクセスして複数のツールを分析し、収集したデータの動作を提供できます。</span><span class="sxs-lookup"><span data-stu-id="05b52-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="05b52-132">[コンテナー監視ソリューション](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)ではログ分析、表示および 1 つの場所で、Docker と Windows コンテナー ホストを管理します。</span><span class="sxs-lookup"><span data-stu-id="05b52-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="05b52-133">ソリューションは、どのコンテナーを示しています。 実行して、どのようなコンテナー イメージを実行していると、コンテナーが実行されています。</span><span class="sxs-lookup"><span data-stu-id="05b52-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="05b52-134">コンテナーで使用されているコマンドを含む、詳細な監査情報を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="05b52-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="05b52-135">また、コンテナーを表示し、Docker または Windows のホストをリモートで表示することがなく一元的なログを検索トラブルシューティングすることもできます。</span><span class="sxs-lookup"><span data-stu-id="05b52-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="05b52-136">ホスト上のノイズの多いと使用の余分なリソースがあるコンテナーを検索できます。</span><span class="sxs-lookup"><span data-stu-id="05b52-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="05b52-137">さらに、一元的な CPU、メモリ、記憶域、およびネットワーク使用率およびパフォーマンスについては、コンテナーを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="05b52-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="05b52-138">Windows を実行するコンピューター上には、集中管理し、Windows Server からログを比較することができます、HYPER-V と Docker のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="05b52-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="05b52-139">ソリューションには、次のコンテナー orchestrators がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="05b52-139">The solution supports the following container orchestrators:</span></span>

-   <span data-ttu-id="05b52-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="05b52-140">Docker Swarm</span></span>

-   <span data-ttu-id="05b52-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="05b52-141">DC/OS</span></span>

-   <span data-ttu-id="05b52-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="05b52-142">Kubernetes</span></span>

-   <span data-ttu-id="05b52-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="05b52-143">Service Fabric</span></span>

-   <span data-ttu-id="05b52-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="05b52-144">Red Hat OpenShift</span></span>

<span data-ttu-id="05b52-145">図 4-11 は、さまざまなコンテナー ホストのエージェントと OMS との間の関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="05b52-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![ログ分析コンテナー監視ソリューション](./media/image11.png)

> <span data-ttu-id="05b52-147">**図 4-11。**</span><span class="sxs-lookup"><span data-stu-id="05b52-147">**Figure 4-11.**</span></span> <span data-ttu-id="05b52-148">ログ分析コンテナー監視ソリューション</span><span class="sxs-lookup"><span data-stu-id="05b52-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="05b52-149">ログ分析のコンテナーの監視ソリューションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="05b52-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

-   <span data-ttu-id="05b52-150">1 つの場所のすべてのコンテナー ホストに関する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05b52-150">See information about all container hosts in a single location.</span></span>

-   <span data-ttu-id="05b52-151">対象のコンテナを実行しているどのようなイメージを実行して、実行しています。</span><span class="sxs-lookup"><span data-stu-id="05b52-151">Know which containers are running, what image they're running, and where they're running.</span></span>

-   <span data-ttu-id="05b52-152">コンテナーにおけるアクションの監査証跡を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05b52-152">See an audit trail for actions on containers.</span></span>

-   <span data-ttu-id="05b52-153">表示して、Docker ホストへのリモート ログインに関係なく一元的なログを検索してトラブルシューティングを行います。</span><span class="sxs-lookup"><span data-stu-id="05b52-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

-   <span data-ttu-id="05b52-154">「ノイズの多い近隣」場合があり、ホスト上余分なリソースを消費するコンテナーを検索します。</span><span class="sxs-lookup"><span data-stu-id="05b52-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

-   <span data-ttu-id="05b52-155">一元的な CPU、メモリ、記憶域、およびネットワーク使用率およびパフォーマンスについては、コンテナーを表示します。</span><span class="sxs-lookup"><span data-stu-id="05b52-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="05b52-156">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="05b52-156">Additional resources</span></span>

-   <span data-ttu-id="05b52-157">**Microsoft Azure での監視の概要**</span><span class="sxs-lookup"><span data-stu-id="05b52-157">**Overview of monitoring in Microsoft Azure**</span></span>

[<span data-ttu-id="05b52-158">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview</span><span class="sxs-lookup"><span data-stu-id="05b52-158">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview</span></span>](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   <span data-ttu-id="05b52-159">**Application Insights とは何ですか。**</span><span class="sxs-lookup"><span data-stu-id="05b52-159">**What is Application Insights?**</span></span>

[<span data-ttu-id="05b52-160">https://docs.microsoft.com/azure/application-insights/app-insights-overview</span><span class="sxs-lookup"><span data-stu-id="05b52-160">https://docs.microsoft.com/azure/application-insights/app-insights-overview</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   <span data-ttu-id="05b52-161">**ログ分析は何ですか。**</span><span class="sxs-lookup"><span data-stu-id="05b52-161">**What is Log Analytics?**</span></span>

[<span data-ttu-id="05b52-162">https://docs.microsoft.com/azure/log-analytics/log-analytics-overview</span><span class="sxs-lookup"><span data-stu-id="05b52-162">https://docs.microsoft.com/azure/log-analytics/log-analytics-overview</span></span>](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   <span data-ttu-id="05b52-163">**ログ分析でコンテナー監視ソリューション**</span><span class="sxs-lookup"><span data-stu-id="05b52-163">**Container Monitoring solution in Log Analytics**</span></span>

[<span data-ttu-id="05b52-164">https://docs.microsoft.com/azure/log-analytics/log-analytics-containers</span><span class="sxs-lookup"><span data-stu-id="05b52-164">https://docs.microsoft.com/azure/log-analytics/log-analytics-containers</span></span>](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   <span data-ttu-id="05b52-165">**Azure のモニターの概要**</span><span class="sxs-lookup"><span data-stu-id="05b52-165">**Overview of Azure Monitor**</span></span>

[<span data-ttu-id="05b52-166">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor</span><span class="sxs-lookup"><span data-stu-id="05b52-166">https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor</span></span>](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   <span data-ttu-id="05b52-167">**Operations Management Suite (OMS) とは何ですか。**</span><span class="sxs-lookup"><span data-stu-id="05b52-167">**What is Operations Management Suite (OMS)?**</span></span>

[<span data-ttu-id="05b52-168">https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview</span><span class="sxs-lookup"><span data-stu-id="05b52-168">https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview</span></span>](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   <span data-ttu-id="05b52-169">**OMS を使用して Service Fabric で Windows Server コンテナーの監視**</span><span class="sxs-lookup"><span data-stu-id="05b52-169">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

[<span data-ttu-id="05b52-170">https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver</span><span class="sxs-lookup"><span data-stu-id="05b52-170">https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver</span></span>](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
<span data-ttu-id="05b52-171">[前へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[次へ](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="05b52-171">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>

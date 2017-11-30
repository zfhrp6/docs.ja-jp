---
title: "コンテナー化アプリケーションのサービスを監視します。"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3e4a78eb47d0e6712919c89b6f52ec8e4248fb23
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2017
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="5c6f4-104">コンテナー化アプリケーションのサービスを監視します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-104">Monitor containerized application services</span></span>

<span data-ttu-id="5c6f4-105">監視して、アプリケーションの動作を分析する方法があるアプリケーションを複数のコンテナーと microservices に分割が重要です。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-105">It is critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the application.</span></span>

## <a name="microsoft-application-insights"></a><span data-ttu-id="5c6f4-106">Microsoft Application Insights</span><span class="sxs-lookup"><span data-stu-id="5c6f4-106">Microsoft Application Insights</span></span>

<span data-ttu-id="5c6f4-107">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview)ライブ アプリケーションを監視する拡張可能な分析サービスです。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-107">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="5c6f4-108">検出し、パフォーマンスの問題を診断し、ユーザーはどの機能実際にアプリを理解するために実行できます。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-108">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="5c6f4-109">継続的にパフォーマンスを改善するのに役立つことを目的と使いやすさのサービスやアプリケーションの開発者に設計されています。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-109">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="5c6f4-110">Application Insights は、web/サービスとスタンドアロンの両方で、さまざまなプラットフォームなど、.NET、Java、Node.js とその他の多くのプラットフォームでは、ホストの内部設置型またはクラウド上のアプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-110">Application Insights works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a><span data-ttu-id="5c6f4-111">QA を Application Insights を使用する環境でのアプリの Docker の分析</span><span class="sxs-lookup"><span data-stu-id="5c6f4-111">Analyzing Docker apps in QA environments using Application Insights</span></span>

<span data-ttu-id="5c6f4-112">Docker に関連してライフ サイクル イベントおよび Application Insights での Docker コンテナーからパフォーマンス カウンターをグラフにできます。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-112">As it pertains to Docker, you can chart life-cycle events and performance counters from Docker containers on Application Insights.</span></span> <span data-ttu-id="5c6f4-113">だけを実行する必要があります、[アプリケーション Insights Docker イメージ](https://hub.docker.com/r/microsoft/applicationinsights/)コンテナー、ホストとそれには他の Docker images と同様にホストのパフォーマンス カウンターを表示します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-113">You just need to run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) as a container in your host, and it will display performance counters for the host as well as for the other Docker images.</span></span> <span data-ttu-id="5c6f4-114">このアプリケーション Insights Docker イメージ (図 6-1) に役立つパフォーマンスおよびアクティビティの Docker ホスト (つまり、Linux Vm)、Docker コンテナーと実行中のアプリケーションに関する製品利用統計情報を収集して、コンテナー化アプリケーションを監視するには内にします。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-114">This Application Insights Docker image (Figure 6-1) helps you to monitor your containerized applications by collecting telemetry about the performance and activity of your Docker host (that is, your Linux VMs), Docker containers and the applications running within them.</span></span>

![例](./media/image1.png)

<span data-ttu-id="5c6f4-116">図 6-1。 Application Insights の Docker ホストとコンテナーの監視</span><span class="sxs-lookup"><span data-stu-id="5c6f4-116">Figure 6-1: Application Insights monitoring Docker hosts and containers</span></span>

<span data-ttu-id="5c6f4-117">実行すると、[アプリケーション Insights Docker イメージ](https://hub.docker.com/r/microsoft/applicationinsights/)Docker ホスト上のメリットが以下。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-117">When you run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) on your Docker host, you benefit from the following:</span></span>

-   <span data-ttu-id="5c6f4-118">ホストで実行されているすべてのコンテナーに関する製品利用統計情報のライフ サイクル-開始、停止、およびなどです。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-118">Life-cycle telemetry about all the containers running on the host—start, stop, and so on.</span></span>

-   <span data-ttu-id="5c6f4-119">すべてのコンテナーのパフォーマンス カウンター: CPU、メモリ、ネットワーク使用率などです。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-119">Performance counters for all the containers: CPU, memory, network usage, and more.</span></span>

-   <span data-ttu-id="5c6f4-120">インストールされている場合[Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)アプリでは、コンテナーで実行されている、それらのアプリのすべてのテレメトリは、コンテナーとホスト マシンを識別するプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-120">If you also installed [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) in the apps running in the containers, all the telemetry of those apps will have additional properties identifying the container and host machine.</span></span> <span data-ttu-id="5c6f4-121">したがって、たとえば、複数のホストで実行されているアプリのインスタンスがあれば、簡単にされますホストによってアプリのテレメトリをフィルター処理すること。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-121">So, for example, if you have instances of an app running in more than one host, you'll easily be able to filter your app telemetry by host.</span></span>

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a><span data-ttu-id="5c6f4-122">Application Insights を設定するアプリケーションの Docker と Docker ホストを監視するには</span><span class="sxs-lookup"><span data-stu-id="5c6f4-122">Setting up Application Insights to monitor Docker applications and Docker hosts</span></span>

<span data-ttu-id="5c6f4-123">Application Insights リソースを作成するには、下記の一覧に表示される記事は、設定を指示します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-123">To create an Application Insights resource, follow the instructions in the articles presented in the list that follows.</span></span> <span data-ttu-id="5c6f4-124">Azure ポータルを必要なスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-124">Azure Portal will create the necessary script for you.</span></span>

-   <span data-ttu-id="5c6f4-125">**Application Insights での Docker アプリケーションの監視:**[https://docs.microsoft.com/azure/application-insights/app-insights-docker  ](https://docs.microsoft.com/azure/application-insights/app-insights-docker)</span><span class="sxs-lookup"><span data-stu-id="5c6f4-125">**Monitor Docker applications in Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)</span></span>

-   <span data-ttu-id="5c6f4-126">**Docker Hub、Github にあるアプリケーション Insights Docker イメージ:**</span><span class="sxs-lookup"><span data-stu-id="5c6f4-126">**Application Insights Docker image at Docker Hub and Github:**</span></span>  
<span data-ttu-id="5c6f4-127">[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/)と<https://github.com/Microsoft/ApplicationInsights-Docker></span><span class="sxs-lookup"><span data-stu-id="5c6f4-127">[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) and <https://github.com/Microsoft/ApplicationInsights-Docker></span></span>

-   <span data-ttu-id="5c6f4-128">**ASP.NET の Application Insights を設定します。**</span><span class="sxs-lookup"><span data-stu-id="5c6f4-128">**Set up Application Insights for ASP.NET:**</span></span>  
[<span data-ttu-id="5c6f4-129">https://docs.microsoft.com/azure/application-insights/app-insights-asp-net</span><span class="sxs-lookup"><span data-stu-id="5c6f4-129">https://docs.microsoft.com/azure/application-insights/app-insights-asp-net</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   <span data-ttu-id="5c6f4-130">**Web ページの application Insights:**</span><span class="sxs-lookup"><span data-stu-id="5c6f4-130">**Application Insights for web pages:**</span></span>  
<span data-ttu-id="5c6f4-131"><https://docs.microsoft.com/azure/application-insights/app-insights-javascript></span><span class="sxs-lookup"><span data-stu-id="5c6f4-131"><https://docs.microsoft.com/azure/application-insights/app-insights-javascript></span></span>

## <a name="microsoft-operations-management-suite"></a><span data-ttu-id="5c6f4-132">Microsoft Operations Management Suite</span><span class="sxs-lookup"><span data-stu-id="5c6f4-132">Microsoft Operations Management Suite</span></span>

<span data-ttu-id="5c6f4-133">[Operations Management Suite](http://microsoft.com/oms)簡略化された IT 管理ソリューションをログ分析、automation、backup、およびサイトの回復を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-133">[Operations Management Suite](http://microsoft.com/oms) is a simplified IT management solution that provides log analytics, automation, backup, and site recovery.</span></span> <span data-ttu-id="5c6f4-134">基づく[クエリ](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/)Operations Management Suite に上げることができます[アラート](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts)経由で修復を設定および[Azure Automation](https://docs.microsoft.com/azure/automation/)です。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-134">Based on [queries](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) in Operations Management Suite, you can raise [alerts](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) and set remediation via [Azure Automation](https://docs.microsoft.com/azure/automation/).</span></span> <span data-ttu-id="5c6f4-135">1 つのペインのガラスのビューを提供する、既存の管理ソリューションともシームレスに統合できます。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-135">It also seamlessly integrates with your existing management solutions to provide a single pane-of-glass view.</span></span> <span data-ttu-id="5c6f4-136">Operations Management Suite は、管理し、オンプレミスの保護およびインフラストラクチャをクラウドに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-136">Operations Management Suite helps you to manage and protect your on-premises and cloud infrastructure.</span></span>

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a><span data-ttu-id="5c6f4-137">[Operations Management Suite](http://microsoft.com/oms) Docker のコンテナー ソリューション</span><span class="sxs-lookup"><span data-stu-id="5c6f4-137">[Operations Management Suite](http://microsoft.com/oms) Container Solution for Docker</span></span>

<span data-ttu-id="5c6f4-138">自身で有益なサービスを提供することだけでなく、Operations Management Suite コンテナー ソリューション管理および監視できます Docker ホストとコンテナー、コンテナーとコンテナー ホストである、に関する情報を表示することによってコンテナーが実行されています。障害が発生した、または、Docker デーモンとコンテナーでのログに送信される*stdout*と*stderr*です。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-138">In addition to providing valuable services on its own, the Operations Management Suite Container Solution can manage and monitor Docker hosts and containers by showing information about where your containers and container hosts are, which containers are running or failed, and Docker daemon and container logs sent to *stdout* and *stderr*.</span></span> <span data-ttu-id="5c6f4-139">また、CPU、メモリ、ネットワーク、およびコンテナーおよびトラブルシューティングを行うし、ノイズの多い近隣ノードとコンテナーを検索に役立つホストの記憶域などのパフォーマンス メトリックを示します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-139">It also shows performance metrics such as CPU, memory, network, and storage for the container and hosts to help you troubleshoot and find noisy neighbor containers.</span></span>

![](./media/image2.png)

<span data-ttu-id="5c6f4-140">図 6-2: Operations Management Suite で示すように Docker コンテナーについて</span><span class="sxs-lookup"><span data-stu-id="5c6f4-140">Figure 6-2: Information about Docker containers shown by Operations Management Suite</span></span>

<span data-ttu-id="5c6f4-141">Application Insights と Operations Management Suite 焦点をアクティビティの監視ただし、Application Insights 重点的により、アプリ内で実行されているその SDK によりアプリ自体を監視します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-141">Application Insights and Operations Management Suite both focus on monitoring activities; however, Application Insights focuses more on monitoring the apps themselves thanks to its SDK running within the app.</span></span> <span data-ttu-id="5c6f4-142">ただし、Operations Management Suite 重点的により、ホストの周囲のインフラストラクチャとながら、非常に柔軟なデータ ドリブン/検索システム規模でログに詳細な分析を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-142">However, Operations Management Suite focuses much more on the infrastructure around the hosts, plus it offers deep analysis on logs at scale while providing a very flexible data-driven search/query system.</span></span>

<span data-ttu-id="5c6f4-143">Operations Management Suite がクラウド ベース サービスとして実装されているため素早くことができます、立ち上がっており実行中インフラストラクチャ サービスでの最小限の投資でします。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-143">Because Operations Management Suite is implemented as a cloud-based service, you can have it up and running quickly with minimal investment in infrastructure services.</span></span> <span data-ttu-id="5c6f4-144">新機能では、保存する継続的なメンテナンスに、自動的に配信され、コストをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-144">New features are delivered automatically, saving you from ongoing maintenance and upgrade costs.</span></span>

<span data-ttu-id="5c6f4-145">Operations Management Suite コンテナー ソリューションでは、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-145">Using Operations Management Suite Container Solution, you can do the following:</span></span>

-   <span data-ttu-id="5c6f4-146">集中管理し、何百万ものスケールで Docker コンテナーからログを関連付ける</span><span class="sxs-lookup"><span data-stu-id="5c6f4-146">Centralize and correlate millions of logs from Docker containers at scale</span></span>

-   <span data-ttu-id="5c6f4-147">1 つの場所のすべてのコンテナー ホストに関する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-147">See information about all container hosts in a single location</span></span>

-   <span data-ttu-id="5c6f4-148">対象のコンテナを実行しているし、実行しているどのようなイメージを実行します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-148">Know which containers are running, what image they're running, and where they're running</span></span>

-   <span data-ttu-id="5c6f4-149">コンテナー ホスト上の問題を引き起こす可能性のある「ノイズの多い近隣」コンテナーをすばやく診断します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-149">Quickly diagnose "noisy neighbor" containers that can cause problems on container hosts</span></span>

-   <span data-ttu-id="5c6f4-150">コンテナーにおけるアクションの監査証跡を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-150">See an audit trail for actions on containers</span></span>

-   <span data-ttu-id="5c6f4-151">表示し、Docker ホストへのリモート処理なしでログを一元的な検索でのトラブルシューティングします。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-151">Troubleshoot by viewing and searching centralized logs without remoting to the Docker hosts</span></span>

-   <span data-ttu-id="5c6f4-152">「ノイズの多い近隣」と、ホスト上余分なリソースを消費になる可能性があるコンテナーを検索します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-152">Find containers that might be "noisy neighbors" and consuming excess resources on a host</span></span>

-   <span data-ttu-id="5c6f4-153">一元的な CPU、メモリ、記憶域、およびコンテナーのネットワークの使用状況とパフォーマンス情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-153">View centralized CPU, memory, storage, and network usage and performance information for containers</span></span>

-   <span data-ttu-id="5c6f4-154">生成して、Docker コンテナーに Azure automation のテスト</span><span class="sxs-lookup"><span data-stu-id="5c6f4-154">Generate test Docker containers with Azure Automation</span></span>

<span data-ttu-id="5c6f4-155">型のようにクエリを実行するパフォーマンスの情報を表示する図 6-3 に示すように、パフォーマンスを = です。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-155">You can see performance information by running queries like Type=Perf, as shown in Figure 6-3.</span></span>

![DockerPerfMetricsView](./media/image3.png)<span data-ttu-id="5c6f4-157">{幅高さ"5.78625 in"を = ="3.25"}</span><span class="sxs-lookup"><span data-stu-id="5c6f4-157">{width="5.78625in" height="3.25in"}</span></span>

<span data-ttu-id="5c6f4-158">Operations Management Suite で示すように Docker ホストのパフォーマンス メトリックを図 6-3:</span><span class="sxs-lookup"><span data-stu-id="5c6f4-158">Figure 6-3: Performance metrics of Docker hosts shown by Operations Management Suite</span></span>

<span data-ttu-id="5c6f4-159">Operations Management Suite での標準機能ではまたクエリを保存できると便利ですが増えるし、システム内の傾向を検出、クエリを保持します。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-159">Saving queries is also a standard feature in Operations Management Suite and can help you keep queries you've found useful and discover trends in your system.</span></span>

<span data-ttu-id="5c6f4-160">**詳細については** でコンテナー ソリューションをインストールして、Docker の構成に関する情報を検索する[Operations Management Suite](http://microsoft.com/oms)に進み、 <https://docs.microsoft.com/azure/ログの分析/ログの分析-コンテナー>です。</span><span class="sxs-lookup"><span data-stu-id="5c6f4-160">**More info** To find information on installing and configuring the Docker container solution in [Operations Management Suite](http://microsoft.com/oms), go to <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5c6f4-161">[前](管理、運用の docker-environments.md) [次へ] (../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="5c6f4-161">[Previous] (manage-production-docker-environments.md) [Next] (../key-takeaways/index.md)</span></span>

---
title: "Docker とは何ですか。"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c75b2fa87e5aad93693c76c3bbd135044b36525f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="what-is-docker"></a><span data-ttu-id="f71c5-104">Docker とは何ですか。</span><span class="sxs-lookup"><span data-stu-id="f71c5-104">What is Docker?</span></span>

<span data-ttu-id="f71c5-105">[Docker](https://www.docker.com/)は、[オープン ソース プロジェクト](https://github.com/docker/docker)クラウドまたは内部設置型で実行でき、移植可能で自分のコンテナーとしてのアプリケーションの展開を自動化するため (を参照してください図 1-2)。</span><span class="sxs-lookup"><span data-stu-id="f71c5-105">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run in the cloud or on-premises (see Figure 1-2).</span></span> <span data-ttu-id="f71c5-106">Docker はでも、[会社](https://www.docker.com/)を昇格し、このテクノロジは、クラウド、Linux、およびなどの Microsoft Windows ベンダーと共同で作業を開発します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-106">Docker is also a [company](https://www.docker.com/) that promotes and develops this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![](./media/image2.png)

<span data-ttu-id="f71c5-107">図 1-2: ハイブリッド クラウドのすべてのレイヤーでコンテナーを展開する Docker</span><span class="sxs-lookup"><span data-stu-id="f71c5-107">Figure 1-2: Docker deploys containers at all layers of the hybrid cloud</span></span>

<span data-ttu-id="f71c5-108">Docker イメージ コンテナーは、Linux と Windows 上でネイティブに実行できます。</span><span class="sxs-lookup"><span data-stu-id="f71c5-108">Docker image containers can run natively on Linux and Windows.</span></span> <span data-ttu-id="f71c5-109">ただし、Windows イメージは Windows ホストでのみ実行できます、Linux のイメージは、Linux、ホスト、ホスト サーバーまたは VM でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="f71c5-109">However, Windows images can run only on Windows hosts and Linux images can run only on Linux hosts, meaning a host server or a VM.</span></span>

<span data-ttu-id="f71c5-110">開発者は、Windows、Linux、または macOS を開発環境を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f71c5-110">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="f71c5-111">開発用コンピューターでは、開発者は、どの Docker イメージが展開、アプリとその依存関係を含む Docker ホストを実行します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-111">On the development computer, the developer runs a Docker host to which Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="f71c5-112">Linux または Mac で作業する開発者は、Linux ベース、Docker ホストを使用して、Linux コンテナーにのみイメージを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f71c5-112">Developers who work on Linux or on the Mac use a Docker host that is Linux based, and they can create images only for Linux containers.</span></span> <span data-ttu-id="f71c5-113">(Mac で作業する開発者はコードを編集したり、Docker コマンド ライン インターフェイスを実行\[CLI\]から macOS などが、このドキュメントの作成時点で、コンテナーが macOS 上で直接実行しないでください)。Windows で作業する開発者は、Linux または Windows コンテナーのいずれかのイメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f71c5-113">(Developers working on the Mac can edit code or run the Docker command-line interface \[CLI\] from macOS, but, as of this writing, containers do not run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="f71c5-114">Docker が付属する開発環境でコンテナーをホストし、その他の開発者向けのツールを提供、 [Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows または macOS です。</span><span class="sxs-lookup"><span data-stu-id="f71c5-114">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="f71c5-115">これらの製品では、必要な VM のコンテナーをホストする (、Docker ホスト) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f71c5-115">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="f71c5-116">Docker も使用できるように[Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)エンタープライズ開発のために設計されていますが、IT チームがビルドによって使用されますが、出荷、および実稼働環境で大規模な基幹業務アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-116">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="f71c5-117">実行する[Windows コンテナー](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)ランタイムの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="f71c5-117">To run [Windows Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), there are two types of runtimes:</span></span>

-   <span data-ttu-id="f71c5-118">**Windows Server コンテナー** このランタイムには、プロセスと名前空間の分離テクノロジによる分離をアプリケーションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f71c5-118">**Windows Server Container** This runtime provides application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="f71c5-119">Windows Server コンテナーは、コンテナー ホストとホストで実行されているすべてのコンテナーに、カーネルを共有します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-119">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

-   <span data-ttu-id="f71c5-120">**HYPER-V コンテナー** で各コンテナーを大幅に最適化された VM で実行されている Windows Server コンテナーによって提供される分離性を展開します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-120">**Hyper-V Container** This expands on the isolation provided by Windows Server Containers by running each container in a highly optimized VM.</span></span> <span data-ttu-id="f71c5-121">コンテナーでは、HYPER-V、分離性を提供することは、この構成では、コンテナー ホストのカーネルを共有されません。</span><span class="sxs-lookup"><span data-stu-id="f71c5-121">In this configuration, the kernel of the container host is not shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="f71c5-122">これらのコンテナーのイメージは同じ方法で作成され、同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-122">The images for these containers are created in the same way and function the same.</span></span> <span data-ttu-id="f71c5-123">イメージからコンテナーを作成する方法に違いが、HYPER-V コンテナーの実行で追加のパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="f71c5-123">The difference is in how the container is created from the image—running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="f71c5-124">詳細については、「 [Hyper-v コンテナー](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview)です。</span><span class="sxs-lookup"><span data-stu-id="f71c5-124">For details, see [Hyper-V Containers](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).</span></span>

## <a name="comparing-docker-containers-with-vms"></a><span data-ttu-id="f71c5-125">Vm での Docker コンテナーの比較</span><span class="sxs-lookup"><span data-stu-id="f71c5-125">Comparing Docker containers with VMs</span></span>

<span data-ttu-id="f71c5-126">図 1-3 の Vm と Docker の比較を表示するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="f71c5-126">Figure 1-3 shows a comparison between VMs and Docker containers.</span></span>

<span data-ttu-id="f71c5-127">コンテナーがはるかに少ないリソースを必要とするため (たとえば、する必要はありません、完全な OS)、簡単に展開され、高速が開始します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-127">Because containers require far fewer resources (for example, they do not need a full OS), they are easy to deploy and they start fast.</span></span> <span data-ttu-id="f71c5-128">これにより、密度の高い、コストを減らす、ハードウェアの同じ単位でより多くのサービスを実行できることを意味することです。</span><span class="sxs-lookup"><span data-stu-id="f71c5-128">This makes it possible for you to have higher density, meaning that you can run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="f71c5-129">同じカーネルを実行する副作用として Vm よりも低い分離を実現します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-129">As a side effect of running on the same kernel, you achieve less isolation than VMs.</span></span>

<span data-ttu-id="f71c5-130">イメージの主な目的は、することが環境 (依存関係) 同じ上でさまざまな展開です。</span><span class="sxs-lookup"><span data-stu-id="f71c5-130">The main goal of an image is that it makes the environment (dependencies) the same across different deployments.</span></span> <span data-ttu-id="f71c5-131">つまり、コンピューターにデバッグおよび保証同じ環境内の別のコンピューターに展開できます。</span><span class="sxs-lookup"><span data-stu-id="f71c5-131">This means that you can debug it on your machine and then deploy it to another machine with the same environment guaranteed.</span></span>

<span data-ttu-id="f71c5-132">コンテナー イメージは、アプリやサービスをパッケージ化し、信頼性が高く、再現可能な方法で展開する方法です。</span><span class="sxs-lookup"><span data-stu-id="f71c5-132">A container image is a way to package an app or service and deploy it in a reliable and reproducible manner.</span></span> <span data-ttu-id="f71c5-133">この点で、Docker は、テクノロジだけではありませんも理念され、処理します。</span><span class="sxs-lookup"><span data-stu-id="f71c5-133">In this respect, Docker is not only a technology, it's also a philosophy and a process.</span></span>

<span data-ttu-id="f71c5-134">Docker を使用する場合と開発者を聞くことができません () で"、私のコンピューターしないのはなぜ実稼働環境でですか?"</span><span class="sxs-lookup"><span data-stu-id="f71c5-134">When using Docker, you will not hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="f71c5-135">できます単に言われるように、「で実行される Docker、」Docker のパッケージ化されたアプリケーションは、サポートされている Docker 環境で実行でき、すべての配置先 (Dev、QA、ステージング、運用環境などです。) 上に意図された方法を実行するためです。</span><span class="sxs-lookup"><span data-stu-id="f71c5-135">They can simply say, "It runs on Docker," because the packaged Docker application can be run on any supported Docker environment, and it will run the way it was intended to on all deployment destinations (Dev, QA, staging, production, etc.).</span></span>

![](./media/image3.png)

<span data-ttu-id="f71c5-136">Docker コンテナーへの従来の仮想マシンの図 1-3: 比較</span><span class="sxs-lookup"><span data-stu-id="f71c5-136">Figure 1-3: Comparison of traditional VMs to Docker containers</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f71c5-137">[前](index.md) [次へ] (docker terminology.md)</span><span class="sxs-lookup"><span data-stu-id="f71c5-137">[Previous] (index.md) [Next] (docker-terminology.md)</span></span>

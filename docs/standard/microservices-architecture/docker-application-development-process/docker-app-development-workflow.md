---
title: "Docker のアプリの開発のワークフロー"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker のアプリの開発のワークフロー"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="c56d0-104">Docker のアプリの開発のワークフロー</span><span class="sxs-lookup"><span data-stu-id="c56d0-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="c56d0-105">アプリケーションの開発ライフ サイクルは、各開発者のマシンを開発者がコードを使用する言語を使用して、アプリケーションと、テストをローカルで開始されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-105">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="c56d0-106">どの言語、フレームワーク、および開発者が、このワークフローは、プラットフォームに関係なく、開発者は常に開発およびテストして、Docker コンテナーがローカルでこれ。</span><span class="sxs-lookup"><span data-stu-id="c56d0-106">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="c56d0-107">各コンテナー (Docker イメージのインスタンス) には、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c56d0-107">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="c56d0-108">オペレーティング システムの選択 (たとえば、Linux ディストリビューション、Windows Nano Server、または Windows Server Core)。</span><span class="sxs-lookup"><span data-stu-id="c56d0-108">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="c56d0-109">ファイル (アプリケーションのバイナリなど) は開発者が追加されました。</span><span class="sxs-lookup"><span data-stu-id="c56d0-109">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="c56d0-110">構成情報 (環境の設定と依存関係)。</span><span class="sxs-lookup"><span data-stu-id="c56d0-110">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="c56d0-111">Docker コンテナー ベースのアプリケーションを開発するためのワークフロー</span><span class="sxs-lookup"><span data-stu-id="c56d0-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="c56d0-112">このセクションの内容について説明します、*内部ループ*Docker コンテナー ベースのアプリケーションでワークフローを開発します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="c56d0-113">内部ループ ワークフローことを意味は加味していませんより広範な DevOps ワークフローだけでは開発者のコンピューターに、開発作業について説明します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-113">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="c56d0-114">環境をセットアップする最初の手順が含まれているものが 1 回だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-114">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="c56d0-115">アプリケーションは、独自のサービスと追加のライブラリ (依存関係) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="c56d0-116">通常行う Docker アプリケーションを構築するときに図 5-1 に示すように基本的な手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="c56d0-117">**図 5-1。**</span><span class="sxs-lookup"><span data-stu-id="c56d0-117">**Figure 5-1.**</span></span> <span data-ttu-id="c56d0-118">Docker コンテナー詰めアプリケーションを開発するためのステップ バイ ステップのワークフロー</span><span class="sxs-lookup"><span data-stu-id="c56d0-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="c56d0-119">このガイドでこのプロセス全体の詳細については、主要な手順の説明には、Visual Studio 環境に焦点を当てたです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="c56d0-120">エディター/CLI 開発手法 (たとえば、Visual Studio Code と macos Docker CLI または Windows) を使用しているときに、Visual Studio を使用する場合よりも詳細には、通常、すべての手順を知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="c56d0-121">CLI 環境での作業の詳細については、電子書籍を参照してください[Microsoft プラットフォームとツールと Docker のコンテナー詰めアプリケーション ライフ サイクル](http://aka.ms/dockerlifecycleebook/)です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-121">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="c56d0-122">Visual Studio 2015 または Visual Studio 2017 を使用しているときにこれらの手順の多くは自動的に処理、生産性を大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-122">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="c56d0-123">これは、Visual Studio 2017 を使用して複数のコンテナー アプリケーションを対象とするときに特に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="c56d0-124">たとえば、1 つだけのマウス クリックでは、Visual Studio、Dockerfile と docker compose.yml ファイルを追加、プロジェクト、アプリケーションの構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-124">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="c56d0-125">Visual Studio でアプリケーションを実行するときに、Docker イメージを構築および Docker; で直接、複数のコンテナー アプリケーションを実行一度に複数のコンテナーをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="c56d0-126">これらの機能には、開発速度が上がります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-126">These features will boost your development speed.</span></span>

<span data-ttu-id="c56d0-127">ただし、Visual Studio によって、これらの手順を自動化するためにだけないわけでは何が起こっているかを知る必要はありません docker の下。</span><span class="sxs-lookup"><span data-stu-id="c56d0-127">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="c56d0-128">そのため、方法を紹介内のすべてのステップを説明します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-128">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="c56d0-129">手順 1.</span><span class="sxs-lookup"><span data-stu-id="c56d0-129">Step 1.</span></span> <span data-ttu-id="c56d0-130">コーディングを開始し、初期アプリケーションまたはサービスの基準を作成</span><span class="sxs-lookup"><span data-stu-id="c56d0-130">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="c56d0-131">Docker アプリケーションを開発することは、Docker せずアプリケーションを開発する方法に似ています。</span><span class="sxs-lookup"><span data-stu-id="c56d0-131">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="c56d0-132">違いは、Docker の開発中に展開しているアプリケーションまたはサービス、ローカル環境での Docker コンテナー内で実行するテストです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-132">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="c56d0-133">コンテナーには、Linux コンテナーまたは Windows コンテナーのいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-133">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="c56d0-134">Visual Studio で、ローカル環境をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-134">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="c56d0-135">を開始するには、必ず確保[Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows がインストールされて、次の手順で説明したようにします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-135">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="c56d0-136">Docker for Windows CE を概要します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-136">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="c56d0-137">さらに、Visual Studio 2017 年 1 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-137">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="c56d0-138">これは優先経由での Visual Studio 2015、Visual Studio Tools for Docker アドイン with Visual Studio 2017 がコンテナーのデバッグのサポートと同様に、Docker のサポートを高度なためです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-138">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="c56d0-139">選択した場合、visual Studio 2017 は Docker のツールを含めます、 **.NET Core と Docker**図 5-2 に示すように、インストール中に負荷します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-139">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="c56d0-140">**図 5-2**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-140">**Figure 5-2**.</span></span> <span data-ttu-id="c56d0-141">選択すると、 **.NET Core と Docker** Visual Studio 2017 セットアップ中にワークロード</span><span class="sxs-lookup"><span data-stu-id="c56d0-141">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="c56d0-142">(通常は .NET Core コンテナーの使用を計画している場合) での通常の .NET でアプリケーションをコーディングを開始して、アプリケーションで Docker を有効にすると、展開、および Docker でテストする前にします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-142">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="c56d0-143">ただし、実際の環境となるし、問題をできるだけ早く検出できるため、できるだけ早く Docker で作業を開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="c56d0-144">これを使用するように Visual Studio では、これを簡単に処理をほぼ感じる透過的な Docker のため、Visual Studio からの複数のコンテナー アプリケーションをデバッグするときに最適な例です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c56d0-145">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-145">Additional resources</span></span>

-   <span data-ttu-id="c56d0-146">**Docker for Windows CE の概要**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="c56d0-146">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="c56d0-147">**Visual Studio 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)</span><span class="sxs-lookup"><span data-stu-id="c56d0-147">**Visual Studio 2017**
[*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="c56d0-148">手順 2.</span><span class="sxs-lookup"><span data-stu-id="c56d0-148">Step 2.</span></span> <span data-ttu-id="c56d0-149">既存の .NET 基本イメージに関連する Dockerfile を作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="c56d0-150">を作成する各カスタム イメージの Dockerfile する必要がありますVisual Studio または Docker CLI を使用して手動でから自動的に展開するかどうかを展開するには、各コンテナーの Dockerfile が必要 (実行 docker と docker のコマンドを作成) します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="c56d0-151">アプリケーションに 1 つのカスタム サービスが含まれている場合、1 つの Dockerfile 必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="c56d0-152">アプリケーション (microservices アーキテクチャ) のように複数のサービスが含まれている場合はサービスごとに 1 つの Dockerfile する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="c56d0-153">Dockerfile は、アプリケーションまたはサービスのルート フォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="c56d0-154">Docker を設定し、コンテナーで、アプリケーションまたはサービスを実行する方法を指示するコマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c56d0-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="c56d0-155">手動でコードで、Dockerfile を作成し、.NET の依存関係と共にプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="c56d0-156">Visual Studio と Docker のツールでは、このタスクには、いくつかのマウス クリックが必要です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-156">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="c56d0-157">という名前のオプションは Visual Studio 2017 で新しいプロジェクトを作成するときに**を有効にするコンテナー (Docker) サポート**ように、図 5-3。</span><span class="sxs-lookup"><span data-stu-id="c56d0-157">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="c56d0-158">**図 5-3**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-158">**Figure 5-3**.</span></span> <span data-ttu-id="c56d0-159">Visual Studio 2017 で新しいプロジェクトを作成する場合は、Docker のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-159">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="c56d0-160">Visual Studio では、プロジェクト ファイルを右クリックし、オプションを選択して、新規または既存のプロジェクトでの Docker のサポートを有効にすることもできます**追加 Docker プロジェクトはサポート**図 5-4 に示すように、します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-160">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="c56d0-161">**図 5-4**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-161">**Figure 5-4**.</span></span> <span data-ttu-id="c56d0-162">既存の Visual Studio 2017 プロジェクトでの Docker のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-162">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="c56d0-163">(ASP.NET Web アプリケーションや Web API サービスの場合) などのプロジェクトでこの操作は、Dockerfile を必要な構成でプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-163">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="c56d0-164">また、ソリューション全体の docker compose.yml ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-164">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="c56d0-165">次のセクションでは、その各ファイルに書き込まれる情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-165">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="c56d0-166">Visual Studio は、この作業を行うことができますが、Dockerfile に何を理解すると便利です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-166">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="c56d0-167">オプション a: 既存の公式 .NET Docker イメージを使用して、プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-167">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="c56d0-168">通常、公式のリポジトリから取得できます、基本イメージの上にコンテナーのカスタム イメージをビルドする、 [Docker Hub](https://hub.docker.com/)レジストリです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-168">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="c56d0-169">ある正確に Visual Studio での Docker のサポートを有効にすると、バック グラウンドで動作します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-169">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="c56d0-170">Dockerfile では、既存の aspnetcore イメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-170">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="c56d0-171">以前どの Docker images とフレームワークと選択した OS に応じて、使用できるリポジトリを説明します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-171">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="c56d0-172">たとえば、ASP.NET Core (Linux または Windows) を使用する場合は、使用するイメージは、microsoft/aspnetcore:2.0 です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-172">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="c56d0-173">したがって、のみ、どのようなコンテナーを使用する基本の Docker イメージを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-173">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="c56d0-174">Microsoft から追加することによって行うを/、Dockerfile を aspnetcore:2.0 です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-174">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="c56d0-175">Visual Studio によって自動的に実行これがこの値を更新するバージョンを更新する場合は。</span><span class="sxs-lookup"><span data-stu-id="c56d0-175">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="c56d0-176">バージョン番号を Docker Hub からの公式の .NET イメージ リポジトリを使うと、同じ言語の機能が (開発、テスト、および実稼働環境を含む) すべてのマシンで使用できることができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-176">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="c56d0-177">次の例では、Dockerfile ASP.NET Core コンテナー用のサンプルを示します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-177">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="c56d0-178">この場合、コンテナーは、バージョン 2.0 の公式の ASP.NET Core Docker イメージ (Linux と Windows のマルチ arch) に基づきます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-178">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="c56d0-179">これは、設定`FROM microsoft/aspnetcore:2.0`です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-179">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="c56d0-180">(この基本イメージに関する詳細については、次を参照してください、 [ASP.NET Core Docker イメージ](https://hub.docker.com/r/microsoft/aspnetcore/)ページおよび[.NET Core Docker イメージ](https://hub.docker.com/r/microsoft/dotnet/)ページです。)。Dockerfile で (ここでは、ポート 80、公開設定で構成された) の実行時に使用する TCP ポートでリッスンするように Docker に指示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-180">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="c56d0-181">言語とを使用しているフレームワークによって、Dockerfile では、追加の構成設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-181">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="c56d0-182">インスタンスでは、ENTRYPOINT 行\["dotnet"、"MySingleContainerWebApp.dll"\] .NET Core アプリケーションの実行に Docker に指示します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-182">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="c56d0-183">SDK と .NET Core CLI (dotnet CLI) をビルドして、.NET アプリケーションの実行を使用している場合、この設定は別になります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-183">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="c56d0-184">一番下の行が、エントリ ポイントの行とその他の設定になります、アプリケーション用に選択した言語とプラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-184">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c56d0-185">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-185">Additional resources</span></span>

-   <span data-ttu-id="c56d0-186">**.NET Core アプリケーションの Docker イメージを構築**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="c56d0-186">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)</span></span>

-   <span data-ttu-id="c56d0-187">**独自のイメージを構築**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-187">**Build your own image**.</span></span> <span data-ttu-id="c56d0-188">Docker、公式のドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-188">In the official Docker documentation.</span></span>
    [<span data-ttu-id="c56d0-189">*https://docs.docker.com/engine/tutorials/dockerimages/*</span><span class="sxs-lookup"><span data-stu-id="c56d0-189">*https://docs.docker.com/engine/tutorials/dockerimages/*</span></span>](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="c56d0-190">マルチ arch イメージ リポジトリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-190">Using multi-arch image repositories</span></span>

<span data-ttu-id="c56d0-191">1 つのリポジトリには、Linux イメージと Windows イメージなどのプラットフォームのバリエーションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-191">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="c56d0-192">この機能は、Microsoft (基本イメージの作成者) のようなベンダーは (つまり、Linux および Windows) に複数のプラットフォームに対応する 1 つのリポジトリを作成するを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-192">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="c56d0-193">たとえば、 [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub レジストリに使用可能なリポジトリが同じリポジトリ名を使用して Linux および Windows Nano Server のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-193">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="c56d0-194">タグを指定すると、明示的なプラットフォームを対象とする場合は、次の場合と同様に。</span><span class="sxs-lookup"><span data-stu-id="c56d0-194">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="c56d0-195">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="c56d0-195">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="c56d0-196">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="c56d0-196">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="c56d0-197">しかし、これは、2017 中旬以降新しいを指定する場合、同じイメージの名前も、同じタグ (複数のアーキテクチャをサポートする aspnetcore イメージ) のような新しいマルチ arch イメージが展開して、Docker ホスト OS によって Linux または Windows のバージョンを使用して、、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-197">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="c56d0-198">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="c56d0-198">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="c56d0-199">この方法により、Windows ホストからイメージをプルするときは、その Windows バリアントをプルして、Linux バリアントがプルする Linux ホストから同じイメージの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-199">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="c56d0-200">オプション b: は最初から基本イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-200">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="c56d0-201">独自 Docker の基本イメージは、最初から作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-201">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="c56d0-202">Docker、によって開始しているユーザーに対してこのシナリオは推奨されませんが、独自の基本イメージの特定のビットを設定する場合は、これを行います。</span><span class="sxs-lookup"><span data-stu-id="c56d0-202">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c56d0-203">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-203">Additional resources</span></span>

-   <span data-ttu-id="c56d0-204">**.NET Core イメージを複数 arch**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-204">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="c56d0-205">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="c56d0-205">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="c56d0-206">**基本イメージを作成する**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-206">**Create a base image**.</span></span> <span data-ttu-id="c56d0-207">Docker の正式なドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-207">Official Docker documentation.</span></span>
    [<span data-ttu-id="c56d0-208">*https://docs.docker.com/engine/userguide/eng-image/baseimages/*</span><span class="sxs-lookup"><span data-stu-id="c56d0-208">*https://docs.docker.com/engine/userguide/eng-image/baseimages/*</span></span>](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="c56d0-209">手順 3.</span><span class="sxs-lookup"><span data-stu-id="c56d0-209">Step 3.</span></span> <span data-ttu-id="c56d0-210">カスタム Docker イメージを作成し、それらのアプリケーションまたはサービスを埋め込む</span><span class="sxs-lookup"><span data-stu-id="c56d0-210">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="c56d0-211">各サービスに対して、アプリケーションで、関連するイメージを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-211">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="c56d0-212">1 つのサービスまたは web アプリケーションのアプリケーションが構成されている場合は、1 つのイメージだけができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-212">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="c56d0-213">Docker images する用 Visual Studio でに自動的に構築されたに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c56d0-213">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="c56d0-214">次の手順はのみエディター/CLI ワークフローに必要なし、わかりやすくするための下にどうなるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-214">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="c56d0-215">Developer、する必要がありますプッシュ、完了するまでにローカルで開発およびテスト機能、または (GitHub) する場合など、ソース管理システムに変更します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-215">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="c56d0-216">これは、Docker イメージを作成してローカルの Docker ホスト (Windows または Linux VM) にコンテナーを展開して実行、テスト、およびそれらのコンテナーをローカルでデバッグする必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-216">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="c56d0-217">Docker CLI と、Dockerfile を使用して、ローカル環境でカスタム イメージを作成するには、docker のビルド コマンド、図 5-5 を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-217">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="c56d0-218">**図 5-5**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-218">**Figure 5-5**.</span></span> <span data-ttu-id="c56d0-219">カスタム Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-219">Creating a custom Docker image</span></span>

<span data-ttu-id="c56d0-220">必要に応じて、プロジェクト フォルダーから docker ビルドを直接実行するには、代わりに最初に、必要な .NET ライブラリの配置可能なフォルダーを生成することができ、dotnet を実行して、バイナリは、発行、および、docker ビルド コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-220">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="c56d0-221">Docker イメージを作成、名前 cesardl/netcore-webapi-マイクロ サービスをこれには-docker: 最初。</span><span class="sxs-lookup"><span data-stu-id="c56d0-221">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="c56d0-222">この例では、: 特定のバージョンを表すタグを 1 つ目はします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-222">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="c56d0-223">カスタム イメージが構成される Docker アプリケーションを作成する必要がありますごとには、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-223">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="c56d0-224">複数のコンテナーのアプリケーションが行われる場合 (つまり、これがマルチ コンテナー アプリケーションの場合)、使用することも、--関連で公開されるメタデータを使用して単一のコマンドですべての関連するイメージを作成するビルドのコマンドを docker 構成docker compose.yml ファイル。</span><span class="sxs-lookup"><span data-stu-id="c56d0-224">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="c56d0-225">既存のイメージ、ローカル リポジトリに docker を使用してイメージ コマンドは検索できます、図 5-6 に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-225">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="c56d0-226">**図 5 ~ 6 です。**</span><span class="sxs-lookup"><span data-stu-id="c56d0-226">**Figure 5-6.**</span></span> <span data-ttu-id="c56d0-227">Docker イメージのコマンドを使用して既存のイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-227">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="c56d0-228">Visual Studio で Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-228">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="c56d0-229">Visual Studio を使用して、Docker のサポートでプロジェクトを作成する場合は、明示的に作成しないイメージ。</span><span class="sxs-lookup"><span data-stu-id="c56d0-229">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="c56d0-230">代わりに、f5 キーを押して dockerized アプリケーションまたはサービスを実行するのイメージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-230">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="c56d0-231">この手順は Visual Studio で、自動と、発生することは表示されませんが行われている内容を知ることは重要であるにします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-231">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="c56d0-232">手順 4.</span><span class="sxs-lookup"><span data-stu-id="c56d0-232">Step 4.</span></span> <span data-ttu-id="c56d0-233">複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-233">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="c56d0-234">[Docker compose.yml](https://docs.docker.com/compose/compose-file/)ファイルでは、デプロイ コマンドで構成されるアプリケーションとして配置するのには関連するサービスのセットを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-234">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="c56d0-235">Docker compose.yml ファイルを使用するには、次の例に似たコンテンツを持つ、主にファイルまたはソリューションのルート フォルダーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-235">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

<span data-ttu-id="c56d0-236">この docker compose.yml ファイルに簡略化し、マージされたバージョンがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c56d0-236">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="c56d0-237">接続文字列のように、デプロイ環境に依存している構成情報に加えて、常に適用される (など、カスタム イメージの名前)、各コンテナーの静的構成データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c56d0-237">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="c56d0-238">以降のセクションで、docker compose.yml 構成に複数の分割方法を学習は docker 構成ファイルと環境と実行の種類 (デバッグまたはリリース) によってオーバーライド値。</span><span class="sxs-lookup"><span data-stu-id="c56d0-238">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="c56d0-239">Docker compose.yml ファイルの例は、5 つのサービスを定義します。 webmvc サービス (web アプリケーション)、2 つの microservices (catalog.api および ordering.api)、および 1 つのデータ ソース コンテナー、sql.data、コンテナーとして実行されている Linux に SQL Server に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c56d0-239">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="c56d0-240">各サービスは、Docker イメージはそれぞれに必要なため、コンテナーとして配置されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-240">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="c56d0-241">Docker compose.yml ファイルは、どのようなコンテナーを使用しているだけでなく、個別の構成方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-241">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="c56d0-242">たとえば、webmvc コンテナー ファイル内の定義、.yml:</span><span class="sxs-lookup"><span data-stu-id="c56d0-242">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="c56d0-243">構築済み eshop を使用して/web: 最新バージョンのイメージです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-243">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="c56d0-244">ただしを構成することも、イメージの一部として作成される、docker 構成ビルドに基づいて実行を追加の構成: docker-compose ファイル内のセクションです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-244">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="c56d0-245">2 つの環境変数 (CatalogUrl および OrderingUrl) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-245">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="c56d0-246">公開されているポート 80、ホスト コンピューター上の外部ポート 80 をコンテナー上を転送します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-246">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="c56d0-247">カタログと順序付けのサービスに web アプリをリンク、依存\_設定にします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-247">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="c56d0-248">これにより、それらのサービスを開始するまで待機するサービスです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-248">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="c56d0-249">お microservices と複数のコンテナーのアプリを実装する方法について説明しているときに後のセクションで、docker compose.yml ファイルを再確認します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-249">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="c56d0-250">Visual Studio 2017 での docker compose.yml の操作</span><span class="sxs-lookup"><span data-stu-id="c56d0-250">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="c56d0-251">図 5-7 に示すように、Visual Studio ソリューションでサービス プロジェクトに Docker ソリューションのサポートを追加する場合は、Visual Studio がプロジェクトに Dockerfile を追加し、docker compose.yml ファイルとソリューションのサービス セクション (プロジェクト) を追加します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-251">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="c56d0-252">これは、複数のコンテナー ソリューションの作成を開始する簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-252">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="c56d0-253">Docker compose.yml ファイルを開くし、それらを他の機能も更新します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-253">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="c56d0-254">**図 5-7**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-254">**Figure 5-7**.</span></span> <span data-ttu-id="c56d0-255">ASP.NET Core プロジェクトを右クリックして Visual Studio 2017 で Docker のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-255">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="c56d0-256">Visual Studio での Docker のサポートを追加するだけでなく、Dockerfile をプロジェクトに追加、構成情報をソリューション レベルで設定されているいくつかのグローバル docker compose.yml ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-256">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="c56d0-257">Visual Studio でソリューションに Docker のサポートを追加した後は、図 5-8 に示すように、追加の docker compose.yml ファイルを含むソリューション エクスプ ローラーで新しいノード (docker compose.dcproj プロジェクト ファイル) にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-257">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="c56d0-258">**図 5-8**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-258">**Figure 5-8**.</span></span> <span data-ttu-id="c56d0-259">**Docker 構成**ツリー ノードを Visual Studio 2017 のソリューション エクスプ ローラーの追加</span><span class="sxs-lookup"><span data-stu-id="c56d0-259">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="c56d0-260">使用して単一の docker compose.yml ファイルを使用して複数のコンテナー アプリケーションを展開する可能性があります、docker にコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-260">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="c56d0-261">環境 (運用と開発) と実行によっての値をオーバーライドするために、Visual Studio がそれらのグループを追加するただし、型 (デバッグとリリース)。</span><span class="sxs-lookup"><span data-stu-id="c56d0-261">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="c56d0-262">この機能は、以降のセクションで説明されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-262">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="c56d0-263">手順 5.</span><span class="sxs-lookup"><span data-stu-id="c56d0-263">Step 5.</span></span> <span data-ttu-id="c56d0-264">ビルドおよび実行する、Docker アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c56d0-264">Build and run your Docker application</span></span>

<span data-ttu-id="c56d0-265">アプリケーションの 1 つのコンテナーのみの場合は、Docker ホスト (仮想マシンまたは物理サーバー) に展開することで実行できます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-265">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="c56d0-266">ただし、アプリケーションに複数のサービスが含まれている場合として展開できますが、構成されたアプリケーションを 1 つの CLI コマンドを使用するか (docker の構成を)、または Visual Studio が、内部的には、そのコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-266">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="c56d0-267">さまざまなオプションを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="c56d0-267">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="c56d0-268">オプション a: Docker CLI での単一のコンテナーの実行</span><span class="sxs-lookup"><span data-stu-id="c56d0-268">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="c56d0-269">Docker run コマンド、図 5 ~ 9 を使用して Docker コンテナーを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-269">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="c56d0-270">**図 5-9**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-270">**Figure 5-9**.</span></span> <span data-ttu-id="c56d0-271">Docker run コマンドを使用して Docker コンテナーの実行</span><span class="sxs-lookup"><span data-stu-id="c56d0-271">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="c56d0-272">ここでは、コマンドは、ホスト コンピューターのポート 80 をコンテナーの内部ポート 5000 をバインドします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-272">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="c56d0-273">これには、ホストがポート 80 でリッスンしていると、コンテナーに 5000 のポートに転送することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-273">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="c56d0-274">オプション b: 複数のコンテナー アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-274">Option B: Running a multi-container application</span></span>

<span data-ttu-id="c56d0-275">ほとんどのエンタープライズ シナリオで Docker アプリケーションはで構成される複数のサービスは図 5 ~ 10 に示すように複数のコンテナーのアプリケーションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-275">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="c56d0-276">**図 5-10**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-276">**Figure 5-10**.</span></span> <span data-ttu-id="c56d0-277">展開されている Docker コンテナーでの VM</span><span class="sxs-lookup"><span data-stu-id="c56d0-277">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="c56d0-278">Docker CLI を使用して複数のコンテナー アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-278">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="c56d0-279">Docker を実行するアプリケーションを実行する、複数のコンテナー Docker CLI を使用してのコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-279">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="c56d0-280">マルチ コンテナー アプリケーションを展開するソリューション レベルであるこのコマンドは docker compose.yml ファイルです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-280">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="c56d0-281">図 5-11 は、docker compose.yml ファイルを含む、メイン プロジェクト ディレクトリから、コマンドを実行する場合、結果を示します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-281">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="c56d0-282">**図 5-11**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-282">**Figure 5-11**.</span></span> <span data-ttu-id="c56d0-283">例の結果は実行されている場合、コマンドを docker 構成</span><span class="sxs-lookup"><span data-stu-id="c56d0-283">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="c56d0-284">Docker の後にコマンドの実行を作成、VM 形式を図 5 ~ 10 に示すように、Docker ホストに展開されたアプリケーションとその関連するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-284">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="c56d0-285">実行していると、Visual Studio での複数のコンテナー アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="c56d0-285">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="c56d0-286">Visual Studio 2017 を使用して複数のコンテナー アプリケーションを実行する単純なを取得できません。</span><span class="sxs-lookup"><span data-stu-id="c56d0-286">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="c56d0-287">ことができます実行だけでなく、複数のコンテナー アプリケーションが標準のブレークポイントを設定して Visual Studio から直接のすべてのコンテナーをデバッグすることです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-287">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="c56d0-288">前述のたびに、ソリューション内のプロジェクトに Docker ソリューションのサポートを追加する前に、そのプロジェクトがソリューション全体を一度にデバッグまたは実行することができます、グローバル (ソリューション レベル) docker compose.yml ファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-288">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="c56d0-289">Visual Studio は Docker ソリューションのサポートが有効になっているプロジェクトごとに 1 つのコンテナーを起動し、内部のすべての手順を実行する (dotnet 発行、docker ビルドなどです。)。</span><span class="sxs-lookup"><span data-stu-id="c56d0-289">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="c56d0-290">ここで重要なは、図 5-12 に示すように、Visual Studio 2017 では、追加**Docker**コマンドで、F5 キーを操作します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-290">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="c56d0-291">このオプションでは、ソリューション レベルで docker compose.yml ファイルで定義されているすべてのコンテナーを実行して、複数のコンテナー アプリケーションをデバッグまたは実行できることができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-291">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="c56d0-292">複数のコンテナー ソリューションをデバッグする機能にすると複数のブレークポイント、それぞれのブレークポイントを設定するには、別のプロジェクト (コンテナー) で Visual Studio からのデバッグ中には、別々 のプロジェクトで定義されているしで実行されているブレークポイントで停止別のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-292">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="c56d0-293">**図 5-12**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-293">**Figure 5-12**.</span></span> <span data-ttu-id="c56d0-294">Visual Studio 2017 で複数のコンテナーのアプリの実行</span><span class="sxs-lookup"><span data-stu-id="c56d0-294">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c56d0-295">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-295">Additional resources</span></span>

-   <span data-ttu-id="c56d0-296">**ASP.NET コンテナー ホストに展開してリモート Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="c56d0-296">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="c56d0-297">テストと orchestrators と展開に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="c56d0-297">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="c56d0-298">Docker 構成し、実行 docker コマンド (またはを実行していると Visual Studio でのコンテナーのデバッグ) が適切では、開発環境でコンテナーをテストします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-298">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="c56d0-299">対象としている Docker クラスター orchestrators などの Docker Swarm 続き DC/OS、Kubernetes 場合に、このアプローチを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c56d0-299">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="c56d0-300">ようにクラスターを使用している場合[Docker Swarm モード](https://docs.docker.com/engine/swarm/)(以降で使用可能で Docker CE および Windows 用の Mac バージョン 1.12)、する必要があります配置およびテストのような追加のコマンドで[docker サービスを作成](https://docs.docker.com/engine/reference/commandline/service_create/)の1 つのサービスです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-300">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="c56d0-301">使用する場合は、複数のコンテナーから成るアプリケーションを展開する場合は、[バンドルを作成する docker](https://docs.docker.com/compose/reference/bundle/)と[docker 展開 myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/)として構成されたアプリケーションを配置する、*スタック*.</span><span class="sxs-lookup"><span data-stu-id="c56d0-301">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="c56d0-302">詳細については、ブログの投稿を参照してください。 [Introducing 実験的な分散アプリケーションのバンドル](https://blog.docker.com/2016/06/docker-app-bundle/)Docker のドキュメントにします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-302">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="c56d0-303">Docker のサイトです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-303">on the Docker site.</span></span>

<span data-ttu-id="c56d0-304">[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)と[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/)さまざまな展開コマンドおよびスクリプトも使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-304">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="c56d0-305">手順 6.</span><span class="sxs-lookup"><span data-stu-id="c56d0-305">Step 6.</span></span> <span data-ttu-id="c56d0-306">Docker をローカルの Docker ホストを使用してアプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-306">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="c56d0-307">この手順は、アプリケーションの実行内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-307">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="c56d0-308">1 つのコンテナーまたはサービスとして展開されている単純な .NET Core の Web アプリケーションで Docker ホストのブラウザーを開き、図 5-13 ように、そのサイトに移動して、サービスにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-308">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="c56d0-309">(場合は、Dockerfile の構成は、ポート 80 以外のものであるホストに、コンテナーをマップ ホスト ポスト URL に含める。)</span><span class="sxs-lookup"><span data-stu-id="c56d0-309">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host post in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="c56d0-310">**図 5-13**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-310">**Figure 5-13**.</span></span> <span data-ttu-id="c56d0-311">Localhost を使用してローカルで Docker アプリケーションのテストの例</span><span class="sxs-lookup"><span data-stu-id="c56d0-311">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="c56d0-312">Docker を localhost をポイントしていない場合は、IP をホスト (既定では、Docker の CE を使用する場合、その必要があります)、サービスに移動するには、マシンのネットワーク カードの IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-312">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="c56d0-313">ブラウザーでこの URL が説明されている例では、特定のコンテナーをポート 80 を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c56d0-313">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="c56d0-314">ただし、内部的には、要求にリダイレクトされます-port 5000、前の手順で説明するよう、docker run コマンド、付きで展開されて方法があるためです。</span><span class="sxs-lookup"><span data-stu-id="c56d0-314">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="c56d0-315">図 5-14 に示すように、ターミナルから curl を使用してアプリケーションをテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-315">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="c56d0-316">Windows 上の Docker のインストール、使用する既定値の Docker ホストの IP とは、常にコンピューターの実際の IP アドレスに加えて 10.0.75.1 です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-316">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="c56d0-317">**図 5-14**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-317">**Figure 5-14**.</span></span> <span data-ttu-id="c56d0-318">Curl を使用してローカルで Docker アプリケーションのテストの例</span><span class="sxs-lookup"><span data-stu-id="c56d0-318">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="c56d0-319">テストと Visual Studio 2017 とコンテナーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="c56d0-319">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="c56d0-320">実行するいると、Visual Studio 2017 とコンテナーのデバッグ、するコンテナーせずに実行する場合と、ほぼ同じ方法で、.NET アプリケーションをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-320">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="c56d0-321">テストと、Visual Studio を使用せずにデバッグ</span><span class="sxs-lookup"><span data-stu-id="c56d0-321">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="c56d0-322">エディター/CLI アプローチを使用して、開発する場合はより困難にコンテナーのデバッグとトレースを生成することでデバッグします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-322">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c56d0-323">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-323">Additional resources</span></span>

-   <span data-ttu-id="c56d0-324">**ローカルの Docker コンテナーでアプリをデバッグ**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="c56d0-324">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="c56d0-325">**Steve Lasker です。ビルド、デバッグ、Docker を使用した ASP.NET Core アプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="c56d0-325">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="c56d0-326">ビデオ。</span><span class="sxs-lookup"><span data-stu-id="c56d0-326">Video.</span></span>
    [<span data-ttu-id="c56d0-327">*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*</span><span class="sxs-lookup"><span data-stu-id="c56d0-327">*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*</span></span>](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="c56d0-328">Visual Studio でのコンテナーを開発するときに、簡略化されたワークフロー</span><span class="sxs-lookup"><span data-stu-id="c56d0-328">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="c56d0-329">実際には、Visual Studio を使用するときに、ワークフローは、エディター/CLI アプローチを使用する場合よりもはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-329">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="c56d0-330">Dockerfile に関連するほとんどの Docker で必要な手順と docker compose.yml ファイルが非表示または図 5-15 に示すように、Visual Studio によって簡略化します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-330">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="c56d0-331">**図 5-15**です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-331">**Figure 5-15**.</span></span> <span data-ttu-id="c56d0-332">Visual Studio で開発するときに、簡略化されたワークフロー</span><span class="sxs-lookup"><span data-stu-id="c56d0-332">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="c56d0-333">さらに、手順 2. (プロジェクトに追加する Docker のサポート) を 1 回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-333">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="c56d0-334">したがって、.NET を使用して、その他の開発時に、ワークフローは、通常開発タスクに似ています。</span><span class="sxs-lookup"><span data-stu-id="c56d0-334">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="c56d0-335">何が起こって (イメージ ビルド プロセス、どのような基本イメージを使用する、コンテナーなどの展開) の背後および場合によっては、Dockerfile またはファイルを編集 docker compose.yml の動作をカスタマイズする必要がありますも知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c56d0-335">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="c56d0-336">ほとんどの作業がよりもずっと生産性を向上するので、Visual Studio を使用して、大幅に簡略化します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-336">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c56d0-337">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-337">Additional resources</span></span>

-   <span data-ttu-id="c56d0-338">**Steve Lasker です。Visual Studio 2017 を使用した .NET docker 開発**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="c56d0-338">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="c56d0-339">**Jeffrey T. Fritz です。Visual Studio の新しい Docker ツールを使用して、コンテナーに置かれる .NET Core アプリ**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="c56d0-339">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="c56d0-340">Dockerfile の PowerShell コマンドを使用して Windows コンテナーを設定するには</span><span class="sxs-lookup"><span data-stu-id="c56d0-340">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="c56d0-341">[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)を Docker イメージに、既存の Windows アプリケーションを変換し、Docker エコシステムの残りの部分と同じツールを使用して展開できます。</span><span class="sxs-lookup"><span data-stu-id="c56d0-341">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="c56d0-342">Windows コンテナーを使用するには、PowerShell コマンドで実行する、Dockerfile では、次の例で示すように。</span><span class="sxs-lookup"><span data-stu-id="c56d0-342">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="c56d0-343">ここでは、私たちは Windows Server Core 基本イメージ (FROM の設定) を使用して、PowerShell コマンド (実行の設定) を使用して IIS をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c56d0-343">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="c56d0-344">同様の方法で ASP.NET 4.x、.NET 4.6、またはその他の Windows ソフトウェアなどの追加コンポーネントを設定する PowerShell コマンドを使用することもできません。</span><span class="sxs-lookup"><span data-stu-id="c56d0-344">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="c56d0-345">たとえば、Dockerfile に次のコマンドは、ASP.NET 4.5 を設定します。</span><span class="sxs-lookup"><span data-stu-id="c56d0-345">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="c56d0-346">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c56d0-346">Additional resources</span></span>

-   <span data-ttu-id="c56d0-347">**aspnet-docker/Dockerfile です。**</span><span class="sxs-lookup"><span data-stu-id="c56d0-347">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="c56d0-348">Windows の機能を組み込む dockerfile からを実行する Powershell コマンドの例です。</span><span class="sxs-lookup"><span data-stu-id="c56d0-348">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [<span data-ttu-id="c56d0-349">*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*</span><span class="sxs-lookup"><span data-stu-id="c56d0-349">*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*</span></span>](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="c56d0-350">[前](index.md) [次へ] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="c56d0-350">[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>

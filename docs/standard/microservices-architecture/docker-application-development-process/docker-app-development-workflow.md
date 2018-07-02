---
title: Docker アプリの開発ワークフロー
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker アプリの開発ワークフロー'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0627a61e910b1d278fd2e604dd8de7021fdb0fed
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106218"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="0eaca-103">Docker アプリの開発ワークフロー</span><span class="sxs-lookup"><span data-stu-id="0eaca-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="0eaca-104">アプリケーション開発のライフサイクルは、各開発者のコンピューターで開始されます。このとき、アプリケーションは、開発者は好みの言語で記述され、ローカルでテストされます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-104">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="0eaca-105">このワークフローでは、開発者が選択している言語、フレームワークおよびプラットフォームにかかわらず、常に Docker コンテナーはローカルで開発およびテストされます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="0eaca-106">各コンテナー (Docker イメージのインスタンス) には、次のコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-106">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="0eaca-107">選択したオペレーティング システム (例: Linux ディストリビューション、Windows Nano Server、または Windows Server Core)。</span><span class="sxs-lookup"><span data-stu-id="0eaca-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="0eaca-108">開発者が追加したファイル (アプリケーションのバイナリなど)。</span><span class="sxs-lookup"><span data-stu-id="0eaca-108">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="0eaca-109">構成情報 (環境の設定および依存関係)。</span><span class="sxs-lookup"><span data-stu-id="0eaca-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="0eaca-110">Docker のコンテナー ベースのアプリケーションを開発するためのワークフロー</span><span class="sxs-lookup"><span data-stu-id="0eaca-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="0eaca-111">このセクションでは、Docker のコンテナー ベースのアプリケーションの*内側のループ*の開発ワークフローについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="0eaca-112">内側のループのワークフローとは、DevOps のより全体的なワークフローではなく、開発者のコンピューター上で実行される開発作業のみを意味しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="0eaca-113">環境を設定する初期手順は、一度のみ実行されるものなので含まれていません。</span><span class="sxs-lookup"><span data-stu-id="0eaca-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="0eaca-114">アプリケーションは、自分のサービスと追加のライブラリ (依存関係) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="0eaca-115">Docker アプリケーションを構築するときの基本手順を次の図 5-1 に示します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="0eaca-116">**図 5-1**</span><span class="sxs-lookup"><span data-stu-id="0eaca-116">**Figure 5-1.**</span></span> <span data-ttu-id="0eaca-117">Docker のコンテナー化されたアプリケーションを開発するための詳細なワークフロー</span><span class="sxs-lookup"><span data-stu-id="0eaca-117">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="0eaca-118">このガイドでは、すべての手順が詳細に記載されており、主要な各手順は、Visual Studio の環境を使用して説明しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-118">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="0eaca-119">エディターと CLI を使用する開発手法 (例: Visual Studio Code と macOS または Windows 上の Docker CLI) を使用する場合、Visual Studio を使用する場合よりも、通常はより詳細に全手順を把握している必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-119">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="0eaca-120">CLI 環境での作業の詳細については、電子書籍、「[Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/)」 (Microsoft のプラットフォームおよびツールとコンテナー化された Docker アプリケーションのライフサイクル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0eaca-120">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="0eaca-121">Visual Studio 2015 または Visual Studio 2017 を使用している場合、これらの手順の多くは自動処理されるので、生産性が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-121">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="0eaca-122">これは、Visual Studio 2017 で、複数のコンテナー アプリケーションを対象としているとき特にそうです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-122">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="0eaca-123">たとえば、マウスを 1 回クリックするだけで、Visual Studio では、アプリケーションに適した構成で Dockerfile と docker-compose.yml ファイルをプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-123">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="0eaca-124">そのアプリケーションを Visual Studio で実行すると、Docker イメージが構築され、Docker で直接マルチコンテナー アプリケーションが実行されます。また、一度に複数のコンテナーをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-124">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="0eaca-125">これらの機能により、開発の速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-125">These features will boost your development speed.</span></span>

<span data-ttu-id="0eaca-126">ただし、Visual Studio によって、これらの手順が自動化されるからといって、Docker の背後で何が起こっているのか知らなくてもよいというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="0eaca-126">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="0eaca-127">そのため、次のガイダンスでは、各手順を詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-127">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="0eaca-128">手順 1.</span><span class="sxs-lookup"><span data-stu-id="0eaca-128">Step 1.</span></span> <span data-ttu-id="0eaca-129">コーディングを開始して、初期アプリケーションまたはサービス ベースラインを作成します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-129">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="0eaca-130">Docker アプリケーションの開発方法は、Docker を使用しないアプリケーションの開発方法と似ています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-130">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="0eaca-131">違いは、Docker 用を開発している場合、ローカル環境で Docker コンテナー内で実行するアプリケーションまたはサービスを開発またはテストするということです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-131">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="0eaca-132">コンテナーには、Linux コンテナーまたは Windows コンテナーのいずれも使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-132">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="0eaca-133">Visual Studio でのローカル環境のセットアップ</span><span class="sxs-lookup"><span data-stu-id="0eaca-133">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="0eaca-134">最初に、次の手順で説明する、Windows 用の [Docker Community Edition (CE)](https://www.docker.com/community-edition) がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-134">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

<span data-ttu-id="0eaca-135">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (Windows 用の Docker CE の概要)</span><span class="sxs-lookup"><span data-stu-id="0eaca-135">[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/)</span></span>

<span data-ttu-id="0eaca-136">Visual Studio 2017 もインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-136">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="0eaca-137">Visual Studio 2017 には、コンテナーのデバッグのサポートなど、Docker をサポートするより高度な機能があるため、Visual Studio Tools for Docker アドインが組み込まれた Visual Studio 2015 よりも適しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-137">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="0eaca-138">Visual Studio 2017 には、インストール時に **.NET Core と Docker** ワークロードを選択した場合、図 5-2 のように Docker 用のツールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-138">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="0eaca-139">**図 5-2**</span><span class="sxs-lookup"><span data-stu-id="0eaca-139">**Figure 5-2**.</span></span> <span data-ttu-id="0eaca-140">Visual Studio 2017 のセットアップ時の **.NET Core と Docker** ワークロードの選択</span><span class="sxs-lookup"><span data-stu-id="0eaca-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="0eaca-141">アプリケーションのコーディングは、アプリケーションで Docker を有効にし、Docker を展開してテストする前から、単純な .NET で開始することができます (コンテナーを使用する計画がある場合、通常は .NET Core)。</span><span class="sxs-lookup"><span data-stu-id="0eaca-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="0eaca-142">ただし、実際の環境となることに加え、問題が早く検出されるため、できるだけ早く Docker で作業を開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0eaca-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="0eaca-143">Docker は、Visual Studio では、ほとんど透過的で、使用しやすくなっているため、このようにすることが推奨されます。この最良の例は、Visual Studio からのマルチコンテナー アプリケーションのデバッグです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0eaca-144">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-144">Additional resources</span></span>

-   <span data-ttu-id="0eaca-145">**Windows 用の Docker CE の概要**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="0eaca-145">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="0eaca-146">**Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="0eaca-146">**Visual Studio 2017**
[*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="0eaca-147">手順 2.</span><span class="sxs-lookup"><span data-stu-id="0eaca-147">Step 2.</span></span> <span data-ttu-id="0eaca-148">既存の .NET 基本イメージに関連する Dockerfile を作成します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-148">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="0eaca-149">Dockerfile は、構築するカスタム イメージごとに必要です。また、Visual Studio から自動的に展開する場合も、Docker CLI (docker run および docker-compose コマンド) を使用して手動で展開する場合も、展開するコンテナーごとに Dockerfile が必要です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-149">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="0eaca-150">アプリケーションにカスタム サービスが 1 つ含まれている場合、Dockerfile が 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-150">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="0eaca-151">(マイクロサービス アーキテクチャの場合のように) アプリケーションに複数のサービスが含まれる場合、サービスごとに Dockerfile が 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-151">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="0eaca-152">Dockerfile は、アプリケーションまたはサービスのルート フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-152">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="0eaca-153">これには、コンテナーでアプリケーションまたはサービスを設定して実行する方法を Docker に指示するコマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-153">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="0eaca-154">手動でコードに Dockerfile を作成し、.NET の依存関係と共にプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-154">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="0eaca-155">Visual Studio と Docker 用のツールでは、このタスクはマウスを何度かクリックするのみで実行できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-155">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="0eaca-156">Visual Studio 2017 で新しいプロジェクトを作成する場合、図 5-3 に示す **[Enable Docker Support]** \(Docker サポートを有効にする\) というオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-156">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="0eaca-157">**図 5-3**</span><span class="sxs-lookup"><span data-stu-id="0eaca-157">**Figure 5-3**.</span></span> <span data-ttu-id="0eaca-158">Visual Studio 2017 で新しいプロジェクトを作成するときの Docker サポートの有効化</span><span class="sxs-lookup"><span data-stu-id="0eaca-158">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="0eaca-159">Visual Studio でプロジェクト ファイルを右クリックし、図 5-4 のとおり、**[追加]、[Docker プロジェクト サポート]** の順にオプションを選択しても、新規、または既存のプロジェクトで Docker サポートを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-159">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="0eaca-160">**図 5-4**</span><span class="sxs-lookup"><span data-stu-id="0eaca-160">**Figure 5-4**.</span></span> <span data-ttu-id="0eaca-161">既存の Visual Studio 2017 プロジェクトでの Docker サポートの有効化</span><span class="sxs-lookup"><span data-stu-id="0eaca-161">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="0eaca-162">(ASP.NET Web アプリケーションや Web API サービスなどの) プロジェクトでこの操作を実行すると、必要な構成で、プロジェクトに Dockerfile が追加されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-162">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="0eaca-163">また、ソリューション全体に docker-compose.yml ファイルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-163">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="0eaca-164">次のセクションでは、それらの各ファイルに書き込まれる情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-164">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="0eaca-165">この作業は、Visual Studio が実行してくれますが、Dockerfile に何が書き込まれるかを理解しておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-165">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="0eaca-166">オプション A: 既存の公式の .NET Docker イメージを使用してプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="0eaca-166">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="0eaca-167">通常、公式のリポジトリである [Docker Hub](https://hub.docker.com/) レジストリから取得できる基本イメージ上にコンテナーのカスタム イメージをビルドします。</span><span class="sxs-lookup"><span data-stu-id="0eaca-167">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="0eaca-168">Visual Studio で Docker のサポートを有効にした場合、背後ではこれがまさに発生します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-168">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="0eaca-169">Dockerfile では、既存の aspnetcore イメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-169">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="0eaca-170">選択した OS とフレームワークによって、使用できる Docker イメージとリポジトリについては、既に説明しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-170">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="0eaca-171">たとえば、ASP.NET Core (Linux または Windows) を使用したい場合は、microsoft/aspnetcore:2.0 のイメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-171">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="0eaca-172">この場合は、コンテナーに使用する基本の Docker イメージのみを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-172">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="0eaca-173">これは、Dockerfile に FROM microsoft/aspnetcore:2.0 を追加することによって行います。</span><span class="sxs-lookup"><span data-stu-id="0eaca-173">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="0eaca-174">これは、Visual Studio が自動的に実行しますが、バージョンを更新する場合は、この値を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-174">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="0eaca-175">バージョン番号を使用して Docker Hub の公式の .NET イメージ リポジトリを使うと、同じ言語機能が (開発、テスト、および実稼働環境などの) すべてのコンピューターで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-175">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="0eaca-176">次の例では、ASP.NET Core コンテナー用のサンプルの Dockerfile を示しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-176">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="0eaca-177">この場合、コンテナーは、公式の ASP.NET Core Docker イメージ (Linux および Windows 用マルチアーチ) のバージョン 2.0 に基づいています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-177">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="0eaca-178">この設定は、`FROM microsoft/aspnetcore:2.0` です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-178">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="0eaca-179">(この基本イメージの詳細については、「[ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/)」 (ASP.NET Core Docker イメージ) ページと「[.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/)」 (.NET Core Docker イメージ) ページを参照してください)。Dockerfile では、実行時に使用する、リッスンする TCP ポートを、Docker に指示する必要があります (ここでは、EXPOSE 設定で構成したポート 80)。</span><span class="sxs-lookup"><span data-stu-id="0eaca-179">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="0eaca-180">使用している言語とフレームワークによっては、Dockerfile に別の構成設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="0eaca-181">たとえば、\["dotnet", "MySingleContainerWebApp.dll"\] の ENTRYPOINT 行では、.NET Core アプリケーションを実行するよう Docker に指示しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-181">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="0eaca-182">SDK と .NET Core CLI (dotnet CLI) を使用して、.NET アプリケーションをビルドおよび実行している場合、設定はこれとは別になります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-182">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="0eaca-183">つまり、アプリケーションに選択した言語とプラットフォームにより、ENTRYPOINT 行とその他の設定は別になります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-183">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0eaca-184">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-184">Additional resources</span></span>

-   <span data-ttu-id="0eaca-185">**.NET Core アプリケーションの Docker イメージのビルド**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="0eaca-185">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="0eaca-186">**Build your own image (独自のイメージのビルド)**。</span><span class="sxs-lookup"><span data-stu-id="0eaca-186">**Build your own image**.</span></span> <span data-ttu-id="0eaca-187">Docker の公式なドキュメント内にあります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-187">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="0eaca-188">マルチアーキテクチャ イメージ リポジトリの使用</span><span class="sxs-lookup"><span data-stu-id="0eaca-188">Using multi-arch image repositories</span></span>

<span data-ttu-id="0eaca-189">単一のリポジトリには、Linux イメージや Windows イメージなどのプラットフォーム バリアントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-189">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="0eaca-190">この機能では、Microsoft (基本イメージの作成者) などのベンダーが、複数のプラットフォーム (つまり、Linux および Windows) に対応できるリポジトリを 1 つ作成できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-190">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="0eaca-191">たとえば、Docker Hub レジストリにある [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) リポジトリでは、同じリポジトリ名を使用して Linux および Windows Nano Server をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-191">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="0eaca-192">タグを指定する場合、次の場合のように、明示的にプラットフォームを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-192">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="0eaca-193">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="0eaca-193">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="0eaca-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="0eaca-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="0eaca-195">しかし、これは 2017 年の中ごろからのものであり、同じイメージ名を指定した場合、同じタグを使用した場合でも、次の例で示すように、(マルチアーキテクチャをサポートする aspnetcore イメージなどの) 新しいマルチアーキテクチャ イメージは、展開する Docker ホストの OS に応じて Linux または Windows バージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-195">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="0eaca-196">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="0eaca-196">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="0eaca-197">この場合、Windows ホストからイメージをプルした場合、Windows バリアントがプルされ、同じイメージ名が Linux ホストからプルされた場合、Linux バリアントがプルされます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-197">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="0eaca-198">オプション B: 一から基本イメージを作成する</span><span class="sxs-lookup"><span data-stu-id="0eaca-198">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="0eaca-199">独自の Docker 基本イメージを一から作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-199">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="0eaca-200">このシナリオは、Docker を初めて使用するユーザーには推奨されませんが、独自の基本イメージの特定のビットを設定したい場合にそれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-200">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0eaca-201">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-201">Additional resources</span></span>

-   <span data-ttu-id="0eaca-202">**Multi-arch .NET Core images** (マルチアーキテクチャの .NET Core のイメージ)</span><span class="sxs-lookup"><span data-stu-id="0eaca-202">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="0eaca-203">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="0eaca-203">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="0eaca-204">**Create a base image** (基本イメージを作成する)</span><span class="sxs-lookup"><span data-stu-id="0eaca-204">**Create a base image**.</span></span> <span data-ttu-id="0eaca-205">Docker の公式なドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-205">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="0eaca-206">手順 3.</span><span class="sxs-lookup"><span data-stu-id="0eaca-206">Step 3.</span></span> <span data-ttu-id="0eaca-207">カスタマイズした Docker イメージを作成し、それにアプリケーションまたはサービスを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-207">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="0eaca-208">アプリケーションの各サービスには、関連イメージを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-208">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="0eaca-209">アプリケーションが 1 つのサービスまたは Web アプリケーションで構成されている場合、イメージは 1 つのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-209">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="0eaca-210">Docker イメージは、Visual Studio が自動的に構築することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0eaca-210">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="0eaca-211">次の手順は、エディター/CLI ワークフローにのみ必要であり、背後で何が起こっているのか説明するために示しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-211">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="0eaca-212">開発者は、完全な機能をプッシュできるか、(GitHub などの) ソース管理システムに変更するまで、ローカルで開発およびテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-212">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="0eaca-213">つまり、Docker イメージを作成してローカルの Docker ホスト (Windows または Linux VM) にコンテナーを展開し、それらのローカルのコンテナーに対して実行、テスト、およびデバッグをする必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-213">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="0eaca-214">Docker CLI と Dockerfile を使用して、ローカルの環境にカスタム イメージを作成するには、図 5-5 のとおり、docker build コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-214">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="0eaca-215">**図 5-5**</span><span class="sxs-lookup"><span data-stu-id="0eaca-215">**Figure 5-5**.</span></span> <span data-ttu-id="0eaca-216">カスタム Docker イメージの作成</span><span class="sxs-lookup"><span data-stu-id="0eaca-216">Creating a custom Docker image</span></span>

<span data-ttu-id="0eaca-217">必要に応じて、プロジェクト フォルダーから docker build を直接実行する代わりに、dotnet publish を実行して必要な .NET ライブラリとバイナリを使用して、展開可能なフォルダーをまず生成し、次いで docker build コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-217">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="0eaca-218">これにより、cesardl/netcore-webapi-microservice-docker:first という名前の Docker イメージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-218">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="0eaca-219">このとき、:first は特定のバージョンを表すタグです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-219">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="0eaca-220">この手順は、構成した Docker アプリケーション用に作成する必要のある各カスタム イメージで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-220">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="0eaca-221">アプリケーションが複数のコンテナーで作成されている場合 (つまり、マルチコンテナー アプリケーションの場合)、docker-compose up ビルド コマンドでは、関連する docker-compose.yml ファイルで公開されているメタデータを使用して、1 つのコマンドですべての関連イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-221">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="0eaca-222">図 5-6 の docker images コマンドを使用すると、ローカル リポジトリの既存のイメージを検索できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-222">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="0eaca-223">**図 5-6**</span><span class="sxs-lookup"><span data-stu-id="0eaca-223">**Figure 5-6.**</span></span> <span data-ttu-id="0eaca-224">docker images コマンドを使用した既存のイメージの表示</span><span class="sxs-lookup"><span data-stu-id="0eaca-224">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="0eaca-225">Visual Studio での Docker イメージの作成</span><span class="sxs-lookup"><span data-stu-id="0eaca-225">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="0eaca-226">Visual Studio を使用して、Docker のサポートでプロジェクトを作成する場合、イメージは明示的には作成されません。</span><span class="sxs-lookup"><span data-stu-id="0eaca-226">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="0eaca-227">代わりに、F5 キーを押し、Docker 化されたアプリケーションまたはサービスを実行することによって、イメージは作成されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-227">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="0eaca-228">この手順は Visual Studio では自動的に行われ、それが実行されるのを見ることはできませんが、背後で何が行われているか知ることは重要です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-228">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="0eaca-229">手順 4.</span><span class="sxs-lookup"><span data-stu-id="0eaca-229">Step 4.</span></span> <span data-ttu-id="0eaca-230">マルチ コンテナー Docker アプリケーションを構築するときの docker-compose.yml へのサービスの定義</span><span class="sxs-lookup"><span data-stu-id="0eaca-230">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="0eaca-231">[docker-compose.yml](https://docs.docker.com/compose/compose-file/) ファイルでは、展開用のコマンドを使用して構成済みのアプリケーションとして関連サービスのセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-231">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="0eaca-232">docker-compose.yml ファイルを使用する場合、メインまたはルート ソリューション フォルダーに、次の例と類似した内容でファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-232">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="0eaca-233">なお、この docker-compose.yml ファイルは、簡略化され、結合されたバージョンです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-233">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="0eaca-234">これには、必ずある (カスタム イメージ名などの) 各コンテナー用の静的な構成データと、展開環境によっては異なる場合のある、接続文字列などの構成情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-234">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="0eaca-235">後半のセクションでは、複数の docker-compose ファイルに docker-compose.yml 構成を分割し、環境と実行の種類 (デバッグまたはリリース) に応じて、値をオーバーライドする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-235">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="0eaca-236">docker-compose.yml ファイルの例では、webmvc サービス (Web アプリケーション)、2 つのマイクロサービス (catalog.api および ordering.api)、1 つのデータ ソース コンテナー、コンテナーとして実行される Linux 用 SQL Server の sql.data の 5 つのサービスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-236">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="0eaca-237">各サービスはコンテナーとして展開されるので、それぞれに Docker イメージが必要です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-237">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="0eaca-238">docker-compose.yml ファイルでは、どのコンテナーが使用されているかのみでなく、それらがどのように個々に構成されるかが指定されています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-238">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="0eaca-239">たとえば、.yml ファイルの webmvc コンテナーの定義は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-239">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="0eaca-240">事前にビルドされている eshop/web:latest イメージが使用されています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-240">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="0eaca-241">ただし、docker-compose の実行の一部として、docker-compose ファイルの build: セクションの追加構成を加え、イメージがビルドされるように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-241">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="0eaca-242">2 つの環境変数 (CatalogUrl および OrderingUrl) を初期化します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-242">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="0eaca-243">コンテナー上の公開されているポート 80 を、ホスト コンピューター上の外部ポート 80 に転送します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-243">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="0eaca-244">depends\_on 設定を使用して、カタログと順序付けサービスに Web アプリをリンクします。</span><span class="sxs-lookup"><span data-stu-id="0eaca-244">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="0eaca-245">これにより、サービスは、それらのサービスが開始されるまで待機するようになります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-245">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="0eaca-246">docker-compose.yml ファイルについては、マイクロサービスとマルチコンテナー アプリを実装する方法について説明する後のセクションで、再確認します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-246">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="0eaca-247">Visual Studio 2017 での docker-compose.yml の操作</span><span class="sxs-lookup"><span data-stu-id="0eaca-247">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="0eaca-248">図 5-7 のように、Visual Studio ソリューションのサービス プロジェクトに Docker ソリューションのサポートを追加する場合、Visual Studio ではプロジェクトに Dockerfile を追加し、docker-compose.yml ファイルでソリューションにサービス セクション (プロジェクト) を追加します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-248">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="0eaca-249">これでは、マルチコンテナー ソリューションを簡単に作成開始できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-249">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="0eaca-250">その後、docker-compose.yml ファイルを開き、追加機能で更新することができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-250">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="0eaca-251">**図 5-7**</span><span class="sxs-lookup"><span data-stu-id="0eaca-251">**Figure 5-7**.</span></span> <span data-ttu-id="0eaca-252">Visual Studio 2017 への ASP.NET Core プロジェクトの右クリックでの Docker サポートの追加</span><span class="sxs-lookup"><span data-stu-id="0eaca-252">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="0eaca-253">Visual Studio に Docker のサポートを追加すると、プロジェクトに Dockerfile が追加されるだけでなく、ソリューション レベルで設定されているいくつかのグローバル docker-compose.yml ファイルに構成情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-253">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="0eaca-254">Visual Studio でソリューションに Docker のサポートを追加すると、図 5-8 のとおり、追加された docker compose.yml ファイルが含まれた新しいノード (docker-compose.dcproj プロジェクト ファイル) がソリューション エクスプローラーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-254">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="0eaca-255">**図 5-8**.</span><span class="sxs-lookup"><span data-stu-id="0eaca-255">**Figure 5-8**.</span></span> <span data-ttu-id="0eaca-256">Visual Studio 2017 のソリューション エクスプローラーに追加された **docker-compose** ツリー ノード</span><span class="sxs-lookup"><span data-stu-id="0eaca-256">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="0eaca-257">docker-compose up コマンドを使用すると、1 つの docker-compose.yml ファイルで、マルチコンテナー アプリケーションを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-257">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="0eaca-258">ただし、Visual Studio がそれらのグループを追加するので、環境 (開発対本番) と実行の種類 (リリース対デバッグ) に応じて値をオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-258">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="0eaca-259">この機能は、後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-259">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="0eaca-260">手順 5.</span><span class="sxs-lookup"><span data-stu-id="0eaca-260">Step 5.</span></span> <span data-ttu-id="0eaca-261">Docker アプリケーションのビルドと実行</span><span class="sxs-lookup"><span data-stu-id="0eaca-261">Build and run your Docker application</span></span>

<span data-ttu-id="0eaca-262">アプリケーションにコンテナーが 1 つしかない場合、Docker ホスト (仮想マシンまたは物理サーバー) に展開して実行することができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-262">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="0eaca-263">ただし、アプリケーションに複数のサービスが含まれている場合、単一の CLI コマンド (docker-compose up) を使用するか、背後でそのコマンドを使用する Visual Studio を使用して、構成されたアプリケーションとして展開することができます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-263">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="0eaca-264">別のオプションを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="0eaca-264">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="0eaca-265">オプション A: Docker CLI で単一のコンテナーを実行する</span><span class="sxs-lookup"><span data-stu-id="0eaca-265">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="0eaca-266">図 5-9 のとおり、docker run コマンドを使用して Docker コンテナーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-266">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="0eaca-267">**図 5-9**</span><span class="sxs-lookup"><span data-stu-id="0eaca-267">**Figure 5-9**.</span></span> <span data-ttu-id="0eaca-268">docker run コマンドを使用した Docker コンテナーの実行</span><span class="sxs-lookup"><span data-stu-id="0eaca-268">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="0eaca-269">この場合、このコマンドによって、コンテナーの内部ポート 5000 がホスト コンピューターのポート 80 にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-269">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="0eaca-270">つまり、ホストはポート 80 をリッスンし、コンテナーのポート 5000 に転送することを意味します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-270">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="0eaca-271">オプション B: マルチコンテナー アプリケーションを実行する</span><span class="sxs-lookup"><span data-stu-id="0eaca-271">Option B: Running a multi-container application</span></span>

<span data-ttu-id="0eaca-272">多くのエンタープライズ シナリオでは、Docker アプリケーションは複数のサービスで構成されています。つまり、図 5-10 のようにマルチコンテナーのアプリケーションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-272">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="0eaca-273">**図 5-10**</span><span class="sxs-lookup"><span data-stu-id="0eaca-273">**Figure 5-10**.</span></span> <span data-ttu-id="0eaca-274">Docker コンテナーが展開された VM</span><span class="sxs-lookup"><span data-stu-id="0eaca-274">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="0eaca-275">Docker CLI を使用したマルチコンテナー アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="0eaca-275">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="0eaca-276">Docker CLI を使用してマルチコンテナー アプリケーションを実行するには、docker-compose up コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-276">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="0eaca-277">このコマンドでは、ソリューション レベルにある、マルチコンテナー アプリケーションを展開する docker compose.yml ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-277">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="0eaca-278">図 5-11 は、docker-compose.yml ファイルを含む、メインのプロジェクト ディレクトリからコマンドを実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-278">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="0eaca-279">**図 5-11**</span><span class="sxs-lookup"><span data-stu-id="0eaca-279">**Figure 5-11**.</span></span> <span data-ttu-id="0eaca-280">docker-compose up コマンドの実行結果の例</span><span class="sxs-lookup"><span data-stu-id="0eaca-280">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="0eaca-281">docker-compose up コマンドを実行すると、アプリケーションとその関連コンテナーが、図 5-10 の VM の図のとおり、Docker ホストに展開されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-281">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="0eaca-282">Visual Studio を使用したマルチコンテナー アプリケーションの実行とデバッグ</span><span class="sxs-lookup"><span data-stu-id="0eaca-282">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="0eaca-283">Visual Studio 2017 を使用したマルチコンテナー アプリケーションの実行は非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-283">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="0eaca-284">Visual Studio で標準のブレークポイントを設定すると、マルチコンテナー アプリケーションを実行するのみでなく、そのコンテナーをすべて直接デバッグすることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-284">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="0eaca-285">既に説明したとおり、ソリューション内のプロジェクトに Docker ソリューションのサポートを追加するたびに、そのプロジェクトは、グローバル (ソリューション レベル) docker-compose.yml ファイルに構成され、一度にソリューション全体を実行またはデバッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-285">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="0eaca-286">Visual Studio では、Docker ソリューションのサポートが有効になっているプロジェクトごとに 1 つのコンテナーが起動され、内部のすべての手順をユーザーのために実行してくれます (dotnet publish、docker build など)。</span><span class="sxs-lookup"><span data-stu-id="0eaca-286">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="0eaca-287">ここで重要なのは、図 5-12 のとおり、Visual Studio 2017 には、F5 のアクション用に追加の **Docker** コマンドがあることです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-287">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="0eaca-288">このオプションでは、ソリューション レベルで docker-compose.yml ファイルに定義されているすべてのコンテナーを実行して、マルチコンテナー アプリケーションを実行またはデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-288">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="0eaca-289">マルチコンテナー ソリューションをデバッグできるということは、異なるプロジェクト (コンテナー) にそれぞれブレークポイントを設定でき (いくつかブレークポイントを設定でき)、Visual Studio でデバッグする際、別のプロジェクトに定義され、別のコンテナーで実行されているブレークポイントで停止されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-289">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="0eaca-290">**図 5-12**</span><span class="sxs-lookup"><span data-stu-id="0eaca-290">**Figure 5-12**.</span></span> <span data-ttu-id="0eaca-291">Visual Studio 2017 でのマルチコンテナー アプリの実行</span><span class="sxs-lookup"><span data-stu-id="0eaca-291">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0eaca-292">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-292">Additional resources</span></span>

-   <span data-ttu-id="0eaca-293">**リモート Docker ホストへの ASP.NET コンテナーのデプロイ**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="0eaca-293">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="0eaca-294">オーケストレーターを使用したテストと展開に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="0eaca-294">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="0eaca-295">docker-compose up および docker run コマンド (または Visual Studio でのコンテナーの実行およびデバッグ) を使用して、開発環境でコンテナーを十分にテストできます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-295">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="0eaca-296">ただし、Docker クラスター、Docker Swarm、Mesosphere DC/OS、Kubernetes などのオーケストレーターをターゲットとしている場合は、このアプローチは使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-296">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="0eaca-297">[Docker Swarm モード](https://docs.docker.com/engine/swarm/) (Docker CE for Windows および Mac のバージョン 1.12 以降で利用可能) などのクラスターを使用している場合、1 つのサービスに [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) などのその他のコマンドを使用して展開およびテストをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-297">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="0eaca-298">いくつかのコンテナーで構成されるアプリケーションを展開する場合、[docker compose bundle](https://docs.docker.com/compose/reference/bundle/) および [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) を使用して、構成されたアプリケーションを*スタック*として展開できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-298">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="0eaca-299">詳細については、Docker サイト上の Docker ドキュメント「[Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/)」(実験的な分散アプリケーション バンドルの概要) のブログ投稿を参照してください</span><span class="sxs-lookup"><span data-stu-id="0eaca-299">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="0eaca-300">。</span><span class="sxs-lookup"><span data-stu-id="0eaca-300">on the Docker site.</span></span>

<span data-ttu-id="0eaca-301">[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) と [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) については、同様に別の展開用のコマンドとスクリプトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-301">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="0eaca-302">手順 6.</span><span class="sxs-lookup"><span data-stu-id="0eaca-302">Step 6.</span></span> <span data-ttu-id="0eaca-303">ローカル Docker ホストを使用した Docker アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="0eaca-303">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="0eaca-304">この手順は、アプリケーションで何が実行されているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-304">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="0eaca-305">単一のコンテナーやサービスとして展開された単純な .NET Core Web アプリケーションでは、図 5-13 のように、Docker ホストでブラウザーを開き、サイトに移動して、サービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-305">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="0eaca-306">(Dockerfile の構成で、コンテナーがホストの 80 以外のポートにマップされる場合、この URL にホスト ポストを含めます。)</span><span class="sxs-lookup"><span data-stu-id="0eaca-306">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="0eaca-307">**図 5-13**</span><span class="sxs-lookup"><span data-stu-id="0eaca-307">**Figure 5-13**.</span></span> <span data-ttu-id="0eaca-308">localhost を使用したローカルでの Docker アプリケーションのテスト例</span><span class="sxs-lookup"><span data-stu-id="0eaca-308">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="0eaca-309">localhost が Docker ホスト IP をポイントしていない場合 (Docker CE を使用している場合、既定ではしている必要があります)、サービスに移動するには、コンピューターのネットワーク カードの IP アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-309">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="0eaca-310">なお、ブラウザーのこの URL では、説明している特定のコンテナーの例に、ポート 80 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-310">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="0eaca-311">ただし、前の手順で説明したとおり、docker run コマンドで展開されたとおり、要求は内部でポート 5000 にリダイレクトされています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-311">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="0eaca-312">図 5-14 のとおり、ターミナルからカールを使用して、アプリケーションをテストすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-312">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="0eaca-313">Windows の Docker インストールでは、既定の Docker ホスト IP は、常にマシンの実際の IP アドレスに 10.0.75.1 を加えたものです。</span><span class="sxs-lookup"><span data-stu-id="0eaca-313">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="0eaca-314">**図 5-14**</span><span class="sxs-lookup"><span data-stu-id="0eaca-314">**Figure 5-14**.</span></span> <span data-ttu-id="0eaca-315">カールを使用したローカルでの Docker アプリケーションのテスト例</span><span class="sxs-lookup"><span data-stu-id="0eaca-315">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="0eaca-316">Visual Studio 2017 を使用したコンテナーのテストおよびデバッグ</span><span class="sxs-lookup"><span data-stu-id="0eaca-316">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="0eaca-317">Visual Studio 2017 でコンテナーを実行またはデバッグする場合、.NET アプリケーションのデバッグは、コンテナーを使用しないでデバッグするのとほぼ同じ方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-317">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="0eaca-318">Visual Studio を使用しないデバッグおよびテスト</span><span class="sxs-lookup"><span data-stu-id="0eaca-318">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="0eaca-319">エディター/CLI アプローチを使用して開発をする場合、コンテナーのデバッグはより難しいので、トレースを生成してデバッグした方がよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="0eaca-319">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0eaca-320">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-320">Additional resources</span></span>

-   <span data-ttu-id="0eaca-321">**ローカルの Docker コンテナーでアプリをデバッグする**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="0eaca-321">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="0eaca-322">**作成者: Steve Lasker。Docker を使用した ASP.NET Core アプリのビルド、デバッグおよび展開。**</span><span class="sxs-lookup"><span data-stu-id="0eaca-322">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="0eaca-323">ビデオ。</span><span class="sxs-lookup"><span data-stu-id="0eaca-323">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="0eaca-324">Visual Studio でのコンテナー開発の簡略ワークフロー</span><span class="sxs-lookup"><span data-stu-id="0eaca-324">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="0eaca-325">Visual Studio を使用するワークフローは、エディター/CLI アプローチを使用するワークフローよりも、実際はるかに簡単になります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-325">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="0eaca-326">Dockerfile と docker-compose.yml ファイルに関係する Docker で必要な多くの手順は、図 5-15 のとおり、Visual Studio では背後で実行されるか、簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-326">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="0eaca-327">**図 5-15**。</span><span class="sxs-lookup"><span data-stu-id="0eaca-327">**Figure 5-15**.</span></span> <span data-ttu-id="0eaca-328">Visual Studio での開発の簡略ワークフロー</span><span class="sxs-lookup"><span data-stu-id="0eaca-328">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="0eaca-329">これに加え、(プロジェクトに Docker のサポートを追加する) 手順 2 を、一度のみ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-329">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="0eaca-330">つまり、ワークフローは、他の任意の開発に .NET を使用する場合の通常の開発タスクと似たものになります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-330">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="0eaca-331">背後で何が起こっているのか (イメージのビルド手順、使用している基本イメージ、コンテナーの展開など) を理解しておく必要があり、動作をカスタマイズするのに Dockerfile または docker-compose.yml ファイルを編集する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0eaca-331">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="0eaca-332">しかし、多くの作業は Visual Studio を使用することで大幅に簡略化され、ユーザーの生産性を向上させます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-332">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0eaca-333">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-333">Additional resources</span></span>

-   <span data-ttu-id="0eaca-334">**作成者: Steve Lasker。Visual Studio 2017 を使用した .NET Docker の開発**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="0eaca-334">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="0eaca-335">**作成者: Jeffrey T. Fritz。Visual Studio の新しい Docker ツールを使用してコンテナーに .NET Core アプリを配置する**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="0eaca-335">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="0eaca-336">Windows コンテナーを設定するための PowerShell コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="0eaca-336">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="0eaca-337">[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)は、既存の Windows アプリケーションを Docker イメージに変換して、Docker エコシステムの残りと同じツールで展開できます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-337">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="0eaca-338">Windows コンテナーを使用するには、次の例のように、Dockerfile で PowerShell コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0eaca-338">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="0eaca-339">この場合は、Windows Server Core 基本イメージ (FROM 設定) を使用して、PowerShell コマンド (RUN 設定) で IIS をインストールしています。</span><span class="sxs-lookup"><span data-stu-id="0eaca-339">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="0eaca-340">同様に、PowerShell コマンドを使用して、ASP.NET 4.x、.NET 4.6、またはその他の任意の Windows ソフトウェアなどの追加コンポーネントを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-340">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="0eaca-341">たとえば、Dockerfile の次のコマンドでは、ASP.NET 4.5 が設定されます。</span><span class="sxs-lookup"><span data-stu-id="0eaca-341">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="0eaca-342">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0eaca-342">Additional resources</span></span>

-   <span data-ttu-id="0eaca-343">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="0eaca-343">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="0eaca-344">Windows の機能を含めるために dockerfile から実行する Powershell コマンドの例です。</span><span class="sxs-lookup"><span data-stu-id="0eaca-344">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="0eaca-345">[前へ](index.md)
[次へ](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="0eaca-345">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>

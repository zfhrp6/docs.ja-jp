---
title: Docker アプリ用の内部ループ開発ワークフロー
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: cda9aa77ca033dced8b6b30538f19f28a5fa63a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579211"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="33cf5-103">Docker アプリ用の内部ループ開発ワークフロー</span><span class="sxs-lookup"><span data-stu-id="33cf5-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="33cf5-104">サイクル全体の DevOps のまたがりメモリ割り当て、外側のループ ワークフローをトリガーする前に、各開発者のコンピューターで、アプリ自体をコーディング、言語またはプラットフォームを使用して、およびそれをローカルでのテスト (図 4-14) はすべて開始します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="33cf5-105">すべてのケースでする必要が非常に重要なポイント共通に、選択した言語、フレームワーク、またはプラットフォームに関係なく。</span><span class="sxs-lookup"><span data-stu-id="33cf5-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="33cf5-106">この特定のワークフローで常に開発およびテストして、Docker コンテナーなくローカルです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="33cf5-107">図 4-14: 内部ループ開発コンテキスト</span><span class="sxs-lookup"><span data-stu-id="33cf5-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="33cf5-108">これらのコンポーネントは、コンテナーまたは Docker イメージのインスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="33cf5-109">たとえば、Linux ディストリビューション (Windows) オペレーティング システムの選択</span><span class="sxs-lookup"><span data-stu-id="33cf5-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="33cf5-110">Developer (アプリのバイナリなど) によって追加されたファイル</span><span class="sxs-lookup"><span data-stu-id="33cf5-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="33cf5-111">(たとえば、環境の設定と依存関係) の構成</span><span class="sxs-lookup"><span data-stu-id="33cf5-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="33cf5-112">Docker によって実行するどのようなプロセスの手順</span><span class="sxs-lookup"><span data-stu-id="33cf5-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="33cf5-113">(次のセクションで説明) のプロセスとして Docker を使用する内部ループ開発ワークフローを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="33cf5-114">考慮する、環境をセットアップする最初の手順は含まれず、1 回だけを行う必要があるため。</span><span class="sxs-lookup"><span data-stu-id="33cf5-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="33cf5-115">Visual Studio Code と Docker CLI を使用して、Docker コンテナー内の 1 つのアプリの構築</span><span class="sxs-lookup"><span data-stu-id="33cf5-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="33cf5-116">アプリは、独自のサービスと追加のライブラリ (依存関係) から構成されています。</span><span class="sxs-lookup"><span data-stu-id="33cf5-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="33cf5-117">図 4-15 では、通常、各ステップの詳細な説明を続けて、Docker アプリを構築するときに実行するために必要な基本手順を示します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="33cf5-118">Docker CLI を使用する Docker コンテナー詰めアプリケーション ライフ サイクルの図 4-15: 高度なワークフロー</span><span class="sxs-lookup"><span data-stu-id="33cf5-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="33cf5-119">手順 1: Visual Studio のコードでコーディングを開始し、初期アプリケーション/サービスの基準を作成します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="33cf5-120">アプリケーションを開発する方法は、Docker なく行う方法に非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="33cf5-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="33cf5-121">違いは、開発中に展開しているアプリケーションまたは (Linux VM または Windows) など、ローカル環境に配置している Docker コンテナー内で実行されているサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="33cf5-122">**ローカル環境の設定**</span><span class="sxs-lookup"><span data-stu-id="33cf5-122">**Setting up your local environment**</span></span>

<span data-ttu-id="33cf5-123">Mac および Windows 向けの Docker の最新のバージョンがこれまでに、Docker のアプリケーションの開発よりも簡単と、セットアップは簡単です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="33cf5-124">**詳細については** Docker for Windows の設定手順についてを参照してください[ https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="33cf5-125">Mac の Docker を設定する方法についてを参照してください<https://docs.docker.com/docker-for-mac/>です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="33cf5-126">さらに、実際に Docker CLI を使用しているときにアプリケーションを開発することができるように、コード エディターが必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="33cf5-127">Microsoft は、軽量なコード エディターで IntelliSense を示し、Mac、Windows、および Linux ではサポートされているは、Visual Studio のコードを提供[の多数の言語サポート](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、移動、Java、Ruby、Python、およびほとんど最新の言語)、[デバッグ](https://code.visualstudio.com/Docs/editor/debugging)、 [Git と統合](https://code.visualstudio.com/Docs/editor/versioncontrol)と[拡張機能のサポート](https://code.visualstudio.com/docs/extensions/overview)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="33cf5-128">このエディターは、Mac および Linux の開発者にとって最適です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="33cf5-129">Windows もに、完全な Visual Studio アプリケーションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="33cf5-130">**詳細については** か、Visual Studio for Windows、Mac、Linux をインストールする方法の詳細についてを参照してください[ http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span></span>

<span data-ttu-id="33cf5-131">Docker CLI を使用して、コード エディターを使用して、コードの記述が Visual Studio のコードを使用する場合、作成者 Dockerfile を容易に行えます、docker compose.yml ファイル ワークスペースにします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="33cf5-132">さらに、下に Docker CLI を使用して詳細な操作を実行できるスクリプトを要求する IDE から Visual Studio のコードのタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="33cf5-133">Visual Studio のコードは、インストールする必要があります拡張機能によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="33cf5-134">そのためには、キーを押して Ctrl + Shift + P、次のように入力します。 **ext インストール**、拡張機能を実行し: Marketplace 拡張機能の一覧を表示する拡張機能のインストール コマンド。</span><span class="sxs-lookup"><span data-stu-id="33cf5-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="33cf5-135">次に、入力**docker**結果をフィルター処理し、図 4-16 の図のように、Dockerfile と Docker 構成ファイル (yml) サポートの拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="33cf5-136">図 4-16: Visual Studio のコードに Docker 拡張機能をインストールします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="33cf5-137">手順 2: 既存のイメージ (plain OS または開発環境を .NET Core、Node.js、および Ruby など) に関連する DockerFile を作成します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="33cf5-138">カスタム イメージを構築および配置するコンテナーごとに、DockerFile は必要があります、したがって、1 つのカスタム サービスのアプリが構成されている場合する必要があります単一 DockerFile です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="33cf5-139">しかし、アプリが複数のサービス (microservices アーキテクチャ) のように構成されている場合は、サービスごとの 1 つの Dockerfile を必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="33cf5-140">DockerFile は通常、アプリやサービスのルート フォルダー内に配置しているし、その Docker を設定し、そのアプリやサービスを実行する方法を認識するために必要なコマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="33cf5-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="33cf5-141">DockerFile を作成し、コードと共にプロジェクトに追加することができます (node.js、.NET Core など)、または、環境に新しい場合は、次のヒントを確認します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="33cf5-142">というコマンド ライン ツールを使用する[yo docker](https://github.com/Microsoft/generator-docker)を選択して、必要な Docker 構成ファイルに追加の言語のプロジェクトからファイルをスキャフォールディングします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="33cf5-143">基本的には、開発者が作業の開始を支援するために作成、適切な DockerFile で docker compose.yml、およびその他の関連付けられているスクリプトをビルドして、Docker コンテナーを実行します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="33cf5-144">この yeoman ジェネレーターに、選択した開発言語と移行先コンテナーのホストを確認するいくつかの質問を求められます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="33cf5-146">たとえば、図 4-17 を示しています、端末から 2 つのスクリーン ショット windows と Mac では、どちらの場合も、実行されている yo、docker で動作するよう既に構成サンプルのコード プロジェクト (.NET Core では現在、Golang、および Node.js としてサポートされている言語) を生成します。Docker の上部に表示。</span><span class="sxs-lookup"><span data-stu-id="33cf5-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="33cf5-147">図 4-17: yo docker コマンド ツール ウィンドウ (左) と、Mac 上</span><span class="sxs-lookup"><span data-stu-id="33cf5-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="33cf5-148">図 4-18 では、docker を使用した yo を作成したら、既存の .NET Core プロジェクトをスキャフォールディングする例を示します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="33cf5-149">図 4 ~ 18: yo 既存の .NET Core の docker でプロジェクトを配置</span><span class="sxs-lookup"><span data-stu-id="33cf5-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="33cf5-150">DockerFile からは、(microsoft/dotnet:1.0.0-core"から"を使用して) などが使用されるどのような基本の Docker イメージを指定します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="33cf5-151">任意の正式なリポジトリから取得できる基本イメージの上にカスタム イメージ ビルドは通常、 [Docker Hub レジストリ](https://hub.docker.com/)(と同様に、 [.NET Core のイメージ](https://hub.docker.com/r/microsoft/dotnet/)または 1 個[for Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="33cf5-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="33cf5-152">***オプション a: を使用する既存の正式な Docker イメージ***</span><span class="sxs-lookup"><span data-stu-id="33cf5-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="33cf5-153">バージョン番号を持つ言語スタックの公式のリポジトリを使うと、同じ言語の機能が (開発、テスト、および実稼働環境を含む) すべてのマシンで使用できることができます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="33cf5-154">.NET Core コンテナー用 DockerFile のサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-154">Following is a sample DockerFile for a .NET Core container:</span></span>

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="33cf5-155">この場合、使用されている公式の ASP.NET Core Docker イメージのバージョン 1.0.1 for Linux microsoft/aspnetcore:1.0.1 をという名前です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="33cf5-156">詳細についてを参照してください、 [ASP.NET Core Docker イメージ ページ](https://hub.docker.com/r/microsoft/aspnetcore/)と[.NET Core Docker イメージ ページ](https://hub.docker.com/r/microsoft/dotnet/)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="33cf5-157">でした使用するノード: 4 などの別の比較可能なイメージ-Node.js、または開発言語で提供されているその他の多くの事前構成済みイメージの onbuild [Docker Hub](https://hub.docker.com/explore/)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="33cf5-158">DockerFile で (ポート 80) などの実行時に使用する TCP ポートをリッスンするように Docker に指示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="33cf5-159">Docker は、アプリを実行する方法を認識しているように、dockerfile を使用している言語/フレームワークによって追加できる構成の他の行があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="33cf5-160">インスタンスでは、ENTRYPOINT 行が必要な\["dotnet"、"MyCustomMicroservice.dll"\]をビルドして、サービスを実行する方法に応じて複数のバリアントを持つことができますが、.NET Core のアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="33cf5-161">.NET アプリをビルドして、実行、SDK と dotnet CLI を使用している場合は、若干異なるがなります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="33cf5-162">一番下の行が、ENTRYPOINT 行と追加の行になりますアプリケーション用に選択した言語またはプラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="33cf5-163">**詳細については** .NET Core アプリケーションの Docker イメージを構築する方法についてを参照してください<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="33cf5-164">独自のイメージの構築に関する詳細については、するには[ https://docs.docker.com/engine/\チュートリアル/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="33cf5-165">**マルチプラット フォームのイメージ リポジトリ**</span><span class="sxs-lookup"><span data-stu-id="33cf5-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="33cf5-166">Windows コンテナーより多く使用されているになると、1 つのリポジトリは Linux と Windows イメージなどのプラットフォームのバリエーションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="33cf5-167">これは、新しい機能により、複数のプラットフォームを対象に 1 つのリポジトリを使用する仕入先の Docker が受け取った[microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) dockerhub を使用してレジストリで利用可能なリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="33cf5-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="33cf5-168">機能が有効になると、このイメージを Windows ホストからプルすると、Linux バリアントがプルする Linux ホストから同じイメージの名前をプルする一方には Windows バリアントが除去されます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="33cf5-169">***基本イメージを最初からオプション b: を作成***</span><span class="sxs-lookup"><span data-stu-id="33cf5-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="33cf5-170">これで説明したよう、最初から独自 Docker の基本イメージを作成することができます[記事](https://docs.docker.com/engine/userguide/eng-image/baseimages/)Docker からです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="33cf5-171">これは、シナリオ Docker、によって起動した場合に、最適な可能性がありますが、独自の基本イメージの特定のビットを設定する場合は、行うことができます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="33cf5-172">手順 3: 埋め込みことで、サービス、カスタム Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="33cf5-173">サービスごとにカスタム アプリを構成するには、関連するイメージを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="33cf5-174">1 つのサービスまたは web アプリのアプリが構成されている場合は、1 つのイメージを必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="33cf5-175">"外側のループ DevOps workflow"を考慮に入れて、イメージから作成されます自動ビルド プロセスによって、ソース コードをリポジトリにプッシュ Git (継続的インテグレーション) ため、イメージはグローバル環境で作成されるたびに、ソース コードです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="33cf5-176">しかし、その外側のループのルートに、考慮する前に、Docker アプリケーションが実際には正しく動作するソース管理システム (Git など) が正しく動作しないコードをプッシュしないようにすることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="33cf5-177">そのため、各開発者が最初にために必要な内部ループ プロセス全体をローカルでテストし、完全な機能をプッシュまたはソース管理システムを変更するまでの開発を続行します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="33cf5-178">図 4-19 に示すように、ローカル環境と、DockerFile を使用してイメージを作成するに docker ビルド コマンドを使用することができます (実行することもできます docker 構成設定によっていくつかのコンテナー/サービスで構成されたアプリケーションの構築) します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="33cf5-179">図 4-19: docker のビルドの実行</span><span class="sxs-lookup"><span data-stu-id="33cf5-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="33cf5-180">必要に応じて、docker を直接実行する代わりに、プロジェクトのフォルダーからビルド最初できますを生成して、配置可能なフォルダー実行 dotnet を使用してコマンドを発行し、docker ビルドを実行に必要な .NET ライブラリとします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="33cf5-181">この例では、名前 cesardl/netcore-webapi-マイクロ サービスを Docker イメージを作成これ-docker: 最初 (: 1 つ目は、特定のバージョンと同様に、タグ)。</span><span class="sxs-lookup"><span data-stu-id="33cf5-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="33cf5-182">複数のコンテナーを使用して構成済みの Docker アプリケーションを作成する必要がカスタム イメージごとにこの手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="33cf5-183">既存のイメージ、ローカル リポジトリ (開発用コンピューター) に、docker を使用してイメージ コマンドは検索できます、図 4-20 を示すようにします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="33cf5-184">図 4-20: docker のイメージを使用して既存のイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="33cf5-185">手順 4: (省略可能) を定義する docker compose.yml の複数のサービスで構成される Docker アプリを構築するときに、サービス</span><span class="sxs-lookup"><span data-stu-id="33cf5-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="33cf5-186">Docker compose.yml ファイルでは、次の手順」セクションで説明する展開コマンドを使用して構築されたアプリケーションとして展開に関連するサービスのセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="33cf5-187">その、main でファイルまたはソリューションのルート フォルダー; を作成する必要があります。類似のコンテンツは、次の docker compose.yml ファイルにこれが必要です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

```yml
version: '2'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="33cf5-188">この特定のケースでは、このファイルは 2 つのサービスを定義します。 web サービス (カスタム サービス) と redis サービス (一般的なキャッシュ サービス)。</span><span class="sxs-lookup"><span data-stu-id="33cf5-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="33cf5-189">各サービスには、コンテナーとしてデプロイため、各具象 Docker イメージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="33cf5-190">この特定の web サービスのイメージは、以下を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="33cf5-191">現在のディレクトリに、DockerFile をビルドします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="33cf5-192">公開されているポート 80 をコンテナー ホスト マシン上のポート 81 上を転送します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="33cf5-193">/Code、コンテナー内にイメージを再作成しなくても、コードを変更できるようにするホスト上のプロジェクト ディレクトリをマウントします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="33cf5-194">Redis サービスへの web サービスをリンクします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-194">Link the web service to the redis service</span></span>

<span data-ttu-id="33cf5-195">Redis サービスが使用、[最新公開 redis イメージ](https://hub.docker.com/_/redis/)Docker Hub レジストリから取得します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="33cf5-196">[redis](https://redis.io/)はサーバー側アプリケーション用のキャッシュが非常に一般的なシステムです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="33cf5-197">手順 5: ビルドし、Docker のアプリの実行</span><span class="sxs-lookup"><span data-stu-id="33cf5-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="33cf5-198">アプリに 1 つのコンテナーのみがある場合だけ、(VM または物理サーバー) は Docker ホストに展開することで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="33cf5-199">ただし、複数のサービス、アプリが構成されている場合必要*組み立てる*、すぎます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="33cf5-200">さまざまなオプションを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="33cf5-200">Let's see the different options.</span></span>

<span data-ttu-id="33cf5-201">***A: 実行の 1 つのコンテナーまたはサービスをオプションします。***</span><span class="sxs-lookup"><span data-stu-id="33cf5-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="33cf5-202">次に示すように docker run コマンドを使用して、Docker イメージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="33cf5-203">この特定の展開のおありますリダイレクト 5000 内部ポートにポート 80 に送信された要求に注意してください。</span><span class="sxs-lookup"><span data-stu-id="33cf5-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="33cf5-204">ここで、外部ポート 80、ホスト レベルで、アプリケーションがリッスンしています。</span><span class="sxs-lookup"><span data-stu-id="33cf5-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="33cf5-205">***オプション b: 作成と実行、複数のコンテナー アプリケーション***</span><span class="sxs-lookup"><span data-stu-id="33cf5-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="33cf5-206">ほとんどのエンタープライズ シナリオでは、Docker アプリケーションを複数のサービスはから構成されます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="33cf5-207">このような場合は、コマンドを実行して docker 構成を (図 4-21)、以前作成した可能性があります、docker compose.yml ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="33cf5-208">このコマンドを実行するいると、そのすべての関連するコンテナーで構成されるアプリケーションが展開します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="33cf5-209">図 4-21:「docker の構成を」コマンドの実行結果</span><span class="sxs-lookup"><span data-stu-id="33cf5-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="33cf5-210">Docker を実行した後に作成、展開するアプリケーションとその関連するコンテナー、Docker ホストに VM 形式を図 4-22 を示すようにします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="33cf5-211">図 4-22: VM 展開されている Docker コンテナーを</span><span class="sxs-lookup"><span data-stu-id="33cf5-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="33cf5-212">注 docker の構成と docker の実行は、開発環境で、コンテナーのテストに対して十分である可能性がありますがいないそれらを使用するすべての場合は Docker クラスターの操作を必要として、orchestrators などの Docker Swarm 続き DC/OS、Kubernetesためにスケール アップします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="33cf5-213">ようにクラスターを使用している場合[Docker Swarm モード](https://docs.docker.com/engine/swarm/)(以降で使用可能では、Docker for Windows と Mac バージョン 1.12)、する必要がある配置した場合など、docker サービスを 1 つのサービスの作成やその他のコマンドをテストするにはバンドルを作成 docker を使用して複数のコンテナーで構成したアプリの配置、および docker が記事で説明したように、スタックとして構成済みのアプリを展開することで myBundleFile を展開[アプリケーション バンドルの分散](https://blog.docker.com/2016/06/docker-app-bundle/)Docker からです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="33cf5-214">[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)と[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment)は、さまざまな展開コマンドと、スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="33cf5-215">手順 6: (ローカル CD VM) では、ローカルで Docker アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="33cf5-216">この手順は、アプリが何によって異なります。</span><span class="sxs-lookup"><span data-stu-id="33cf5-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="33cf5-217">非常に単純な .NET Core Web API"Hello World"が 1 つのコンテナーまたはサービスとしてデプロイされている、DockerFile で指定された TCP ポートを提供することにより、サービスにアクセスするはだけです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="33cf5-218">サービスに移動する localhost が有効でない場合は、このコマンドを使用して、マシンの IP アドレスを検出します。</span><span class="sxs-lookup"><span data-stu-id="33cf5-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="33cf5-219">docker-machine ip *your-container-name*</span><span class="sxs-lookup"><span data-stu-id="33cf5-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="33cf5-220">Docker ホストのブラウザーを開き、およびそのサイトに移動図 4-23 に示すようにを実行しているアプリ/サービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="33cf5-221">図 4-23: localhost を使用してローカルで Docker アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="33cf5-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="33cf5-222">上の説明に従って、実行、docker を使用した展開された方法であるためにはポート 80 が使用が内部的に 5000 のポートにリダイレクトされましたされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="33cf5-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="33cf5-223">端末から CURL を使用して、これをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="33cf5-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="33cf5-224">図 4 ~ 24 の図のよう、Windows で Docker のインストールでは、既定の IP、10.0.75.1、です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="33cf5-225">図 4 ~ 24: CURL を使用してローカルでの Docker アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="33cf5-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="33cf5-226">**Docker で実行されているコンテナーのデバッグ**</span><span class="sxs-lookup"><span data-stu-id="33cf5-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="33cf5-227">Visual Studio のコードは、Node.js と .NET Core コンテナーのようなその他のプラットフォームを使用している場合に、Docker のデバッグをサポートします。</span><span class="sxs-lookup"><span data-stu-id="33cf5-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="33cf5-228">デバッグすることもできます Docker でコンテナーを .NET Core、Visual Studio を使用する場合、次のセクションで説明されているようです。</span><span class="sxs-lookup"><span data-stu-id="33cf5-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="33cf5-229">**詳細情報:** Node.js Docker コンテナーのデバッグに関する詳細については、するには<https://blog.docker.com/2016/07/live-debugging-docker/>と[ https://blogs.msdn.microsoft.com/\ ユーザー\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/)です。</span><span class="sxs-lookup"><span data-stu-id="33cf5-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="33cf5-230">[前] (docker-アプリの開発-environment.md) [次へ] (visual-studio のツールでの-docker.md)</span><span class="sxs-lookup"><span data-stu-id="33cf5-230">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span></span>

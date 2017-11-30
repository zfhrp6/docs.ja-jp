---
title: ".NET Core と Docker を基礎します。"
description: "Docker と .NET Core の基本チュートリアル"
keywords: ".NET、.NET core、Docker、チュートリアル"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="ca891-104">.NET Core と Docker を基礎します。</span><span class="sxs-lookup"><span data-stu-id="ca891-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="ca891-105">このチュートリアルでは、Docker コンテナーをビルドおよび .NET Core アプリケーションのタスクの配置で説明します。</span><span class="sxs-lookup"><span data-stu-id="ca891-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="ca891-106">このチュートリアルの中には、次の操作を説明します。</span><span class="sxs-lookup"><span data-stu-id="ca891-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ca891-107">Dockerfile を作成する方法</span><span class="sxs-lookup"><span data-stu-id="ca891-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="ca891-108">.NET Core アプリケーションを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="ca891-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="ca891-109">Docker コンテナーにアプリを展開する方法です。</span><span class="sxs-lookup"><span data-stu-id="ca891-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="ca891-110">[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)を使用して、 [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)速やかに構築してとしてアプリをパッケージ化[Docker images](https://docs.docker.com/glossary/?term=image)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="ca891-111">これらのイメージが記述された、 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)を展開し実行する形式、[コンテナー階層化](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="ca891-112">作業を開始する最も簡単な方法を .NET core:</span><span class="sxs-lookup"><span data-stu-id="ca891-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="ca891-113">Docker イメージを作成する前に、containerize するアプリケーションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca891-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="ca891-114">これは、Linux、MacOS、または Windows に作成できます。</span><span class="sxs-lookup"><span data-stu-id="ca891-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="ca891-115">行うには最速で簡単な方法では、.NET Core を使用します。</span><span class="sxs-lookup"><span data-stu-id="ca891-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="ca891-116">.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/index.md)」(.NET Core SDK の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca891-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="ca891-117">Windows と Linux の両方のコンテナーをビルドする[マルチ arch ベース タグ](https://github.com/dotnet/announcements/issues/14)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="ca891-118">最初の .NET Core Docker アプリ</span><span class="sxs-lookup"><span data-stu-id="ca891-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ca891-119">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ca891-119">Prerequisites</span></span>

<span data-ttu-id="ca891-120">このチュートリアルを完了します。</span><span class="sxs-lookup"><span data-stu-id="ca891-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="ca891-121">.NET 2.0 SDK をコアします。</span><span class="sxs-lookup"><span data-stu-id="ca891-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="ca891-122">インストール[.NET Core SDK 2.0](https://www.microsoft.com/net/core)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="ca891-123">.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca891-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="ca891-124">まだ行っていない場合、好きなコード エディターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ca891-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="ca891-125">コード エディターをインストールする必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="ca891-125">Need to install a code editor?</span></span> <span data-ttu-id="ca891-126">再試行[Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="ca891-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="ca891-127">Docker クライアントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="ca891-127">Installing Docker Client</span></span>

<span data-ttu-id="ca891-128">インストール[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)またはそれ以降の Docker クライアント。</span><span class="sxs-lookup"><span data-stu-id="ca891-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="ca891-129">Docker クライアントをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="ca891-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="ca891-130">Linux ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="ca891-130">Linux distributions</span></span>

   * [<span data-ttu-id="ca891-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="ca891-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="ca891-132">Debian</span><span class="sxs-lookup"><span data-stu-id="ca891-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="ca891-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="ca891-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="ca891-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ca891-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="ca891-135">macOS</span><span class="sxs-lookup"><span data-stu-id="ca891-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="ca891-136">[Windows](https://docs.docker.com/docker-for-windows/)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="ca891-137">Dockerization のコンソール アプリケーションを .NET Core 2.0 を作成します。</span><span class="sxs-lookup"><span data-stu-id="ca891-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="ca891-138">コマンド プロンプトを開き、*Hello* という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca891-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="ca891-139">作成したフォルダーに移動し、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="ca891-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="ca891-140">簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="ca891-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="ca891-141">[`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca891-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="ca891-142">また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。</span><span class="sxs-lookup"><span data-stu-id="ca891-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="ca891-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="ca891-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="ca891-144">プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。</span><span class="sxs-lookup"><span data-stu-id="ca891-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="ca891-145">`OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。</span><span class="sxs-lookup"><span data-stu-id="ca891-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="ca891-146">`TargetFramework` タグは、対象の .NET 実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca891-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="ca891-147">高度なシナリオでは、複数のターゲット フレームワークを指定して、単一の操作で指定されたフレームワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca891-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="ca891-148">このチュートリアルでは、.NET Core 2.0 おビルドします。</span><span class="sxs-lookup"><span data-stu-id="ca891-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="ca891-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="ca891-149">`Program.cs`:</span></span>

   <span data-ttu-id="ca891-150">プログラムの起動`using System`です。</span><span class="sxs-lookup"><span data-stu-id="ca891-150">The program starts by `using System`.</span></span> <span data-ttu-id="ca891-151">このステートメントは、次の場合、"すべての取り込み、`System`のこのファイルのスコープに名前空間です"。</span><span class="sxs-lookup"><span data-stu-id="ca891-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="ca891-152">`System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca891-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="ca891-153">次に、`Hello` という名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="ca891-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="ca891-154">名前空間は、自分の好きを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ca891-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="ca891-155">`Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。</span><span class="sxs-lookup"><span data-stu-id="ca891-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="ca891-156">この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca891-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="ca891-157">この例では、プログラムのみを書き込みます"Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ca891-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="ca891-158">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="ca891-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="ca891-159">.NET Core で 2.x、 **dotnet 新しい**実行、 [ `dotnet restore` ](../tools/dotnet-restore.md)コマンド。</span><span class="sxs-lookup"><span data-stu-id="ca891-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="ca891-160">**Dotnet 復元**との依存関係のツリーを復元する[NuGet](https://www.nuget.org/)(.NET パッケージ マネージャー) 呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ca891-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="ca891-161">NuGet では、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca891-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="ca891-162">分析し、 *Hello.csproj*ファイル</span><span class="sxs-lookup"><span data-stu-id="ca891-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="ca891-163">ファイルのダウンロードの依存関係 (またはコンピューターのキャッシュから grabs)</span><span class="sxs-lookup"><span data-stu-id="ca891-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="ca891-164">書き込みます、 *obj/project.assets.json*ファイル</span><span class="sxs-lookup"><span data-stu-id="ca891-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="ca891-165">*Project.assets.json*ファイルは、NuGet の依存関係グラフ、バインディングの解像度、およびその他のアプリのメタデータの完全なセット。</span><span class="sxs-lookup"><span data-stu-id="ca891-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="ca891-166">ファイルがなどの他のツールで使用が必要なこの[ `dotnet build` ](../tools/dotnet-build.md)と[ `dotnet run` ](../tools/dotnet-run.md)、ソース コードを処理します。</span><span class="sxs-lookup"><span data-stu-id="ca891-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="ca891-167">[`dotnet run`](../tools/dotnet-run.md)呼び出し[ `dotnet build` ](../tools/dotnet-build.md)が正常に構築し、呼び出しを確認する`dotnet <assembly.dll>`アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca891-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="ca891-168">高度なシナリオは、次を参照してください。 [.NET Core アプリケーションの配置](../deploying/index.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="ca891-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="ca891-169">.NET Core アプリケーションを dockerize します。</span><span class="sxs-lookup"><span data-stu-id="ca891-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="ca891-170">こんにちは .NET Core コンソール アプリは正常にローカルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca891-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="ca891-171">今すぐみましょうステップを実行すること、さらに、ビルドおよび Docker でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca891-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="ca891-172">最初の Dockerfile</span><span class="sxs-lookup"><span data-stu-id="ca891-172">Your first Dockerfile</span></span>

<span data-ttu-id="ca891-173">テキスト エディターを開き、始めましょう!</span><span class="sxs-lookup"><span data-stu-id="ca891-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="ca891-174">まだでアプリを構築しましたこんにちはディレクトリから取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="ca891-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="ca891-175">いずれかの Linux の次の Docker 命令を追加または[Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/)を新しいファイル。</span><span class="sxs-lookup"><span data-stu-id="ca891-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="ca891-176">完了したら、としてこんにちはディレクトリのルートに保存**Dockerfile**、拡張子のない (にファイルの種類を設定する必要があります`All types (*.*)`または似た)。</span><span class="sxs-lookup"><span data-stu-id="ca891-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="ca891-177">Dockerfile には、順番に実行される Docker ビルド命令が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ca891-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="ca891-178">最初の命令である必要があります[ **FROM**](https://docs.docker.com/engine/reference/builder/#from)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="ca891-179">この命令は、新しいビルド ステージを初期化し、残りの手順については、ベース イメージを設定します。</span><span class="sxs-lookup"><span data-stu-id="ca891-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="ca891-180">マルチ arch タグでは、Windows または Linux のいずれかのコンテナーをプル Docker for Windows に応じて[コンテナー モード](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="ca891-181">この例のベース イメージが microsoft/dotnet リポジトリから 2.0 sdk イメージです。</span><span class="sxs-lookup"><span data-stu-id="ca891-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="ca891-182">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir)命令セット、作業ディレクトリ、残りの実行、CMD、エントリ ポイント、コピー、および追加の Dockerfile の命令。</span><span class="sxs-lookup"><span data-stu-id="ca891-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="ca891-183">ディレクトリが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="ca891-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="ca891-184">この場合、WORKDIR はアプリのディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ca891-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="ca891-185">[**コピー** ](https://docs.docker.com/engine/reference/builder/#copy)命令がソース パスから新しいファイルまたはディレクトリをコピーし、変換先コンテナー ファイル システムに追加します。</span><span class="sxs-lookup"><span data-stu-id="ca891-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="ca891-186">この命令で、c# プロジェクト ファイルをコンテナーおコピーします。</span><span class="sxs-lookup"><span data-stu-id="ca891-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="ca891-187">[**実行**](https://docs.docker.com/engine/reference/builder/#run)命令は、現在のイメージの上に新しいレイヤーでどのようなコマンドを実行し、結果をコミットします。</span><span class="sxs-lookup"><span data-stu-id="ca891-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="ca891-188">結果のコミットされたイメージは、Dockerfile の次の手順に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca891-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="ca891-189">実行中**dotnet 復元**c# プロジェクト ファイルの必要な依存関係を取得します。</span><span class="sxs-lookup"><span data-stu-id="ca891-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="ca891-190">これは、**コピー**コードは、コピー、ファイルの残りの部分に、コンテナーに新しい[レイヤー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)です。</span><span class="sxs-lookup"><span data-stu-id="ca891-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="ca891-191">これを使用してアプリを公開**実行**命令します。</span><span class="sxs-lookup"><span data-stu-id="ca891-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="ca891-192">[ **Dotnet 発行**](../tools/dotnet-publish.md)コマンド、アプリケーションをコンパイルでは、その依存関係をプロジェクト ファイルで指定された読み取り、結果として得られる一連のファイルをディレクトリに発行します。</span><span class="sxs-lookup"><span data-stu-id="ca891-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="ca891-193">アプリが発行された、**リリース**構成と既定のディレクトリに出力します。</span><span class="sxs-lookup"><span data-stu-id="ca891-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="ca891-194">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint)命令により、実行可能ファイルとして実行するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="ca891-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="ca891-195">これで、Dockerfile を。</span><span class="sxs-lookup"><span data-stu-id="ca891-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="ca891-196">イメージへのアプリをコピーします。</span><span class="sxs-lookup"><span data-stu-id="ca891-196">copies your app to the image</span></span>
* <span data-ttu-id="ca891-197">イメージに、アプリの依存関係</span><span class="sxs-lookup"><span data-stu-id="ca891-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="ca891-198">実行可能ファイルとして実行するアプリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ca891-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="ca891-199">ビルドおよび実行するこんにちは .NET Core 2.0 アプリ</span><span class="sxs-lookup"><span data-stu-id="ca891-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="ca891-200">必須の Docker コマンド</span><span class="sxs-lookup"><span data-stu-id="ca891-200">Essential Docker commands</span></span>

<span data-ttu-id="ca891-201">これらの Docker コマンドは、不可欠な。</span><span class="sxs-lookup"><span data-stu-id="ca891-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="ca891-202">docker のビルド</span><span class="sxs-lookup"><span data-stu-id="ca891-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="ca891-203">docker の実行</span><span class="sxs-lookup"><span data-stu-id="ca891-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="ca891-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="ca891-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="ca891-205">docker stop</span><span class="sxs-lookup"><span data-stu-id="ca891-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="ca891-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="ca891-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="ca891-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="ca891-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="ca891-208">docker イメージ</span><span class="sxs-lookup"><span data-stu-id="ca891-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="ca891-209">ビルドおよび実行します。</span><span class="sxs-lookup"><span data-stu-id="ca891-209">Build and run</span></span>

<span data-ttu-id="ca891-210">Dockerfile; を作成します。今すぐ Docker では、アプリをビルドして、コンテナーを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca891-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="ca891-211">出力、`docker build`コマンドを次のコンソール出力に似たものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca891-211">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="ca891-212">出力からわかるように、Docker エンジンは、コンテナーの構築に Dockerfile を使用します。</span><span class="sxs-lookup"><span data-stu-id="ca891-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="ca891-213">出力、`docker run`コマンドを次のコンソール出力に似たものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca891-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="ca891-214">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="ca891-214">Congratulations!</span></span> <span data-ttu-id="ca891-215">だけがある場合。</span><span class="sxs-lookup"><span data-stu-id="ca891-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ca891-216">.NET Core のローカルのアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="ca891-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="ca891-217">最初のコンテナーを作成する Dockerfile を作成</span><span class="sxs-lookup"><span data-stu-id="ca891-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="ca891-218">構築され、Dockerized アプリの実行</span><span class="sxs-lookup"><span data-stu-id="ca891-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="ca891-219">次の手順</span><span class="sxs-lookup"><span data-stu-id="ca891-219">Next Steps</span></span>

<span data-ttu-id="ca891-220">ここでは、いくつか次の手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ca891-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="ca891-221">.NET Docker イメージのビデオの概要</span><span class="sxs-lookup"><span data-stu-id="ca891-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="ca891-222">Visual Studio、Docker と Azure のコンテナー インスタンス高度な連携します。</span><span class="sxs-lookup"><span data-stu-id="ca891-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="ca891-223">Azure クイック スタートの docker</span><span class="sxs-lookup"><span data-stu-id="ca891-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="ca891-224">Azure の Docker でのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="ca891-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="ca891-225">Azure のサブスクリプションを持っていない場合[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)30 日間の無料のアカウントと Azure サービスの任意の組み合わせを試す Azure クレジットの get $200 です。</span><span class="sxs-lookup"><span data-stu-id="ca891-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="ca891-226">このサンプルで使用する docker イメージ</span><span class="sxs-lookup"><span data-stu-id="ca891-226">Docker Images used in this sample</span></span>

<span data-ttu-id="ca891-227">次の Docker イメージは、このサンプルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca891-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="ca891-228">関連資料</span><span class="sxs-lookup"><span data-stu-id="ca891-228">Related Resources</span></span>

* [<span data-ttu-id="ca891-229">.NET core Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="ca891-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="ca891-230">Windows コンテナー上の Dockerfile</span><span class="sxs-lookup"><span data-stu-id="ca891-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="ca891-231">.NET framework の Docker のサンプル</span><span class="sxs-lookup"><span data-stu-id="ca891-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="ca891-232">ASP.NET Core dockerhub を使用しての</span><span class="sxs-lookup"><span data-stu-id="ca891-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="ca891-233">.NET Core アプリケーションの Docker のチュートリアルを dockerize します。</span><span class="sxs-lookup"><span data-stu-id="ca891-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="ca891-234">Visual Studio Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="ca891-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="ca891-235">Azure のコンテナー インスタンスを Azure のコンテナー レジストリから Docker イメージを展開します。</span><span class="sxs-lookup"><span data-stu-id="ca891-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
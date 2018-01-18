---
title: ".NET Core での Docker の基礎の学習"
description: "Docker と .NET Core の基本チュートリアル"
keywords: ".NET, .NET Core, Docker, チュートリアル"
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
ms.workload: dotnetcore
ms.openlocfilehash: 79ded2ce5de5100c18301127a2654f8791b8ed76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="208b7-104">.NET Core での Docker の基礎の学習</span><span class="sxs-lookup"><span data-stu-id="208b7-104">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="208b7-105">このチュートリアルでは、Docker コンテナー ビルドと .NET Core アプリケーションの展開タスクについて学習します。</span><span class="sxs-lookup"><span data-stu-id="208b7-105">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="208b7-106">このチュートリアルを通して、以下のことを学びます。</span><span class="sxs-lookup"><span data-stu-id="208b7-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="208b7-107">Dockerfile の作成方法</span><span class="sxs-lookup"><span data-stu-id="208b7-107">How to create a Dockerfile</span></span>
> * <span data-ttu-id="208b7-108">.NET Core アプリの作成方法</span><span class="sxs-lookup"><span data-stu-id="208b7-108">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="208b7-109">Docker コンテナーにアプリを展開する方法</span><span class="sxs-lookup"><span data-stu-id="208b7-109">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="208b7-110">[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)では [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)を使用してアプリを簡単にビルドし、[Docker イメージ](https://docs.docker.com/glossary/?term=image)としてパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="208b7-110">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="208b7-111">これらのイメージは [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 形式で記述され、[階層型コンテナー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)に展開され、実行されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-111">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="208b7-112">.NET Core: 入門として最も簡単な方法</span><span class="sxs-lookup"><span data-stu-id="208b7-112">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="208b7-113">Docker イメージを作成する前に、コンテナー化するアプリケーションを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="208b7-113">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="208b7-114">それは Linux、MacOS、Windows で作成できます。</span><span class="sxs-lookup"><span data-stu-id="208b7-114">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="208b7-115">これを行う最も迅速かつ簡単な方法は、.NET Core を利用することです。</span><span class="sxs-lookup"><span data-stu-id="208b7-115">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="208b7-116">.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/index.md)」(.NET Core SDK の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="208b7-116">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="208b7-117">Windows コンテナーと Linux コンテナーの両方を[マルチアーキテクチャ ベース タグ](https://github.com/dotnet/announcements/issues/14)でビルドできます。</span><span class="sxs-lookup"><span data-stu-id="208b7-117">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="208b7-118">初めての .NET Core Docker アプリ</span><span class="sxs-lookup"><span data-stu-id="208b7-118">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="208b7-119">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="208b7-119">Prerequisites</span></span>

<span data-ttu-id="208b7-120">このチュートリアルを完了するには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="208b7-120">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="208b7-121">.NET Core 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="208b7-121">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="208b7-122">[.NET Core SDK 2.0](https://www.microsoft.com/net/core) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="208b7-122">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="208b7-123">.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="208b7-123">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="208b7-124">コード エディターをまだインストールしていなければ、お気に入りのエディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="208b7-124">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="208b7-125">コード エディターをインストールする必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="208b7-125">Need to install a code editor?</span></span> <span data-ttu-id="208b7-126">[Visual Studio](https://visualstudio.com/downloads) をお試しください。</span><span class="sxs-lookup"><span data-stu-id="208b7-126">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="208b7-127">Docker クライアントをインストールする</span><span class="sxs-lookup"><span data-stu-id="208b7-127">Installing Docker Client</span></span>

<span data-ttu-id="208b7-128">[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) 以降の Docker クライアントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="208b7-128">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="208b7-129">Docker クライアントがインストール可能な OS:</span><span class="sxs-lookup"><span data-stu-id="208b7-129">The Docker client can be installed in:</span></span>

* <span data-ttu-id="208b7-130">Linux ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="208b7-130">Linux distributions</span></span>

   * [<span data-ttu-id="208b7-131">CentOS</span><span class="sxs-lookup"><span data-stu-id="208b7-131">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="208b7-132">Debian</span><span class="sxs-lookup"><span data-stu-id="208b7-132">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="208b7-133">Fedora</span><span class="sxs-lookup"><span data-stu-id="208b7-133">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="208b7-134">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="208b7-134">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="208b7-135">macOS</span><span class="sxs-lookup"><span data-stu-id="208b7-135">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="208b7-136">[Windows](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="208b7-136">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="208b7-137">Docker で動作させるために .NET Core 2.0 コンソール アプリを作成する</span><span class="sxs-lookup"><span data-stu-id="208b7-137">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="208b7-138">コマンド プロンプトを開き、*Hello* という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="208b7-138">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="208b7-139">作成したフォルダーに移動し、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="208b7-139">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="208b7-140">簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="208b7-140">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="208b7-141">[`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="208b7-141">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="208b7-142">また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。</span><span class="sxs-lookup"><span data-stu-id="208b7-142">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="208b7-143">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="208b7-143">`Hello.csproj`:</span></span>

   <span data-ttu-id="208b7-144">プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。</span><span class="sxs-lookup"><span data-stu-id="208b7-144">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="208b7-145">`OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。</span><span class="sxs-lookup"><span data-stu-id="208b7-145">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="208b7-146">`TargetFramework` タグは、対象の .NET 実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="208b7-146">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="208b7-147">高度なシナリオでは、複数の対象フレームワークを指定し、1 回の操作で指定したフレームワークにビルドできます。</span><span class="sxs-lookup"><span data-stu-id="208b7-147">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="208b7-148">このチュートリアルでは、.NET Core 2.0 のためにビルドします。</span><span class="sxs-lookup"><span data-stu-id="208b7-148">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="208b7-149">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="208b7-149">`Program.cs`:</span></span>

   <span data-ttu-id="208b7-150">プログラムは `using System` で始まります。</span><span class="sxs-lookup"><span data-stu-id="208b7-150">The program starts by `using System`.</span></span> <span data-ttu-id="208b7-151">これは、"`System` 名前空間のすべてがこのファイルのスコープになる" こと意味します。</span><span class="sxs-lookup"><span data-stu-id="208b7-151">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="208b7-152">`System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="208b7-152">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="208b7-153">次に、`Hello` という名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="208b7-153">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="208b7-154">名前空間は必要なものに変更できます。</span><span class="sxs-lookup"><span data-stu-id="208b7-154">You can change namespace to anything you want.</span></span> <span data-ttu-id="208b7-155">`Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-155">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="208b7-156">この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="208b7-156">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="208b7-157">今回の例では、"Hello World!" とだけ記述されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-157">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="208b7-158">記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="208b7-158">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="208b7-159">.NET Core 2.x では、**dotnet new** で [`dotnet restore`](../tools/dotnet-restore.md) コマンドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-159">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="208b7-160">**dotnet restore** は [NuGet](https://www.nuget.org/) (.NET パッケージ マネージャー) 呼び出しによって依存関係ツリーを復元します。</span><span class="sxs-lookup"><span data-stu-id="208b7-160">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="208b7-161">NuGet は次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="208b7-161">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="208b7-162">*Hello.csproj* ファイルを分析する</span><span class="sxs-lookup"><span data-stu-id="208b7-162">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="208b7-163">ファイル依存関係をダウンロードする (あるいはコンピューター キャッシュから取得する)</span><span class="sxs-lookup"><span data-stu-id="208b7-163">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="208b7-164">*obj/project.assets.json* ファイルを記述する</span><span class="sxs-lookup"><span data-stu-id="208b7-164">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="208b7-165">*project.assets.json* ファイルは、NuGet の依存関係グラフ、バインディング解決、その他のアプリ メタデータをすべて揃えたものです。</span><span class="sxs-lookup"><span data-stu-id="208b7-165">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="208b7-166">この必須ファイルは、ソース コードを正しく処理するために、[`dotnet build`](../tools/dotnet-build.md) や [`dotnet run`](../tools/dotnet-run.md) など、他のツールで使用されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-166">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="208b7-167">[`dotnet run`](../tools/dotnet-run.md) は [`dotnet build`](../tools/dotnet-build.md) を呼び出してビルドの成功を確認し、それから `dotnet <assembly.dll>` を呼び出してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="208b7-167">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="208b7-168">高度なシナリオについては、「[.NET Core アプリケーション展開](../deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="208b7-168">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="208b7-169">.NET Core アプリケーションを Docker で動作させる</span><span class="sxs-lookup"><span data-stu-id="208b7-169">Dockerize the .NET Core application</span></span>

<span data-ttu-id="208b7-170">Hello .NET Core コンソール アプリがローカルで正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-170">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="208b7-171">それでは先に進み、アプリをビルドし、Docker で実行します。</span><span class="sxs-lookup"><span data-stu-id="208b7-171">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="208b7-172">初めての Dockerfile</span><span class="sxs-lookup"><span data-stu-id="208b7-172">Your first Dockerfile</span></span>

<span data-ttu-id="208b7-173">テキスト エディターを開き、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="208b7-173">Open your text editor and let's get started!</span></span> <span data-ttu-id="208b7-174">引き続き、アプリをビルドした Hello ディレクトリから作業します。</span><span class="sxs-lookup"><span data-stu-id="208b7-174">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="208b7-175">Linux コンテナーまたは [Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/)の次の Docker 命令を新しいファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="208b7-175">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="208b7-176">完了したら、Hello ディレクトリのルートに **Dockerfile** として保存します。拡張子は付けません。場合によっては、ファイルの種類を `All types (*.*)` か、それと同様のものに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="208b7-176">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

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

<span data-ttu-id="208b7-177">Dockerfile ファイルには、順次実行される Docker ビルド命令が含まれています。</span><span class="sxs-lookup"><span data-stu-id="208b7-177">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="208b7-178">最初の命令は [**FROM**](https://docs.docker.com/engine/reference/builder/#from) のはずです。</span><span class="sxs-lookup"><span data-stu-id="208b7-178">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="208b7-179">この命令は新しいビルド ステージを初期化し、残りの命令のベース イメージを設定します。</span><span class="sxs-lookup"><span data-stu-id="208b7-179">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="208b7-180">マルチアーキテクチャ タグは、Docker for Windows [コンテナー モード](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)に基づき、Windows コンテナーまたは Linux コンテナーをプルします。</span><span class="sxs-lookup"><span data-stu-id="208b7-180">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="208b7-181">今回の例のベース イメージは microsoft/dotnet リポジトリの 2.0-sdk イメージです。</span><span class="sxs-lookup"><span data-stu-id="208b7-181">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="208b7-182">[**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) 命令は残りの命令、RUN、CMD、ENTRYPOINT、COPY、ADD Dockerfile の作業ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="208b7-182">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="208b7-183">ディレクトリが存在しなければ、作成されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-183">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="208b7-184">今回、WORKDIR がアプリ ディレクトリに設定されています。</span><span class="sxs-lookup"><span data-stu-id="208b7-184">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="208b7-185">[**COPY**](https://docs.docker.com/engine/reference/builder/#copy) 命令はソース パスから新しいファイルまたはディレクトリをコピーし、それをターゲットのコンテナー ファイルシステムに追加します。</span><span class="sxs-lookup"><span data-stu-id="208b7-185">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="208b7-186">この命令により、C# プロジェクトがコンテナーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="208b7-186">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="208b7-187">[**RUN**](https://docs.docker.com/engine/reference/builder/#run) 命令は現在のイメージに加えて新しい層でコマンドを実行し、結果をコミットします。</span><span class="sxs-lookup"><span data-stu-id="208b7-187">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="208b7-188">結果のコミットされたイメージは、Dockerfile の次の手順に使用されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-188">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="208b7-189">**dotnet restore** を実行し、C# プロジェクト ファイルの必要な依存関係を取得します。</span><span class="sxs-lookup"><span data-stu-id="208b7-189">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="208b7-190">この **COPY** 命令は、コンテナーの残りのファイルを新しい[層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)にコピーします。</span><span class="sxs-lookup"><span data-stu-id="208b7-190">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="208b7-191">この **RUN** 命令でアプリが公開されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-191">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="208b7-192">[**dotnet publish**](../tools/dotnet-publish.md) コマンドはアプリケーションをコンパイルし、プロジェクト ファイルに指定されているその依存関係を読み通し、結果的に生成された一連のファイルをディレクトリに公開します。</span><span class="sxs-lookup"><span data-stu-id="208b7-192">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="208b7-193">今回のアプリは **Release** 構成で公開され、既定のディレクトリに出力されます。</span><span class="sxs-lookup"><span data-stu-id="208b7-193">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="208b7-194">[**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) 命令では、コンテナーを実行可能ファイルとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="208b7-194">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="208b7-195">これで次のような Dockerfile が用意されました。</span><span class="sxs-lookup"><span data-stu-id="208b7-195">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="208b7-196">アプリをイメージにコピーする</span><span class="sxs-lookup"><span data-stu-id="208b7-196">copies your app to the image</span></span>
* <span data-ttu-id="208b7-197">アプリの依存関係をイメージにコピーする</span><span class="sxs-lookup"><span data-stu-id="208b7-197">your app's dependencies to the image</span></span>
* <span data-ttu-id="208b7-198">実行可能ファイルとして実行できるようにアプリをビルドする</span><span class="sxs-lookup"><span data-stu-id="208b7-198">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="208b7-199">Hello .NET Core 2.0 アプリをビルドし、実行する</span><span class="sxs-lookup"><span data-stu-id="208b7-199">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="208b7-200">基本的 Docker コマンド</span><span class="sxs-lookup"><span data-stu-id="208b7-200">Essential Docker commands</span></span>

<span data-ttu-id="208b7-201">次の Docker コマンドは不可欠です。</span><span class="sxs-lookup"><span data-stu-id="208b7-201">These Docker commands are essential:</span></span>

* [<span data-ttu-id="208b7-202">docker build</span><span class="sxs-lookup"><span data-stu-id="208b7-202">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="208b7-203">docker run</span><span class="sxs-lookup"><span data-stu-id="208b7-203">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="208b7-204">docker ps</span><span class="sxs-lookup"><span data-stu-id="208b7-204">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="208b7-205">docker stop</span><span class="sxs-lookup"><span data-stu-id="208b7-205">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="208b7-206">docker rm</span><span class="sxs-lookup"><span data-stu-id="208b7-206">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="208b7-207">docker rmi</span><span class="sxs-lookup"><span data-stu-id="208b7-207">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="208b7-208">docker image</span><span class="sxs-lookup"><span data-stu-id="208b7-208">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="208b7-209">ビルドして実行する</span><span class="sxs-lookup"><span data-stu-id="208b7-209">Build and run</span></span>

<span data-ttu-id="208b7-210">Dockerfile を記述しました。これで、Docker はアプリをビルドし、コンテナーを実行します。</span><span class="sxs-lookup"><span data-stu-id="208b7-210">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="208b7-211">`docker build` コマンドからの出力は、次のコンソール出力と同じようなものになります。</span><span class="sxs-lookup"><span data-stu-id="208b7-211">The output from the `docker build` command should be similar to the following console output:</span></span>

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

<span data-ttu-id="208b7-212">この出力からわかるように、Docker エンジンは Dockerfile を利用してコンテナーをビルドしました。</span><span class="sxs-lookup"><span data-stu-id="208b7-212">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="208b7-213">`docker run` コマンドからの出力は、次のコンソール出力と同じようなものになります。</span><span class="sxs-lookup"><span data-stu-id="208b7-213">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="208b7-214">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="208b7-214">Congratulations!</span></span> <span data-ttu-id="208b7-215">今回の成果:</span><span class="sxs-lookup"><span data-stu-id="208b7-215">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="208b7-216">ローカル .NET Core アプリを作成しました</span><span class="sxs-lookup"><span data-stu-id="208b7-216">Created a local .NET Core app</span></span>
> * <span data-ttu-id="208b7-217">Dockerfile を作成し、最初のコンテナーをビルドしました</span><span class="sxs-lookup"><span data-stu-id="208b7-217">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="208b7-218">Docker で動作させるアプリをビルドし、実行しました</span><span class="sxs-lookup"><span data-stu-id="208b7-218">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="208b7-219">次の手順</span><span class="sxs-lookup"><span data-stu-id="208b7-219">Next Steps</span></span>

<span data-ttu-id="208b7-220">次の手順としては以下のものを用意しています。</span><span class="sxs-lookup"><span data-stu-id="208b7-220">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="208b7-221">.NET Docker イメージの入門動画</span><span class="sxs-lookup"><span data-stu-id="208b7-221">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="208b7-222">Visual Studio、Docker、Azure コンテナーのインスタンスの併用の利点</span><span class="sxs-lookup"><span data-stu-id="208b7-222">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="208b7-223">Docker for Azure クイックスタート</span><span class="sxs-lookup"><span data-stu-id="208b7-223">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="208b7-224">Docker for Azure でアプリをデプロイする</span><span class="sxs-lookup"><span data-stu-id="208b7-224">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="208b7-225">Azure サブスクリプションをお持ちでない場合は、[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)して 30 日間の無料アカウントと 200 ドル分の Azure クレジットを取得し、お好きな Azure サービスの組み合わせを試しましょう。</span><span class="sxs-lookup"><span data-stu-id="208b7-225">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="208b7-226">このサンプルで使用されている Docker イメージ</span><span class="sxs-lookup"><span data-stu-id="208b7-226">Docker Images used in this sample</span></span>

<span data-ttu-id="208b7-227">次の Docker イメージはこのサンプルで使用されています</span><span class="sxs-lookup"><span data-stu-id="208b7-227">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="208b7-228">関連資料</span><span class="sxs-lookup"><span data-stu-id="208b7-228">Related Resources</span></span>

* [<span data-ttu-id="208b7-229">.NET Core Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="208b7-229">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="208b7-230">Windows コンテナー上の Dockerfile</span><span class="sxs-lookup"><span data-stu-id="208b7-230">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="208b7-231">.NET Framework Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="208b7-231">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="208b7-232">DockerHub の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="208b7-232">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="208b7-233">.NET Core アプリケーションを Docker で動作させる - Docker チュートリアル</span><span class="sxs-lookup"><span data-stu-id="208b7-233">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="208b7-234">Visual Studio Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="208b7-234">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="208b7-235">Azure Container Registry から Azure Container Instances に Docker イメージを配置する</span><span class="sxs-lookup"><span data-stu-id="208b7-235">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
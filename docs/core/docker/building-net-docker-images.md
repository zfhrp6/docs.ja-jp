---
title: ".NET Core の Docker イメージのビルド"
description: "Docker イメージと .NET Core について"
keywords: .NET, .NET Core, Docker
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.translationtype: HT
ms.sourcegitcommit: 9dc52f3a8c74c1aa575a83cb3bbd579b93fae9ae
ms.openlocfilehash: 0e679ffc22f52de5e2ce8194942efbb2f5299ee4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---

#<a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="c3a2e-104">.NET Core アプリケーションの Docker イメージのビルド</span><span class="sxs-lookup"><span data-stu-id="c3a2e-104">Building Docker Images for .NET Core Applications</span></span>

 
> [!IMPORTANT]
> <span data-ttu-id="c3a2e-105">.NET Core 2.0 は現在、更新作業中です。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-105">We are in the process of updating for .NET Core 2.0.</span></span> <span data-ttu-id="c3a2e-106">下記の手順は最新ではありません。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-106">The instructions below are out of date.</span></span> <span data-ttu-id="c3a2e-107">ご迷惑をおかけして申し訳ありません。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-107">We sincerely apologize for any inconvenience!</span></span>

<span data-ttu-id="c3a2e-108">.NET Core と Docker を一緒に使用する方法を理解するには、まず、提供されるさまざまな Docker イメージと、適切な使用のタイミングを把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-108">In order to get an understanding of how to use .NET Core and Docker together, we must first get to know the different Docker images that are offered and when is the right use case for them.</span></span> <span data-ttu-id="c3a2e-109">ここでは、提供されるバリエーションを確認し、ASP.NET Core Web API をビルドし、Yeoman Docker ツールを使用してデバッグ可能なコンテナーを作成し、さらにプロセスにおいて Visual Studio Code がどのように役立つかを簡単に確認します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-109">Here we will walk through the variations offered, build an ASP.NET Core Web API, use the Yeoman Docker tools to create a debuggable container as well as peek at how Visual Studio Code can assist in the process.</span></span> 

## <a name="docker-image-optimizations"></a><span data-ttu-id="c3a2e-110">Docker イメージの最適化</span><span class="sxs-lookup"><span data-stu-id="c3a2e-110">Docker Image Optimizations</span></span>

<span data-ttu-id="c3a2e-111">開発者向けの Docker イメージをビルドするにあたり、次の主な 3 つのシナリオに重点を置きました。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-111">When building Docker images for developers, we focused on three main scenarios:</span></span>

- <span data-ttu-id="c3a2e-112">.NET Core アプリの開発に使用されるイメージ</span><span class="sxs-lookup"><span data-stu-id="c3a2e-112">Images used to develop .NET Core apps</span></span>
- <span data-ttu-id="c3a2e-113">.NET Core アプリのビルドに使用されるイメージ</span><span class="sxs-lookup"><span data-stu-id="c3a2e-113">Images used to build .NET Core apps</span></span>
- <span data-ttu-id="c3a2e-114">.NET Core アプリの実行に使用されるイメージ</span><span class="sxs-lookup"><span data-stu-id="c3a2e-114">Images used to run .NET Core apps</span></span>

<span data-ttu-id="c3a2e-115">3 つのイメージである理由は、</span><span class="sxs-lookup"><span data-stu-id="c3a2e-115">Why three images?</span></span>
<span data-ttu-id="c3a2e-116">コンテナー化されたアプリケーションを開発、ビルドおよび実行する場合、優先順位がそれぞれ異なるためです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-116">When developing, building and running containerized applications, we have different priorities.</span></span>
- <span data-ttu-id="c3a2e-117">**開発:**  変更をどれだけ速く繰り返せるかと、変更のデバッグ機能。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-117">**Development:**  How fast can you iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="c3a2e-118">イメージのサイズはそれほど重要ではなく、むしろ、コードを変更し、それをすばやく確認できるかが重要になります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-118">The size of the image isn't as important, rather can you make changes to your code and see them quickly.</span></span> <span data-ttu-id="c3a2e-119">Visual Studio Code で使用する [yo docker](https://aka.ms/yodocker) などの一部のツールでは、開発時にこのイメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-119">Some of our tools, like [yo docker](https://aka.ms/yodocker) for use in Visual Studio Code use this image during development time.</span></span> 
- <span data-ttu-id="c3a2e-120">**ビルド:** アプリのコンパイルに必要なもの。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-120">**Build:** What's needed to compile your app.</span></span> <span data-ttu-id="c3a2e-121">これには、コンパイラと、バイナリを最適化するためのその他の依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-121">This includes the compiler and any other dependencies to optimize the binaries.</span></span> <span data-ttu-id="c3a2e-122">このイメージは配置するのではなく、実稼働イメージに配置するコンテンツをビルドする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-122">This image isn't the image you deploy, rather it's an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="c3a2e-123">このイメージは継続的インテグレーション、またはビルド環境で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-123">This image would be used in your continuous integration, or build environment.</span></span> <span data-ttu-id="c3a2e-124">たとえば、ビルド エージェントに直接すべての依存関係をインストールするのではなく、ビルド エージェントがビルド イメージをインスタンス化し、イメージ内に含まれるアプリのビルドに必要なすべての依存関係と共にアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-124">For instance, rather than installing all the dependencies directly on a build agent, the build agent would instance a build image to compile the application with all the dependencies required to build the app contained within the image.</span></span> <span data-ttu-id="c3a2e-125">この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-125">Your build agent only needs to know how to run this Docker image.</span></span> 
- <span data-ttu-id="c3a2e-126">**実稼働:** イメージをどれだけ速く配置し、開始できるか。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-126">**Production:** How fast you can deploy and start your image.</span></span> <span data-ttu-id="c3a2e-127">このイメージは小さいため、Docker レジストリから Docker ホストにネットワーク経由ですばやく移動できます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-127">This image is small so it can quickly travel across the network from your Docker Registry to your Docker hosts.</span></span> <span data-ttu-id="c3a2e-128">コンテンツは実行できる状態であるため、Docker の実行から結果の処理までを最速で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-128">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="c3a2e-129">変更できない Docker モデルの場合は、コードを動的にコンパイルする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-129">In the immutable Docker model, there's no need for dynamic compilation of code.</span></span> <span data-ttu-id="c3a2e-130">このイメージに配置するコンテンツは、アプリケーションの実行に必要なバイナリとコンテンツに制限されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-130">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span> <span data-ttu-id="c3a2e-131">たとえば、`dotnet publish` を使用して発行された出力には、コンパイル済みのバイナリ、イメージ、.js および .css ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-131">For example, the published output using `dotnet publish` which contains the compiled binaries, images, .js and .css files.</span></span> <span data-ttu-id="c3a2e-132">時間の経過と共に、事前に Just-In-Time (JIT) にコンパイルされたパッケージを含むイメージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-132">Over time, you'll see images that contain pre-jitted packages.</span></span>  

<span data-ttu-id="c3a2e-133">複数のバージョンの .NET Core イメージがありますが、すべて 1 つ以上のレイヤーを共有します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-133">Though there are multiple versions of the .NET Core image, they all share one or more layers.</span></span> <span data-ttu-id="c3a2e-134">格納に必要なディスク容量やレジストリからプルするデルタは、全体よりはるかに少なくなります。これは、すべてのイメージが同じ基本レイヤーとおそらく他のレイヤーを共有しているためです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-134">The amount of disk space needed to store or the delta to pull from your registry is much smaller than the whole because all of the images share the same base layer and potentially others.</span></span>  

## <a name="docker-image-variations"></a><span data-ttu-id="c3a2e-135">Docker イメージのバリエーション</span><span class="sxs-lookup"><span data-stu-id="c3a2e-135">Docker image variations</span></span>

<span data-ttu-id="c3a2e-136">上記の目標を達成するために、[microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) にはイメージ バリアントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-136">To achieve the goals above, we provide image variants under [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

- <span data-ttu-id="c3a2e-137">`microsoft/dotnet:<version>-sdk`: **microsoft/dotnet:1.0.0-preview2-sdk** です。このイメージには、.NET Core とコマンド ライン ツール (CLI) を含む .NET Core SDK が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-137">`microsoft/dotnet:<version>-sdk` : that is **microsoft/dotnet:1.0.0-preview2-sdk**, this image contains the .NET Core SDK which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="c3a2e-138">このイメージは **開発シナリオ** にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-138">This image maps to the **development scenario**.</span></span> <span data-ttu-id="c3a2e-139">このイメージは、ローカル開発、デバッグおよび単体テストに使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-139">You would use this image for local development, debugging and unit testing.</span></span> <span data-ttu-id="c3a2e-140">たとえば、コードをチェックインする前に、すべての開発を行います。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-140">For example, all the development you do, before you check in your code.</span></span> <span data-ttu-id="c3a2e-141">このイメージは、**ビルド** シナリオでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-141">This image can also be used for your **build** scenarios.</span></span>

- <span data-ttu-id="c3a2e-142">`microsoft/dotnet:<version>-core`: **microsoft/dotnet:1.0.0-core** です。このイメージは[ポータブル .NET Core アプリケーション](../deploying/index.md)を実行します。**実稼働**でアプリケーションを実行するために最適化されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-142">`microsoft/dotnet:<version>-core` : that is **microsoft/dotnet:1.0.0-core**, image which runs [portable .NET Core applications](../deploying/index.md) and it is optimized for running your application in **production**.</span></span> <span data-ttu-id="c3a2e-143">これには SDK が含まれていません。`dotnet publish` の最適化された出力を取得するためのものです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-143">It does not contain the SDK, and is meant to take the optimized output of `dotnet publish`.</span></span> <span data-ttu-id="c3a2e-144">ポータブル ランタイムは、共有イメージ レイヤーによる利点が得られるため、複数のコンテナーを実行する Docker コンテナー シナリオに最適です。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-144">The portable runtime is well suited for Docker container scenarios as running multiple containers benefit from shared image layers.</span></span>  

## <a name="alternative-images"></a><span data-ttu-id="c3a2e-145">その他のイメージ</span><span class="sxs-lookup"><span data-stu-id="c3a2e-145">Alternative images</span></span>

<span data-ttu-id="c3a2e-146">開発、ビルドおよび実稼働の最適化されたシナリオに加え、次の追加イメージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-146">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

- <span data-ttu-id="c3a2e-147">`microsoft/dotnet:<version>-onbuild`: **microsoft/dotnet:1.0.0-preview2-onbuild** です。これには [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) トリガーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-147">`microsoft/dotnet:<version>-onbuild` : that is **microsoft/dotnet:1.0.0-preview2-onbuild**, contains [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) triggers.</span></span> <span data-ttu-id="c3a2e-148">このビルドではアプリケーションを[コピー](https://docs.docker.com/engine/reference/builder/#/copy)し、`dotnet restore` を実行して [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) の `dotnet run` 命令を作成して、Docker イメージの実行時にアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-148">The build will [COPY](https://docs.docker.com/engine/reference/builder/#/copy) your application, run `dotnet restore` and create an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` instruction to run the application when the Docker image is run.</span></span> <span data-ttu-id="c3a2e-149">実稼働用にイメージは最適化されませんが、単にソース コードをイメージにコピーして実行する際に便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-149">While not an optimized image for production, some may find it useful to simply copy their source code into an image and run it.</span></span> 

- <span data-ttu-id="c3a2e-150">`microsoft/dotnet:<version>-core-deps`: **microsoft/dotnet:1.0.0-core-deps** です。自己完結型アプリケーションを実行する場合は、このイメージを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-150">`microsoft/dotnet:<version>-core-deps` : that is **microsoft/dotnet:1.0.0-core-deps**, if you wish to run self-contained applications use this image.</span></span> <span data-ttu-id="c3a2e-151">これには、.NET Core で必要なすべてのネイティブの依存関係があるオペレーティング システムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-151">It contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="c3a2e-152">このイメージを、独自のカスタム CoreFX または CoreCLR ビルドの基本イメージとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-152">This image can also be used as a base image for your own custom CoreFX or CoreCLR builds.</span></span> <span data-ttu-id="c3a2e-153">**onbuild** バリアントは単にコードをイメージに配置して実行するために最適化されますが、このイメージは、アプリケーションと共にパッケージ化された .NET ランタイムがある .NET Core アプリの実行に必要なオペレーティング システムの依存関係のみを持つように最適化されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-153">While the **onbuild** variant is optimized to simply place your code in an image and run it, this image is optimized to have only the operating system dependencies required to run .NET Core apps that have the .NET runtime packaged with the application.</span></span> <span data-ttu-id="c3a2e-154">通常、このイメージは同じホスト上の複数の .NET Core コンテナーを実行するために最適化されません。これは、イメージにはそれぞれアプリケーション内に .NET Core ランタイムがあるためです。イメージをレイヤー化する利点はありません。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-154">This image isn't generally optimized for running multiple .NET Core containers on the same host, as each image carries the .NET Core runtime within the application, and you will not benefit from image layering.</span></span>   

<span data-ttu-id="c3a2e-155">各バリアントの最新バージョン:</span><span class="sxs-lookup"><span data-stu-id="c3a2e-155">Latest versions of each variant:</span></span>

- <span data-ttu-id="c3a2e-156">`microsoft/dotnet` または `microsoft/dotnet:latest` (SDK を含む)</span><span class="sxs-lookup"><span data-stu-id="c3a2e-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (includes SDK)</span></span>
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

<span data-ttu-id="c3a2e-157">ここでは、さまざまなサイズを表示するための開発用コンピューターでの `docker pull <imagename>` の実行後のイメージのリストを示します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-157">Here is a list of the images after a `docker pull <imagename>` on a development machine to show the various sizes.</span></span> <span data-ttu-id="c3a2e-158">開発/ビルド バリアントの `microsoft/dotnet:1.0.0-preview2-sdk` には、アプリケーションの開発とビルドのための SDK が含まれているため、サイズが大きくなっていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-158">Notice, the development/build variant, `microsoft/dotnet:1.0.0-preview2-sdk` is larger as it contains the SDK to develop and build your application.</span></span> <span data-ttu-id="c3a2e-159">実稼働バリアントの `microsoft/dotnet:core` には .NET Core ランタイムのみが含まれるため、サイズは小さくなっています。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-159">The production variant, `microsoft/dotnet:core` is smaller, as it only contains the .NET Core runtime.</span></span> <span data-ttu-id="c3a2e-160">Linux で使用できる最小イメージの `core-deps` は非常に小さくなっていますが、アプリケーションはこれと一緒に .NET ランタイムのプライベート コピーをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-160">The minimal image capable of being used on Linux, `core-deps`, is quite smaller, however your application will need to copy a private copy of the .NET runtime with it.</span></span> <span data-ttu-id="c3a2e-161">コンテナーは既にプライベート分離バリアになっているため、複数の dotnet ベース コンテナーを実行するとその最適化が失われます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-161">Since containers are already private isolation barriers, you will lose that optimization when running multiple dotnet based containers.</span></span> 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a><span data-ttu-id="c3a2e-162">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c3a2e-162">Prerequisites</span></span>

<span data-ttu-id="c3a2e-163">ビルドと実行には、以下のいくつかのものをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-163">To build and run, you'll need a few things installed:</span></span>

- [<span data-ttu-id="c3a2e-164">.NET Core</span><span class="sxs-lookup"><span data-stu-id="c3a2e-164">.NET Core</span></span>](http://dot.net)
- <span data-ttu-id="c3a2e-165">[Docker](https://www.docker.com/products/docker)。Docker コンテナーをローカルで実行するためのものです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-165">[Docker](https://www.docker.com/products/docker) to run your Docker containers locally</span></span>
- [<span data-ttu-id="c3a2e-166">Node.js</span><span class="sxs-lookup"><span data-stu-id="c3a2e-166">Node.js</span></span>](https://nodejs.org/)
- <span data-ttu-id="c3a2e-167">[ASP.NET の Yeoman ジェネレーター](https://github.com/omnisharp/generator-aspnet)。Web API アプリケーションを作成するためのものです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-167">[Yeoman generator for ASP.NET](https://github.com/omnisharp/generator-aspnet) for creating the Web API application</span></span>
- <span data-ttu-id="c3a2e-168">[Docker の Yeoman ジェネレーター](http://aka.ms/yodocker)。Microsoft が提供するものです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-168">[Yeoman generator for Docker](http://aka.ms/yodocker) from Microsoft</span></span>

<span data-ttu-id="c3a2e-169">以下の npm を使用して、ASP.NET Core と Docker の Yeoman ジェネレーターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-169">Install the Yeoman generators for ASP.NET Core and Docker using npm</span></span> 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> <span data-ttu-id="c3a2e-170">このサンプルでは、エディターに [Visual Studio Code](http://code.visualstudio.com) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-170">This sample will be using [Visual Studio Code](http://code.visualstudio.com) for the editor.</span></span>

## <a name="creating-the-web-api-application"></a><span data-ttu-id="c3a2e-171">Web API アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="c3a2e-171">Creating the Web API application</span></span>

<span data-ttu-id="c3a2e-172">参照ポイントとして、アプリケーションをコンテナー化する前に、まず、アプリケーションをローカルで実行します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-172">For a reference point, before we containerize the application, first run the application locally.</span></span> 

<span data-ttu-id="c3a2e-173">完成したアプリケーションは [GitHub の dotnet/docs リポジトリ](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images)にあります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-173">The finished application is located in the [dotnet/docs repository on GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images).</span></span> <span data-ttu-id="c3a2e-174">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-174">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="c3a2e-175">アプリケーションのディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-175">Create a directory for your application.</span></span>

<span data-ttu-id="c3a2e-176">そのディレクトリでコマンドまたはターミナル セッションを開き、以下のように入力して ASP.NET Yeoman ジェネレーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-176">Open a command or terminal session in that directory and use the ASP.NET Yeoman generator by typing the following:</span></span>
```
yo aspnet
```

<span data-ttu-id="c3a2e-177">**Web API アプリケーション**を選択し、アプリ名として **api** と入力してから Enter をタップします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-177">Select **Web API Application** and type **api** for the name of the app and tap enter.</span></span>  <span data-ttu-id="c3a2e-178">アプリケーションがスキャフォールディングされたら、`/api` ディレクトリに変更し、`dotnet restore` を使用して NuGet 依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-178">Once the application is scaffolded, change to the `/api` directory and restore the NuGet dependencies using `dotnet restore`.</span></span>

```
cd api
dotnet restore
```

<span data-ttu-id="c3a2e-179">`dotnet run` を使用し、**http://localhost:5000/api/values** を参照してアプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-179">Test the application using `dotnet run` and browsing to **http://localhost:5000/api/values**</span></span>

```javascript
[
    "value1",
    "value2"
]
```

<span data-ttu-id="c3a2e-180">`Ctrl+C` を使用してアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-180">Use `Ctrl+C` to stop the application.</span></span>

## <a name="adding-docker-support"></a><span data-ttu-id="c3a2e-181">Docker サポートの追加</span><span class="sxs-lookup"><span data-stu-id="c3a2e-181">Adding Docker support</span></span>

<span data-ttu-id="c3a2e-182">プロジェクトへの Docker サポートの追加は、Microsoft の Yeoman ジェネレーターを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-182">Adding Docker support to the project is achieved using the Yeoman generator from Microsoft.</span></span> <span data-ttu-id="c3a2e-183">現在、コンテナー内でのプロジェクトのビルドと実行に役立つ Dockerfile とスクリプトを作成するにより、.NET Core、Node.js および Go プロジェクトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-183">It currently supports .NET Core, Node.js and Go projects by creating a Dockerfile and scripts that help build and run projects inside containers.</span></span> <span data-ttu-id="c3a2e-184">エディターのデバッグとコマンド パレットのサポートのために Visual Studio Code 固有のファイル (launch.json、tasks.json) も追加されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-184">Visual Studio Code specific files are also added (launch.json, tasks.json) for editor debugging and command palette support.</span></span>

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js
```

- <span data-ttu-id="c3a2e-185">プロジェクトの種類として `.NET Core` を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-185">Select `.NET Core` as the project type</span></span>
- <span data-ttu-id="c3a2e-186">`rtm`: .NET Core のバージョン用。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-186">`rtm` for the version of .NET Core</span></span>
- <span data-ttu-id="c3a2e-187">`Y`: プロジェクトで Web サーバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-187">`Y` the project uses a web server</span></span>
- <span data-ttu-id="c3a2e-188">`5000`: Web API アプリケーションがリッスンしているポート (http://localhost:5000) です。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-188">`5000` is the port the Web API application is listening on (http://localhost:5000)</span></span>
- <span data-ttu-id="c3a2e-189">`api`: イメージ名用。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-189">`api` for the image name</span></span>
- <span data-ttu-id="c3a2e-190">`api`: サービス名用。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-190">`api` for the service name</span></span>
- <span data-ttu-id="c3a2e-191">`api`: 構成プロジェクト用。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-191">`api` for the compose project</span></span> 
- <span data-ttu-id="c3a2e-192">`Y`: 現在の Dockerfile を上書きします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-192">`Y` to overwrite the current Dockerfile</span></span>

<span data-ttu-id="c3a2e-193">ジェネレーターが完了すると、以下のファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-193">When the generator is complete, the following files are added to the project</span></span>

- <span data-ttu-id="c3a2e-194">.vscode/launch.json</span><span class="sxs-lookup"><span data-stu-id="c3a2e-194">.vscode/launch.json</span></span>
- <span data-ttu-id="c3a2e-195">Dockerfile.debug</span><span class="sxs-lookup"><span data-stu-id="c3a2e-195">Dockerfile.debug</span></span>
- <span data-ttu-id="c3a2e-196">Dockerfile</span><span class="sxs-lookup"><span data-stu-id="c3a2e-196">Dockerfile</span></span>
- <span data-ttu-id="c3a2e-197">docker-compose.debug.yml</span><span class="sxs-lookup"><span data-stu-id="c3a2e-197">docker-compose.debug.yml</span></span>
- <span data-ttu-id="c3a2e-198">docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="c3a2e-198">docker-compose.yml</span></span>
- <span data-ttu-id="c3a2e-199">dockerTask.ps1</span><span class="sxs-lookup"><span data-stu-id="c3a2e-199">dockerTask.ps1</span></span>
- <span data-ttu-id="c3a2e-200">dockerTask.sh</span><span class="sxs-lookup"><span data-stu-id="c3a2e-200">dockerTask.sh</span></span>
- <span data-ttu-id="c3a2e-201">.vscode/tasks.json</span><span class="sxs-lookup"><span data-stu-id="c3a2e-201">.vscode/tasks.json</span></span>

<span data-ttu-id="c3a2e-202">ジェネレーターは 2 つの Dockerfile を作成します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-202">The generator creates two Dockerfiles.</span></span>

<span data-ttu-id="c3a2e-203">**Dockerfile.debug** - このファイルは **microsoft/dotnet:1.0.0-preview2-sdk** イメージに基づいています。イメージ バリアント リストのイメージの場合は、SDK、CLI および .NET Core が含まれ、開発やデバッグ (F5) 用に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-203">**Dockerfile.debug** - this file is based on the **microsoft/dotnet:1.0.0-preview2-sdk** image which if you note from the list of image variants, includes the SDK, CLI and .NET Core and will be the image used for development and debugging (F5).</span></span> <span data-ttu-id="c3a2e-204">これらすべてのコンポーネントを含めると、サイズが約 540 MB の大きなイメージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-204">Including all of these components produces a larger image with a size roughly of 540MB.</span></span>

<span data-ttu-id="c3a2e-205">**Dockerfile** - このイメージは **microsoft/dotnet:1.0.0-core** に基づくリリース イメージで、実稼働で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-205">**Dockerfile** - this image is the release image based on **microsoft/dotnet:1.0.0-core** and should be used for production.</span></span> <span data-ttu-id="c3a2e-206">ビルド時のこのイメージは約 253 MB です。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-206">This image when built is approximately 253 MB.</span></span>

### <a name="creating-the-docker-images"></a><span data-ttu-id="c3a2e-207">Docker イメージの作成</span><span class="sxs-lookup"><span data-stu-id="c3a2e-207">Creating the Docker images</span></span>
<span data-ttu-id="c3a2e-208">`dockerTask.sh` または `dockerTask.ps1` スクリプトを使用して、特定の環境の **api** アプリケーション用にイメージとコンテナーをビルドまたは構成することができます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-208">Using the `dockerTask.sh` or `dockerTask.ps1` script, we can build or compose the image and container for the **api** application for a specific environment.</span></span> <span data-ttu-id="c3a2e-209">以下のコマンドを実行して、**debug** イメージをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-209">Build the **debug** image by running the following command.</span></span>

```bash
./dockerTask.sh build debug
```

<span data-ttu-id="c3a2e-210">このイメージでは ASP.NET アプリケーションをビルドし、`dotnet restore` を実行して、デバッガーをイメージに追加し、`ENTRYPOINT` を設定して最後にアプリをイメージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-210">The image will build the ASP.NET application, run `dotnet restore`, add the debugger to the image, set an `ENTRYPOINT` and finally copy the app to the image.</span></span> <span data-ttu-id="c3a2e-211">その結果、`TAG` が *debug* の *api* という名前の Docker イメージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-211">The result is a Docker image named *api* with a `TAG` of *debug*.</span></span>  <span data-ttu-id="c3a2e-212">`docker images` を使用した場合のコンピューター上のイメージは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-212">See the images on the machine using `docker images`.</span></span>

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

<span data-ttu-id="c3a2e-213">イメージを生成し、Docker コンテナー内でアプリケーションを実行する別の方法は、Visual Studio Code でアプリケーションを開き、デバッグ ツールを使用することです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-213">Another way to generate the image and run the application within the Docker container is to open the application in Visual Studio Code and use the debugging tools.</span></span> 

<span data-ttu-id="c3a2e-214">Visual Studio Code の左側にあるビュー バーのデバッグ アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-214">Select the debugging icon in the View Bar on the left side of Visual Studio Code.</span></span>

![vscode デバッグ アイコン](./media/building-net-docker-images/debugging_debugicon.png)

<span data-ttu-id="c3a2e-216">次に、再生アイコンまたは F5 をタップして、イメージを生成し、コンテナー内でアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-216">Then tap the play icon or F5 to generate the image and start the application within the container.</span></span> <span data-ttu-id="c3a2e-217">Web API は、http://localhost:5000 の既定の Web ブラウザーを使用して起動されます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-217">The Web API will be launched using your default web browser at http://localhost:5000.</span></span>

![VSCode Docker ツールのデバッグ](./media/building-net-docker-images/docker-tools-vscode-f5.png)

<span data-ttu-id="c3a2e-219">アプリケーションがコンテナー内ではなく、開発用コンピューターでローカルに実行されている場合と同じように、アプリケーションでのブレーク ポイントの設定やステップスルーなどを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-219">You may set break points in your application, step through, etc. just as if the application was running locally on your development machine as opposed to inside the container.</span></span> <span data-ttu-id="c3a2e-220">コンテナー内でのデバッグのメリットは、運用環境に配置されるイメージと同じであることです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-220">The benefit to debugging within the container is this is the same image that would be deployed to a production environment.</span></span>

<span data-ttu-id="c3a2e-221">リリースまたは実稼働イメージを作成する場合、`release` 環境名を渡すターミナルからコマンドを実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-221">Creating the release or production image requires simply running the command from the terminal passing the `release` environment name.</span></span>

```bash
./dockerTask build release
```

<span data-ttu-id="c3a2e-222">このコマンドは、より小さな **microsoft/dotnet:core** 基本イメージに基づいてイメージを作成し、ポート 5000 を[公開](https://docs.docker.com/engine/reference/builder/#/expose)し、`dotnet api.dll` の [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) を設定して `/app` ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-222">The command creates the image based on the smaller **microsoft/dotnet:core** base image, [EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) port 5000, sets the [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) for `dotnet api.dll` and copies it to the `/app` directory.</span></span> <span data-ttu-id="c3a2e-223">デバッガー、SDK または `dotnet restore` がない場合、イメージは非常に小さくなります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-223">There is no debugger, SDK or `dotnet restore` resulting in a much smaller image.</span></span> <span data-ttu-id="c3a2e-224">イメージの名前は **api** で、`TAG` は **latest** になります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-224">The image is named **api** with a `TAG` of **latest**.</span></span>

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a><span data-ttu-id="c3a2e-225">まとめ</span><span class="sxs-lookup"><span data-stu-id="c3a2e-225">Summary</span></span>

<span data-ttu-id="c3a2e-226">Docker ジェネレーターを使用して Web API アプリケーションに必要なファイルを追加することで、開発および実稼働バージョンのイメージを作成するプロセスが簡単になりました。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-226">Using the Docker generator to add the necessary files to our Web API application made the process simple to create the development and production versions of the images.</span></span>  <span data-ttu-id="c3a2e-227">また、クロス プラットフォームのツールを使用し、PowerShell スクリプトを指定することで、コンテナー内のアプリケーションのステップ スルー デバッグを提供する Windows と Visual Studio Code の統合と同じ結果が得られるようになります。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-227">The tooling is cross platform by also providing a PowerShell script to accomplish the same results on Windows and Visual Studio Code integration providing step through debugging of the application within the container.</span></span> <span data-ttu-id="c3a2e-228">イメージ バリアントとターゲット シナリオを理解することで、実稼働配置用に最適化されたイメージを生成できるだけでなく、内部ループの開発プロセスを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="c3a2e-228">By understanding the image variants and the target scenarios, you can optimize your inner-loop development process, while achieving optimized images for production deployments.</span></span>  




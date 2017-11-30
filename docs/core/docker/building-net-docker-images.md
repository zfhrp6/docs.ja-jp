---
title: ".NET Core の Docker イメージのビルド"
description: "Docker イメージと .NET Core について"
keywords: .NET, .NET Core, Docker
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
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="f25a4-104">.NET Core アプリケーションの Docker イメージのビルド</span><span class="sxs-lookup"><span data-stu-id="f25a4-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="f25a4-105">このチュートリアルでは Docker で .NET Core を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="f25a4-106">最初に、提供され、Microsoft とユース ケースで保持されているさまざまな Docker イメージをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="f25a4-107">ビルドし、ASP.NET Core アプリケーションの dockerize 方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="f25a4-108">このチュートリアルの中には、次の操作を説明します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f25a4-109">Microsoft .NET Core Docker イメージについてください。</span><span class="sxs-lookup"><span data-stu-id="f25a4-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="f25a4-110">ASP.NET Core Dockerize するサンプル アプリを取得します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="f25a4-111">ASP.NET サンプル アプリをローカルで実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="f25a4-112">ビルドおよび Docker を使用した Linux コンテナーのサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="f25a4-113">ビルドおよび Docker for Windows コンテナーでサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="f25a4-114">Docker イメージの最適化</span><span class="sxs-lookup"><span data-stu-id="f25a4-114">Docker Image Optimizations</span></span>

<span data-ttu-id="f25a4-115">開発者向けの Docker イメージをビルドするにあたり、次の主な 3 つのシナリオに重点を置きました。</span><span class="sxs-lookup"><span data-stu-id="f25a4-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="f25a4-116">.NET Core アプリの開発に使用されるイメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="f25a4-117">.NET Core アプリのビルドに使用されるイメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="f25a4-118">.NET Core アプリの実行に使用されるイメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="f25a4-119">3 つのイメージである理由は、</span><span class="sxs-lookup"><span data-stu-id="f25a4-119">Why three images?</span></span>
<span data-ttu-id="f25a4-120">開発、構築、およびコンテナー化アプリケーションを実行している、ときに、異なる優先順位があります。</span><span class="sxs-lookup"><span data-stu-id="f25a4-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="f25a4-121">**開発:**優先順位について重点的に説明は、変更、および変更をデバッグする機能にすばやく反復処理します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="f25a4-122">イメージのサイズが、重要ではないではなくことができます、コードに変更を加えるそれらをすばやく確認しますか。</span><span class="sxs-lookup"><span data-stu-id="f25a4-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="f25a4-123">**ビルド:**このイメージには、コンパイラとバイナリを最適化するために他の依存関係を含むアプリのコンパイルに必要なすべてが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f25a4-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="f25a4-124">実稼働のイメージに配置する資産を作成するのにビルド イメージを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="f25a4-125">ビルド イメージが、継続的インテグレーションは、またはビルド環境で使用されます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="f25a4-126">これにより、ビルド エージェントをコンパイルし、ビルドの画像インスタンスの (すべての必要な依存関係を持つ) アプリケーションをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="f25a4-127">この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。</span><span class="sxs-lookup"><span data-stu-id="f25a4-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="f25a4-128">**実稼働:**どの程度の速度を配置して、イメージを起動できますか。</span><span class="sxs-lookup"><span data-stu-id="f25a4-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="f25a4-129">Docker レジストリから Docker ホストのネットワーク パフォーマンスが最適化されたために、このイメージは小さなです。</span><span class="sxs-lookup"><span data-stu-id="f25a4-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="f25a4-130">コンテンツは実行できる状態であるため、Docker の実行から結果の処理までを最速で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="f25a4-131">動的なコード コンパイル Docker モデルでは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f25a4-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="f25a4-132">このイメージに配置するコンテンツは、アプリケーションの実行に必要なバイナリとコンテンツに制限されます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="f25a4-133">たとえば、`dotnet publish`出力が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="f25a4-134">コンパイル済みバイナリ</span><span class="sxs-lookup"><span data-stu-id="f25a4-134">the compiled binaries</span></span>
    * <span data-ttu-id="f25a4-135">.js および .css ファイル</span><span class="sxs-lookup"><span data-stu-id="f25a4-135">.js and .css files</span></span>


<span data-ttu-id="f25a4-136">含める理由、`dotnet publish`運用イメージのコマンドの出力が保存されますその ' サイズを最小限にします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="f25a4-137">一部の画像を .NET Core は、比較的軽量プロセスは、最新のタグをダウンロードするための別のタグの間のレイヤーを共有します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="f25a4-138">コンピューターに既に以前のバージョンが場合、このアーキテクチャは、必要なディスク領域を減少します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="f25a4-139">複数のアプリケーションでは、一般的なイメージを使用して、同じコンピューター上、ときに、メモリは、共通のイメージの間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="f25a4-140">イメージは、共有する同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f25a4-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="f25a4-141">Docker イメージのバリエーション</span><span class="sxs-lookup"><span data-stu-id="f25a4-141">Docker image variations</span></span>

<span data-ttu-id="f25a4-142">上記の目標を達成するには、するには、イメージのバリエーションを指定お[ `microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/)です。</span><span class="sxs-lookup"><span data-stu-id="f25a4-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="f25a4-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) このイメージには、.NET Core およびコマンドライン ツール (CLI) を含む、.NET Core SDK が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f25a4-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="f25a4-144">このイメージは **開発シナリオ** にマップされます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="f25a4-145">このイメージを使用して、ローカルの開発、デバッグ、および単体テストをします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="f25a4-146">このイメージは、**ビルド** シナリオでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="f25a4-147">使用して`microsoft/dotnet:sdk`常に最新バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="f25a4-148">使用する場合、不明なニーズに関する場合、`microsoft/dotnet:<version>-sdk`イメージ。</span><span class="sxs-lookup"><span data-stu-id="f25a4-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="f25a4-149">「事実上」のイメージとして設計となっており、throw として使用する退席中のコンテナー (ソース コードをマウントおよびアプリを起動するコンテナーを起動) と、基本イメージから他のイメージを構築します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="f25a4-150">`microsoft/dotnet:<version>-runtime`: このイメージは、.NET Core (ランタイムおよびライブラリ) が含まれており、で .NET Core アプリを実行するために最適化された**運用**です。</span><span class="sxs-lookup"><span data-stu-id="f25a4-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="f25a4-151">その他のイメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-151">Alternative images</span></span>

<span data-ttu-id="f25a4-152">開発、ビルドおよび実稼働の最適化されたシナリオに加え、次の追加イメージが提供されます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="f25a4-153">`microsoft/dotnet:<version>-runtime-deps`**ランタイム deps**イメージには、すべての .NET Core で必要なネイティブの依存関係と、オペレーティング システムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f25a4-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="f25a4-154">このイメージは[自己完結型アプリケーション](https://docs.microsoft.com/dotnet/core/deploying/index)です。</span><span class="sxs-lookup"><span data-stu-id="f25a4-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="f25a4-155">各バリアントの最新バージョン:</span><span class="sxs-lookup"><span data-stu-id="f25a4-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="f25a4-156">`microsoft/dotnet`または`microsoft/dotnet:latest`(SDK のイメージの別名)</span><span class="sxs-lookup"><span data-stu-id="f25a4-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="f25a4-157">サンプルを探索するには</span><span class="sxs-lookup"><span data-stu-id="f25a4-157">Samples to explore</span></span>

* <span data-ttu-id="f25a4-158">[この ASP.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)ASP.NET Core 実稼働環境用のアプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="f25a4-159">このサンプルは、Linux と Windows の両方のコンテナーで動作します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="f25a4-160">この .NET Core Docker サンプルのベスト プラクティス パターン[実稼働用アプリの .NET Core Docker イメージを構築します。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="f25a4-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="f25a4-161">最初の ASP.NET Core Docker アプリ</span><span class="sxs-lookup"><span data-stu-id="f25a4-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="f25a4-162">このチュートリアルでは、dockerize するアプリの ASP.NET Core Docker サンプル アプリケーションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="f25a4-163">この ASP.NET Core Docker サンプル アプリケーションでは、実稼働環境用のアプリを ASP.NET Core 用 Docker イメージを構築するためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="f25a4-164">このサンプルは、Linux と Windows の両方のコンテナーで動作します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="f25a4-165">Dockerfile の例では、ASP.NET Core ランタイム Docker の基本イメージに基づく ASP.NET Core アプリケーション Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="f25a4-166">使用して、 [Docker 複数段階の機能をビルドする](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)に。</span><span class="sxs-lookup"><span data-stu-id="f25a4-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="f25a4-167">基づくコンテナーでサンプルをビルド、**大きい**ASP.NET Core ビルド Docker 基本イメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="f25a4-168">基づいた Docker イメージに、最後のビルド結果をコピー、**小さい**ASP.NET Core Docker ランタイムの基本イメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="f25a4-169">ビルド イメージには、実行時のイメージではありませんが、アプリケーションの構築に必要なツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f25a4-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f25a4-170">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f25a4-170">Prerequisites</span></span>

<span data-ttu-id="f25a4-171">でビルドして実行するには、次の項目をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="f25a4-172">.NET 2.0 SDK をコアします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="f25a4-173">インストール[.NET Core SDK 2.0](https://www.microsoft.com/net/core)です。</span><span class="sxs-lookup"><span data-stu-id="f25a4-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="f25a4-174">まだ行っていない場合、好きなコード エディターをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="f25a4-175">コード エディターをインストールする必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="f25a4-175">Need to install a code editor?</span></span> <span data-ttu-id="f25a4-176">再試行[Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="f25a4-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="f25a4-177">Docker クライアントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-177">Installing Docker Client</span></span>

<span data-ttu-id="f25a4-178">インストール[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)またはそれ以降の Docker クライアント。</span><span class="sxs-lookup"><span data-stu-id="f25a4-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="f25a4-179">Docker クライアントをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="f25a4-180">Linux ディストリビューション</span><span class="sxs-lookup"><span data-stu-id="f25a4-180">Linux distributions</span></span>

   * [<span data-ttu-id="f25a4-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="f25a4-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="f25a4-182">Debian</span><span class="sxs-lookup"><span data-stu-id="f25a4-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="f25a4-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="f25a4-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="f25a4-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f25a4-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="f25a4-185">macOS</span><span class="sxs-lookup"><span data-stu-id="f25a4-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="f25a4-186">[Windows](https://docs.docker.com/docker-for-windows/)です。</span><span class="sxs-lookup"><span data-stu-id="f25a4-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="f25a4-187">サンプル リポジトリの Git のインストール</span><span class="sxs-lookup"><span data-stu-id="f25a4-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="f25a4-188">インストール[git](https://git-scm.com/download)リポジトリを複製する場合。</span><span class="sxs-lookup"><span data-stu-id="f25a4-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="f25a4-189">サンプル アプリケーションを取得します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-189">Getting the sample application</span></span>

<span data-ttu-id="f25a4-190">サンプルを入手する最も簡単な方法は、複製することによって、[サンプル リポジトリ](https://github.com/dotnet/dotnet-docker-samples)git で、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="f25a4-191">(小さなは) リポジトリは .NET Core Docker サンプル リポジトリから zip としてダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="f25a4-192">ASP.NET アプリケーションをローカルで実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="f25a4-193">参照ポイントとして、アプリケーションをコンテナー化する前に、まず、アプリケーションをローカルで実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="f25a4-194">ビルドおよび (、手順には、リポジトリのルートが想定しています)、次のコマンドを使用して、.NET Core 2.0 SDK と、アプリケーションをローカルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="f25a4-195">アプリケーションが起動したらを参照してください。 **http://localhost:5000** web ブラウザーにします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="f25a4-196">ビルドおよび Docker を使用した Linux コンテナーのサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="f25a4-197">ビルドして、(、手順には、リポジトリのルートが想定しています)、次のコマンドを使用して Linux コンテナーを使用して、Docker でサンプルを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="f25a4-198">`docker run` '-P' 引数のマップ、ローカル コンピューターのポート 80 をコンテナーに 5000 のポート (ポート マッピング形式は`host:container`)。</span><span class="sxs-lookup"><span data-stu-id="f25a4-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="f25a4-199">詳細については、次を参照してください。、[実行 docker](https://docs.docker.com/engine/reference/commandline/exec/)コマンド ライン パラメーターで参照します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="f25a4-200">アプリケーションが起動したらを参照してください。 **http://localhost:5000** web ブラウザーにします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="f25a4-201">ビルドおよび Docker for Windows コンテナーでサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="f25a4-202">ビルドして、(、手順には、リポジトリのルートが想定しています)、次のコマンドを使用して Windows コンテナーを使用して、Docker でサンプルを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="f25a4-203">移動する必要があります、**コンテナーの IP アドレス**(http://localhost) ではなく直接ブラウザーで Windows コンテナーを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="f25a4-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="f25a4-204">次の手順で、コンテナーの IP アドレスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="f25a4-205">別のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-205">Open up another command prompt.</span></span>
* <span data-ttu-id="f25a4-206">実行`docker ps`に、実行中のコンテナーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f25a4-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="f25a4-207">"Aspnetcore_sample"コンテナーが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f25a4-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="f25a4-208">`docker exec aspnetcore_sample ipconfig` を実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="f25a4-209">コンテナーの IP アドレスをコピーし、ブラウザー (たとえば、172.29.245.43) に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="f25a4-210">Docker exec には、名前とハッシュ識別用のコンテナーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f25a4-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="f25a4-211">名前 (aspnetcore_sample) は、この例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="f25a4-212">次の実行中の Windows コンテナーの IP アドレスを取得する方法の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f25a4-212">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> <span data-ttu-id="f25a4-213">Docker exec は、実行中のコンテナーで新しいコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="f25a4-214">詳細については、次を参照してください。、 [docker exec リファレンス](https://docs.docker.com/engine/reference/commandline/exec/)コマンド ライン パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="f25a4-215">使用してローカルで実稼働環境に展開する準備が整っているアプリケーションを作成することができます、 [dotnet 発行](../tools/dotnet-publish.md)コマンド。</span><span class="sxs-lookup"><span data-stu-id="f25a4-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="f25a4-216">-C リリース引数は、リリース モード (既定ではデバッグ モード) でアプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="f25a4-217">詳細については、次を参照してください。、 [dotnet run リファレンス](../tools/dotnet-run.md)コマンド ライン パラメーターにします。</span><span class="sxs-lookup"><span data-stu-id="f25a4-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="f25a4-218">アプリケーションを実行できる**Windows**次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="f25a4-219">アプリケーションを実行できる**Linux**または**macOS**次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="f25a4-220">このサンプルで使用する docker イメージ</span><span class="sxs-lookup"><span data-stu-id="f25a4-220">Docker Images used in this sample</span></span>

<span data-ttu-id="f25a4-221">次の Docker イメージは、このサンプルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="f25a4-222">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="f25a4-222">Congratulations!</span></span> <span data-ttu-id="f25a4-223">だけがある場合。</span><span class="sxs-lookup"><span data-stu-id="f25a4-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f25a4-224">Microsoft .NET Core Docker images 学習</span><span class="sxs-lookup"><span data-stu-id="f25a4-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="f25a4-225">ASP.NET Core Dockerize するサンプル アプリを取得しました</span><span class="sxs-lookup"><span data-stu-id="f25a4-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="f25a4-226">ASP.NET サンプル アプリをローカルに実行されていました</span><span class="sxs-lookup"><span data-stu-id="f25a4-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="f25a4-227">構築され、Docker を使用した Linux コンテナーのサンプルを実行</span><span class="sxs-lookup"><span data-stu-id="f25a4-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="f25a4-228">構築され、Docker for Windows コンテナーで、サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="f25a4-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="f25a4-229">**次の手順**</span><span class="sxs-lookup"><span data-stu-id="f25a4-229">**Next Steps**</span></span>

<span data-ttu-id="f25a4-230">ここでは、いくつか次の手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f25a4-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="f25a4-231">Visual Studio Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="f25a4-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="f25a4-232">Azure のコンテナー インスタンスを Azure のコンテナー レジストリから Docker イメージを展開します。</span><span class="sxs-lookup"><span data-stu-id="f25a4-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="f25a4-233">Visual Studio のコードでデバッグ</span><span class="sxs-lookup"><span data-stu-id="f25a4-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="f25a4-234">手 Visual Studio での取得 Mac、コンテナー、およびサーバーなしのコード、クラウド内</span><span class="sxs-lookup"><span data-stu-id="f25a4-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="f25a4-235">Mac のラボの Docker と Visual Studio の概要</span><span class="sxs-lookup"><span data-stu-id="f25a4-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="f25a4-236">Azure のサブスクリプションを持っていない場合[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)30 日間の無料のアカウントと Azure サービスの任意の組み合わせを試す Azure クレジットの get $200 です。</span><span class="sxs-lookup"><span data-stu-id="f25a4-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

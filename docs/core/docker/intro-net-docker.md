---
title: .NET および Docker の概要
description: Docker と .NET Core について
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.custom: mvc
ms.openlocfilehash: bc652a375abd03bbc70f055b34d6ecea4d9fc374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="91c13-103">.NET および Docker の概要</span><span class="sxs-lookup"><span data-stu-id="91c13-103">Introduction to .NET and Docker</span></span>

<span data-ttu-id="91c13-104">この記事では、Docker 上での .NET の使用に関する概要と概念的な基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="91c13-104">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="91c13-105">Docker: アプリをパッケージ化して任意の場所で配置および実行する</span><span class="sxs-lookup"><span data-stu-id="91c13-105">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="91c13-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) はオープンなプラットフォームであり、開発者や管理者は[イメージ](https://docs.docker.com/glossary/?term=image)のビルド、配布、および分散アプリケーションの実行を[コンテナー](https://www.docker.com/what-container)という大まかに分けられた環境で行えます。</span><span class="sxs-lookup"><span data-stu-id="91c13-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="91c13-107">この手法を使用すると、開発、QA、運用環境の間でアプリケーションのライフ サイクルを効率的に管理できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-107">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="91c13-108">[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)は [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)を使用し、アプリを [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 形式で記述されているファイルを用いて作成された [Docker イメージ](https://docs.docker.com/glossary/?term=image)として速やかにビルドしパッケージ化したうえで、[階層型コンテナー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)に配置して実行します。</span><span class="sxs-lookup"><span data-stu-id="91c13-108">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="91c13-109">独自の[階層型イメージ](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)を Dockerfile として作成することも、または[レジストリ](https://docs.docker.com/glossary/?term=registry)から [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub) などの既存のものを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="91c13-109">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="91c13-110">[Docker コンテナー、イメージ、およびレジストリの相互の関係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)は、[コンテナー化されたアプリケーションやマイクロサービスの設計および構築](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)を行う際に重要となる概念です。</span><span class="sxs-lookup"><span data-stu-id="91c13-110">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="91c13-111">この手法を用いると開発および配置にかかる時間を大幅に短縮できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-111">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="91c13-112">さらに詳しく読む (視聴する)</span><span class="sxs-lookup"><span data-stu-id="91c13-112">Further reading (and watching)</span></span>

* [<span data-ttu-id="91c13-113">Windows ベースのコンテナー: エンタープライズ レベルの制御が可能な最新のアプリ開発。</span><span class="sxs-lookup"><span data-stu-id="91c13-113">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="91c13-114">Docker の概要</span><span class="sxs-lookup"><span data-stu-id="91c13-114">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="91c13-115">Windows コンテナー上の Dockerfile</span><span class="sxs-lookup"><span data-stu-id="91c13-115">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="91c13-116">Dockerfile を記述するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="91c13-116">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="91c13-117">.NET Core アプリケーション用の Docker イメージのビルド</span><span class="sxs-lookup"><span data-stu-id="91c13-117">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="91c13-118">.NET Docker イメージを入手する</span><span class="sxs-lookup"><span data-stu-id="91c13-118">Getting .NET Docker images</span></span>

<span data-ttu-id="91c13-119">公式の .NET Docker イメージは Microsoft により作成および最適化されており、</span><span class="sxs-lookup"><span data-stu-id="91c13-119">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="91c13-120">Docker Hub の Microsoft リポジトリで一般公開されています。</span><span class="sxs-lookup"><span data-stu-id="91c13-120">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="91c13-121">各リポジトリには .NET のバージョンや OS のバージョンによって複数のイメージがあります。</span><span class="sxs-lookup"><span data-stu-id="91c13-121">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="91c13-122">イメージ リポジトリの多くではさまざまなタグを利用できるため、フレームワークのバージョンと OS (Linux ディストリビューションや Windows のバージョン) 両方を指定して選択できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-122">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="91c13-123">シナリオ ベースのガイダンス</span><span class="sxs-lookup"><span data-stu-id="91c13-123">Scenario based guidance</span></span>

<span data-ttu-id="91c13-124">Microsoft は .NET リポジトリをきめ細かく焦点を合わせたものにしたいと考えています。これは特定のシナリオやワークロードのことを示しています。</span><span class="sxs-lookup"><span data-stu-id="91c13-124">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="91c13-125">`microsoft/aspnetcore` イメージは Docker 上の ASP.NET Core アプリに最適化されているため、コンテナーを迅速に起動できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-125">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="91c13-126">.NET Core イメージ (`microsoft/dotnet`) は .NET Core をベースとしたコンソール アプリ向けです。</span><span class="sxs-lookup"><span data-stu-id="91c13-126">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="91c13-127">たとえば、バッチ プロセスや Azure WebJobs、その他のコンソールのシナリオなどでは最適化された .NET Core イメージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c13-127">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="91c13-128">Docker と .NET アプリケーションを使用する水平方向のシナリオとして最もわかりやすいのは、運用環境のデプロイとホスティングのシナリオです。</span><span class="sxs-lookup"><span data-stu-id="91c13-128">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="91c13-129">運用はシナリオのひとつに過ぎません。それ以外のシナリオも同じように有用です。</span><span class="sxs-lookup"><span data-stu-id="91c13-129">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="91c13-130">これらのシナリオは .NET に固有のものではなく、多くの開発者プラットフォームに当てはまると思われます。</span><span class="sxs-lookup"><span data-stu-id="91c13-130">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="91c13-131">**摩擦の少ないインストール** - .NET をローカルにインストールせずに試せます。</span><span class="sxs-lookup"><span data-stu-id="91c13-131">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="91c13-132">.NET が組み込まれた Docker イメージをダウンロードするだけです。</span><span class="sxs-lookup"><span data-stu-id="91c13-132">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="91c13-133">**コンテナーでの開発** - 一貫性のある環境で開発し、開発環境と運用環境を近づけることができます (開発者マシン上のグローバルな状態などの問題を回避できます)。</span><span class="sxs-lookup"><span data-stu-id="91c13-133">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="91c13-134">Visual Studio Tools for Docker を使用すると、Visual Studio から直接コンテナーを起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="91c13-134">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="91c13-135">**コンテナーでのテスト** - コンテナーでテストを行い、環境の構成が正しくなかったり、前回のテストからの変更が適用されていなかったりすることなどに起因するエラーを減らせます。</span><span class="sxs-lookup"><span data-stu-id="91c13-135">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="91c13-136">**コンテナーでのビルド** - コンテナーでコードをビルドすることで、共有のビルド マシンを複数の環境用に正しく構成する必要がなくなり、その代わりとして "BYOC" (独自のコンテナーを使用) の手法に移行できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-136">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="91c13-137">**あらゆる環境で配置** - お使いのあらゆる環境からイメージを配置できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-137">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="91c13-138">この手法によって、通常は外部の構成 (たとえば、挿入された環境変数など) を利用するイメージの動作が変わり、構成の違いに起因するエラーが減ります。</span><span class="sxs-lookup"><span data-stu-id="91c13-138">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="91c13-139">Docker コンテナー開発に .NET Core と .NET Framework のどちらを使用するかを判断するための一般的なガイダンスは[こちら](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md)です。</span><span class="sxs-lookup"><span data-stu-id="91c13-139">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="91c13-140">Docker 開発の一般的なシナリオ</span><span class="sxs-lookup"><span data-stu-id="91c13-140">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="91c13-141">.NET Core</span><span class="sxs-lookup"><span data-stu-id="91c13-141">.NET Core</span></span>

<span data-ttu-id="91c13-142">**.NET Core リソース**</span><span class="sxs-lookup"><span data-stu-id="91c13-142">**.NET Core resources**</span></span>

 <span data-ttu-id="91c13-143">関心のあるシナリオに合わせて .NET Core のサンプルを選択します。</span><span class="sxs-lookup"><span data-stu-id="91c13-143">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="91c13-144">すべてのサンプルの手順で、Windows、Linux、または macOS のホストから Windows または Linux の Docker イメージをターゲットにする方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="91c13-144">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="91c13-145">サンプルでは .NET Core 2.0 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="91c13-145">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="91c13-146">Docker の[マルチ ステージ ビルド](https://github.com/dotnet/announcements/issues/18)と[マルチ アーキテクチャ タグ](https://github.com/dotnet/announcements/issues/14)が (適切な場合には) 使用されています。</span><span class="sxs-lookup"><span data-stu-id="91c13-146">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="91c13-147">Docker Hub 上の .NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-147">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="91c13-148">.NET Core アプリケーションを Docker で動作させる</span><span class="sxs-lookup"><span data-stu-id="91c13-148">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="91c13-149">この .NET Core の Docker サンプルでは、[.NET Core の開発プロセスにおいて Docker を使用する](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)方法を示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-149">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="91c13-150">このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。</span><span class="sxs-lookup"><span data-stu-id="91c13-150">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="91c13-151">この .NET Core の Docker サンプルでは、[運用環境用の .NET Core アプリの Docker イメージをビルドする](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)方法に関するベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-151">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="91c13-152">このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。</span><span class="sxs-lookup"><span data-stu-id="91c13-152">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="91c13-153">この [.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)では、[自己完結型の .NET Core アプリケーション](../deploying/index.md)用の Docker イメージをビルドするためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-153">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="91c13-154">[コンテナー間で基本イメージを共有する](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)利点を得られないような、運用向けの最小コンテナーで使用します。</span><span class="sxs-lookup"><span data-stu-id="91c13-154">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="91c13-155">ただし Docker の下位レイヤーは共有可能です。</span><span class="sxs-lookup"><span data-stu-id="91c13-155">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="91c13-156">ARM32/Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="91c13-156">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="91c13-157">.NET Core ランタイム ARM32 ビルドに関する告知</span><span class="sxs-lookup"><span data-stu-id="91c13-157">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="91c13-158">Docker Hub の ARM32/Raspberry Pi 用 .NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-158">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="91c13-159">GitHub の ARM32/Raspberry Pi 用 .NET Core Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="91c13-159">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="91c13-160">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="91c13-160">.NET Framework</span></span>

* [<span data-ttu-id="91c13-161">DockerHub の .NET Framework イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-161">.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet-framework/)

<span data-ttu-id="91c13-162">このリポジトリには、.NET Framework のさまざまな Docker 構成を示すサンプルが保存されています。</span><span class="sxs-lookup"><span data-stu-id="91c13-162">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="91c13-163">これらのイメージを独自の Docker イメージのベースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="91c13-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="91c13-164">**.NET Framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="91c13-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="91c13-165">[dotnet-framework: 4.7 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)では、[.NET Framework 4.7](../../framework/whats-new/index.md#v47) の使用方法について基礎的な "hello world" で説明します。</span><span class="sxs-lookup"><span data-stu-id="91c13-165">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="91c13-166">[.NET Framework 4.7 の Docker イメージ](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile)に依存するアプリを構築して配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).</span></span>

<span data-ttu-id="91c13-167">**.NET Framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="91c13-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="91c13-168">[dotnet-framework: 4.6.2 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)では、[.NET Framework 4.6.2](../../framework/whats-new/index.md#v462) の使用方法について基礎的な "hello world" で説明します。</span><span class="sxs-lookup"><span data-stu-id="91c13-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="91c13-169">[.NET Framework 4.6.2 の Docker イメージ](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile)に依存するアプリを構築して配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).</span></span>

<span data-ttu-id="91c13-170">**.NET Framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="91c13-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="91c13-171">[dotnet-framework:3.5 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)では、[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile) の使用方法について基礎的な "hello world" で説明します。</span><span class="sxs-lookup"><span data-stu-id="91c13-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile).</span></span> <span data-ttu-id="91c13-172">Docker で .NET Framework 3.5 に依存するプロジェクトを構築して配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="91c13-173">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="91c13-173">ASP.NET Core</span></span>

* <span data-ttu-id="91c13-174">[この ASP.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)は、運用向けの ASP.NET Core アプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="91c13-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="91c13-175">このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。</span><span class="sxs-lookup"><span data-stu-id="91c13-175">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="91c13-176">DockerHub の ASP.NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-176">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="91c13-177">GitHub の ASP.NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-177">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="91c13-178">ASP.NET フレームワーク</span><span class="sxs-lookup"><span data-stu-id="91c13-178">ASP.NET Framework</span></span>

* [<span data-ttu-id="91c13-179">DockerHub の ASP.NET フレームワーク イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-179">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="91c13-180">.NET Framework 4.6.2 の ASP.NET Web フォーム アプリケーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="91c13-180">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="91c13-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="91c13-181">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="91c13-182">DockerHub の Windows Communication Framework (WCF) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-182">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="91c13-183">GitHub の Windows Communication Framework (WCF) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-183">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

* [<span data-ttu-id="91c13-184">完全な .NET Framework 4.6.2 を使用する Windows Communication Framework (WCF) の Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="91c13-184">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="91c13-185">インターネット インフォメーション サーバー (IIS)</span><span class="sxs-lookup"><span data-stu-id="91c13-185">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="91c13-186">DockerHub のインターネット インフォメーション サーバー (IIS) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-186">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="91c13-187">GitHub のインターネット インフォメーション サーバー (IIS) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-187">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="91c13-188">その他の Microsoft スタック コンテナー イメージを操作する</span><span class="sxs-lookup"><span data-stu-id="91c13-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="91c13-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="91c13-189">Microsoft SQL Server</span></span>

* [<span data-ttu-id="91c13-190">Docker クイック スタートで Linux 2017 用 Microsoft SQL Server コンテナー イメージを実行する</span><span class="sxs-lookup"><span data-stu-id="91c13-190">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="91c13-191">DockerHub の Linux 用 Microsoft SQL Server イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-191">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [<span data-ttu-id="91c13-192">DockerHub のWindows コンテナー用 Microsoft SQL Server Express Edition イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-192">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="91c13-193">DockerHub の Windows コンテナー用 Microsoft SQL Server Developer Edition イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-193">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="91c13-194">Visual Studio Team Services (VSTS) エージェント</span><span class="sxs-lookup"><span data-stu-id="91c13-194">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="91c13-195">DockerHub の Visual Studio Team Services (VSTS) エージェント イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-195">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="91c13-196">GitHub の Visual Studio Team Services (VSTS) エージェント イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-196">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="91c13-197">Operations Management Suite (OMS) Linux エージェント</span><span class="sxs-lookup"><span data-stu-id="91c13-197">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="91c13-198">Operations Management Suite (OMS) Linux エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="91c13-198">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [<span data-ttu-id="91c13-199">DockerHub の Operations Management Suite (OMS) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-199">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/oms/)

* [<span data-ttu-id="91c13-200">GitHub の Operations Management Suite (OMS) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-200">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="91c13-201">Microsoft Azure コマンド ライン インターフェイス (CLI)</span><span class="sxs-lookup"><span data-stu-id="91c13-201">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="91c13-202">DockerHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-202">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cli/) 

* [<span data-ttu-id="91c13-203">GitHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-203">Microsoft Azure Command-Line Interface (CLI) images on GitHub</span></span>](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> <span data-ttu-id="91c13-204">Azure サブスクリプションをお持ちでない場合は、[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)して 30 日間の無料アカウントと 200 ドル分の Azure クレジットを取得し、お好きな Azure サービスの組み合わせを試しましょう。</span><span class="sxs-lookup"><span data-stu-id="91c13-204">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="91c13-205">Microsoft Azure Cosmos DB Emulator (Windows コンテナーのみ)</span><span class="sxs-lookup"><span data-stu-id="91c13-205">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="91c13-206">DockerHub の Microsoft Azure Cosmos DB Emulator イメージ</span><span class="sxs-lookup"><span data-stu-id="91c13-206">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="91c13-207">Microsoft Azure Cosmos DB Emulator をローカルでの開発とテストに使用する</span><span class="sxs-lookup"><span data-stu-id="91c13-207">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="91c13-208">Docker 開発の豊かなエコシステムについて学習する</span><span class="sxs-lookup"><span data-stu-id="91c13-208">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="91c13-209">Docker プラットフォームとさまざまな Docker イメージについて学んだので、次のステップとして Docker の豊かなエコシステムについて学習しましょう。</span><span class="sxs-lookup"><span data-stu-id="91c13-209">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="91c13-210">以下のリンクでは、コンテナー開発を補完する Microsoft のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="91c13-210">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="91c13-211">.NET と Docker を組み合わせて使用する</span><span class="sxs-lookup"><span data-stu-id="91c13-211">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [<span data-ttu-id="91c13-212">複数コンテナーのマイクロサービス ベース .NET アプリケーションの設計と開発</span><span class="sxs-lookup"><span data-stu-id="91c13-212">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [<span data-ttu-id="91c13-213">Visual Studio Code の Docker 拡張</span><span class="sxs-lookup"><span data-stu-id="91c13-213">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile)
* [<span data-ttu-id="91c13-214">Azure Service Fabric の使用方法を学習する</span><span class="sxs-lookup"><span data-stu-id="91c13-214">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index)
* [<span data-ttu-id="91c13-215">Service Fabric の入門サンプル</span><span class="sxs-lookup"><span data-stu-id="91c13-215">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="91c13-216">Windows コンテナーの利点</span><span class="sxs-lookup"><span data-stu-id="91c13-216">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="91c13-217">Visual Studio Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="91c13-217">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [<span data-ttu-id="91c13-218">Azure Container Registry から Azure Container Instances に Docker イメージを配置する</span><span class="sxs-lookup"><span data-stu-id="91c13-218">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="91c13-219">Visual Studio Code でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="91c13-219">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [<span data-ttu-id="91c13-220">クラウドにおける Visual Studio for Mac、コンテナー、サーバーレス コードの入門</span><span class="sxs-lookup"><span data-stu-id="91c13-220">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="91c13-221">Docker と Visual Studio for Mac の入門ラボ</span><span class="sxs-lookup"><span data-stu-id="91c13-221">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="91c13-222">次の手順</span><span class="sxs-lookup"><span data-stu-id="91c13-222">Next steps</span></span>

* [<span data-ttu-id="91c13-223">.NET Core での Docker の基礎の学習</span><span class="sxs-lookup"><span data-stu-id="91c13-223">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="91c13-224">.NET Core の Docker イメージのビルド</span><span class="sxs-lookup"><span data-stu-id="91c13-224">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)

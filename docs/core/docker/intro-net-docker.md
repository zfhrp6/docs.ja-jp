---
title: ".NET および Docker の概要"
description: "Docker と .NET Core について"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload:
- dotnetcore
ms.openlocfilehash: dabc7c0c4a0afab8edf7d2bab410bb9635821936
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2018
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="0b515-104">.NET および Docker の概要</span><span class="sxs-lookup"><span data-stu-id="0b515-104">Introduction to .NET and Docker</span></span>

<span data-ttu-id="0b515-105">この記事では、Docker 上での .NET の使用に関する概要と概念的な基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="0b515-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="0b515-106">Docker: アプリをパッケージ化して任意の場所で配置および実行する</span><span class="sxs-lookup"><span data-stu-id="0b515-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="0b515-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) はオープンなプラットフォームであり、開発者や管理者は[イメージ](https://docs.docker.com/glossary/?term=image)のビルド、配布、および分散アプリケーションの実行を[コンテナー](https://www.docker.com/what-container)という大まかに分けられた環境で行えます。</span><span class="sxs-lookup"><span data-stu-id="0b515-107">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="0b515-108">この手法を使用すると、開発、QA、運用環境の間でアプリケーションのライフ サイクルを効率的に管理できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="0b515-109">[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)は [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)を使用し、アプリを [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) 形式で記述されているファイルを用いて作成された [Docker イメージ](https://docs.docker.com/glossary/?term=image)として速やかにビルドしパッケージ化したうえで、[階層型コンテナー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)に配置して実行します。</span><span class="sxs-lookup"><span data-stu-id="0b515-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="0b515-110">独自の[階層型イメージ](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)を Dockerfile として作成することも、または[レジストリ](https://docs.docker.com/glossary/?term=registry)から [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub) などの既存のものを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0b515-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="0b515-111">[Docker コンテナー、イメージ、およびレジストリの相互の関係](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md)は、[コンテナー化されたアプリケーションやマイクロサービスの設計および構築](../../standard/microservices-architecture/architect-microservice-container-applications/index.md)を行う際に重要となる概念です。</span><span class="sxs-lookup"><span data-stu-id="0b515-111">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="0b515-112">この手法を用いると開発および配置にかかる時間を大幅に短縮できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="0b515-113">さらに詳しく読む (視聴する)</span><span class="sxs-lookup"><span data-stu-id="0b515-113">Further reading (and watching)</span></span>

* [<span data-ttu-id="0b515-114">Windows ベースのコンテナー: エンタープライズ レベルの制御が可能な最新のアプリ開発。</span><span class="sxs-lookup"><span data-stu-id="0b515-114">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="0b515-115">Docker の概要</span><span class="sxs-lookup"><span data-stu-id="0b515-115">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="0b515-116">Windows コンテナー上の Dockerfile</span><span class="sxs-lookup"><span data-stu-id="0b515-116">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="0b515-117">Dockerfile を記述するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="0b515-117">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="0b515-118">.NET Core アプリケーション用の Docker イメージのビルド</span><span class="sxs-lookup"><span data-stu-id="0b515-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="0b515-119">.NET Docker イメージを入手する</span><span class="sxs-lookup"><span data-stu-id="0b515-119">Getting .NET Docker images</span></span>

<span data-ttu-id="0b515-120">公式の .NET Docker イメージは Microsoft により作成および最適化されており、</span><span class="sxs-lookup"><span data-stu-id="0b515-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="0b515-121">Docker Hub の Microsoft リポジトリで一般公開されています。</span><span class="sxs-lookup"><span data-stu-id="0b515-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="0b515-122">各リポジトリには .NET のバージョンや OS のバージョンによって複数のイメージがあります。</span><span class="sxs-lookup"><span data-stu-id="0b515-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="0b515-123">イメージ リポジトリの多くではさまざまなタグを利用できるため、フレームワークのバージョンと OS (Linux ディストリビューションや Windows のバージョン) 両方を指定して選択できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="0b515-124">シナリオ ベースのガイダンス</span><span class="sxs-lookup"><span data-stu-id="0b515-124">Scenario based guidance</span></span>

<span data-ttu-id="0b515-125">Microsoft は .NET リポジトリをきめ細かく焦点を合わせたものにしたいと考えています。これは特定のシナリオやワークロードのことを示しています。</span><span class="sxs-lookup"><span data-stu-id="0b515-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="0b515-126">`microsoft/aspnetcore` イメージは Docker 上の ASP.NET Core アプリに最適化されているため、コンテナーを迅速に起動できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="0b515-127">.NET Core イメージ (`microsoft/dotnet`) は .NET Core をベースとしたコンソール アプリ向けです。</span><span class="sxs-lookup"><span data-stu-id="0b515-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="0b515-128">たとえば、バッチ プロセスや Azure WebJobs、その他のコンソールのシナリオなどでは最適化された .NET Core イメージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0b515-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="0b515-129">Docker と .NET アプリケーションを使用する水平方向のシナリオとして最もわかりやすいのは、運用環境のデプロイとホスティングのシナリオです。</span><span class="sxs-lookup"><span data-stu-id="0b515-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="0b515-130">運用はシナリオのひとつに過ぎません。それ以外のシナリオも同じように有用です。</span><span class="sxs-lookup"><span data-stu-id="0b515-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="0b515-131">これらのシナリオは .NET に固有のものではなく、多くの開発者プラットフォームに当てはまると思われます。</span><span class="sxs-lookup"><span data-stu-id="0b515-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="0b515-132">**摩擦の少ないインストール** - .NET をローカルにインストールせずに試せます。</span><span class="sxs-lookup"><span data-stu-id="0b515-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="0b515-133">.NET が組み込まれた Docker イメージをダウンロードするだけです。</span><span class="sxs-lookup"><span data-stu-id="0b515-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="0b515-134">**コンテナーでの開発** - 一貫性のある環境で開発し、開発環境と運用環境を近づけることができます (開発者マシン上のグローバルな状態などの問題を回避できます)。</span><span class="sxs-lookup"><span data-stu-id="0b515-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="0b515-135">Visual Studio Tools for Docker を使用すると、Visual Studio から直接コンテナーを起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="0b515-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="0b515-136">**コンテナーでのテスト** - コンテナーでテストを行い、環境の構成が正しくなかったり、前回のテストからの変更が適用されていなかったりすることなどに起因するエラーを減らせます。</span><span class="sxs-lookup"><span data-stu-id="0b515-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="0b515-137">**コンテナーでのビルド** - コンテナーでコードをビルドすることで、共有のビルド マシンを複数の環境用に正しく構成する必要がなくなり、その代わりとして "BYOC" (独自のコンテナーを使用) の手法に移行できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="0b515-138">**あらゆる環境で配置** - お使いのあらゆる環境からイメージを配置できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="0b515-139">この手法によって、通常は外部の構成 (たとえば、挿入された環境変数など) を利用するイメージの動作が変わり、構成の違いに起因するエラーが減ります。</span><span class="sxs-lookup"><span data-stu-id="0b515-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="0b515-140">Docker コンテナー開発に .NET Core と .NET Framework のどちらを使用するかを判断するための一般的なガイダンスは[こちら](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b515-140">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="0b515-141">Docker 開発の一般的なシナリオ</span><span class="sxs-lookup"><span data-stu-id="0b515-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="0b515-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b515-142">.NET Core</span></span>

<span data-ttu-id="0b515-143">**.NET Core リソース**</span><span class="sxs-lookup"><span data-stu-id="0b515-143">**.NET Core resources**</span></span>

 <span data-ttu-id="0b515-144">関心のあるシナリオに合わせて .NET Core のサンプルを選択します。</span><span class="sxs-lookup"><span data-stu-id="0b515-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="0b515-145">すべてのサンプルの手順で、Windows、Linux、または macOS のホストから Windows または Linux の Docker イメージをターゲットにする方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="0b515-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="0b515-146">サンプルでは .NET Core 2.0 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0b515-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="0b515-147">Docker の[マルチ ステージ ビルド](https://github.com/dotnet/announcements/issues/18)と[マルチ アーキテクチャ タグ](https://github.com/dotnet/announcements/issues/14)が (適切な場合には) 使用されています。</span><span class="sxs-lookup"><span data-stu-id="0b515-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="0b515-148">Docker Hub 上の .NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-148">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="0b515-149">.NET Core アプリケーションを Docker で動作させる</span><span class="sxs-lookup"><span data-stu-id="0b515-149">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="0b515-150">この .NET Core の Docker サンプルでは、[.NET Core の開発プロセスにおいて Docker を使用する](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="0b515-151">このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。</span><span class="sxs-lookup"><span data-stu-id="0b515-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="0b515-152">この .NET Core の Docker サンプルでは、[運用環境用の .NET Core アプリの Docker イメージをビルドする](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)方法に関するベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="0b515-153">このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。</span><span class="sxs-lookup"><span data-stu-id="0b515-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="0b515-154">この [.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)では、[自己完結型の .NET Core アプリケーション](../deploying/index.md)用の Docker イメージをビルドするためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="0b515-155">[コンテナー間で基本イメージを共有する](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)利点を得られないような、運用向けの最小コンテナーで使用します。</span><span class="sxs-lookup"><span data-stu-id="0b515-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="0b515-156">ただし Docker の下位レイヤーは共有可能です。</span><span class="sxs-lookup"><span data-stu-id="0b515-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="0b515-157">ARM32/Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="0b515-157">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="0b515-158">.NET Core ランタイム ARM32 ビルドに関する告知</span><span class="sxs-lookup"><span data-stu-id="0b515-158">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="0b515-159">Docker Hub の ARM32/Raspberry Pi 用 .NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-159">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="0b515-160">GitHub の ARM32/Raspberry Pi 用 .NET Core Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="0b515-160">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="0b515-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0b515-161">.NET Framework</span></span>

* [<span data-ttu-id="0b515-162">DockerHub の .NET Framework イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-162">.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet-framework/)

<span data-ttu-id="0b515-163">このリポジトリには、.NET Framework のさまざまな Docker 構成を示すサンプルが保存されています。</span><span class="sxs-lookup"><span data-stu-id="0b515-163">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="0b515-164">これらのイメージを独自の Docker イメージのベースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b515-164">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="0b515-165">**.NET Framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="0b515-165">**.NET Framework 4.7**</span></span>

<span data-ttu-id="0b515-166">[dotnet-framework: 4.7 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)では、[.NET Framework 4.7](../../framework/whats-new/index.md#v47) の使用方法について基礎的な "hello world" で説明します。</span><span class="sxs-lookup"><span data-stu-id="0b515-166">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="0b515-167">[.NET Framework 4.7 の Docker イメージ](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile)に依存するアプリを構築して配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-167">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="0b515-168">**.NET Framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="0b515-168">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="0b515-169">[dotnet-framework: 4.6.2 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)では、[.NET Framework 4.6.2](../../framework/whats-new/index.md#v462) の使用方法について基礎的な "hello world" で説明します。</span><span class="sxs-lookup"><span data-stu-id="0b515-169">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="0b515-170">[.NET Framework 4.6.2 の Docker イメージ](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2)に依存するアプリを構築して配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-170">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="0b515-171">**.NET Framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="0b515-171">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="0b515-172">[dotnet-framework:3.5 のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)では、[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5) の使用方法について基礎的な "hello world" で説明します。</span><span class="sxs-lookup"><span data-stu-id="0b515-172">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="0b515-173">Docker で .NET Framework 3.5 に依存するプロジェクトを構築して配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-173">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="0b515-174">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b515-174">ASP.NET Core</span></span>

* <span data-ttu-id="0b515-175">[この ASP.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)は、運用向けの ASP.NET Core アプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="0b515-175">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="0b515-176">このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。</span><span class="sxs-lookup"><span data-stu-id="0b515-176">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="0b515-177">DockerHub の ASP.NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-177">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="0b515-178">GitHub の ASP.NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-178">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="0b515-179">ASP.NET フレームワーク</span><span class="sxs-lookup"><span data-stu-id="0b515-179">ASP.NET Framework</span></span>

* [<span data-ttu-id="0b515-180">DockerHub の ASP.NET フレームワーク イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-180">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="0b515-181">.NET Framework 4.6.2 の ASP.NET Web フォーム アプリケーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="0b515-181">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="0b515-182">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="0b515-182">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="0b515-183">DockerHub の Windows Communication Framework (WCF) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-183">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="0b515-184">GitHub の Windows Communication Framework (WCF) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-184">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

* [<span data-ttu-id="0b515-185">完全な .NET Framework 4.6.2 を使用する Windows Communication Framework (WCF) の Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="0b515-185">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="0b515-186">インターネット インフォメーション サーバー (IIS)</span><span class="sxs-lookup"><span data-stu-id="0b515-186">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="0b515-187">DockerHub のインターネット インフォメーション サーバー (IIS) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-187">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="0b515-188">GitHub のインターネット インフォメーション サーバー (IIS) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-188">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="0b515-189">その他の Microsoft スタック コンテナー イメージを操作する</span><span class="sxs-lookup"><span data-stu-id="0b515-189">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="0b515-190">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="0b515-190">Microsoft SQL Server</span></span>

* [<span data-ttu-id="0b515-191">Docker クイック スタートで Linux 2017 用 Microsoft SQL Server コンテナー イメージを実行する</span><span class="sxs-lookup"><span data-stu-id="0b515-191">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="0b515-192">DockerHub の Linux 用 Microsoft SQL Server イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-192">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="0b515-193">DockerHub の Windows コンテナー用 Microsoft SQL Server イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-193">Microsoft SQL Server for Windows Containers images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="0b515-194">DockerHub のWindows コンテナー用 Microsoft SQL Server Express Edition イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-194">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="0b515-195">DockerHub の Windows コンテナー用 Microsoft SQL Server Developer Edition イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-195">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="0b515-196">Visual Studio Team Services (VSTS) エージェント</span><span class="sxs-lookup"><span data-stu-id="0b515-196">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="0b515-197">DockerHub の Visual Studio Team Services (VSTS) エージェント イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-197">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="0b515-198">GitHub の Visual Studio Team Services (VSTS) エージェント イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-198">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="0b515-199">Operations Management Suite (OMS) Linux エージェント</span><span class="sxs-lookup"><span data-stu-id="0b515-199">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="0b515-200">Operations Management Suite (OMS) Linux エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="0b515-200">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [<span data-ttu-id="0b515-201">DockerHub の Operations Management Suite (OMS) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-201">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="0b515-202">GitHub の Operations Management Suite (OMS) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-202">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="0b515-203">Microsoft Azure コマンド ライン インターフェイス (CLI)</span><span class="sxs-lookup"><span data-stu-id="0b515-203">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="0b515-204">DockerHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-204">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cli/) 

* [<span data-ttu-id="0b515-205">GitHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-205">Microsoft Azure Command-Line Interface (CLI) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> <span data-ttu-id="0b515-206">Azure サブスクリプションをお持ちでない場合は、[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)して 30 日間の無料アカウントと 200 ドル分の Azure クレジットを取得し、お好きな Azure サービスの組み合わせを試しましょう。</span><span class="sxs-lookup"><span data-stu-id="0b515-206">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="0b515-207">Microsoft Azure Cosmos DB Emulator (Windows コンテナーのみ)</span><span class="sxs-lookup"><span data-stu-id="0b515-207">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="0b515-208">DockerHub の Microsoft Azure Cosmos DB Emulator イメージ</span><span class="sxs-lookup"><span data-stu-id="0b515-208">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="0b515-209">Microsoft Azure Cosmos DB Emulator をローカルでの開発とテストに使用する</span><span class="sxs-lookup"><span data-stu-id="0b515-209">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="0b515-210">Docker 開発の豊かなエコシステムについて学習する</span><span class="sxs-lookup"><span data-stu-id="0b515-210">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="0b515-211">Docker プラットフォームとさまざまな Docker イメージについて学んだので、次のステップとして Docker の豊かなエコシステムについて学習しましょう。</span><span class="sxs-lookup"><span data-stu-id="0b515-211">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="0b515-212">以下のリンクでは、コンテナー開発を補完する Microsoft のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0b515-212">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="0b515-213">.NET と Docker を組み合わせて使用する</span><span class="sxs-lookup"><span data-stu-id="0b515-213">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [<span data-ttu-id="0b515-214">複数コンテナーのマイクロサービス ベース .NET アプリケーションの設計と開発</span><span class="sxs-lookup"><span data-stu-id="0b515-214">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [<span data-ttu-id="0b515-215">Visual Studio Code の Docker 拡張</span><span class="sxs-lookup"><span data-stu-id="0b515-215">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile)
* [<span data-ttu-id="0b515-216">Azure Service Fabric の使用方法を学習する</span><span class="sxs-lookup"><span data-stu-id="0b515-216">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index)
* [<span data-ttu-id="0b515-217">Service Fabric の入門サンプル</span><span class="sxs-lookup"><span data-stu-id="0b515-217">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="0b515-218">Windows コンテナーの利点</span><span class="sxs-lookup"><span data-stu-id="0b515-218">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="0b515-219">Visual Studio Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="0b515-219">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [<span data-ttu-id="0b515-220">Azure Container Registry から Azure Container Instances に Docker イメージを配置する</span><span class="sxs-lookup"><span data-stu-id="0b515-220">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="0b515-221">Visual Studio Code でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="0b515-221">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [<span data-ttu-id="0b515-222">クラウドにおける Visual Studio for Mac、コンテナー、サーバーレス コードの入門</span><span class="sxs-lookup"><span data-stu-id="0b515-222">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="0b515-223">Docker と Visual Studio for Mac の入門ラボ</span><span class="sxs-lookup"><span data-stu-id="0b515-223">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="0b515-224">次の手順</span><span class="sxs-lookup"><span data-stu-id="0b515-224">Next steps</span></span>

* [<span data-ttu-id="0b515-225">.NET Core での Docker の基礎の学習</span><span class="sxs-lookup"><span data-stu-id="0b515-225">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="0b515-226">.NET Core の Docker イメージのビルド</span><span class="sxs-lookup"><span data-stu-id="0b515-226">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)

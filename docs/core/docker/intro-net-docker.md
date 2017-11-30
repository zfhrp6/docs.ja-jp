---
title: ".NET と Docker の概要"
description: "Understanding Docker と .NET Core"
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
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="99a46-104">.NET と Docker の概要</span><span class="sxs-lookup"><span data-stu-id="99a46-104">Introduction to .NET and Docker</span></span>

 <span data-ttu-id="99a46-105">この記事では、概要と Docker の .NET を使用する概念の背景を提供します。</span><span class="sxs-lookup"><span data-stu-id="99a46-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span> 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="99a46-106">Docker: を展開して任意の場所を実行するアプリをパッケージ化</span><span class="sxs-lookup"><span data-stu-id="99a46-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="99a46-107">[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined)をビルドするには、開発者および管理者を有効にするオープン プラットフォームは、[イメージ](https://docs.docker.com/glossary/?term=image)、出荷、およびと呼ばれる疎に分離された環境で分散アプリケーションを実行、[コンテナー](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="99a46-107">[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="99a46-108">この方法には、開発、品質保証、および運用環境間で効率的なアプリケーション ライフ サイクル管理ができます。</span><span class="sxs-lookup"><span data-stu-id="99a46-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="99a46-109">[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)を使用して、 [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)速やかに構築してとしてアプリをパッケージ化[Docker images](https://docs.docker.com/glossary/?term=image)で記述されたファイルを使用して作成された、 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)が展開されているし、で実行する形式、[コンテナー階層化](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="99a46-110">作成することも、独自[画像上層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)dockerfile または既存のものから使用すると、[レジストリ](https://docs.docker.com/glossary/?term=registry)と同様、 [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="99a46-111">[Docker コンテナー、画像、およびレジストリの関係](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries)重要な概念と[を設計および構築コンテナー詰めアプリケーションまたは microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-111">The [relationship between Docker containers, images, and registries](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) is an important concept when [architecting and building containerized applications or microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/).</span></span> <span data-ttu-id="99a46-112">この方法では、開発と配置までの時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="99a46-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="99a46-113">関連項目 (および監視)</span><span class="sxs-lookup"><span data-stu-id="99a46-113">Further reading (and watching)</span></span>

* [<span data-ttu-id="99a46-114">Windows ベースのコンテナー: エンタープライズ レベルの制御を使用した最新のアプリの開発。</span><span class="sxs-lookup"><span data-stu-id="99a46-114">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="99a46-115">Docker の概要</span><span class="sxs-lookup"><span data-stu-id="99a46-115">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="99a46-116">Windows コンテナー上の Dockerfile</span><span class="sxs-lookup"><span data-stu-id="99a46-116">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="99a46-117">Dockerfile を記述するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="99a46-117">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="99a46-118">.NET Core アプリケーションの Docker イメージの構築</span><span class="sxs-lookup"><span data-stu-id="99a46-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="99a46-119">.NET Docker イメージを取得します。</span><span class="sxs-lookup"><span data-stu-id="99a46-119">Getting .NET Docker Images</span></span>

<span data-ttu-id="99a46-120">公式の .NET Docker イメージが作成され、Microsoft によって最適化します。</span><span class="sxs-lookup"><span data-stu-id="99a46-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="99a46-121">Docker Hub に Microsoft リポジトリにはパブリックに使用です。</span><span class="sxs-lookup"><span data-stu-id="99a46-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="99a46-122">各リポジトリには、.NET のバージョンや OS のバージョンに基づいて、複数のイメージを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="99a46-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="99a46-123">ほとんどのイメージ リポジトリは、特定のフレームワークのバージョンと OS (Linux ディストリビューションまたは Windows のバージョン) の両方を選択するための広範なタグ付けを提供します。</span><span class="sxs-lookup"><span data-stu-id="99a46-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="99a46-124">シナリオ ベースのガイダンス</span><span class="sxs-lookup"><span data-stu-id="99a46-124">Scenario Based Guidance</span></span>

<span data-ttu-id="99a46-125">.NET リポジトリ用の Microsoft の目的は、特定のシナリオやワークロードを表す焦点を当てており、詳細なリポジトリにはします。</span><span class="sxs-lookup"><span data-stu-id="99a46-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="99a46-126">`microsoft/aspnetcore`イメージが最適化されているため、Docker に ASP.NET Core アプリケーション コンテナー開始時間を短縮します。</span><span class="sxs-lookup"><span data-stu-id="99a46-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="99a46-127">.NET Core イメージ (`microsoft/dotnet`) ベースの .NET Core コンソール アプリを意図しています。</span><span class="sxs-lookup"><span data-stu-id="99a46-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="99a46-128">たとえば、バッチ処理、Azure web ジョブ、およびその他のコンソール シナリオは、最適化の .NET Core イメージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99a46-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="99a46-129">Docker と .NET アプリケーションを使用して最もわかりやすいの水平方向のシナリオは運用環境のデプロイとホストです。</span><span class="sxs-lookup"><span data-stu-id="99a46-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="99a46-130">結局、運用環境は 1 つのシナリオとその他のものがある均等に便利です。</span><span class="sxs-lookup"><span data-stu-id="99a46-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="99a46-131">これらのシナリオでは、.NET に固有ではありませんが、ほとんどの開発者向けプラットフォームに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99a46-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="99a46-132">**低摩擦インストール**— .NET をローカルにインストールせずに試みることができます。</span><span class="sxs-lookup"><span data-stu-id="99a46-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="99a46-133">だけで、.NET を使用して Docker イメージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="99a46-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="99a46-134">**コンテナーで開発**— (開発者のマシン上のグローバル状態などの問題を回避できます) のような開発および運用環境を作成、一貫性のある環境で開発できます。</span><span class="sxs-lookup"><span data-stu-id="99a46-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="99a46-135">Docker 用の visual Studio Tools を Visual Studio から直接、コンテナーを起動することもできます。</span><span class="sxs-lookup"><span data-stu-id="99a46-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="99a46-136">**コンテナーでテスト**: 正しく構成されていない環境による障害を減らすことをコンテナーでテストできますまたはその他の変更が最後のテストから残されました。</span><span class="sxs-lookup"><span data-stu-id="99a46-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="99a46-137">**コンテナーにビルド**— 複数の環境の共有のビルド コンピューターを正しく構成しますが、"BYOC"に移動する代わりにする必要性を回避する、コンテナー内のコードを構築できます (独自のコンテナーを bring) アプローチです。</span><span class="sxs-lookup"><span data-stu-id="99a46-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="99a46-138">**すべての環境で展開**— すべて自分の環境のイメージを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="99a46-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="99a46-139">この方法は、通常動作を変更する、イメージ外部構成 (たとえば、挿入された環境変数など) を使用して、構成の違いによるエラーを軽減します。</span><span class="sxs-lookup"><span data-stu-id="99a46-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="99a46-140">[一般的なガイダンス](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance)Docker コンテナーの開発の .NET Core と .NET Framework 間を決定するためです。</span><span class="sxs-lookup"><span data-stu-id="99a46-140">[General guidance](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="99a46-141">一般的な Docker 開発シナ リオ</span><span class="sxs-lookup"><span data-stu-id="99a46-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="99a46-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="99a46-142">.NET Core</span></span>

<span data-ttu-id="99a46-143">**.NET core リソース**</span><span class="sxs-lookup"><span data-stu-id="99a46-143">**.NET Core resources**</span></span>

 <span data-ttu-id="99a46-144">関心のある、シナリオに合わせて .NET Core のサンプルを選択します。</span><span class="sxs-lookup"><span data-stu-id="99a46-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="99a46-145">すべての手順の例では、Windows、Linux、または macOS ホストからの Windows または Linux Docker のイメージを対象にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99a46-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="99a46-146">サンプルは、.NET Core 2.0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="99a46-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="99a46-147">Docker を使用している[マルチ ステージのビルド](https://github.com/dotnet/announcements/issues/18)と[マルチ arch タグ](https://github.com/dotnet/announcements/issues/14)適切な場合です。</span><span class="sxs-lookup"><span data-stu-id="99a46-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="99a46-148">Dockerhub を使用して上の .NET core イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-148">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="99a46-149">.NET Core アプリケーションを dockerize します。</span><span class="sxs-lookup"><span data-stu-id="99a46-149">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="99a46-150">この .NET Core Docker がサンプル方法[Docker を使用して、.NET Core 開発工程で](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="99a46-151">このサンプルは、Linux と Windows の両方のコンテナーで動作します。</span><span class="sxs-lookup"><span data-stu-id="99a46-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="99a46-152">この .NET Core Docker サンプルのベスト プラクティス パターン[実稼働用アプリの .NET Core Docker イメージを構築します。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="99a46-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="99a46-153">このサンプルは、Linux と Windows の両方のコンテナーで動作します。</span><span class="sxs-lookup"><span data-stu-id="99a46-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="99a46-154">これは、 [.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)用 Docker イメージを構築するためのベスト プラクティス パターンを示します[自己完結型の .NET Core アプリケーション](https://docs.microsoft.com/dotnet/core/deploying/)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](https://docs.microsoft.com/dotnet/core/deploying/).</span></span> <span data-ttu-id="99a46-155">利点も最小運用コンテナーの使用[コンテナー間での基本イメージを共有](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="99a46-156">ただし、Docker の下位のレイヤーを共有する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99a46-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="99a46-157">ARM32 Raspberry π/</span><span class="sxs-lookup"><span data-stu-id="99a46-157">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="99a46-158">.NET core ランタイム ARM32 ビルド アナウンス</span><span class="sxs-lookup"><span data-stu-id="99a46-158">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="99a46-159">ARM32 Raspberry Pi .NET Core のイメージ DockerHub に/</span><span class="sxs-lookup"><span data-stu-id="99a46-159">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="99a46-160">ARM32 Raspberry Pi .NET Core Docker サンプル GitHub を/</span><span class="sxs-lookup"><span data-stu-id="99a46-160">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="99a46-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="99a46-161">.NET Framework</span></span>

* <span data-ttu-id="99a46-162">[Dockerhub を使用して上の .NET framework イメージ](https://hub.docker.com/r/microsoft/dotnet-framework/)このリポジトリにはさまざまな .NET Framework の Docker 構成を示すサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99a46-162">[.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/) This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="99a46-163">これらのイメージは、独自の Docker イメージのベースとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="99a46-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="99a46-164">**.NET framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="99a46-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="99a46-165">[、 [Dotnet-フレームワーク: 4.7 サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)の基本的な"hello world"の使用を示します、 [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-165">[The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47).</span></span> <span data-ttu-id="99a46-166">作成および証明書利用者アプリケーションを配置する方法を示します、 [.NET Framework 4.7 docker イメージ](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="99a46-167">**.NET framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="99a46-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="99a46-168">[Dotnet-フレームワーク: 4.6.2 サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)の基本的な"hello world"の使用を示します、 [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462).</span></span> <span data-ttu-id="99a46-169">作成および証明書利用者アプリケーションを配置する方法を示します、 [.NET Framework 4.6.2 docker イメージ](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="99a46-170">**.NET framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="99a46-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="99a46-171">[Dotnet-framework: 3.5 サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)の基本的な"hello world"の使用を示します[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5)です。</span><span class="sxs-lookup"><span data-stu-id="99a46-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="99a46-172">ビルドし、Docker で .NET Framework 3.5 に依存するプロジェクトを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99a46-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="99a46-173">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="99a46-173">ASP.NET Core</span></span>

* <span data-ttu-id="99a46-174">[この ASP.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)ASP.NET Core 実稼働環境用のアプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="99a46-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="99a46-175">このサンプルは、Linux と Windows の両方のコンテナーで動作します。</span><span class="sxs-lookup"><span data-stu-id="99a46-175">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="99a46-176">Dockerhub を使用して上の ASP.NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-176">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="99a46-177">GitHub 上の ASP.NET Core イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-177">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="99a46-178">ASP.NET フレームワーク</span><span class="sxs-lookup"><span data-stu-id="99a46-178">ASP.NET Framework</span></span> 

* [<span data-ttu-id="99a46-179">Dockerhub を使用して上の ASP.NET フレームワークの画像</span><span class="sxs-lookup"><span data-stu-id="99a46-179">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="99a46-180">.NET Framework 4.6.2 サンプルの ASP.NET Web フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="99a46-180">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="99a46-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="99a46-181">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="99a46-182">Dockerhub を使用して上の Windows Communication Framework (WCF) イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-182">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="99a46-183">GitHub の Windows Communication Framework (WCF) イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-183">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

* [<span data-ttu-id="99a46-184">.NET Framework 4.6.2 完全を使用する Windows Communication Framework (WCF) Docker サンプル</span><span class="sxs-lookup"><span data-stu-id="99a46-184">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="99a46-185">インターネット インフォメーション サービス (IIS)</span><span class="sxs-lookup"><span data-stu-id="99a46-185">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="99a46-186">DockerHub にインターネット インフォメーション サーバー (IIS) のイメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-186">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="99a46-187">GitHub 上のインターネット インフォメーション サーバー (IIS) の画像</span><span class="sxs-lookup"><span data-stu-id="99a46-187">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="99a46-188">その他の Microsoft スタック コンテナー イメージとの対話します。</span><span class="sxs-lookup"><span data-stu-id="99a46-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="99a46-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="99a46-189">Microsoft SQL Server</span></span>

* [<span data-ttu-id="99a46-190">Docker クイック スタートで Linux 2017 コンテナー イメージが、Microsoft SQL Server を実行します。</span><span class="sxs-lookup"><span data-stu-id="99a46-190">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="99a46-191">Linux イメージ dockerhub を使用して Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="99a46-191">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="99a46-192">Dockerhub を使用して上の Microsoft SQL Server の Windows コンテナー イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-192">Microsoft SQL Server for Windows Containers images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="99a46-193">Dockerhub を使用して上の Windows コンテナー用の Microsoft SQL Server Express Edition イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-193">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="99a46-194">Dockerhub を使用して上の Windows コンテナー用の Microsoft SQL Server Developer Edition イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-194">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="99a46-195">Visual Studio Team Services (VSTS) エージェント</span><span class="sxs-lookup"><span data-stu-id="99a46-195">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="99a46-196">Dockerhub を使用して visual Studio Team Services (VSTS) エージェントをイメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-196">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="99a46-197">GitHub 上の visual Studio Team Services (VSTS) エージェント イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-197">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="99a46-198">Operations Management Suite (OMS) Linux エージェント</span><span class="sxs-lookup"><span data-stu-id="99a46-198">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="99a46-199">Operations Management Suite (OMS) Linux エージェントの概要</span><span class="sxs-lookup"><span data-stu-id="99a46-199">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [<span data-ttu-id="99a46-200">DockerHub に operations Management Suite (OMS) のイメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-200">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [<span data-ttu-id="99a46-201">GitHub で operations Management Suite (OMS) のイメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-201">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="99a46-202">Microsoft Azure コマンド ライン インターフェイス (CLI)</span><span class="sxs-lookup"><span data-stu-id="99a46-202">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="99a46-203">Dockerhub を使用して上の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-203">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](Docker image for Microsoft Azure Command Line Interface) 

* [<span data-ttu-id="99a46-204">GitHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-204">Microsoft Azure Command Line Interface (CLI) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

> [!Note]
> <span data-ttu-id="99a46-205">Azure のサブスクリプションを持っていない場合[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)30 日間の無料のアカウントと Azure サービスの任意の組み合わせを試す Azure クレジットの get $200 です。</span><span class="sxs-lookup"><span data-stu-id="99a46-205">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="99a46-206">Microsoft Azure Cosmos DB エミュレーター (Windows コンテナーのみ)</span><span class="sxs-lookup"><span data-stu-id="99a46-206">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="99a46-207">Dockerhub を使用して上の Microsoft Azure Cosmos DB エミュレーター イメージ</span><span class="sxs-lookup"><span data-stu-id="99a46-207">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="99a46-208">ローカルの開発およびテスト用 Azure Cosmos DB エミュレーターの使用</span><span class="sxs-lookup"><span data-stu-id="99a46-208">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="99a46-209">豊富な Docker 開発エコシステムを調べる</span><span class="sxs-lookup"><span data-stu-id="99a46-209">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="99a46-210">Docker プラットフォームとさまざまな Docker イメージについて説明しましたが、これで、次の手順では、豊富な Docker エコシステムを調査します。</span><span class="sxs-lookup"><span data-stu-id="99a46-210">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="99a46-211">次のリンクは、Microsoft のツールがコンテナーの開発を補完する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99a46-211">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="99a46-212">.NET と Docker の併用</span><span class="sxs-lookup"><span data-stu-id="99a46-212">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [<span data-ttu-id="99a46-213">デザインおよび複数のコンテナーおよびマイクロ サービス ベースの .NET アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="99a46-213">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [<span data-ttu-id="99a46-214">Visual Studio コード Docker 拡張機能</span><span class="sxs-lookup"><span data-stu-id="99a46-214">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile) 
* [<span data-ttu-id="99a46-215">Azure Service Fabric を使用する方法をについてください。</span><span class="sxs-lookup"><span data-stu-id="99a46-215">Learn how to use Azure Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/) 
* [<span data-ttu-id="99a46-216">Service Fabric 作業の開始サンプル</span><span class="sxs-lookup"><span data-stu-id="99a46-216">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="99a46-217">Windows コンテナーの利点</span><span class="sxs-lookup"><span data-stu-id="99a46-217">Benefits of Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="99a46-218">Visual Studio Docker ツールの使用</span><span class="sxs-lookup"><span data-stu-id="99a46-218">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="99a46-219">Azure のコンテナー インスタンスを Azure のコンテナー レジストリから Docker イメージを展開します。</span><span class="sxs-lookup"><span data-stu-id="99a46-219">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="99a46-220">Visual Studio のコードでデバッグ</span><span class="sxs-lookup"><span data-stu-id="99a46-220">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="99a46-221">手 Visual Studio での取得 Mac、コンテナー、およびサーバーなしのコード、クラウド内</span><span class="sxs-lookup"><span data-stu-id="99a46-221">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="99a46-222">Mac のラボの Docker と Visual Studio の概要</span><span class="sxs-lookup"><span data-stu-id="99a46-222">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="99a46-223">次の手順</span><span class="sxs-lookup"><span data-stu-id="99a46-223">Next Steps</span></span>

* [<span data-ttu-id="99a46-224">.NET Core と Docker を基礎します。</span><span class="sxs-lookup"><span data-stu-id="99a46-224">Learn Docker Basics with .NET Core</span></span>](../docker/docker-basics-dotnet-core.md)
* [<span data-ttu-id="99a46-225">.NET Core Docker イメージを構築します。</span><span class="sxs-lookup"><span data-stu-id="99a46-225">Building .NET Core Docker Images</span></span>](../docker/building-net-docker-images)
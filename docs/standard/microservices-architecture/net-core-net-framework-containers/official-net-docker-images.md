---
title: 公式の .NET Docker イメージ
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 公式の .NET Docker イメージ
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 8664493f3d5d5e03cccbe1c33f2c2abe048e3f57
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105577"
---
# <a name="official-net-docker-images"></a><span data-ttu-id="e306a-103">公式の .NET Docker イメージ</span><span class="sxs-lookup"><span data-stu-id="e306a-103">Official .NET Docker images</span></span>

<span data-ttu-id="e306a-104">公式の .NET Docker イメージは Microsoft により作成および最適化された Docker イメージです。</span><span class="sxs-lookup"><span data-stu-id="e306a-104">The Official .NET Docker images are Docker images created and optimized by Microsoft.</span></span> <span data-ttu-id="e306a-105">[Docker Hub](https://hub.docker.com/u/microsoft/) の Microsoft リポジトリで一般公開されています。</span><span class="sxs-lookup"><span data-stu-id="e306a-105">They are publicly available in the Microsoft repositories on [Docker Hub](https://hub.docker.com/u/microsoft/).</span></span> <span data-ttu-id="e306a-106">各リポジトリには、.NET のバージョンに応じて、また OS (Linux Debian、Alpine Linux、Windows Nano Server、Windows Server Core など) とそのバージョンに応じて、複数のイメージを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e306a-106">Each repository can contain multiple images, depending on .NET versions, and depending on the OS and versions (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).</span></span>

<span data-ttu-id="e306a-107">.NET Core 2.1 以降は、ASP.NET Core 用を含むすべての .NET Core イメージが Docker Hub の [.NET Core イメージ リポジトリ](https://hub.docker.com/r/microsoft/dotnet/)で提供されています。</span><span class="sxs-lookup"><span data-stu-id="e306a-107">Since .NET Core 2.1, all the .NET Core images, including for ASP.NET Core are available at Docker Hub at the [.NET Core image repo](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="e306a-108">イメージ リポジトリの多くではさまざまなタグを利用できるため、特定のフレームワーク バージョンだけでなく、OS (Linux ディストリビューションまたは Windows のバージョン) も選択できます。</span><span class="sxs-lookup"><span data-stu-id="e306a-108">Most image repos provide extensive tagging to help you select not just a specific framework version, but also to choose an OS (Linux distro or Windows version).</span></span>


## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a><span data-ttu-id="e306a-109">開発と運用における .NET Core および Docker イメージの最適化</span><span class="sxs-lookup"><span data-stu-id="e306a-109">.NET Core and Docker image optimizations for development versus production</span></span>

<span data-ttu-id="e306a-110">Microsoft では開発者向けの Docker イメージをビルドするにあたり、次の主な 2 つのシナリオに重点を置きました。</span><span class="sxs-lookup"><span data-stu-id="e306a-110">When building Docker images for developers, Microsoft focused on the following main scenarios:</span></span>

-   <span data-ttu-id="e306a-111">.NET Core アプリの*開発*およびビルドに使用されるイメージ。</span><span class="sxs-lookup"><span data-stu-id="e306a-111">Images used to *develop* and build .NET Core apps.</span></span>

-   <span data-ttu-id="e306a-112">.NET Core アプリの実行に "*使用*" されるイメージ。</span><span class="sxs-lookup"><span data-stu-id="e306a-112">Images used to *run* .NET Core apps.</span></span>

<span data-ttu-id="e306a-113">なぜ複数のイメージですか。</span><span class="sxs-lookup"><span data-stu-id="e306a-113">Why multiple images?</span></span> <span data-ttu-id="e306a-114">コンテナー化されたアプリケーションを開発、ビルド、実行する場合、通常は優先順位がそれぞれ異なります。</span><span class="sxs-lookup"><span data-stu-id="e306a-114">When developing, building, and running containerized applications, you usually have different priorities.</span></span> <span data-ttu-id="e306a-115">このような個々のタスク向けにさまざまなイメージを提供することによって、Microsoft は、アプリを開発、ビルド、および展開する個々のプロセスの最適化を支援しています。</span><span class="sxs-lookup"><span data-stu-id="e306a-115">By providing different images for these separate tasks, Microsoft helps optimize the separate processes of developing, building, and deploying apps.</span></span>

### <a name="during-development-and-build"></a><span data-ttu-id="e306a-116">開発中およびビルド中</span><span class="sxs-lookup"><span data-stu-id="e306a-116">During development and build</span></span>

<span data-ttu-id="e306a-117">開発中に重要な点は、変更を繰り返し処理する速さと、変更をデバッグする機能です。</span><span class="sxs-lookup"><span data-stu-id="e306a-117">During development, what is important is how fast you can iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="e306a-118">コードを変更し、それをすばやく確認する機能に比べて、イメージのサイズはそれほど重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="e306a-118">The size of the image is not as important as the ability to make changes to your code and see the changes quickly.</span></span> <span data-ttu-id="e306a-119">ツールおよび "ビルドエージェント コンテナー" の中には、開発プロセスおよびビルド プロセス時に ASP.NET Core の開発イメージ (**microsoft/dotnet:2.1-sdk**) を使用するものがあります。</span><span class="sxs-lookup"><span data-stu-id="e306a-119">Some tools and "build-agent containers", use the development ASP.NET Core image (**microsoft/dotnet:2.1-sdk**) during development and build process.</span></span> <span data-ttu-id="e306a-120">Docker コンテナー内でビルドを行う場合は、アプリをコンパイルするために必要な要素が重要となります。</span><span class="sxs-lookup"><span data-stu-id="e306a-120">When building inside a Docker container, the important aspects are the elements that are needed in order to compile your app.</span></span> <span data-ttu-id="e306a-121">これには、コンパイラおよびその他の .NET 依存関係に加えて、Web 開発の依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e306a-121">This includes the compiler and any other .NET dependencies, plus web development dependencies.</span></span>

<span data-ttu-id="e306a-122">この種のビルド イメージが重要な理由は何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="e306a-122">Why is this type of build image important?</span></span> <span data-ttu-id="e306a-123">このイメージは、実稼働環境には展開しません。</span><span class="sxs-lookup"><span data-stu-id="e306a-123">You do not deploy this image to production.</span></span> <span data-ttu-id="e306a-124">実稼働イメージに配置するコンテンツをビルドする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e306a-124">Instead, it is an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="e306a-125">このイメージは、継続的インテグレーション (CI) 環境、または Docker マルチステージ ビルド使用時のビルド環境で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e306a-125">This image would be used in your continuous integration (CI) environment or build environment when using Docker Multi-stage builds.</span></span>

### <a name="in-production"></a><span data-ttu-id="e306a-126">実稼働環境</span><span class="sxs-lookup"><span data-stu-id="e306a-126">In production</span></span>

<span data-ttu-id="e306a-127">実稼働環境で重要な点は、実稼働 .NET Core イメージに基づいてコンテナーの展開および運用開始をいかに速く行えるかということです。</span><span class="sxs-lookup"><span data-stu-id="e306a-127">What is important in production is how fast you can deploy and start your containers based on a production .NET Core image.</span></span> <span data-ttu-id="e306a-128">したがって、**microsoft/dotnet:2.1-aspnetcore-runtime** に基づくランタイムのみのイメージは、ネットワーク経由で Docker レジストリから Docker ホストまで迅速に送信できるように小さくなっています。</span><span class="sxs-lookup"><span data-stu-id="e306a-128">Therefore, the runtime-only image based on **microsoft/dotnet:2.1-aspnetcore-runtime** is small so that it can travel quickly across the network from your Docker registry to your Docker hosts.</span></span> <span data-ttu-id="e306a-129">コンテンツは実行できる状態であるため、コンテナーの開始から結果の処理までを最速で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e306a-129">The contents are ready to run, enabling the fastest time from starting the container to processing results.</span></span> <span data-ttu-id="e306a-130">Docker モデルでは、ビルド コンテナーを使用するときに dotnet build または dotnet publish を実行する場合のように C\# コードからコンパイルを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e306a-130">In the Docker model, there is no need for compilation from C\# code, as there is when you run dotnet build or dotnet publish when using the build container.</span></span>

<span data-ttu-id="e306a-131">この最適化されたイメージでは、アプリケーションを実行するために必要なバイナリとその他のコンテンツのみを配置します。</span><span class="sxs-lookup"><span data-stu-id="e306a-131">In this optimized image you put only the binaries and other content needed to run the application.</span></span> <span data-ttu-id="e306a-132">たとえば、dotnet publish で作成されたコンテンツには、コンパイルされた .NET バイナリ、イメージ、.js、および .css ファイルのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e306a-132">For example, the content created by dotnet publish contains only the compiled .NET binaries, images, .js, and .css files.</span></span> <span data-ttu-id="e306a-133">時間の経過と共に、事前に Just-In-Time (JIT) にコンパイルされたパッケージを含むイメージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e306a-133">Over time, you will see images that contain pre-jitted packages.</span></span>

<span data-ttu-id="e306a-134">.NET Core イメージおよび ASP.NET Core イメージには複数のバージョンがありますが、これらはすべて、基本レイヤーなどの 1 つまたは複数のレイヤーを共有します。</span><span class="sxs-lookup"><span data-stu-id="e306a-134">Although there are multiple versions of the .NET Core and ASP.NET Core images, they all share one or more layers, including the base layer.</span></span> <span data-ttu-id="e306a-135">そのため、イメージの格納に必要なディスク領域は小さくて済みます。カスタム イメージとその基本イメージ間のデルタのみで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e306a-135">Therefore, the amount of disk space needed to store an image is small; it consists only of the delta between your custom image and its base image.</span></span> <span data-ttu-id="e306a-136">結果として、レジストリからイメージを迅速にプルすることができます。</span><span class="sxs-lookup"><span data-stu-id="e306a-136">The result is that it is quick to pull the image from your registry.</span></span>

<span data-ttu-id="e306a-137">Docker Hub の .NET イメージ リポジトリを探索すると、タグで分類またはマークされた複数のイメージ バージョンを見つかります。</span><span class="sxs-lookup"><span data-stu-id="e306a-137">When you explore the .NET image repositories at Docker Hub, you will find multiple image versions classified or marked with tags.</span></span> <span data-ttu-id="e306a-138">これらのタグは、次の示すように、必要とするバージョンに応じて使用するものを特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e306a-138">These tags help to decide which one to use, depending on the version you need, like those in the following table:</span></span>

-   <span data-ttu-id="e306a-139">microsoft/dotnet:**2.1-aspnetcore-runtime**</span><span class="sxs-lookup"><span data-stu-id="e306a-139">microsoft/dotnet:**2.1-aspnetcore-runtime**</span></span>

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   <span data-ttu-id="e306a-140">microsoft/**dotnet:2.1-sdk**</span><span class="sxs-lookup"><span data-stu-id="e306a-140">microsoft/**dotnet:2.1-sdk**</span></span>

        .NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
<span data-ttu-id="e306a-141">[前へ](net-container-os-targets.md)
[次へ](../architect-microservice-container-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e306a-141">[Previous](net-container-os-targets.md)
[Next](../architect-microservice-container-applications/index.md)</span></span>

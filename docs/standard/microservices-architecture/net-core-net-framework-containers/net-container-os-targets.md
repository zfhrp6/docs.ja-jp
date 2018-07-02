---
title: .NET コンテナーで対象とする OS
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | .NET コンテナーで対象とする OS'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 53b279a3325ae0fb662cd91a6f7f454b765196ff
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251013"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="d9c5d-103">.NET コンテナーで対象とする OS</span><span class="sxs-lookup"><span data-stu-id="d9c5d-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="d9c5d-104">Docker でサポートされているオペレーティング システムの多様性と、.NET Framework と .NET Core の違いを考慮し、使用しているフレームワークに応じて特定の OS と特定のバージョンを対象にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="d9c5d-105">Windows の場合、Windows Server Core または Windows Nano Server を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="d9c5d-106">これらの Windows バージョンには、.NET Framework または .NET Core で必要になる可能性がある異なる特性 (Windows Server Core の IIS と Nest Server の Kestrel のような自己ホスト型 Web サーバー) があります。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="d9c5d-107">Linux の場合、複数のディストリビューションを利用できます。また、Linux は公式の .NET Docker イメージ (Debian など) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="d9c5d-108">使用している .NET Framework に応じて使用できる OS のバージョンについては、図 3-1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="d9c5d-109">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="d9c5d-109">**Figure 3-1.**</span></span> <span data-ttu-id="d9c5d-110">.NET Framework のバージョンに応じて対象にすることができるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="d9c5d-110">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="d9c5d-111">別の Linux ディストリビューションを使用したい場合や、Microsoft が提供していないバージョンのイメージが必要な場合は、独自の Docker イメージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-111">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="d9c5d-112">たとえば、従来の .NET Framework と Windows Server Core 上で実行されている ASP.NET Core を使用してイメージを作成することができます (ただし、Docker の場合はあまり一般的ではないシナリオです)。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-112">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="d9c5d-113">Dockerfile ファイルにイメージ名を追加すると、次の例のように、使用するタグに応じてオペレーティング システムとバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d9c5d-113">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="d9c5d-114">microsoft/**dotnet:2.1-runtime**</span><span class="sxs-lookup"><span data-stu-id="d9c5d-114">microsoft/**dotnet:2.1-runtime**</span></span>

        .NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.

-   <span data-ttu-id="d9c5d-115">microsoft/**dotnet:2.1-aspnetcore-runtime**</span><span class="sxs-lookup"><span data-stu-id="d9c5d-115">microsoft/**dotnet:2.1-aspnetcore-runtime**</span></span>
    
        ASP.NET Core 2.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 

-   <span data-ttu-id="d9c5d-116">microsoft/**dotnet:2.1-aspnetcore-runtime-alpine**</span><span class="sxs-lookup"><span data-stu-id="d9c5d-116">microsoft/**dotnet:2.1-aspnetcore-runtime-alpine**</span></span> 

        .NET Core 2.1 runtime-only on Linux Alpine distro

-   <span data-ttu-id="d9c5d-117">microsoft/**dotnet:2.1-aspnetcore-runtime-nanoserver-1803**</span><span class="sxs-lookup"><span data-stu-id="d9c5d-117">microsoft/**dotnet:2.1-aspnetcore-runtime-nanoserver-1803**</span></span> 

        .NET Core 2.1 runtime-only on Windows Nano Server (Windows Server version 1803)




>[!div class="step-by-step"]
<span data-ttu-id="d9c5d-118">[前へ] (container-framework-choice-factors.md) [次へ] (official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="d9c5d-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>

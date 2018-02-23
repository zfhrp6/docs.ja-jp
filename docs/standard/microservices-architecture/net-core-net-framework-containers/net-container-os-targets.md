---
title: ".NET コンテナーで対象とする OS"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | .NET コンテナーで対象とする OS"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ef7a21efa23be3a5181f08066a093abbb915c20f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="c0478-104">.NET コンテナーで対象とする OS</span><span class="sxs-lookup"><span data-stu-id="c0478-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="c0478-105">Docker でサポートされているオペレーティング システムの多様性と、.NET Framework と .NET Core の違いを考慮し、使用しているフレームワークに応じて特定の OS と特定のバージョンを対象にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0478-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="c0478-106">Windows の場合、Windows Server Core または Windows Nano Server を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0478-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="c0478-107">これらの Windows バージョンには、.NET Framework または .NET Core で必要になる可能性がある異なる特性 (Windows Server Core の IIS と Nest Server の Kestrel のような自己ホスト型 Web サーバー) があります。</span><span class="sxs-lookup"><span data-stu-id="c0478-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="c0478-108">Linux の場合、複数のディストリビューションを利用できます。また、Linux は公式の .NET Docker イメージ (Debian など) でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c0478-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="c0478-109">使用している .NET Framework に応じて使用できる OS のバージョンについては、図 3-1 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0478-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="c0478-110">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="c0478-110">**Figure 3-1.**</span></span> <span data-ttu-id="c0478-111">.NET Framework のバージョンに応じて対象にすることができるオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="c0478-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="c0478-112">別の Linux ディストリビューションを使用したい場合や、Microsoft が提供していないバージョンのイメージが必要な場合は、独自の Docker イメージを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c0478-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="c0478-113">たとえば、従来の .NET Framework と Windows Server Core 上で実行されている ASP.NET Core を使用してイメージを作成することができます (ただし、Docker の場合はあまり一般的ではないシナリオです)。</span><span class="sxs-lookup"><span data-stu-id="c0478-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="c0478-114">Dockerfile ファイルにイメージ名を追加すると、次の例のように、使用するタグに応じてオペレーティング システムとバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c0478-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="c0478-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span><span class="sxs-lookup"><span data-stu-id="c0478-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="c0478-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span><span class="sxs-lookup"><span data-stu-id="c0478-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="c0478-117">microsoft/**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="c0478-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="c0478-118">[前へ] (container-framework-choice-factors.md) [次へ] (official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="c0478-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>

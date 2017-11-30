---
title: ".NET のコンテナーでのターゲットにどのような OS"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |.NET のコンテナーでのターゲットにどのような OS"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="88ca7-104">.NET のコンテナーでのターゲットにどのような OS</span><span class="sxs-lookup"><span data-stu-id="88ca7-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="88ca7-105">Docker と .NET Framework と .NET Core の違いによってサポートされるオペレーティング システムの多様性を指定するには、特定の OS とを使用するために、フレームワークによって特定のバージョンをターゲットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="88ca7-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="88ca7-106">Windows の場合は、Windows Server Core または Nano Server の Windows を使用できます。</span><span class="sxs-lookup"><span data-stu-id="88ca7-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="88ca7-107">これらのバージョンの Windows では、必要となる .NET Framework または .NET Core でそれぞれ異なる特性 (Windows Server Core と Nano Server で Kestrel のように自己ホスト型の web サーバーで IIS) を提供します。</span><span class="sxs-lookup"><span data-stu-id="88ca7-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="88ca7-108">For Linux ディストリビューションの場合は複数、使用可能な (Debian) などの公式の .NET Docker イメージでサポートされているです。</span><span class="sxs-lookup"><span data-stu-id="88ca7-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="88ca7-109">図 3-1 によっては、.NET framework を使用可能な OS バージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="88ca7-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="88ca7-110">**図 3-1。**</span><span class="sxs-lookup"><span data-stu-id="88ca7-110">**Figure 3-1.**</span></span> <span data-ttu-id="88ca7-111">.NET framework のバージョンによって対象とするオペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="88ca7-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="88ca7-112">さまざまな Linux ディストリビューションを使用するか、Microsoft では提供されないバージョンのイメージが必要な場合は、独自の Docker イメージを作成できます。</span><span class="sxs-lookup"><span data-stu-id="88ca7-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="88ca7-113">たとえば、従来の .NET Framework および Windows Server Core では、Docker のないのため、一般的なシナリオで実行されている ASP.NET Core と、イメージを作成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88ca7-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="88ca7-114">Dockerfile は、ファイルをイメージ名を追加する場合は、オペレーティング システムおよび使用すると、次の例のように、タグによってバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="88ca7-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="88ca7-115">microsoft/**dotnet:2.0.0-ランタイム-jessie**</span><span class="sxs-lookup"><span data-stu-id="88ca7-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="88ca7-116">microsoft/**dotnet:2.0.0-ランタイム-nanoserver-1709**</span><span class="sxs-lookup"><span data-stu-id="88ca7-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="88ca7-117">microsoft/**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="88ca7-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="88ca7-118">[前](コンテナーのフレームワークの選択-factors.md) [次へ] (公式の net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="88ca7-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>

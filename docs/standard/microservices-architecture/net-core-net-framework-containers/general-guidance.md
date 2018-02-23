---
title: "一般的なガイダンス"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 一般的なガイダンス"
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
ms.openlocfilehash: fa58d1d81b2d1523baf123d4963db2ca00fee15d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="general-guidance"></a><span data-ttu-id="df8b8-104">一般的なガイダンス</span><span class="sxs-lookup"><span data-stu-id="df8b8-104">General guidance</span></span>

<span data-ttu-id="df8b8-105">このセクションでは、どのような場合に .NET Core または .NET Framework を選択すべきかの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="df8b8-105">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="df8b8-106">後続のセクションでこれらの選択の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="df8b8-106">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="df8b8-107">次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET Core と Linux または Windows のコンテナーを併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df8b8-107">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="df8b8-108">クロスプラット フォームが必要である。</span><span class="sxs-lookup"><span data-stu-id="df8b8-108">You have cross-platform needs.</span></span> <span data-ttu-id="df8b8-109">たとえば、Linux と Windows のコンテナーの両方を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="df8b8-109">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="df8b8-110">アプリケーション アーキテクチャがマイクロサービスに基づく場合。</span><span class="sxs-lookup"><span data-stu-id="df8b8-110">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="df8b8-111">コンテナーを高速で起動する必要があり、かつコンテナーあたりのフットプリントを小さくして密度を高めたり、ハードウェア ユニットあたりのコンテナーを増やしてコストを削減したりしたい場合。</span><span class="sxs-lookup"><span data-stu-id="df8b8-111">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="df8b8-112">つまり、コンテナー化された .NET アプリケーションを新たに作成する場合には、.NET Core を既定の選択肢として考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df8b8-112">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="df8b8-113">これには多くの利点があり、コンテナーの理念や作業スタイルとぴったりと適合します。</span><span class="sxs-lookup"><span data-stu-id="df8b8-113">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="df8b8-114">.NET Core を使用するその他の利点は、同じマシンで複数の .NET バージョンのアプリケーションを同時に実行できることです。</span><span class="sxs-lookup"><span data-stu-id="df8b8-114">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="df8b8-115">この利点は、コンテナーを使用しないサーバーまたは VM にとってはさらに重要になります。コンテナーは、アプリが必要とする .NET バージョンを特定するためです。</span><span class="sxs-lookup"><span data-stu-id="df8b8-115">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="df8b8-116">(基礎となる OS と互換性がある場合。)</span><span class="sxs-lookup"><span data-stu-id="df8b8-116">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="df8b8-117">次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET Framework と Windows コンテナーを併用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df8b8-117">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="df8b8-118">現在、アプリケーションで .NET Framework を使用し、Windows で強い依存関係がある場合。</span><span class="sxs-lookup"><span data-stu-id="df8b8-118">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="df8b8-119">.NET Core がサポートしていない Windows API を使用する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="df8b8-119">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="df8b8-120">.NET Core で使用できないサードパーティ製の .NET ライブラリまたは NuGet パッケージを使用する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="df8b8-120">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="df8b8-121">Docker で .NET Framework を使用すると、展開に関する問題を最小限に抑えて、展開のエクスペリエンスを改善できます。</span><span class="sxs-lookup"><span data-stu-id="df8b8-121">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="df8b8-122">この[*リストアンドシフトのシナリオ*](https://aka.ms/liftandshiftwithcontainersebook)は、ASP.NET WebForms、MVC Web アプリ、WCF (Windows Communication Foundation) サービスなどの、もともと従来の .NET Framework を使用して開発された旧式のアプリケーションをコンテナー化する場合に重要です。</span><span class="sxs-lookup"><span data-stu-id="df8b8-122">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="df8b8-123">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="df8b8-123">Additional resources</span></span>

-   <span data-ttu-id="df8b8-124">**電子ブック: Azure と Windows コンテナーを使用して既存の .NET Framework アプリケーションを最新化する**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="df8b8-124">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="df8b8-125">**サンプル アプリ: Windows コンテナーを使用した従来の ASP.NET Web アプリの最新化**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="df8b8-125">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="df8b8-126">[前へ] (index.md) [次へ] (net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="df8b8-126">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>

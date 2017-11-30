---
title: "一般的なガイダンス"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |一般的なガイダンス"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a><span data-ttu-id="50b85-104">一般的なガイダンス</span><span class="sxs-lookup"><span data-stu-id="50b85-104">General guidance</span></span>

<span data-ttu-id="50b85-105">このセクションでは、.NET Core または .NET Framework を選択するための概要を示します。</span><span class="sxs-lookup"><span data-stu-id="50b85-105">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="50b85-106">次のセクションでこれらのオプションの詳細についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="50b85-106">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="50b85-107">Linux または Windows のコンテナーでコンテナー Docker サーバー アプリケーションの .NET Core を使用する必要があるとき。</span><span class="sxs-lookup"><span data-stu-id="50b85-107">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="50b85-108">クロスプラット フォームが必要である。</span><span class="sxs-lookup"><span data-stu-id="50b85-108">You have cross-platform needs.</span></span> <span data-ttu-id="50b85-109">たとえば、Linux と Windows コンテナーの両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="50b85-109">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="50b85-110">アプリケーションのアーキテクチャは、microservices に基づいています。</span><span class="sxs-lookup"><span data-stu-id="50b85-110">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="50b85-111">高速コンテナーを起動し、コストを削減するために、高密度を実現するためにコンテナーまたはハードウェア ユニットあたり複数のコンテナーにつき、小さなフット プリントを対象にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="50b85-111">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="50b85-112">つまり、新しいコンテナー化 .NET アプリケーションを作成するときに、既定の選択肢として .NET Core を検討してください。</span><span class="sxs-lookup"><span data-stu-id="50b85-112">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="50b85-113">数多くの利点し、最適なコンテナーの考え方と作業のスタイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="50b85-113">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="50b85-114">.NET Core を使用するその他の利点は、同じコンピューター内のアプリケーションの .NET バージョンをサイド バイ サイドを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="50b85-114">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="50b85-115">この利点は、コンテナー、アプリが必要な .NET のバージョンを特定するためにサーバーまたは Vm をコンテナーを使用しない方が重要です。</span><span class="sxs-lookup"><span data-stu-id="50b85-115">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="50b85-116">ある限りは、基になる OS との互換性。)</span><span class="sxs-lookup"><span data-stu-id="50b85-116">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="50b85-117">Windows コンテナーでコンテナー Docker サーバー アプリケーションの .NET Framework を使用する必要があるとき。</span><span class="sxs-lookup"><span data-stu-id="50b85-117">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="50b85-118">アプリケーションは現在 .NET Framework を使用して、Windows で強力な依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="50b85-118">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="50b85-119">.NET Core でサポートされていない Windows Api を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50b85-119">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="50b85-120">サード パーティ製の .NET ライブラリまたは .NET core はない NuGet パッケージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50b85-120">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="50b85-121">.NET Framework を使用して、Docker での展開に関する問題を最小限に抑えることで、配置操作を向上できます。</span><span class="sxs-lookup"><span data-stu-id="50b85-121">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="50b85-122">これは、 [*リフト アンド シフト"シナリオ*](https://aka.ms/liftandshiftwithcontainersebook)は、最初に開発された従来の .NET Framework と ASP.NET WebForms、MVC web アプリケーションまたは WCF (と同じようにレガシ アプリケーションを containerizing にとって重要Windows Communication Foundation) サービス。</span><span class="sxs-lookup"><span data-stu-id="50b85-122">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="50b85-123">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="50b85-123">Additional resources</span></span>

-   <span data-ttu-id="50b85-124">**電子書籍: Azure と Windows コンテナーの既存の .NET Framework アプリケーションを最新化**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="50b85-124">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="50b85-125">**アプリのサンプル: Windows コンテナーを使用する従来の ASP.NET web アプリの近代化**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="50b85-125">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="50b85-126">[前](index.md) [次へ] (net-コア ・ コンテナー ・ scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="50b85-126">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>

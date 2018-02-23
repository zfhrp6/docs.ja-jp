---
title: "意思決定テーブル。 Docker に使用する .NET Frameworks"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 意思決定テーブル、Docker に使用する .NET Frameworks"
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
ms.openlocfilehash: 40e6a14e7e3515194185e1f4558c91ac29429108
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="15d22-105">意思決定テーブル: Docker に使用する .NET Frameworks</span><span class="sxs-lookup"><span data-stu-id="15d22-105">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="15d22-106">次では、.NET Framework または .NET Core および Windows または Linux コンテナーを使用するかどうかをまとめています。</span><span class="sxs-lookup"><span data-stu-id="15d22-106">The following summarizes whether to use .NET Framework or .NET Core, and Windows or Linux containers.</span></span> <span data-ttu-id="15d22-107">Linux コンテナーには、Linux ベースの Docker ホスト (VM またはサーバー) が必要であり、Windows コンテナーには、Windows Server ベースの Docker ホスト (VM またはサーバー) が必要であることを覚えておいてください。</span><span class="sxs-lookup"><span data-stu-id="15d22-107">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

<span data-ttu-id="15d22-108">決定に影響を与えるアプリケーションの機能がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="15d22-108">There are several features of your application that affect your decision.</span></span> <span data-ttu-id="15d22-109">これらの機能の重要性を考え、決定をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-109">You should weigh the importance of these features when making your decision.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15d22-110">開発用のコンピューターは、Linux または Windows の Docker ホストを 1 つ実行します。</span><span class="sxs-lookup"><span data-stu-id="15d22-110">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="15d22-111">1 つのソリューションで同時に実行してテストしたい関連するマイクロサービスは、同じコンテナー プラットフォームで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-111">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

* <span data-ttu-id="15d22-112">アプリケーション アーキテクチャに、**コンテナー上のマイクロサービス**を選択しました。</span><span class="sxs-lookup"><span data-stu-id="15d22-112">Your application architecture choice is **Microservices on containers**.</span></span>
    - <span data-ttu-id="15d22-113">.NET の実装には、*.NET Core* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-113">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="15d22-114">コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-114">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="15d22-115">アプリケーション アーキテクチャに、**モノリシック アプリケーション**を選択しました。</span><span class="sxs-lookup"><span data-stu-id="15d22-115">Your application architecture choice is a **Monolithic application**.</span></span>
    - <span data-ttu-id="15d22-116">.NET の実装には、*.NET Core* または *.NET Framework* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-116">Your .NET implementation choice can be either *.NET Core* or *.NET Framework*.</span></span>
    - <span data-ttu-id="15d22-117">*.NET Core* を選択した場合、コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-117">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="15d22-118">*.NET Framework* を選択した場合、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-118">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="15d22-119">アプリケーションは、**コンテナー ベースの新しい開発 ("グリーン フィールド")** です。</span><span class="sxs-lookup"><span data-stu-id="15d22-119">Your application is a  **New container-based development ("green-field")**.</span></span>
    - <span data-ttu-id="15d22-120">.NET の実装には、*.NET Core* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-120">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="15d22-121">コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-121">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="15d22-122">アプリケーションは、**コンテナーに移行する Windows Server のレガシー アプリケーション ("ブラウン フィールド")** です。</span><span class="sxs-lookup"><span data-stu-id="15d22-122">Your application is a **Windows Server legacy app ("brown-field") migration to containers**</span></span>
    - <span data-ttu-id="15d22-123">.NET の実装は、フレームワークの依存関係に基づいて *.NET Framework* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-123">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="15d22-124">.NET Framework との依存関係のため、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-124">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="15d22-125">アプリケーションの設計目標は、**クラス最高のパフォーマンスと拡張性**です。</span><span class="sxs-lookup"><span data-stu-id="15d22-125">Your application's design goal is **Best-in-class performance and scalability**.</span></span>
    - <span data-ttu-id="15d22-126">.NET の実装には、*.NET Core* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-126">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="15d22-127">コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-127">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="15d22-128">**ASP.NET Core** を使用して、アプリケーションをビルドしました。</span><span class="sxs-lookup"><span data-stu-id="15d22-128">You built your application using **ASP.NET Core**.</span></span>
    - <span data-ttu-id="15d22-129">.NET の実装には、*.NET Core* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-129">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="15d22-130">他のフレームワークとの依存関係がある場合、*.NET Framework* の実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="15d22-130">You can use the *.NET Framework* implementation, if you have other framework dependencies.</span></span>
    - <span data-ttu-id="15d22-131">*.NET Core* を選択した場合、コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-131">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="15d22-132">*.NET Framework* を選択した場合、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-132">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="15d22-133">**ASP.NET 4 (MVC 5、Web API 2、および Web Forms)** を使用してアプリケーションをビルドしました。</span><span class="sxs-lookup"><span data-stu-id="15d22-133">You built your application using **ASP.NET 4 (MVC 5, Web API 2, and Web Forms)**.</span></span>
    - <span data-ttu-id="15d22-134">.NET の実装は、フレームワークの依存関係に基づいて *.NET Framework* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-134">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="15d22-135">.NET Framework との依存関係のため、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-135">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="15d22-136">アプリケーションで、**SignalR サービス**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="15d22-136">Your application uses **SignalR services**.</span></span>
    - <span data-ttu-id="15d22-137">.NET の実装には、*.NET Framework* または *.NET Core 2.1 (リリースされた場合) 以降*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-137">Your .NET implementation choice can be *.NET Framework*, or *.NET Core 2.1 (when released) or later*.</span></span>
    - <span data-ttu-id="15d22-138">コンテナー プラットフォームには、.NET Framework で SignalR 実装を選択した場合は、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-138">Your container platform choice must be *Windows containers* if you chose the SignalR implementation in .NET Framework.</span></span>
    - <span data-ttu-id="15d22-139">コンテナー プラットフォームには、(リリースされた場合) .NET Core 2.1 以降で SignalR 実装を選択している場合は、Linux コンテナーまたは Windows コンテナーのいずれかを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-139">Your container platform choice can be either Linux containers or Windows containers if you chose the SignalR implementation in .NET Core 2.1 or later (when released).</span></span>  
    - <span data-ttu-id="15d22-140">**SignalR サービス**が *.NET Core* 上で実行されている場合、*Linux コンテナーまたは Windows コンテナー*を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="15d22-140">When **SignalR services** run on *.NET Core*, you can use *Linux containers or Windows Containers*.</span></span>
* <span data-ttu-id="15d22-141">アプリケーションで、**WCF、WF、およびその他の従来のフレームワーク**を使用しています。</span><span class="sxs-lookup"><span data-stu-id="15d22-141">Your application uses **WCF, WF, and other legacy frameworks**.</span></span>
    - <span data-ttu-id="15d22-142">.NET の実装には、*.NET Framework* または *(今後のリリースのロードマップで) .NET Core* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-142">Your .NET implementation choice is *.NET Framework*, or *.NET Core (in the roadmap for a future release)*.</span></span>
    - <span data-ttu-id="15d22-143">.NET Framework との依存関係のため、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-143">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="15d22-144">アプリケーションで、**Azure サービスを消費**します。</span><span class="sxs-lookup"><span data-stu-id="15d22-144">Your application involves **Consumption of Azure services**.</span></span>
    - <span data-ttu-id="15d22-145">.NET の実装には、*.NET Framework* または *.NET Core (最終的にはすべての Azure サービスで .NET Core 用のクライアント SDK が提供されます)* を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-145">Your .NET implementation choice is *.NET Framework*, or *.NET Core (eventually all Azure services will provide client SDKs for .NET Core)*.</span></span>
    - <span data-ttu-id="15d22-146">.NET Framework のクライアント API を使用している場合、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d22-146">Your container platform choice must be *Windows containers* if you use .NET Framework client APIs.</span></span>
    - <span data-ttu-id="15d22-147">*.NET Core* 用のクライアント API を使用している場合、*Linux コンテナーと Windows コンテナー*のいずれかを選択することも可能です。</span><span class="sxs-lookup"><span data-stu-id="15d22-147">If you use client APIs available for *.NET Core*, you can also choose between *Linux containers and Windows containers*.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="15d22-148">[前へ] (net-framework-container-scenarios.md) [戻る] (net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="15d22-148">[Previous] (net-framework-container-scenarios.md) [Next] (net-container-os-targets.md)</span></span>

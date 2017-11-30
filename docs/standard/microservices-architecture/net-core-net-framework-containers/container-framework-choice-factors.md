---
title: "意思決定テーブル。 Docker を使用する .NET フレームワーク"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |意思決定テーブル、Docker を使用する .NET フレームワーク"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="97cef-105">意思決定テーブル: Docker に使用する .NET フレームワーク</span><span class="sxs-lookup"><span data-stu-id="97cef-105">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="97cef-106">.NET Framework または .NET Core および Windows または Linux のコンテナーを使用するかどうかを以下にまとめます。</span><span class="sxs-lookup"><span data-stu-id="97cef-106">The following summarizes whether to use .NET Framework or .NET Core, and Windows or Linux containers.</span></span> <span data-ttu-id="97cef-107">Linux コンテナーのことに注意して、Linux ベースの Docker ホスト (Vm またはサーバー) を作成する必要があり、Windows コンテナーの必要がある Windows Server ベースの Docker ホスト (Vm またはサーバー)。</span><span class="sxs-lookup"><span data-stu-id="97cef-107">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

<span data-ttu-id="97cef-108">アプリケーションの決定に影響を与えるいくつかの機能があります。</span><span class="sxs-lookup"><span data-stu-id="97cef-108">There are several features of your application that affect your decision.</span></span> <span data-ttu-id="97cef-109">決定を行う際に、これらの機能の重要性を比較検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97cef-109">You should weigh the importance of these features when making your decision.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="97cef-110">開発用コンピューターでは、Linux または Windows のいずれか 1 つの Docker ホストを実行します。</span><span class="sxs-lookup"><span data-stu-id="97cef-110">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="97cef-111">実行し、同時に 1 つのソリューションをテストする関連 microservices は、すべて同じコンテナー プラットフォーム上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97cef-111">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

* <span data-ttu-id="97cef-112">アプリケーション アーキテクチャが選択肢として、**コンテナーに対する Microservices**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-112">Your application architecture choice is **Microservices on containers**.</span></span>
    - <span data-ttu-id="97cef-113">.NET 実装の選択をする必要があります*.NET Core*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-113">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="97cef-114">コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-114">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="97cef-115">アプリケーション アーキテクチャが選択肢としては、**モノリシック アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-115">Your application architecture choice is a **Monolithic application**.</span></span>
    - <span data-ttu-id="97cef-116">.NET 実装の選択には、いずれかを指定できる*.NET Core*または*.NET Framework*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-116">Your .NET implementation choice can be either *.NET Core* or *.NET Framework*.</span></span>
    - <span data-ttu-id="97cef-117">選択した場合*.NET Core*、コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-117">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="97cef-118">選択した場合*.NET Framework*、コンテナー プラットフォームの選択をする必要があります*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-118">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="97cef-119">アプリケーションが、**新しいコンテナー ベースの開発 (「緑フィールド」)**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-119">Your application is a  **New container-based development ("green-field")**.</span></span>
    - <span data-ttu-id="97cef-120">.NET 実装の選択をする必要があります*.NET Core*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-120">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="97cef-121">コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-121">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="97cef-122">アプリケーションが、 **Windows Server コンテナーへの移行のレガシー アプリケーション (「brown フィールド」)**</span><span class="sxs-lookup"><span data-stu-id="97cef-122">Your application is a **Windows Server legacy app ("brown-field") migration to containers**</span></span>
    - <span data-ttu-id="97cef-123">.NET 実装の選択は*.NET Framework* framework の依存関係に基づいています。</span><span class="sxs-lookup"><span data-stu-id="97cef-123">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="97cef-124">コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework の依存関係が原因です。</span><span class="sxs-lookup"><span data-stu-id="97cef-124">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="97cef-125">アプリケーションの設計目標は**クラスで最高のパフォーマンスとスケーラビリティ**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-125">Your application's design goal is **Best-in-class performance and scalability**.</span></span>
    - <span data-ttu-id="97cef-126">.NET 実装の選択をする必要があります*.NET Core*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-126">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="97cef-127">コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-127">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="97cef-128">使用して、アプリケーションをビルドした**ASP.NET Core**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-128">You built your application using **ASP.NET Core**.</span></span>
    - <span data-ttu-id="97cef-129">.NET 実装の選択をする必要があります*.NET Core*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-129">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="97cef-130">使用することができます、 *.NET Framework*実装では、他のフレームワークの依存関係がある場合。</span><span class="sxs-lookup"><span data-stu-id="97cef-130">You can use the *.NET Framework* implementation, if you have other framework dependencies.</span></span>
    - <span data-ttu-id="97cef-131">選択した場合*.NET Core*、コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-131">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="97cef-132">選択した場合*.NET Framework*、コンテナー プラットフォームの選択をする必要があります*Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-132">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="97cef-133">使用して、アプリケーションをビルドした**(MVC 5 の場合、Web API 2、および Web フォーム) に ASP.NET 4**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-133">You built your application using **ASP.NET 4 (MVC 5, Web API 2, and Web Forms)**.</span></span>
    - <span data-ttu-id="97cef-134">.NET 実装の選択は*.NET Framework* framework の依存関係に基づいています。</span><span class="sxs-lookup"><span data-stu-id="97cef-134">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="97cef-135">コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework の依存関係が原因です。</span><span class="sxs-lookup"><span data-stu-id="97cef-135">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="97cef-136">アプリケーションで使用**SignalR サービス**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-136">Your application uses **SignalR services**.</span></span>
    - <span data-ttu-id="97cef-137">.NET 実装の選択は、 *.NET Framework*、または*.NET Core 2.1 (リリースされた場合) またはそれ以降*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-137">Your .NET implementation choice can be *.NET Framework*, or *.NET Core 2.1 (when released) or later*.</span></span>
    - <span data-ttu-id="97cef-138">コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* SignalR 実装では、.NET Framework で選択した場合。</span><span class="sxs-lookup"><span data-stu-id="97cef-138">Your container platform choice must be *Windows containers* if you chose the SignalR implementation in .NET Framework.</span></span>
    - <span data-ttu-id="97cef-139">コンテナー プラットフォームの選択には、(リリースされた場合)、SignalR 実装では、.NET Core 2.1 以降を選択した場合は、Linux コンテナーまたは Windows コンテナーのいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="97cef-139">Your container platform choice can be either Linux containers or Windows containers if you chose the SignalR implementation in .NET Core 2.1 or later (when released).</span></span>  
    - <span data-ttu-id="97cef-140">ときに**SignalR サービス**'åžàs' *.NET Core*、使用することができます*Linux コンテナーや Windows コンテナー*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-140">When **SignalR services** run on *.NET Core*, you can use *Linux containers or Windows Containers*.</span></span>
* <span data-ttu-id="97cef-141">アプリケーションで使用**WCF、WF、およびその他の従来のフレームワーク**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-141">Your application uses **WCF, WF, and other legacy frameworks**.</span></span>
    - <span data-ttu-id="97cef-142">.NET 実装の選択は*.NET Framework*、または*(将来のリリースのロードマップ) で .NET Core*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-142">Your .NET implementation choice is *.NET Framework*, or *.NET Core (in the roadmap for a future release)*.</span></span>
    - <span data-ttu-id="97cef-143">コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework の依存関係が原因です。</span><span class="sxs-lookup"><span data-stu-id="97cef-143">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="97cef-144">アプリケーションで**消費の Azure サービス**です。</span><span class="sxs-lookup"><span data-stu-id="97cef-144">Your application involves **Consumption of Azure services**.</span></span>
    - <span data-ttu-id="97cef-145">.NET 実装の選択は*.NET Framework*、または*(最終的にすべての Azure サービスでは、クライアント Sdk .NET Core) .NET Core*です。</span><span class="sxs-lookup"><span data-stu-id="97cef-145">Your .NET implementation choice is *.NET Framework*, or *.NET Core (eventually all Azure services will provide client SDKs for .NET Core)*.</span></span>
    - <span data-ttu-id="97cef-146">コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework クライアント Api を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="97cef-146">Your container platform choice must be *Windows containers* if you use .NET Framework client APIs.</span></span>
    - <span data-ttu-id="97cef-147">クライアントの利用可能な Api を使用する場合*.NET Core*、間で選択することもできます。 *Linux コンテナーと Windows コンテナーの*します。</span><span class="sxs-lookup"><span data-stu-id="97cef-147">If you use client APIs available for *.NET Core*, you can also choose between *Linux containers and Windows containers*.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="97cef-148">[前](net-framework-コンテナーの scenarios.md) [次へ] (net-コンテナーの os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="97cef-148">[Previous] (net-framework-container-scenarios.md) [Next] (net-container-os-targets.md)</span></span>

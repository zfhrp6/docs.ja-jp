---
title: ASP.NET Core および Azure での最新の Web アプリケーションの設計
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | 概要
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: 57c2a598e48f855dd540b96c7ebdb522b4197b91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580264"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="1c9f0-103">ASP.NET Core および Azure での最新の Web アプリケーションの設計</span><span class="sxs-lookup"><span data-stu-id="1c9f0-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![カバーの画像](./media/cover.jpg)


<span data-ttu-id="1c9f0-105">.NET Core と ASP.NET Core は、従来の .NET 開発よりも優れたいくつかの利点を提供します。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-105">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="1c9f0-106">次の一部またはすべてがアプリケーションの成功に重要な場合は、サーバー アプリケーションに .NET Core を使用してください。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-106">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="1c9f0-107">クロス プラットフォーム サポート</span><span class="sxs-lookup"><span data-stu-id="1c9f0-107">Cross-platform support</span></span>

-   <span data-ttu-id="1c9f0-108">マイクロサービスの使用</span><span class="sxs-lookup"><span data-stu-id="1c9f0-108">Use of microservices</span></span>

-   <span data-ttu-id="1c9f0-109">Docker コンテナーの使用</span><span class="sxs-lookup"><span data-stu-id="1c9f0-109">Use of Docker containers</span></span>

-   <span data-ttu-id="1c9f0-110">高パフォーマンスとスケーラビリティの要件</span><span class="sxs-lookup"><span data-stu-id="1c9f0-110">High performance and scalability requirements</span></span>

-   <span data-ttu-id="1c9f0-111">同じサーバー上のアプリケーション別の .NET バージョンのサイド バイ サイドのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="1c9f0-111">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="1c9f0-112">従来の .NET アプリケーションはこれらの要件をサポートできますが、ASP.NET Core と .NET Core は、上記のシナリオに対する改善されたサポートを提供するように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-112">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="1c9f0-113">ますます多くの組織が、Microsoft Azure などのサービスを使用してクラウドで Web アプリケーションをホストすることを選択しています。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-113">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="1c9f0-114">アプリケーションまたは組織にとって次のことが重要な場合は、クラウドでのアプリケーションのホストを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-114">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="1c9f0-115">データ センターのコスト (ハードウェア、ソフトウェア、スペース、ユーティリティなど) の投資の削減</span><span class="sxs-lookup"><span data-stu-id="1c9f0-115">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="1c9f0-116">柔軟な料金 (アイドル状態の容量ではなく、使用量に基づく支払い)</span><span class="sxs-lookup"><span data-stu-id="1c9f0-116">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="1c9f0-117">極端な信頼性</span><span class="sxs-lookup"><span data-stu-id="1c9f0-117">Extreme reliability</span></span>

-   <span data-ttu-id="1c9f0-118">強化されたアプリのモビリティ。アプリが展開されている場所と方法を簡単に変更できること。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-118">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="1c9f0-119">柔軟な容量。実際のニーズに基づいたスケール アップまたはスケール ダウン。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-119">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="1c9f0-120">Microsoft Azure でホストされる ASP.NET Core での Web アプリケーションを構築すると、従来型の代替手段よりも優れた多くの競争上の優位性が得られます。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-120">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="1c9f0-121">ASP.NET Core は、最新の Web アプリケーションの開発作業とクラウド ホスティングのシナリオ用に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-121">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="1c9f0-122">このガイドでは、これらの機能を最適に活用するために ASP.NET Core アプリケーションを設計する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-122">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="1c9f0-123">目的</span><span class="sxs-lookup"><span data-stu-id="1c9f0-123">Purpose</span></span>

<span data-ttu-id="1c9f0-124">このガイドでは、ASP.NET Core と Azure を使用したモノリシックな Web アプリケーションの構築に関するエンド ツー エンドのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-124">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="1c9f0-125">このガイドは、エンタープライズ アプリケーションをホストするための Docker、マイクロサービス、およびコンテナーの展開を中心に説明している「*Architecting and Developing Containerized and Microservice-based Applications with .NET*」(.NET を使用したコンテナー化およびマイクロサービス ベースのアプリケーションの設計と開発) を補完します。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-125">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="1c9f0-126">.NET でのコンテナー化されたマイクロサービス ベースのアプリの設計および開発</span><span class="sxs-lookup"><span data-stu-id="1c9f0-126">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="1c9f0-127">**電子ブック**</span><span class="sxs-lookup"><span data-stu-id="1c9f0-127">**e-book**</span></span>  
> <http://aka.ms/MicroservicesEbook>
> - <span data-ttu-id="1c9f0-128">**サンプル アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="1c9f0-128">**Sample Application**</span></span>  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="1c9f0-129">対象読者</span><span class="sxs-lookup"><span data-stu-id="1c9f0-129">Who should use this guide</span></span>

<span data-ttu-id="1c9f0-130">このガイドの対象ユーザーは、主にクラウドでの Microsoft テクノロジとサービスを使用した最新の Web アプリケーションの構築に関心がある開発者、開発担当者、およびアーキテクトです。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-130">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="1c9f0-131">2 番目の対象ユーザーは、ASP.NET や Azure を既に使い慣れていて、新規または既存のプロジェクトに対して ASP.NET Core にアップグレードすることに意味があるかどうかに関する情報を探している技術的な意思決定者です。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-131">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="1c9f0-132">このガイドを使用する方法</span><span class="sxs-lookup"><span data-stu-id="1c9f0-132">How you can use this guide</span></span>

<span data-ttu-id="1c9f0-133">このガイドは、最新の .NET テクノロジと Windows Azure を使用した Web アプリケーションの構築に焦点を当てた比較的小さなドキュメントに凝縮されています。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-133">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="1c9f0-134">そのため、このようなアプリケーションと、技術的な考慮事項を理解するための基盤を提供するものとして、全体を読むことができます。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-134">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="1c9f0-135">ガイドは、サンプル アプリケーションと共に、最初に参照するものとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-135">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="1c9f0-136">関連するサンプル アプリケーションをテンプレートとして使用するか、アプリケーションのコンポーネント部分を整理する方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-136">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="1c9f0-137">独自のアプリケーションでこれらの選択肢を比較検討する場合、ガイドの基本原則とアーキテクチャのカバレッジ、テクノロジのオプション、および決定時の考慮事項を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-137">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="1c9f0-138">これらの考慮事項と営業案件の共通理解を確保するために、チームにこのガイドを自由に転送してください。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="1c9f0-139">用語の共通セットと基本原則を理解して全員が作業すると、一貫性のあるアプリケーションのアーキテクチャのパターンと実践方法を確保するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1c9f0-139">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="1c9f0-140">参照</span><span class="sxs-lookup"><span data-stu-id="1c9f0-140">References</span></span>
- <span data-ttu-id="1c9f0-141">**サーバー アプリ用 .NET Core と .NET Framework の選択**</span><span class="sxs-lookup"><span data-stu-id="1c9f0-141">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
<span data-ttu-id="1c9f0-142">[Next] (modern-web-applications-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="1c9f0-142">[Next] (modern-web-applications-characteristics.md)</span></span>

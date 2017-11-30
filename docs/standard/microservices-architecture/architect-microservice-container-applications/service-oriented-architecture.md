---
title: "サービス指向アーキテクチャ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |サービス指向アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="7c950-104">サービス指向アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7c950-104">Service-oriented architecture</span></span> 

<span data-ttu-id="7c950-105">サービス指向アーキテクチャ (SOA) 過剰使用されている用語、別のユーザーにさまざまなものを意味していました。</span><span class="sxs-lookup"><span data-stu-id="7c950-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="7c950-106">共通の基盤として SOA ことを意味のサブシステムや階層のようなさまざまな種類に分類できます (最も一般的に HTTP サービス) の複数のサービスへの分解によって、アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="7c950-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="7c950-107">これらのサービスようになりましたとして展開できます Docker コンテナー展開の問題を解決するコンテナー イメージのすべての依存関係が含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="7c950-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="7c950-108">ただし、SOA アプリケーションを拡張する必要がある場合は、拡張性があります、可用性の課題を配置する場合は、1 つの Docker ホストに基づきます。</span><span class="sxs-lookup"><span data-stu-id="7c950-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="7c950-109">これは、クラスタ リング ソフトウェアまたはオーケストレーター Docker に役立つ、microservices の展開のアプローチを記述して以降のセクションで説明したようです。</span><span class="sxs-lookup"><span data-stu-id="7c950-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="7c950-110">Docker コンテナーに便利です (ただし、必須ではない) は、従来のサービス指向アーキテクチャより高度な microservices アーキテクチャの両方にします。</span><span class="sxs-lookup"><span data-stu-id="7c950-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="7c950-111">SOA から派生して Microservices が SOA は microservices アーキテクチャと異なる。</span><span class="sxs-lookup"><span data-stu-id="7c950-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="7c950-112">大規模なサーバーの全体のブローカーのような機能には、組織レベルでは、中央 orchestrators と[Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) SOA の典型的な。</span><span class="sxs-lookup"><span data-stu-id="7c950-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="7c950-113">ほとんどの場合、これらは、マイクロ サービス コミュニティでのアンチ パターン。</span><span class="sxs-lookup"><span data-stu-id="7c950-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="7c950-114">実際と主張する人を「マイクロ サービス アーキテクチャは SOA 適切です」</span><span class="sxs-lookup"><span data-stu-id="7c950-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="7c950-115">このガイドは、SOA アプローチは、要件とマイクロ サービス アーキテクチャで使用される手法よりも小さい規範となるために、microservices、について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c950-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="7c950-116">マイクロ サービス ベースのアプリケーションを構築する方法がわかっている場合、単純なサービス指向アプリケーションをビルドする方法も知っておきます。</span><span class="sxs-lookup"><span data-stu-id="7c950-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="7c950-117">[前](docker-アプリケーションの状態-data.md) [次へ] (microservices architecture.md)</span><span class="sxs-lookup"><span data-stu-id="7c950-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>

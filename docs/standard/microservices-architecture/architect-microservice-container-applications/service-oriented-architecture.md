---
title: "サービス指向アーキテクチャ"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | サービス指向アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6a5f0f53f4208c9944adea33fe1aa3f35fed81ab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="ff9fc-104">サービス指向アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ff9fc-104">Service-oriented architecture</span></span> 

<span data-ttu-id="ff9fc-105">サービス指向アーキテクチャ (SOA) は乱用されている用語であり、人によって異なる意味で使われています。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="ff9fc-106">ただし、共通の基準としての SOA は、アプリケーションをサブシステムや階層などのさまざまな種類に分類できる複数のサービス (通常は HTTP サービス) に分解して、アプリケーションを構築することを意味します。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="ff9fc-107">このようなサービスは Docker コンテナーとして展開できます。すべての依存関係がコンテナー イメージに含まれているため、展開の問題が解決します。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="ff9fc-108">ただし、SOA アプリケーションをスケール アップする必要がある場合、単一の Docker ホストに基づいて展開すると、スケーラビリティと可用性に問題が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="ff9fc-109">このような場合に Docker クラスタリング ソフトウェアまたはオーケストレーターが役立ちます。詳細については、マイクロサービスの展開アプローチについて説明する後述のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="ff9fc-110">Docker コンテナーは、従来のサービス指向アーキテクチャと高度なマイクロサービス アーキテクチャの両方にとって便利な機能です (ただし、必須ではありません)。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="ff9fc-111">マイクロサービスは SOA に由来しますが、SOA はマイクロサービス アーキテクチャとは異なります。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="ff9fc-112">大規模な中央のブローカー、組織レベルの中央のオーケストレーター、[エンタープライズ サービス バス (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) などは、SOA の典型的な機能です。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="ff9fc-113">ただしほとんどの場合、マイクロサービス コミュニティではこれらはアンチパターンです。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="ff9fc-114">実際、一部の人は "マイクロサービス アーキテクチャはきちんとした SOA だ" と主張しています。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="ff9fc-115">このガイドでは、マイクロサービスに焦点を当てています。なぜなら、SOA アプローチは、マイクロサービス アーキテクチャで使用される要件や手法ほど規範的ではないからです。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="ff9fc-116">マイクロサービスベースのアプリケーションを構築する方法がわかれば、より単純なサービス指向アプリケーションを構築する方法もわかります。</span><span class="sxs-lookup"><span data-stu-id="ff9fc-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="ff9fc-117">[前へ] (docker-application-state-data.md) [次へ] (microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="ff9fc-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>

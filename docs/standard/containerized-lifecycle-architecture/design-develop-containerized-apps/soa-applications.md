---
title: "SOA アプリケーション"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 81d2b60303e051568b664ec20225d835a09187c0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="soa-applications"></a><span data-ttu-id="fb25d-104">SOA アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fb25d-104">SOA applications</span></span>

<span data-ttu-id="fb25d-105">SOA 過剰使用されている用語、別の人に非常に多くのさまざまなものを意図したもの。</span><span class="sxs-lookup"><span data-stu-id="fb25d-105">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="fb25d-106">少なくともと共通の基盤、SOA、またはサービスの向き、平均する構造体 (最も一般的な HTTP サービス) としてさまざまな種類で分類可能な複数のサービスに分解することによって、アプリケーションのアーキテクチャなどのサブシステムが、または、層とそれ以外の場合にします。</span><span class="sxs-lookup"><span data-stu-id="fb25d-106">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="fb25d-107">今日では、依存関係をすべて、コンテナー イメージに含まれているために、展開に関連する問題を解決する Docker コンテナーとしてそれらのサービスを展開できます。</span><span class="sxs-lookup"><span data-stu-id="fb25d-107">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="fb25d-108">ただし、Soa のスケール アウトする必要がある場合がありますの課題に基づいて 1 つのインスタンスを展開する場合は。</span><span class="sxs-lookup"><span data-stu-id="fb25d-108">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="fb25d-109">これは、Docker のクラスタ リング ソフトウェアまたは orchestrator が支援する場所です。</span><span class="sxs-lookup"><span data-stu-id="fb25d-109">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="fb25d-110">見ていきますこれで、次のセクションで詳しくお microservices アプローチを調べる場合です。</span><span class="sxs-lookup"><span data-stu-id="fb25d-110">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="fb25d-111">1 日の終わりには、コンテナーのクラスタ リング ソリューションは、両方の従来の SOA アーキテクチャまたは各マイクロ サービスがそのデータ モデルを所有するより高度な microservices アーキテクチャ用に便利です。</span><span class="sxs-lookup"><span data-stu-id="fb25d-111">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="fb25d-112">および、複数のデータベースでは、ご協力に感謝するもできるスケール アウト SOA サービスによって共有される単一のデータベースの操作ではなく、データ層です。</span><span class="sxs-lookup"><span data-stu-id="fb25d-112">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="fb25d-113">ただし、データの分割についての説明は、アーキテクチャと設計についてのみです。</span><span class="sxs-lookup"><span data-stu-id="fb25d-113">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="fb25d-114">[前](state-and-data-in-docker-applications.md) [次へ] (調整-高-スケーラビリティ-availability.md)</span><span class="sxs-lookup"><span data-stu-id="fb25d-114">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>

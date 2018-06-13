---
title: SOA アプリケーション
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 37313c4eb437b6b7a362456a7d1ee3b3aecb6020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569426"
---
# <a name="soa-applications"></a><span data-ttu-id="779d8-103">SOA アプリケーション</span><span class="sxs-lookup"><span data-stu-id="779d8-103">SOA applications</span></span>

<span data-ttu-id="779d8-104">SOA 過剰使用されている用語、別の人に非常に多くのさまざまなものを意図したもの。</span><span class="sxs-lookup"><span data-stu-id="779d8-104">SOA was an overused term and meant so many different things to different people.</span></span> <span data-ttu-id="779d8-105">少なくともと共通の基盤、SOA、またはサービスの向き、平均する構造体 (最も一般的な HTTP サービス) としてさまざまな種類で分類可能な複数のサービスに分解することによって、アプリケーションのアーキテクチャなどのサブシステムが、または、層とそれ以外の場合にします。</span><span class="sxs-lookup"><span data-stu-id="779d8-105">But at a minimum and as a common denominator, SOA, or service orientation, mean that you structure the architecture of your application by decomposing it in multiple services (most commonly as HTTP services) that can be classified in different types like subsystems or, in other cases, as tiers.</span></span>

<span data-ttu-id="779d8-106">今日では、依存関係をすべて、コンテナー イメージに含まれているために、展開に関連する問題を解決する Docker コンテナーとしてそれらのサービスを展開できます。</span><span class="sxs-lookup"><span data-stu-id="779d8-106">Today, you can deploy those services as Docker containers, which solves deployment-related issues because all of the dependencies are included within the container image.</span></span> <span data-ttu-id="779d8-107">ただし、Soa のスケール アウトする必要がある場合がありますの課題に基づいて 1 つのインスタンスを展開する場合は。</span><span class="sxs-lookup"><span data-stu-id="779d8-107">However, when you need to scale-out SOAs, you might encounter challenges if you are deploying based on single instances.</span></span> <span data-ttu-id="779d8-108">これは、Docker のクラスタ リング ソフトウェアまたは orchestrator が支援する場所です。</span><span class="sxs-lookup"><span data-stu-id="779d8-108">This is where a Docker clustering software or orchestrator will help you.</span></span> <span data-ttu-id="779d8-109">見ていきますこれで、次のセクションで詳しくお microservices アプローチを調べる場合です。</span><span class="sxs-lookup"><span data-stu-id="779d8-109">We'll look at this in greater detail in the next section when we examine microservices approaches.</span></span>

<span data-ttu-id="779d8-110">1 日の終わりには、コンテナーのクラスタ リング ソリューションは、両方の従来の SOA アーキテクチャまたは各マイクロ サービスがそのデータ モデルを所有するより高度な microservices アーキテクチャ用に便利です。</span><span class="sxs-lookup"><span data-stu-id="779d8-110">At the end of the day, the container clustering solutions are useful for both a traditional SOA architecture or for a more advanced microservices architecture in which each microservice owns its data model.</span></span> <span data-ttu-id="779d8-111">および、複数のデータベースでは、ご協力に感謝するもできるスケール アウト SOA サービスによって共有される単一のデータベースの操作ではなく、データ層です。</span><span class="sxs-lookup"><span data-stu-id="779d8-111">And, thanks to multiple databases, you also can scale-out the data tier instead of working with monolithic databases shared by the SOA services.</span></span> <span data-ttu-id="779d8-112">ただし、データの分割についての説明は、アーキテクチャと設計についてのみです。</span><span class="sxs-lookup"><span data-stu-id="779d8-112">However, the discussion about splitting the data is purely about architecture and design.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="779d8-113">[前] (state-and-data-in-docker-applications.md) [次へ] (調整-高-スケーラビリティ-availability.md)</span><span class="sxs-lookup"><span data-stu-id="779d8-113">[Previous] (state-and-data-in-docker-applications.md) [Next] (orchestrate-high-scalability-availability.md)</span></span>

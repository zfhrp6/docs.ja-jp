---
title: "指数バックオフによる再試行を実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |指数バックオフによる再試行を実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8ad8c6363ddff59915efc076161fe6b76074bbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="d2117-104">指数バックオフによる再試行を実装します。</span><span class="sxs-lookup"><span data-stu-id="d2117-104">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="d2117-105">[*指数バックオフによる再試行*](https://docs.microsoft.com/azure/architecture/patterns/retry)指数関数的に増加する待機時間が終了するまで、最大再試行回数が、操作を再試行しようとする手法は、(、[指数バックオフ](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="d2117-105">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="d2117-106">この手法は、クラウド リソースが断続的に使用できなくなることを複数の数秒何らかの理由でファクトを採用します。</span><span class="sxs-lookup"><span data-stu-id="d2117-106">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="d2117-107">たとえば、オーケストレーター可能性があります移動するコンテナーの負荷分散クラスター内の別のノードにします。</span><span class="sxs-lookup"><span data-stu-id="d2117-107">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="d2117-108">この期間中は、いくつかの要求が失敗します。</span><span class="sxs-lookup"><span data-stu-id="d2117-108">During that time, some requests might fail.</span></span> <span data-ttu-id="d2117-109">別の例には、SQL Azure、ここでデータベースに移動できますを別のサーバーの負荷分散をデータベースが利用できない、数秒のようにデータベース可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d2117-109">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="d2117-110">指数バックオフによる再試行ロジックを実装する方法はたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="d2117-110">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d2117-111">[前](部分的に失敗-strategies.md) [次へ] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="d2117-111">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>

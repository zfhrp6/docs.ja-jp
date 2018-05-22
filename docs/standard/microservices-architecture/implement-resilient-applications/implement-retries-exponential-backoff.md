---
title: 指数バックオフを含む再試行を実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 指数バックオフを含む再試行を実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7f909c6f81abce80bfdf118112271f1f87254793
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="bfa02-103">指数バックオフを含む再試行を実装する</span><span class="sxs-lookup"><span data-stu-id="bfa02-103">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="bfa02-104">[*指数バックオフを含む再試行*](https://docs.microsoft.com/azure/architecture/patterns/retry)は、最大再試行回数に達するまで、指数関数的に増加する待機時間で操作を再試行しようとする手法です ([指数バックオフ](https://en.wikipedia.org/wiki/Exponential_backoff))。</span><span class="sxs-lookup"><span data-stu-id="bfa02-104">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="bfa02-105">この手法を利用すると、何らかの理由でクラウド リソースが数秒以上断続的に使用できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bfa02-105">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="bfa02-106">たとえば、オーケストレーターは、負荷分散のためにコンテナーをクラスター内の別ノードに移動している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bfa02-106">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="bfa02-107">その間は、一部の要求が失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bfa02-107">During that time, some requests might fail.</span></span> <span data-ttu-id="bfa02-108">また、SQL Azure のようなデータベースで、負荷分散のためにデータベースを別のサーバーに移動しているときに、データベースを数秒間使用できなくなる例もあります。</span><span class="sxs-lookup"><span data-stu-id="bfa02-108">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="bfa02-109">指数バックオフを使用する再試行ロジックを実装するには、さまざまなアプローチがあります。</span><span class="sxs-lookup"><span data-stu-id="bfa02-109">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="bfa02-110">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="bfa02-110">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>

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
# <a name="implementing-retries-with-exponential-backoff"></a>指数バックオフによる再試行を実装します。

[*指数バックオフによる再試行*](https://docs.microsoft.com/azure/architecture/patterns/retry)指数関数的に増加する待機時間が終了するまで、最大再試行回数が、操作を再試行しようとする手法は、(、[指数バックオフ](https://en.wikipedia.org/wiki/Exponential_backoff)). この手法は、クラウド リソースが断続的に使用できなくなることを複数の数秒何らかの理由でファクトを採用します。 たとえば、オーケストレーター可能性があります移動するコンテナーの負荷分散クラスター内の別のノードにします。 この期間中は、いくつかの要求が失敗します。 別の例には、SQL Azure、ここでデータベースに移動できますを別のサーバーの負荷分散をデータベースが利用できない、数秒のようにデータベース可能性があります。

指数バックオフによる再試行ロジックを実装する方法はたくさんあります。


>[!div class="step-by-step"]
[前](部分的に失敗-strategies.md) [次へ] (implement-resilient-entity-framework-core-sql-connections.md)

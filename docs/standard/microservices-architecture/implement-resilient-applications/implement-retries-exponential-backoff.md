---
title: 指数バックオフを含む再試行を実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 指数バックオフを含む再試行を実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ee5dd711484ba7861eedbd9613fda1209736d5b6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106919"
---
# <a name="implementing-retries-with-exponential-backoff"></a>指数バックオフを含む再試行を実装する

[*指数バックオフを含む再試行*](https://docs.microsoft.com/azure/architecture/patterns/retry)は、最大再試行回数に達するまで、指数関数的に増加する待機時間で操作を再試行しようとする手法です ([指数バックオフ](https://en.wikipedia.org/wiki/Exponential_backoff))。 この手法を利用すると、何らかの理由でクラウド リソースが数秒以上断続的に使用できなくなる可能性があります。 たとえば、オーケストレーターは、負荷分散のためにコンテナーをクラスター内の別ノードに移動している可能性があります。 その間は、一部の要求が失敗する可能性があります。 また、SQL Azure のようなデータベースで、負荷分散のためにデータベースを別のサーバーに移動しているときに、データベースを数秒間使用できなくなる例もあります。

指数バックオフを使用する再試行ロジックを実装するには、さまざまなアプローチがあります。


>[!div class="step-by-step"]
[前へ](partial-failure-strategies.md)
[次へ](implement-resilient-entity-framework-core-sql-connections.md)

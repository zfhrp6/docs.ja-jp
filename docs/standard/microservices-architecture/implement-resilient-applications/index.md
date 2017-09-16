---
title: "回復性の高いアプリケーションの実装"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 回復性の高いアプリケーションの実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: a1041938891219fd2e3b17d004bb40b544b8ceaa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="implementing-resilient-applications"></a>回復性の高いアプリケーションの実装

*マイクロサービスおよびクラウド ベースのアプリケーションは、最終的に確実に発生する部分的な障害を受け入れる必要があります。そのような部分的な障害に対する回復性があるようにアプリケーションを設計する必要があります。*

回復性は、障害から回復し、引き続き機能する能力です。 障害を回避することではなく、障害が発生するという事実を受け入れ、ダウンタイムまたはデータの損失を回避するようにそれらに対応することです。 回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。

マイクロサービスベースのアプリケーションの設計および導入は難しい作業です。 しかし、何らかの障害が確実に発生する環境で、アプリケーションの稼働を維持する必要もあります。 そのため、アプリケーションは、回復性を持っている必要があります。 ネットワークの停止、クラウド内のノードまたは VM のクラッシュなどの部分的な障害に対処するように設計する必要があります。 クラスタ内でマイクロサービス (コンテナー) を別のノードに移動するだけでも、アプリケーション内での断続的な短いエラーが発生する可能性があります。

アプリケーションの多くの個々のコンポーネントにも、正常性監視機能を組み込むも必要があります。 この章のガイドラインに従うと、複雑で、クラウド ベースの展開で発生する一時的なダウンタイムや定期的な障害があってもスムーズに動作するアプリケーションを作成できます。


>[!div class="step-by-step"]
[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)


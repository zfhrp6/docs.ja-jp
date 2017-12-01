---
title: "作成、進化、およびバージョン管理マイクロ サービス Api とコントラクト"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |作成、進化、およびバージョン管理マイクロ サービス Api とコントラクト"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 433711c3479eafd52bf9f5d53faf8e5707c6c624
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>作成、進化、およびバージョン管理マイクロ サービス Api とコントラクト

マイクロ サービス API は、サービスとクライアント間のコントラクトです。 単独で拡張、マイクロ サービス コントラクトが非常に重要な理由は、その API コントラクトが損なわれていない場合にのみことができます。 コントラクトを変更する場合、クライアント アプリケーションまたは API ゲートウェイに影響します。

API 定義の性質は、どのプロトコルを使用しているによって異なります。 たとえば、メッセージングを使用している場合 (など[AMQP](https://www.amqp.org/))、API は、メッセージの種類。 HTTP と RESTful サービスを使用している場合、Url と、要求と応答の JSON 形式の API で構成されます。

ただし、場合でもよく考えられた、初期のコントラクトは、サービス API が時間の経過と共に変更する必要があります。 このような場合 —、API が複数のクライアント アプリケーションによって使用されるパブリック API である場合に特にと -通常、新しい API コントラクトにアップグレードするすべてのクライアントを強制できません。 通常、サービス コントラクトの新旧両方のバージョンを同時に実行している方法でサービスの新しいバージョンを増分配置する必要があります。 そのため、サービスのバージョン管理するための戦略を理解しておくことができます。

API が変更されたが、API に属性またはパラメーターを追加する場合と同様に、小さいとき、古い API を使用するクライアントを切り替えるし、サービスの新しいバージョンで機能します。 既定値は、必要なすべての不足している属性を提供することができ、クライアントは、すべての余分な応答属性を無視できる場合があります。

ただし、場合によって、サービス API にメジャーと互換性のない変更を加える必要があります。 すぐに新しいバージョンにアップグレードするには、クライアント アプリケーションまたはサービスを強制的にできない可能性があります、ために、サービスは、一定期間の古いバージョンの API をサポートする必要があります。 REST などの HTTP ベースのメカニズムを使用している場合、1 つは、URL または HTTP ヘッダーには、API のバージョン番号を埋め込むにです。 同じサービス インスタンス内で同時に、サービスの両方のバージョンを実装するか、または API のバージョンを処理するそれぞれの異なるインスタンスを展開するかを決定できます。 これをお勧め、[媒介パターン](https://en.wikipedia.org/wiki/Mediator_pattern)(たとえば、 [MediatR ライブラリ](https://github.com/jbogard/MediatR)) を独立したハンドラーを別の実装のバージョンを分離します。

最後に、REST アーキテクチャを使用している場合、 [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia)バージョン管理に最適なソリューションは、サービス、および evolvable Api を許可します。

## <a name="additional-resources"></a>その他の技術情報

-   **Scott Hanselman です。ASP.NET Core RESTful Web API のバージョン管理が簡単に作成**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **RESTful web API のバージョン管理**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **者を務める Roy Fielding です。バージョン管理、Hypermedia、および REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[前](非同期のメッセージに基づく-communication.md) [次へ] (microservices-addressability-サービス-registry.md)

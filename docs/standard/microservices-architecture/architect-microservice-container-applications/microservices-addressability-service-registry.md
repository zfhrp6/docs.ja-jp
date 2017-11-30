---
title: "Microservices addressability およびサービス レジストリ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Microservices addressability およびサービス レジストリ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a>Microservices addressability およびサービス レジストリ

各マイクロ サービスには、その場所を解決するために使用する一意の名前 (URL) があります。 マイクロ サービスが実行されている場所でアドレス指定可能である必要があります。 、元のコンピューターを実行している特定のマイクロ サービスを検討する必要ことできます不適切なすばやく移動します。 DNS が URL を特定のコンピューターに解決される、同じ方法で、マイクロ サービスを現在の場所が探索可能になるよう名前が一意である必要があります。 Microservices には、アドレス指定可能な名前で実行されているインフラストラクチャから独立して構成することが必要があります。 つまりする必要があります、サービスを展開する方法と、検出方法の間の相互作用があること、[サービス レジストリ](http://microservices.io/patterns/service-registry.html)です。 同様に、コンピューターが失敗したときに、レジストリ サービスできる必要がありますを示す、サービスが実行されているようになりました。

[サービス レジストリ パターン](http://microservices.io/patterns/service-registry.html)サービス検出の重要な部分です。 レジストリは、サービス インスタンスのネットワークの場所を含むデータベースです。 サービス レジストリでは、可用性が高く、最新の状態である必要があります。 クライアントは、サービスのレジストリから取得したネットワークの場所でキャッシュでした。 ただし、その情報を最終的に期限切れになりクライアントはサービス インスタンスを検出できなくなります。 その結果、サービス レジストリは、整合性を維持するためにレプリケーションのプロトコルを使用するサーバーのクラスターで構成されます。

マイクロ サービスの展開環境が (以降のセクションで説明する、クラスターと呼ばれます) によって、サービスの検出が組み込まれています。 など、Azure コンテナー サービス環境内 Kubernetes とマラソンと DC/OS がサービスのインスタンスの登録を処理し、登録解除します。 サーバー側の検出のルーターの役割を果たす各クラスター ホストでプロキシでも実行できます。 別の例は、Azure Service Fabric は、そのボックスの名前付けサービスをサービス レジストリにも提供します。

サービス レジストリともこの問題を解決するのに役立つ、API ゲートウェイ パターンの間で特定のオーバー ラップがあることに注意してください。 たとえば、[サービス ファブリック リバース プロキシ](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)API ゲートウェイ サービス Fabrice 名前付けサービスのベースとし、内部のサービスにアドレス解決を解決するのに役立ちますの実装の型です。

## <a name="additional-resources"></a>その他の技術情報

-   **Chris Richardson です。パターン: サービス レジストリ**
    *http://microservices.io/patterns/service-registry.html*

-   **Auth0 です。サービス レジストリ**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **サンガブリエル Schenker です。サービスの検出**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[前](管理-マイクロ サービス-apis.md) [次へ] (microservice-based-composite-ui-shape-layout.md)

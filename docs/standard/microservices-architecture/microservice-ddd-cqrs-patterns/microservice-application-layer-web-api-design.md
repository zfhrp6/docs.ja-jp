---
title: "マイクロ サービスのアプリケーション層および Web API を設計します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |マイクロ サービスのアプリケーション層および Web API を設計します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>マイクロ サービスのアプリケーション層および Web API を設計します。

## <a name="using-solid-principles-and-dependency-injection"></a>純色の基本原則と依存関係の挿入を使用します。

純色の原則は、DDD パターンを持つマイクロ サービスの開発など、モダンでミッション クリティカルなアプリケーションで使用する重要な手法です。 実線は頭字語を 5 つのグループの基本原則です。

-   1 つの責任の原則

-   開く/閉じる原則

-   リスコフ置換原則

-   分離の逆転原則

-   依存関係の逆転原則

ソリッドは、およびそれらの間の依存関係を分離アプリケーションまたはマイクロ サービス内部レイヤーをデザインする方法に関する詳細があります。 ドメインは、アプリケーションの技術的なデザインには無関係です。 最後の原則に従って、依存関係の逆転 (DI) の原則に従ってには、これによりより分離の実装 DDD レイヤー、レイヤーの残りの部分から、インフラストラクチャ レイヤーを分離することができます。

DI は、依存関係の反転の原則を実装する 1 つの方法です。 これは、オブジェクトとその依存関係間の疎結合を実現するための手法です。 、の共同作業者を直接インスタンス化または静的参照を使用して、ではなく、オブジェクト クラスがそのアクションを実行する必要があるに提供される (または「に挿入された」) クラス。 ほとんどの場合、クラスは、明示的な依存関係の原則に従うように、コンス トラクターを使用して、その依存関係を宣言します。 DI は、通常、特定の制御の反転 (IoC) コンテナーに基づきます。 ASP.NET Core の単純な組み込みの IoC コンテナーを提供しますが、Autofac または Ninject と同様に、お気に入り IoC コンテナーを使用することもできます。

純色の原則に従うと、によって、クラス傾向があります必然的に小さく、十分に考慮された、簡単にテストします。 どのように知ることができる多すぎる依存関係が、クラスに挿入されているかどうかですか。 DI コンス トラクターを使用する場合は、簡単に、コンス トラクターのパラメーターの数を調べるだけで検出されるがあります。 多すぎる依存関係がある場合は、これは、記号、通常 (、[コードの匂い](http://deviq.com/code-smells/)) クラスが多すぎる、実行しようとしは単一の責任の原則に違反する可能性があります。

実線を詳しく説明する他のガイドがかかります。 そのため、このガイドでは、するためにこれらのトピックの最小限のナレッジだけが必要です。

#### <a name="additional-resources"></a>その他の技術情報

-   **実線: 基本的な OOP 原則**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **コントロールのコンテナーと依存性の注入パターンの反転**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith です。新しいはグルー**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[前](nosql-データベースの永続化-infrastructure.md) [次へ] (microservice-application-layer-implementation-web-api.md)

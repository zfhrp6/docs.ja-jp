---
title: "マイクロ サービスごとのデータに対して"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |マイクロ サービスごとのデータに対して"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c51daae04215cfa6f5b5b8d2158a8ed1a8949652
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="data-sovereignty-per-microservice"></a>マイクロ サービスごとのデータに対して

Microservices アーキテクチャの重要な規則は、そのドメインのデータとロジック各マイクロ サービスを所有していることです。 完全なアプリケーションでは、そのロジックとデータを所有していると同様ように各マイクロ サービスを所有している、ロジックとデータがマイクロ サービスごとの独立した展開で、自律的なライフ サイクルの下。

これは、ドメインの概念モデルはサブシステムまたは microservices 間で異なることを意味します。 カスタマー リレーションシップ マネジメント (CRM) アプリケーション、トランザクションが、一意の顧客エンティティの属性と、データの各呼び出しサブシステム、および顧客サポート サブシステムを購入し、そのそれぞれが別に、エンタープライズ アプリケーションを検討してください。範囲指定されたコンテキスト (BC)。

この原則は似ている部分[ドメイン ドリブン デザイン (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)ここで、各[コンテキストの境界を付けられた](https://martinfowler.com/bliki/BoundedContext.html)自律的なサブシステムまたはサービスは、そのドメイン モデル (データとロジックの動作) を所有する必要がありますか。 1 つのビジネス マイクロ サービス (1 つまたは複数のサービス) に関連している各 DDD 範囲指定されたコンテキスト。 (お展開に関する次のセクションで、コンテキストの境界を付けられたパターンには、このポイントでします。)

その一方で、多くのアプリケーションで使用する従来の (モノリシック データ) アプローチは、単一の集中化されたデータベースまたは少数のデータベースの設定です。 これは、図 4-7 に示すようにアプリケーション全体とそのすべての内部サブシステムに使用される正規化された SQL データベースでは多くの場合。

![](./media/image7.png)

**図 4-7**です。 データに対して比較: microservices とモノリシック データベース

最初に、集中化されたデータベースのアプローチは、単純な検索し、全ての一貫性のある複数のサブシステム内のエンティティの再利用を有効にするように見えます。 実際には多くのさまざまなサブシステムを使用して、属性と不要な列を含むほとんどの場合、大きなテーブルを持つ終了します。 短い証跡のハイキング、一日中自動車旅行を取り出し、geography を学習、同じ物理的なマップを使用するようになります。

通常、単一のリレーショナル データベースでモノリシックなアプリケーションが 2 つの重要な利点があります: [ACID トランザクション](https://en.wikipedia.org/wiki/ACID)と SQL 言語が、すべてのテーブルと、アプリケーションに関連するデータにわたって両方の機能です。 このアプローチは、簡単に複数のテーブルからデータを結合するクエリを記述する方法を提供します。

ただし、データ アクセス制限が microservices アーキテクチャに移動するとはるかに複雑です。 でも ACID トランザクションはマイクロ サービスまたは範囲指定されたコンテキスト内で使用する必要がありますしたり、各マイクロ サービスが所有するデータがそのマイクロ サービスをプライベートとそのマイクロ サービス API を介してのみアクセスできます。 データをカプセル化により、こと、microservices 疎結合された互いに改善できます。 複数のサービスは、同じデータにアクセスした、スキーマの更新はすべてのサービスに調整された更新プログラムを必要があります。 マイクロ サービス ライフ サイクルの自律性これを使用できなくなります。 分散データ構造を意味 microservices 全体で 1 つの ACID トランザクションは作成できません。 さらにつまり、ビジネス プロセスが複数 microservices にまたがっている場合は、最終的整合性を使用する必要があります。 これは、はるかに単純な SQL 結合よりも実装困難同様に、その他の多くのリレーショナル データベース機能は使用可能な複数 microservices 間で

さらに進んで、異なる microservices 多くの場合、使用して異なる*種類*データベース。 最新のアプリケーション ストアとプロセスのさまざまな種類のデータ、およびリレーショナル データベースは常に最適な選択肢です。 一部のユース ケース、Azure DocumentDB MongoDB などの NoSQL データベースを持つ方が便利なデータ モデル パフォーマンスと SQL Server のように SQL データベースや Azure SQL データベースよりもスケーラビリティの向上を提供します。 それ以外の場合に、リレーショナル データベースは最善の方法ではまだです。 Microservices ベースのアプリケーションが多くの場合とも呼ば SQL、NoSQL のデータベースの組み合わせを使用ため、[多言語の永続化](http://martinfowler.com/bliki/PolyglotPersistence.html)アプローチです。

データ記憶域のパーティション分割された、polyglot 永続的なアーキテクチャには、多くの利点があります。 疎結合サービスおよびより優れたパフォーマンス、スケーラビリティ、コスト、および管理容易性が含まれます。 ただしが生じる場合がいくつかの分散データ管理の課題の説明はして"[ドメイン モデルの境界を識別する](#identifying-domain-model-boundaries-for-each-microservice)"この章で後述します。

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>Microservices とコンテキストの境界を付けられたパターンの間のリレーションシップ

派生したマイクロ サービスの概念、[範囲指定されたコンテキスト (BC) パターン](http://martinfowler.com/bliki/BoundedContext.html)で[ドメイン ドリブン デザイン (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)です。 DDD は、複数 BCs に分割して、その境界を明示されているが、大規模なモデルを処理します。 各ビジネス継続性は、独自のモデルとデータベースが必要同様に、各マイクロ サービスは、その関連データを所有しています。 さらに、各 BC 通常では、独自[ユビキタス言語](http://martinfowler.com/bliki/UbiquitousLanguage.html)ソフトウェア開発者とドメインの専門家間の通信を支援します。

ユビキタス言語でこれらの用語 (主にドメイン エンティティ) は、異なる範囲指定されたコンテキストで別の名前を持つことができます、異なる場合でもドメイン エンティティが同じ id (つまり、一意の ID、エンティティをストレージから読み取りに使用される) を共有します。 たとえば、ユーザー プロファイルの境界を付けられたコンテキストでユーザーのドメイン エンティティ可能性があります id を共有 Buyer ドメイン内のエンティティ、順序付けの境界を付けられたコンテキスト。

マイクロ サービスそのため、範囲指定されたコンテキストのようには分散型サービスであることも指定します。 範囲指定されたコンテキストごとに個別のプロセスとしてビルドおよび述べたとおり、HTTP、HTTPS、Websocket のように分散するプロトコルを使用する必要がありますまたは[AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)です。 コンテキストの境界を付けられたパターンただしは指定されていませんかどうか、範囲指定されたコンテキストは、分散サービス (ジェネリック サブシステム) など、論理的な境界だけであるかどうか、展開モノリシック アプリケーション内で。

強調表示する各範囲指定されたコンテキストのサービスを定義することをお勧めを開始するには重要です。 制約、設計にする必要はありません。 範囲指定されたコンテキストを設計する必要がありますやビジネス マイクロ サービスをいくつかの物理サービスで構成される場合があります。 最終的には、両方のパターンが、— 範囲指定されたコンテキストとマイクロ サービス-密接に関連します。

分散 microservices の形式での実際の境界を取得することによって microservices から DDD の利点があります。 Microservices 間でモデルを共有していないなどのアイデアを何もする境界を付けられたコンテキストでします。

### <a name="additional-resources"></a>その他の技術情報

-   **Chris Richardson です。パターン: サービスごとのデータベースの**
    [*http://microservices.io/patterns/data/database-per-service.html*](http://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler。BoundedContext**
    [*http://martinfowler.com/bliki/BoundedContext.html*](http://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler。PolyglotPersistence**
    [*http://martinfowler.com/bliki/PolyglotPersistence.html*](http://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Alberto Brandolini です。Driven Design コンテキスト マッピングを戦略的なドメイン**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[前](microservices architecture.md) [次へ] (論理のではなく、物理-architecture.md)

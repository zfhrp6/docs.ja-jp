---
title: "EShopOnContainers で DDD マイクロ サービスに適用する CQRS および CQS のアプローチ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |EShopOnContainers で DDD マイクロ サービスに適用する CQRS および CQS のアプローチ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a2c4429a75ca47d4fbcde868b95e76bc65ea2bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>EShopOnContainers で DDD マイクロ サービスに適用する CQRS および CQS のアプローチ

EShopOnContainers 参照アプリケーションの順序付けマイクロ サービスの設計は、CQRS の原則に基づいています。 ただし、だけコマンドからのクエリを分離することと同じデータベースの操作の両方を使用して、最も単純なアプローチを使用します。

これらのパターンと重要な点をここでは、重要な部分はクエリがべき等である: 何回かシステムでは、そのシステムの状態のクエリは変更されませんに関係なく、トランザクション ロジック「書き込み」よりも別の「読み取り」データ モデルを使用する可能性がありますもドメインは、順序付け microservices が同じデータベースを使用するモデルします。 そのため、これは、簡略化した CQRS 方法です。

その一方で、トランザクションおよびデータの更新をトリガーするには、コマンドは、システムの状態を変更します。 コマンドを使用する場合に注意する必要があります。 複雑さと常に変化するビジネス ルールを処理します。 これは、where をモデル化されたシステムがより適切に DDD 手法を適用します。

このガイドで紹介 DDD パターンを広く適用いない必要があります。 設計上の制約を導入します。 これらの制約では、随時、特にのコマンドやその他のシステム状態を変更するコード品質の向上などの利点があります。 ただし、これらの制約は、読み取りやデータを照会する以下のメリットがありますの複雑さを追加します。

このような 1 つのパターンが、集計のパターンは、以降のセクションで詳細を説明します。 簡単に、パターンでは、集計は、ドメイン内の関係の結果として 1 つの単位として多くのドメイン オブジェクトを処理します。 クエリでは、このパターンから利点を常に利用可能性がありますできません。クエリ ロジックの複雑さに増やすことができます。 読み取り専用のクエリでは、複数のオブジェクトを 1 つの集計として扱うことの利点は取得できません。 のみ、複雑さを取得します。

図 9-2 に示すように、このガイドは、マイクロ サービスのトランザクション/更新領域にのみ (つまり、コマンドによってトリガーされる) と DDD パターンを使用してを提案します。 クエリでは、簡単な方法は、および、CQRS 方法に従えば、コマンドから区切る必要があります。

「クエリ側」を実装するための EF コア、AutoMapper プロジェクション、ストアド プロシージャ、ビュー、具体化されたビューまたはマイクロ ORM などの本格的な ORM からさまざまな方法を選択できます。

このガイドでと選びました。 マイクロを使用した直線のクエリを実装する eShopOnContainers (具体的には、順序付けマイクロ サービス) の ORM のような[Dapper](https://github.com/StackExchange/dapper-dot-net)です。 これにより、最適なパフォーマンスを非常にわずかなオーバーヘッド明るい framework 感謝を取得する SQL ステートメントに基づいて任意のクエリを実装できます。

このアプローチを使用するときに SQL データベースへのエンティティの保存方法に影響するモデルの更新も必要があります Dapper またはクエリを実行する、他の独立した (非 EF) アプローチによって使用される SQL クエリを個別の更新プログラムに注意してください。

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS と DDD パターンは最上位レベル アーキテクチャではありません。

その CQRS および (DDD レイヤーやなどの集計にドメイン モデル) のほとんどの DDD パターンを理解することが重要はないアーキテクチャのスタイルはアーキテクチャ パターンのみです。 Microservices、SOA、およびイベント ドリブンのアーキテクチャ (EDA) は、アーキテクチャのスタイルの例を示します。 これらには、多くの microservices など、多くのコンポーネントのシステムがについて説明します。 CQRS と DDD パターンが 1 つのシステムまたはコンポーネントの内部をについて説明します。ここでは、マイクロ サービス内で何か。

異なる範囲指定されたコンテキスト (BCs) は、さまざまなパターンを採用します。 異なる役割が付いており、さまざまなソリューションにつながります。 エラーにつながるどこからでも同じパターンを強制する強調しておきます。 どこからでも CQRS と DDD パターンを使用しません。 多くのサブシステム、BCs、microservices は簡単や単純な CRUD サービスを使用してまたは別のアプローチを使用してより簡単に実装できます。

1 つだけのアプリケーションのアーキテクチャがある: (microservices アーキテクチャなど) の設計は、システムまたはエンド ツー エンドのアプリケーションのアーキテクチャです。 ただし、各範囲指定されたコンテキスト、またはそのアプリケーション内のマイクロ サービスの設計には、独自のトレードオフとアーキテクチャ パターン レベルでの内部設計に関する決定事項が反映されます。 同じアーキテクチャ パターン CQRS または DDD のようにすべての場所を適用しないでください。

####  <a name="additional-resources"></a>その他の技術情報

-   **Martin Fowler。CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Greg Young です。CQS vs です。CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Greg Young です。CQRS ドキュメント**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Greg Young です。CQRS、タスク ベースの Ui とイベントのソースとして**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **Udi Dahan です。CQRS が明確にされました**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **イベント ソース (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[前](apply-simplified-microservice-cqrs-ddd-patterns.md) [次へ] (cqrs マイクロ サービス reads.md)

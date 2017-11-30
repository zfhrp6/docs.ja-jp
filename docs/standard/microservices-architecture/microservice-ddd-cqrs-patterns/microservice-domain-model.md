---
title: "マイクロ サービス ドメイン モデルの設計"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |マイクロ サービス ドメイン モデルの設計"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 455a2c5a39fb9b765b557610ab108f8c75882dbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-microservice-domain-model"></a>マイクロ サービス ドメイン モデルの設計

*ビジネス マイクロ サービスまたは範囲指定されたコンテキストごとに 1 つのドメインの機能豊富なモデルを定義します。*

目標は、ビジネスのマイクロ サービスまたは範囲指定されたコンテキスト (BC) ごとに 1 つのまとまりのあるドメイン モデルを作成します。 注意してください、ただしをビジネス継続性やビジネス マイクロ サービスは、いくつかの物理サービスを 1 つのドメイン モデルを共有することもあります合成でした。 ドメイン モデルには、ルール、動作、ビジネスの言語、および範囲指定されたコンテキストの 1 つまたはそれが表すビジネス マイクロ サービスの制約をキャプチャする必要があります。

## <a name="the-domain-entity-pattern"></a>ドメイン エンティティ パターン

エンティティは、ドメイン オブジェクトを表すし、それらを構成する属性だけでなくとその id、継続性、および時間の経過と共に永続化によって、主に定義します。 Eric Evans は、「その id を使用して、主に定義されているオブジェクトと呼ばれますエンティティ。」 エンティティは、モデルの基本クラスであるために、モデルでは、ドメイン、非常に重要です。 そのため、特定し、それらを慎重に設計する必要があります。

*エンティティの id には、複数の microservices または範囲指定されたコンテキストを通過できます。*

同じ id (ただし、同じエンティティではなく) 複数の境界を付けられたコンテキストまたは microservices モデル化することができます。 ただし、ことを意味しません属性とロジックが同じで、同じエンティティが複数の境界を付けられたコンテキストで実装することです。 代わりに、各範囲指定されたコンテキスト内のエンティティは、その属性とその範囲指定されたコンテキストのドメイン内に必要な動作を制限します。

たとえば、buyer エンティティには、ほとんどで、プロファイルまたは identity マイクロ サービス、id を含むユーザー エンティティで定義されているユーザーの属性の場合があります。 順序付けのマイクロ サービスの購入者エンティティ可能性がありますより少ない属性は、購入者が特定のデータだけが注文処理に関連するためです。 各マイクロ サービスのコンテキストまたは範囲指定されたコンテキストは、そのドメイン モデルに影響します。

*ドメイン エンティティがデータの属性を実装するだけでなく動作を実装する必要があります。*

DDD 内のドメイン エンティティには、ドメイン ロジックまたはエンティティのデータ (メモリ内でアクセス オブジェクト) に関連する動作を実装する必要があります。 たとえば、order エンティティ クラスの一部として、ビジネス ロジックと発注品目、データの検証、および合計の計算の追加などのタスクのメソッドとして実装されている操作が必要です。 エンティティのメソッドの不変性とアプリケーション層にまたがるようにそれらのルールではなく、エンティティのルールように注意します。

図 9-8 は、だけでなくデータの属性が、操作、または関連ドメイン ロジックを持つメソッドを実装しているドメイン エンティティを示しています。

![](./media/image9.png)

**図 9-8**です。 データと動作を実装するドメイン エンティティの設計の例

もちろん、場合によってことができますをエンティティ クラスの一部として、任意のロジックを実装しないエンティティ。 集計内の子エンティティで集計ルートにほとんどのロジックが定義されているために、子エンティティが、特別なロジックを持っていない場合に発生します。 ドメイン エンティティでの代わりに、サービス クラスに実装されるロジックの多くのある複雑なマイクロ サービスがあれば、anemic ドメイン モデルで、次のセクションで説明する辿る可能性があります。

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Anemic ドメイン モデルと豊富なドメイン モデル

記事は[AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html)、Martin ファウラーが anemic ドメイン モデルをこの方法について説明します。

Anemic ドメイン モデルの基本的な現象は、ある一見よう実際の作業です。 オブジェクトがある、ドメイン領域で、名詞にちなんだ名前多くおよび実際のドメイン モデルの構造と豊富なリレーションシップでこれらのオブジェクトが接続されています。 Catch はの動作を確認してすることに注意して、これらのオブジェクトにほとんどすべての動作が存在する get アクセス操作子および set アクセス操作子のバッグより若干となります。

もちろん、anemic ドメイン モデルを使用するときにそれらのデータ モデルはから使用するサービス オブジェクトのセット (従来の名前付き、*ビジネス層*) すべてのドメインまたはビジネス ロジックをキャプチャします。 ビジネス層では、データ モデルの上に装備し、データと同様に、データ モデルを使用します。

Anemic ドメイン モデルは、手続き型の設計のみです。 Anemic エンティティ オブジェクトは、動作 (メソッド) が不足しているので、実際のオブジェクトではできません。 データのプロパティのみ保持あり、したがっていないオブジェクト指向デザインします。 アウト サービス オブジェクト (ビジネス層) に、すべての動作を記述することによって、最終的に[整然としたプログラム](https://en.wikipedia.org/wiki/Spaghetti_code)または[トランザクション スクリプト](https://martinfowler.com/eaaCatalog/transactionScript.html)利点を紛失したため、ドメイン モデル提供します。

マイクロ サービスまたは範囲指定されたコンテキストが非常に単純な場合に関係なく (CRUD サービス)、データのプロパティだけを持つエンティティ オブジェクトの形式で anemic ドメイン モデルが十分でありますおよび DDD のより複雑なパターンを実装する価値があるできない可能性があります。 その場合は、ことが永続化モデルでは単に、CRUD 用のデータのみを使用、エンティティを意図的に作成したためです。

Microservices アーキテクチャは、各範囲指定されたコンテキストに応じて複数のアーキテクチャのアプローチに最適なためにです。 たとえば、eShopOnContainers で順序マイクロ サービス DDD パターンを実装するが、単純な CRUD サービスである、カタログ マイクロ サービスはしません。

一部のユーザーは、anemic ドメイン モデルがアンチ パターンであるとします。 実際に実装する新機能によって異なります。 場合は、マイクロ サービスを作成する単純なのに十分な (たとえば、CRUD サービス)、次のアンチ パターンではない anemic ドメイン モデル。 ただし、絶えず変化するビジネス ルールの多くをあるマイクロ サービスのドメインの複雑さに取り組む必要がある場合、anemic ドメイン モデルにはそのマイクロ サービスまたは範囲指定されたコンテキストのアンチ パターン可能性があります。 その場合は、リッチとして設計することに加えて、動作のデータを格納しているだけでなく (集計、値オブジェクトなど)、追加の DDD パターンを実装するエンティティとモデルがこのようなマイクロ サービスの長期的な成功の大きなメリットを必要があります。

#### <a name="additional-resources"></a>その他の技術情報

-   **DevIQ です。ドメイン エンティティ**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Martin Fowler。ドメイン モデル**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler。Anemic ドメイン モデル**

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>値オブジェクトのパターン

前述の Eric Evans が、"多数のオブジェクト id が使用されない概念です。 これらのオブジェクトについて説明するものの特定の特性。"

エンティティには、id が必要ですが、そうでない、システムにある多くのオブジェクトが、値オブジェクトのパターンと同様にします。 オブジェクトの値は、ドメインの側面を説明する概念ありません id を持つオブジェクトです。 これらは一時的にのみ関係するデザイン要素を表すインスタンス化するオブジェクトです。 関心のある*何*が*した*はします。 例では、数値や文字列が含まれますが、属性のグループなどの上位レベルの概念をすることもできます。

マイクロ サービス内のエンティティのあるものがあります別マイクロ サービス内のエンティティのため、範囲指定されたコンテキスト 2 番目のケースで異なる意味がある可能性。 たとえば、電子商取引アプリケーション内のアドレスがないこと id、個人または会社の顧客のプロファイルの属性のグループを表すことがのみため。 ここでは、アドレスは、値のオブジェクトとして分類される必要があります。 ただし、電力ユーティリティ会社のアプリケーションで顧客の住所をビジネス ドメインあまり重要ででした。 そのため、課金システムは、アドレスに直接リンクできるように、アドレスは、id が必要です。 その場合は、アドレスは、ドメイン エンティティとして分類する必要があります。

名前と姓を持つユーザーは、エンティティ、通常はであるため、ユーザー id を場合でも、姓と名前が別の一連の値と一致場合などそれらの名前を指すことも、別の担当者です。

値オブジェクトはドキュメントで指向データベースを実装して使用し、見やすくリレーショナル データベースと EF などの Orm の管理が困難です。

#### <a name="additional-resources"></a>その他の技術情報

-   **Martin Fowler。値オブジェクト パターン**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **オブジェクトの値**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **テスト駆動型開発内のオブジェクトを値**
    [*https://leanpub.com/tdd-ebook/read\#leanpub 自動値オブジェクト*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Eric Evans。ドメインに基づく設計: は Tackling Complexity in the Heart of Software です。** (予約値オブジェクトの説明を含む)。[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>集計パターン

ドメイン モデルには、さまざまなデータ エンティティと順序フルフィルメントまたはインベントリなどの機能の重要な領域が制御できるプロセスのクラスターが含まれています。 細かい DDD ユニットがあるか、集計は、クラスターまたはグループのエンティティと、まとまりの単位として処理される動作について説明します。

通常、必要なトランザクションに基づく集計を定義します。 典型的な例は、発注品目の一覧が含まれている順序です。 発注品目をエンティティと通常されます。 集計ルートと通常呼ばれる、そのルート エンティティとして、order エンティティを含むも順序集計内の子エンティティになります。

集計を識別するは難しくなります。 集計とは同時に、一致する必要があるオブジェクトのグループが同じオブジェクトのグループを選択し、集計関数をラベルをことはできません。 ドメインの概念で開始し、その概念に関連する最も一般的なトランザクションで使用されているエンティティについて検討する必要があります。 トランザクション全体で一貫性を保つ必要があるこれらのエンティティは、どのようなフォームの集計です。 トランザクション操作についての考え方は、集計を識別する最善の方法でが考えられます。

### <a name="the-aggregate-root-or-root-entity-pattern"></a>集計ルートまたはルート エンティティ パターン

集計は、少なくとも 1 つのエンティティで構成されます。 集計ルート、ルート エンティティまたはプライマリ ientity とも呼ばれます。 さらに、複数の子エンティティおよび値オブジェクトのすべてのエンティティと連携して必要な動作とトランザクションを実装するオブジェクトをこともできます。

集計ルートの目的は、集計; の一貫性を確保するには集計のメソッドを使用する更新プログラムの唯一のエントリ ポイントである必要があります。 または集計のルート クラスを操作します。 集計のルートでのみ、集計内のエンティティに変更をする必要があります。 集約の整合性ガーディアン、すべての不変性と、集計に遵守する必要がありますの一貫性規則を考慮することをお勧めします。 子エンティティまたは値オブジェクトを個別に変更した場合集計ルートは、集計が有効な状態であることを確認できません。 厳密でない区間を含むテーブルのようになります。 管理の一貫性は、集計のルートの主な目的です。

図 9-9、buyer の集計、1 つのエンティティ (集計ルート購入者) が含まれるようにサンプルの集計を表示できます。 順序の集計には、複数のエンティティとオブジェクトの値が含まれています。

![](./media/image10.png)

**図 9-9**です。 複数の集計の例を 1 つのエンティティ

EShopOnContainers 参照アプリケーションの順序付けマイクロ サービスでは、購入者の集計が領域によっては、追加の子エンティティ可能性があることに注意してください。 図 9-9 では、購入者が、集計のルートのみを含む集計の例として、単一のエンティティがである場合のみ示しています。

集計の分離を維持し、それらの間に明確な境界を維持するには DDD ドメイン モデルで集計およびのみが外部キー (FK) フィールド間のナビゲーションを直接が行われないように実装されていることをお勧め、 [マイクロ サービス ドメイン モデルを順序付け](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)eShopOnContainers にします。 次のコードに示すように、Order エンティティには、購入者ではない、EF 中核となるナビゲーション プロパティの FK フィールドのみがあります。

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
}
```

識別して、集計の操作には、研究と経験が必要です。 詳細については、次の他のリソースの一覧を参照してください。

#### <a name="additional-resources"></a>その他の技術情報

-   **Vaughn Vernon。効果的な集計のデザイン - パート i: 1 つの集計のモデリング**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_コミュニティ\_エッセイ\_集計\_一部\_1. pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon。効果的な集計デザインのパート II: 行う集計連携**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf>*

-   **Vaughn Vernon。効果的な集計デザインのパート III: 検出で洞察の獲得**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf>*

-   **Sergey Grybniak です。DDD 戦術的なデザイン パターン**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Chris Richardson です。集計を使用してトランザクション Microservices の開発**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ です。集計パターン**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[前](ddd-指向-microservice.md) [次へ] (net-コア-マイクロ サービスのドメイン-model.md)

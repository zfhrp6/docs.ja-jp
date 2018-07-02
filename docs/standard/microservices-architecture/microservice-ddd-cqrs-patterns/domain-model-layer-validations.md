---
title: ドメイン モデル レイヤーでの検証の設計
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | ドメイン モデル レイヤーでの検証の設計
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c071d269977ccecea9a7d4d79da78d7967bb1618
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105736"
---
# <a name="designing-validations-in-the-domain-model-layer"></a>ドメイン モデル レイヤーでの検証の設計

DDD では、検証規則はインバリアントとして考えることができます。 集計の主な役割は、その集計内のすべてのエンティティの状態の変更にわたってインバリアントを強制することです。

ドメイン エンティティは、常に有効なエンティティである必要があります。 常に true にする必要のあるオブジェクトには、特定のインバリアント数があります。 たとえば、order item オブジェクトは、正の整数である必要がある数量と、アーティクル名および価格を常に持っている必要があります。 そのため、インバリアントの強制は、(特に集計ルートの) ドメイン エンティティの役目となり、エンティティ オブジェクトは有効になっていない限り存在できません。 インバリアント ルールは、コントラクトとして単純に表され、違反があった場合には例外または通知が発生します。

この背後にある理由は、オブジェクトがなってはならない状態にあるため、多くのバグが発生するからです。 [オンライン ディスカッション](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/)での Greg Young による適切な説明を次に示します。

UserProfile を受け取る SendUserCreationEmailService があるとします。Name が null でないそのサービスでどのように合理化できるでしょうか。 再度チェックしますか。 多くの場合、わざわざチェックなどせずに、他の誰かが検証してから自分に送信してくれる "最善の結果を期待" しているのではないでしょうか。 もちろん、記述すべき最初のテストのうちの 1 つである TDD を使用すると、null 名を持つ顧客を送信した場合に、エラーが発生します。 しかし、この種のテストを繰り返し記述しているうちに、"名前が null になることを許可しなかったら、これらのテストのすべては必要ないのではないか" ということに気が付きました。

## <a name="implementing-validations-in-the-domain-model-layer"></a>ドメイン モデル レイヤーでの検証の実装

検証は通常、ドメイン エンティティ コンストラクター内、またはエンティティを更新できるメソッドに実装されます。 検証を実装するには、データを検証し、検証が失敗した場合に例外を発生させるといった、複数の方法があります。 検証に使用する仕様パターンや、例外が発生すると、検証ごとに例外を返すのではなく、エラーのコレクションを返す通知パターンのような、より高度なパターンもあります。

### <a name="validating-conditions-and-throwing-exceptions"></a>条件を検証して例外をスローする

次のコード例は、例外を発生させることによってドメイン エンティティで検証するための最も簡単な方法を示しています。 このセクションの最後にある参照テーブルには、前述したパターンに基づくより高度な実装へのリンクがあります。

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

さらによい例は、内部状態が変わっていないか、メソッドのすべての変更が発生したことを確認する必要を示すものでしょう。 たとえば、次の実装では、オブジェクトが無効な状態のままになります。

```csharp
public void SetAddress(string line1, string line2,
    string city, string state, int zip)
{
    _shipingAddress.line1 = line1 ?? throw new ...
    _shippingAddress.line2 = line2;
    _shippingAddress.city = city ?? throw new ...
    _shippingAddress.state = (IsValid(state) ? state : throw new …);
}
```

状態の値が無効な場合は、address の最初の行と city が既に変更されています。 address が無効になる可能性があります。

同様の方法は、エンティティのコンストラクターで、エンティティの作成後、例外を発生させてそのエンティティが有効であることを確認するために使用できます。

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>データ注釈に基づいてモデルで検証属性を使用する

別の方法は、データ注釈に基づいて検証属性を使用することです。 検証属性はモデルの検証を構成する方法を提供します。この方法は、概念的にはデータベース テーブルでのフィールドの検証に似ています。 これには、データ型の割り当てや必須フィールドなどの制約が含まれます。 その他の種類の検証としては、クレジット カード番号、電話番号、メール アドレスなど、ビジネス ルールを強制するためのデータへのパターンの適用があります。 検証属性は、要件の強制を容易にします。

ただし、次のコードに示すように、この方法は、MVC コントローラーから呼び出す必要がある Microsoft.AspNetCore.Mvc.ModelState から ModelState.IsValid に対する依存関係を取得するため、非常に煩わしい場合があります。 モデル検証は各コントローラー アクションが呼び出される前に行われます。ModelState.IsValid 呼び出しの結果を検査し、適切に対処するのはコントローラー メソッドの役割です。 これを使用するかどうかは、モデルをそのインフラストラクチャとどの程度緊密に結合させるかによります。

```csharp
using System.ComponentModel.DataAnnotations;
// Other using statements ...
// Entity is a custom base class which has the ID
public class Product : Entity
{
    [Required]
    [StringLength(100)]
    public string Title { get; private set; }

    [Required]
    [Range(0, 999.99)]
    public decimal Price { get; private set; }

    [Required]
    [VintageProduct(1970)]
    [DataType(DataType.Date)]
    public DateTime ReleaseDate { get; private set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; private set; }

    // Constructor...
    // Additional methods for entity logic and constructor...
}
```

ただし、DDD の観点から、ドメイン モデルはエンティティの動作メソッド内の例外を使用して、または検証規則を強制する仕様パターンと通知パターンを実装することで、リーンに保つことをお勧めします。 ASP.NET Core でのデータ注釈のような検証フレームワーク、または FluentValidation のようなその他の検証フレームワークには、アプリケーション フレームワークを呼び出すための要件があります。 たとえば、データ注釈で ModelState.IsValid メソッドを呼び出す場合、ASP.NET コントローラーを起動する必要があります。

UI 層内でモデルの検証を許可するために、入力を受け取る ViewModel クラス内 (ドメイン エンティティではなく) のアプリケーション層でデータ注釈を使用するのは合理的です。 ただし、ドメイン モデル内での検証の実行時にはこれを行わないでください。

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>仕様パターンと通知パターンを実装することでエンティティを検証する

最後に、ドメイン モデルで検証を実装するより複雑な方法は、後述するその他の技術情報の一部で説明されているように、仕様パターンと通知パターンを組み合わせて実装することです。

これらのパターンの 1 つだけを使用することもできます。たとえば、コントロール ステートメントを使用して手動で検証していますが、検証エラーの一覧をスタックして返すには通知パターンを使用します。

### <a name="using-deferred-validation-in-the-domain"></a>ドメインで遅延検証を使用する

ドメインで遅延検証に対処するには、さまざまな方法があります。 Vaughn Vernon 氏は自身の著書『[Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)』で、検証に関するセクションでこれらについて説明しています。

### <a name="two-step-validation"></a>2 段階検証

2 段階検証も検討してください。 データ転送オブジェクト (DTO) コマンドにはフィールド レベルの検証を使用し、エンティティ内にはドメイン レベルの検証を使用します。 検証エラーを処理しやすくするために、例外の代わりに結果オブジェクトを返すことで、これを行うことができます。

たとえば、データ注釈を使用したフィールドの検証を使用している場合、検証定義を複製しないでください。 ただし、DTO の場合、実行はサーバー側とクライアント側の両方で可能です (たとえば、コマンドと ViewModels)。

## <a name="additional-resources"></a>その他の技術情報

-   **Rachel Appel。ASP.NET Core MVC でのモデル検証の概要**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler。検証で例外のスローを通知に置き換える**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **仕様と通知のパターン**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **Lev Gorodinski。ドメイン駆動設計 (DDD) での検証**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin Jack。ドメイン モデルの検証**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard。DDD 世界での検証**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[前へ](enumeration-classes-over-enum-types.md)
[次へ](client-side-validation.md)

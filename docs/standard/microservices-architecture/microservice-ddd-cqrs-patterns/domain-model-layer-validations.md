---
title: "ドメイン モデル レイヤーでの検証の設計"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |ドメイン モデル レイヤーでの検証の設計"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f4870d0568c3539f296bcb3f577291cb0250cfca
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="designing-validations-in-the-domain-model-layer"></a>ドメイン モデル レイヤーでの検証の設計

DDD では、検証規則は不変式として考えられます。 集計の主な役割は、その集計内のすべてのエンティティの状態の変更の間での不変部分を強制します。

ドメイン エンティティでは、有効なエンティティを常にある必要があります。 不変式は true。 常にする必要のあるオブジェクトの数があります。 たとえば、注文項目オブジェクトは常に価格および正の整数、およびアーティクル名にする必要がある数量を持ちます。 そのため、不変の強制が (特に、集計ルート) のドメイン エンティティの責任において、およびエンティティ オブジェクトが有効でなくて存在すべきです。 例外または通知は、違反が発生したときに発生してインバリアント ルールは、コントラクト、として表わされる単にします。

この理由は、オブジェクトにされている必要がありますしない状態であるために、多くのバグが発生することです。 Greg Young から適切な説明を次に示します、[オンライン ディスカッション](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):

受け取る、UserProfile... 方法できますお合理化名が null でないサービス SendUserCreationEmailService があるようになりましたみましょう提案ですか。 再度チェックしますか。 可能性の高い、または... をだけをやめるを確認し、「最適なことを願って」— をユーザーが示されていないことを送信する前に検証することを期待します。 もちろんです。 null の名前を持つ顧客を送信するエラーを発生させます。 おを記述する必要があります最初のテストのいずれかの TDD を使用しています。 しかし、ことに注意してこれらのテストを繰り返し記述を開始しました。"になる名前を許可するされない場合に待機する null お必要はありませんこれらすべてのテスト"

## <a name="implementing-validations-in-the-domain-model-layer"></a>ドメイン モデル レイヤーでの検証の実装

ドメイン エンティティのコンス トラクター内、またはエンティティを更新するメソッドで、通常は検証を実装します。 検証中のデータ検証に失敗した場合、発生の例外など、検証を実装する複数の方法はあります。 検証において、仕様パターンを使用するなどのより高度なパターンおよび発生している各検証に対して例外を返す代わりにエラーのコレクションを取得する通知パターンもあります。

### <a name="validating-conditions-and-throwing-exceptions"></a>条件を検証して、例外のスロー

次のコード例では、例外を発生させることによってドメイン エンティティで検証する簡単な方法を示します。 このセクションの最後に参照テーブルでは、既に説明したパターンに基づいたより高度な実装へのリンクを表示できます。

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

さらに良い例は、内部のいずれかの状態が変更されないこと、またはメソッドのすべての変更が発生したことを確認する必要を示しています。 たとえば、次の実装は状態のままにオブジェクトが無効です。

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

状態の値が有効である場合は、アドレスの最初の行と市区町村既に変更されました。 可能性があります、アドレスが無効になります。

作成後、エンティティが有効であるかどうかを確認する例外を発生させるエンティティのコンス トラクターでは、同様のアプローチを使用できます。

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a>データの注釈に基づき、モデルの検証属性の使用

別の方法では、データの注釈に基づく検証属性を使用します。 検証属性は、データベース テーブル内のフィールドの検証に概念的に似ていますが、モデルの検証を構成する方法を提供します。 これには、データ型または必要なフィールドの割り当てなどの制約が含まれます。 その他の種類の検証は、含めるクレジット_カード番号、電話番号など、ビジネス ルールを適用するデータにパターンを適用するまたは電子メール アドレス。 検証属性しやすいようにの要件を強制します。

ただし、次のコードに示すように、この方法があります DDD モデルでも関与するレベル、MVC コント ローラーから呼び出す必要があります Microsoft.AspNetCore.Mvc.ModelState から ModelState.IsValid で依存関係がかかるためです。 モデルの検証が呼び出される、各コント ローラー アクションの前に発生して、呼び出し ModelState.IsValid の結果を検査し、適切に対応するコント ローラーのメソッドの責任です。 これを使用するかは、方法によって異なります。 その基盤となるモデルを密に結合します。

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

ただし、DDD の観点から、ドメイン モデルは最適な保持例外の使用にリーン メソッドでは、エンティティの動作、または検証規則を適用する仕様と通知のパターンを実装することによってされます。 ASP.NET Core でのデータの注釈と同様に、検証フレームワークまたは FluentValidation と同様に他の検証フレームワークは、アプリケーション フレームワークを呼び出すための要件を実行します。 たとえば、データ注釈で ModelState.IsValid メソッドを呼び出すときに、ASP.NET コント ローラーを起動する必要があります。

UI レイヤー内でモデルの検証に使用できるように、入力を受け付ける (ドメイン エンティティ) ではなく ViewModel クラス内のアプリケーション層にデータ注釈を使用してその合理的ことができます。 ただし、必要がありますいないこれで、ドメイン モデル内での検証の除外です。

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a>仕様パターンと通知のパターンを実装することでエンティティを検証します。

最後に、ドメイン モデルで検証を実装するより複雑な方法は、後半に示すその他のリソースの一部で説明するよう通知パターンと組み合わせて仕様パターンを実装することによってです。

使用することできますもこれらのパターンの 1 つに留意 — たとえば、コントロール ステートメントに、手動で検証していますが、通知パターンを使用してスタックが作成され、検証エラーの一覧を返します。

### <a name="using-deferred-validation-in-the-domain"></a>ドメインの遅延検証の使用

ドメインの検証が遅延に対処するさまざまな方法はあります。 著書で[Implementing Domain-Driven デザイン](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)、Vaughn カバーはこれらのセクションでの検証をについて説明します。

### <a name="two-step-validation"></a>2 段階の検証

2 段階の検証も検討してください。 コマンドのデータ転送オブジェクト (Dto) と、エンティティ内のドメイン レベルの検証でフィールド レベルの検証を使用します。 オブジェクトを取得して、結果代わりに例外により、検証エラーを処理しやすくするために、これを行うことができます。

データ注釈を使用したフィールドの検証を使用して、たとえば、する重複しない検証定義します。 サーバー側とクライアント側 dtos の使用の場合の両方に、実行が、指定できます (コマンドと ViewModels のインスタンス)。

## <a name="additional-resources"></a>その他の技術情報

-   **Rachel Appel です。ASP.NET Core MVC でのモデル検証の概要**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)

-   **Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

-   **Martin Fowler。検証時に通知するメッセージの例外のスローを置き換える**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)

-   **仕様と通知パターン**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)

-   **レフ Gorodinski です。ドメイン ベースのデザイン (DDD) での検証**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)

-   **Colin ジャックです。ドメイン モデルの検証**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)

-   **Jimmy Bogard。DDD 世界での検証**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)


>[!div class="step-by-step"]
[前](列挙型のクラス-over-enum-types.md) [次へ] (クライアント側 validation.md)

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
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="966bb-104">ドメイン モデル レイヤーでの検証の設計</span><span class="sxs-lookup"><span data-stu-id="966bb-104">Designing validations in the domain model layer</span></span>

<span data-ttu-id="966bb-105">DDD では、検証規則は不変式として考えられます。</span><span class="sxs-lookup"><span data-stu-id="966bb-105">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="966bb-106">集計の主な役割は、その集計内のすべてのエンティティの状態の変更の間での不変部分を強制します。</span><span class="sxs-lookup"><span data-stu-id="966bb-106">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="966bb-107">ドメイン エンティティでは、有効なエンティティを常にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="966bb-107">Domain entities should always be valid entities.</span></span> <span data-ttu-id="966bb-108">不変式は true。 常にする必要のあるオブジェクトの数があります。</span><span class="sxs-lookup"><span data-stu-id="966bb-108">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="966bb-109">たとえば、注文項目オブジェクトは常に価格および正の整数、およびアーティクル名にする必要がある数量を持ちます。</span><span class="sxs-lookup"><span data-stu-id="966bb-109">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="966bb-110">そのため、不変の強制が (特に、集計ルート) のドメイン エンティティの責任において、およびエンティティ オブジェクトが有効でなくて存在すべきです。</span><span class="sxs-lookup"><span data-stu-id="966bb-110">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="966bb-111">例外または通知は、違反が発生したときに発生してインバリアント ルールは、コントラクト、として表わされる単にします。</span><span class="sxs-lookup"><span data-stu-id="966bb-111">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="966bb-112">この理由は、オブジェクトにされている必要がありますしない状態であるために、多くのバグが発生することです。</span><span class="sxs-lookup"><span data-stu-id="966bb-112">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="966bb-113">Greg Young から適切な説明を次に示します、[オンライン ディスカッション](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span><span class="sxs-lookup"><span data-stu-id="966bb-113">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="966bb-114">受け取る、UserProfile... 方法できますお合理化名が null でないサービス SendUserCreationEmailService があるようになりましたみましょう提案ですか。</span><span class="sxs-lookup"><span data-stu-id="966bb-114">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="966bb-115">再度チェックしますか。</span><span class="sxs-lookup"><span data-stu-id="966bb-115">Do we check it again?</span></span> <span data-ttu-id="966bb-116">可能性の高い、または... をだけをやめるを確認し、「最適なことを願って」— をユーザーが示されていないことを送信する前に検証することを期待します。</span><span class="sxs-lookup"><span data-stu-id="966bb-116">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="966bb-117">もちろんです。 null の名前を持つ顧客を送信するエラーを発生させます。 おを記述する必要があります最初のテストのいずれかの TDD を使用しています。</span><span class="sxs-lookup"><span data-stu-id="966bb-117">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="966bb-118">しかし、ことに注意してこれらのテストを繰り返し記述を開始しました。"になる名前を許可するされない場合に待機する null お必要はありませんこれらすべてのテスト"</span><span class="sxs-lookup"><span data-stu-id="966bb-118">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="966bb-119">ドメイン モデル レイヤーでの検証の実装</span><span class="sxs-lookup"><span data-stu-id="966bb-119">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="966bb-120">ドメイン エンティティのコンス トラクター内、またはエンティティを更新するメソッドで、通常は検証を実装します。</span><span class="sxs-lookup"><span data-stu-id="966bb-120">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="966bb-121">検証中のデータ検証に失敗した場合、発生の例外など、検証を実装する複数の方法はあります。</span><span class="sxs-lookup"><span data-stu-id="966bb-121">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="966bb-122">検証において、仕様パターンを使用するなどのより高度なパターンおよび発生している各検証に対して例外を返す代わりにエラーのコレクションを取得する通知パターンもあります。</span><span class="sxs-lookup"><span data-stu-id="966bb-122">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="966bb-123">条件を検証して、例外のスロー</span><span class="sxs-lookup"><span data-stu-id="966bb-123">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="966bb-124">次のコード例では、例外を発生させることによってドメイン エンティティで検証する簡単な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="966bb-124">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="966bb-125">このセクションの最後に参照テーブルでは、既に説明したパターンに基づいたより高度な実装へのリンクを表示できます。</span><span class="sxs-lookup"><span data-stu-id="966bb-125">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="966bb-126">さらに良い例は、内部のいずれかの状態が変更されないこと、またはメソッドのすべての変更が発生したことを確認する必要を示しています。</span><span class="sxs-lookup"><span data-stu-id="966bb-126">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="966bb-127">たとえば、次の実装は状態のままにオブジェクトが無効です。</span><span class="sxs-lookup"><span data-stu-id="966bb-127">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="966bb-128">状態の値が有効である場合は、アドレスの最初の行と市区町村既に変更されました。</span><span class="sxs-lookup"><span data-stu-id="966bb-128">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="966bb-129">可能性があります、アドレスが無効になります。</span><span class="sxs-lookup"><span data-stu-id="966bb-129">That might make the address invalid.</span></span>

<span data-ttu-id="966bb-130">作成後、エンティティが有効であるかどうかを確認する例外を発生させるエンティティのコンス トラクターでは、同様のアプローチを使用できます。</span><span class="sxs-lookup"><span data-stu-id="966bb-130">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="966bb-131">データの注釈に基づき、モデルの検証属性の使用</span><span class="sxs-lookup"><span data-stu-id="966bb-131">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="966bb-132">別の方法では、データの注釈に基づく検証属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="966bb-132">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="966bb-133">検証属性は、データベース テーブル内のフィールドの検証に概念的に似ていますが、モデルの検証を構成する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="966bb-133">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="966bb-134">これには、データ型または必要なフィールドの割り当てなどの制約が含まれます。</span><span class="sxs-lookup"><span data-stu-id="966bb-134">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="966bb-135">その他の種類の検証は、含めるクレジット_カード番号、電話番号など、ビジネス ルールを適用するデータにパターンを適用するまたは電子メール アドレス。</span><span class="sxs-lookup"><span data-stu-id="966bb-135">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="966bb-136">検証属性しやすいようにの要件を強制します。</span><span class="sxs-lookup"><span data-stu-id="966bb-136">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="966bb-137">ただし、次のコードに示すように、この方法があります DDD モデルでも関与するレベル、MVC コント ローラーから呼び出す必要があります Microsoft.AspNetCore.Mvc.ModelState から ModelState.IsValid で依存関係がかかるためです。</span><span class="sxs-lookup"><span data-stu-id="966bb-137">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="966bb-138">モデルの検証が呼び出される、各コント ローラー アクションの前に発生して、呼び出し ModelState.IsValid の結果を検査し、適切に対応するコント ローラーのメソッドの責任です。</span><span class="sxs-lookup"><span data-stu-id="966bb-138">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="966bb-139">これを使用するかは、方法によって異なります。 その基盤となるモデルを密に結合します。</span><span class="sxs-lookup"><span data-stu-id="966bb-139">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="966bb-140">ただし、DDD の観点から、ドメイン モデルは最適な保持例外の使用にリーン メソッドでは、エンティティの動作、または検証規則を適用する仕様と通知のパターンを実装することによってされます。</span><span class="sxs-lookup"><span data-stu-id="966bb-140">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="966bb-141">ASP.NET Core でのデータの注釈と同様に、検証フレームワークまたは FluentValidation と同様に他の検証フレームワークは、アプリケーション フレームワークを呼び出すための要件を実行します。</span><span class="sxs-lookup"><span data-stu-id="966bb-141">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="966bb-142">たとえば、データ注釈で ModelState.IsValid メソッドを呼び出すときに、ASP.NET コント ローラーを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="966bb-142">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="966bb-143">UI レイヤー内でモデルの検証に使用できるように、入力を受け付ける (ドメイン エンティティ) ではなく ViewModel クラス内のアプリケーション層にデータ注釈を使用してその合理的ことができます。</span><span class="sxs-lookup"><span data-stu-id="966bb-143">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="966bb-144">ただし、必要がありますいないこれで、ドメイン モデル内での検証の除外です。</span><span class="sxs-lookup"><span data-stu-id="966bb-144">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="966bb-145">仕様パターンと通知のパターンを実装することでエンティティを検証します。</span><span class="sxs-lookup"><span data-stu-id="966bb-145">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="966bb-146">最後に、ドメイン モデルで検証を実装するより複雑な方法は、後半に示すその他のリソースの一部で説明するよう通知パターンと組み合わせて仕様パターンを実装することによってです。</span><span class="sxs-lookup"><span data-stu-id="966bb-146">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="966bb-147">使用することできますもこれらのパターンの 1 つに留意 — たとえば、コントロール ステートメントに、手動で検証していますが、通知パターンを使用してスタックが作成され、検証エラーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="966bb-147">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="966bb-148">ドメインの遅延検証の使用</span><span class="sxs-lookup"><span data-stu-id="966bb-148">Using deferred validation in the domain</span></span>

<span data-ttu-id="966bb-149">ドメインの検証が遅延に対処するさまざまな方法はあります。</span><span class="sxs-lookup"><span data-stu-id="966bb-149">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="966bb-150">著書で[Implementing Domain-Driven デザイン](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)、Vaughn カバーはこれらのセクションでの検証をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="966bb-150">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="966bb-151">2 段階の検証</span><span class="sxs-lookup"><span data-stu-id="966bb-151">Two-step validation</span></span>

<span data-ttu-id="966bb-152">2 段階の検証も検討してください。</span><span class="sxs-lookup"><span data-stu-id="966bb-152">Also consider two-step validation.</span></span> <span data-ttu-id="966bb-153">コマンドのデータ転送オブジェクト (Dto) と、エンティティ内のドメイン レベルの検証でフィールド レベルの検証を使用します。</span><span class="sxs-lookup"><span data-stu-id="966bb-153">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="966bb-154">オブジェクトを取得して、結果代わりに例外により、検証エラーを処理しやすくするために、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="966bb-154">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="966bb-155">データ注釈を使用したフィールドの検証を使用して、たとえば、する重複しない検証定義します。</span><span class="sxs-lookup"><span data-stu-id="966bb-155">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="966bb-156">サーバー側とクライアント側 dtos の使用の場合の両方に、実行が、指定できます (コマンドと ViewModels のインスタンス)。</span><span class="sxs-lookup"><span data-stu-id="966bb-156">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="966bb-157">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="966bb-157">Additional resources</span></span>

-   <span data-ttu-id="966bb-158">**Rachel Appel です。ASP.NET Core MVC でのモデル検証の概要**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="966bb-158">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="966bb-159">**Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="966bb-159">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="966bb-160">**Martin Fowler。検証時に通知するメッセージの例外のスローを置き換える**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="966bb-160">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="966bb-161">**仕様と通知パターン**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="966bb-161">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="966bb-162">**レフ Gorodinski です。ドメイン ベースのデザイン (DDD) での検証**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="966bb-162">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="966bb-163">**Colin ジャックです。ドメイン モデルの検証**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="966bb-163">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="966bb-164">**Jimmy Bogard。DDD 世界での検証**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="966bb-164">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="966bb-165">[前](列挙型のクラス-over-enum-types.md) [次へ] (クライアント側 validation.md)</span><span class="sxs-lookup"><span data-stu-id="966bb-165">[Previous] (enumeration-classes-over-enum-types.md) [Next] (client-side-validation.md)</span></span>

---
title: ドメイン モデル レイヤーでの検証の設計
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | ドメイン モデル レイヤーでの検証の設計
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce3cb0c79cbd492224ce1d4ecb25cd02062f11cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="designing-validations-in-the-domain-model-layer"></a><span data-ttu-id="74ff0-103">ドメイン モデル レイヤーでの検証の設計</span><span class="sxs-lookup"><span data-stu-id="74ff0-103">Designing validations in the domain model layer</span></span>

<span data-ttu-id="74ff0-104">DDD では、検証規則はインバリアントとして考えることができます。</span><span class="sxs-lookup"><span data-stu-id="74ff0-104">In DDD, validation rules can be thought as invariants.</span></span> <span data-ttu-id="74ff0-105">集計の主な役割は、その集計内のすべてのエンティティの状態の変更にわたってインバリアントを強制することです。</span><span class="sxs-lookup"><span data-stu-id="74ff0-105">The main responsibility of an aggregate is to enforce invariants across state changes for all the entities within that aggregate.</span></span>

<span data-ttu-id="74ff0-106">ドメイン エンティティは、常に有効なエンティティである必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-106">Domain entities should always be valid entities.</span></span> <span data-ttu-id="74ff0-107">常に true にする必要のあるオブジェクトには、特定のインバリアント数があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-107">There are a certain number of invariants for an object that should always be true.</span></span> <span data-ttu-id="74ff0-108">たとえば、order item オブジェクトは、正の整数である必要がある数量と、アーティクル名および価格を常に持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-108">For example, an order item object always has to have a quantity that must be a positive integer, plus an article name and price.</span></span> <span data-ttu-id="74ff0-109">そのため、インバリアントの強制は、(特に集計ルートの) ドメイン エンティティの役目となり、エンティティ オブジェクトは有効になっていない限り存在できません。</span><span class="sxs-lookup"><span data-stu-id="74ff0-109">Therefore, invariants enforcement is the responsibility of the domain entities (especially of the aggregate root) and an entity object should not be able to exist without being valid.</span></span> <span data-ttu-id="74ff0-110">インバリアント ルールは、コントラクトとして単純に表され、違反があった場合には例外または通知が発生します。</span><span class="sxs-lookup"><span data-stu-id="74ff0-110">Invariant rules are simply expressed as contracts, and exceptions or notifications are raised when they are violated.</span></span>

<span data-ttu-id="74ff0-111">この背後にある理由は、オブジェクトがなってはならない状態にあるため、多くのバグが発生するからです。</span><span class="sxs-lookup"><span data-stu-id="74ff0-111">The reasoning behind this is that many bugs occur because objects are in a state they should never have been in.</span></span> <span data-ttu-id="74ff0-112">[オンライン ディスカッション](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/)での Greg Young による適切な説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="74ff0-112">The following is a good explanation from Greg Young in an [online discussion](http://jeffreypalermo.com/blog/the-fallacy-of-the-always-valid-entity/):</span></span>

<span data-ttu-id="74ff0-113">UserProfile を受け取る SendUserCreationEmailService があるとします。Name が null でないそのサービスでどのように合理化できるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="74ff0-113">Let's propose we now have a SendUserCreationEmailService that takes a UserProfile ... how can we rationalize in that service that Name is not null?</span></span> <span data-ttu-id="74ff0-114">再度チェックしますか。</span><span class="sxs-lookup"><span data-stu-id="74ff0-114">Do we check it again?</span></span> <span data-ttu-id="74ff0-115">多くの場合、わざわざチェックなどせずに、他の誰かが検証してから自分に送信してくれる "最善の結果を期待" しているのではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="74ff0-115">Or more likely ... you just don't bother to check and "hope for the best"—you hope that someone bothered to validate it before sending it to you.</span></span> <span data-ttu-id="74ff0-116">もちろん、記述すべき最初のテストのうちの 1 つである TDD を使用すると、null 名を持つ顧客を送信した場合に、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="74ff0-116">Of course, using TDD one of the first tests we should be writing is that if I send a customer with a null name that it should raise an error.</span></span> <span data-ttu-id="74ff0-117">しかし、この種のテストを繰り返し記述しているうちに、"名前が null になることを許可しなかったら、これらのテストのすべては必要ないのではないか" ということに気が付きました。</span><span class="sxs-lookup"><span data-stu-id="74ff0-117">But once we start writing these kinds of tests over and over again we realize ... "wait if we never allowed name to become null we wouldn't have all of these tests"</span></span>

## <a name="implementing-validations-in-the-domain-model-layer"></a><span data-ttu-id="74ff0-118">ドメイン モデル レイヤーでの検証の実装</span><span class="sxs-lookup"><span data-stu-id="74ff0-118">Implementing validations in the domain model layer</span></span>

<span data-ttu-id="74ff0-119">検証は通常、ドメイン エンティティ コンストラクター内、またはエンティティを更新できるメソッドに実装されます。</span><span class="sxs-lookup"><span data-stu-id="74ff0-119">Validations are usually implemented in domain entity constructors or in methods that can update the entity.</span></span> <span data-ttu-id="74ff0-120">検証を実装するには、データを検証し、検証が失敗した場合に例外を発生させるといった、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-120">There are multiple ways to implement validations, such as verifying data and raising exceptions if the validation fails.</span></span> <span data-ttu-id="74ff0-121">検証に使用する仕様パターンや、例外が発生すると、検証ごとに例外を返すのではなく、エラーのコレクションを返す通知パターンのような、より高度なパターンもあります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-121">There are also more advanced patterns such as using the Specification pattern for validations, and the Notification pattern to return a collection of errors instead of returning an exception for each validation as it occurs.</span></span>

### <a name="validating-conditions-and-throwing-exceptions"></a><span data-ttu-id="74ff0-122">条件を検証して例外をスローする</span><span class="sxs-lookup"><span data-stu-id="74ff0-122">Validating conditions and throwing exceptions</span></span>

<span data-ttu-id="74ff0-123">次のコード例は、例外を発生させることによってドメイン エンティティで検証するための最も簡単な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="74ff0-123">The following code example shows the simplest approach to validation in a domain entity by raising an exception.</span></span> <span data-ttu-id="74ff0-124">このセクションの最後にある参照テーブルには、前述したパターンに基づくより高度な実装へのリンクがあります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-124">In the references table at the end of this section you can see links to more advanced implementations based on the patterns we have discussed previously.</span></span>

```csharp
public void SetAddress(Address address)
{
    _shippingAddress = address?? throw new ArgumentNullException(nameof(address));
}
```

<span data-ttu-id="74ff0-125">さらによい例は、内部状態が変わっていないか、メソッドのすべての変更が発生したことを確認する必要を示すものでしょう。</span><span class="sxs-lookup"><span data-stu-id="74ff0-125">A better example would demonstrate the need to ensure that either the internal state did not change, or that all the mutations for a method occurred.</span></span> <span data-ttu-id="74ff0-126">たとえば、次の実装では、オブジェクトが無効な状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-126">For example, the following implementation would leave the object in an invalid state:</span></span>

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

<span data-ttu-id="74ff0-127">状態の値が無効な場合は、address の最初の行と city が既に変更されています。</span><span class="sxs-lookup"><span data-stu-id="74ff0-127">If the value of the state is invalid, the first address line and the city have already been changed.</span></span> <span data-ttu-id="74ff0-128">address が無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-128">That might make the address invalid.</span></span>

<span data-ttu-id="74ff0-129">同様の方法は、エンティティのコンストラクターで、エンティティの作成後、例外を発生させてそのエンティティが有効であることを確認するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="74ff0-129">A similar approach can be used in the entity’s constructor, raising an exception to make sure that the entity is valid once it is created.</span></span>

### <a name="using-validation-attributes-in-the-model-based-on-data-annotations"></a><span data-ttu-id="74ff0-130">データ注釈に基づいてモデルで検証属性を使用する</span><span class="sxs-lookup"><span data-stu-id="74ff0-130">Using validation attributes in the model based on data annotations</span></span>

<span data-ttu-id="74ff0-131">別の方法は、データ注釈に基づいて検証属性を使用することです。</span><span class="sxs-lookup"><span data-stu-id="74ff0-131">Another approach is to use validation attributes based on data annotations.</span></span> <span data-ttu-id="74ff0-132">検証属性はモデルの検証を構成する方法を提供します。この方法は、概念的にはデータベース テーブルでのフィールドの検証に似ています。</span><span class="sxs-lookup"><span data-stu-id="74ff0-132">Validation attributes provide a way to configure model validation, which is similar conceptually to validation on fields in database tables.</span></span> <span data-ttu-id="74ff0-133">これには、データ型の割り当てや必須フィールドなどの制約が含まれます。</span><span class="sxs-lookup"><span data-stu-id="74ff0-133">This includes constraints such as assigning data types or required fields.</span></span> <span data-ttu-id="74ff0-134">その他の種類の検証としては、クレジット カード番号、電話番号、メール アドレスなど、ビジネス ルールを強制するためのデータへのパターンの適用があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-134">Other types of validation include applying patterns to data to enforce business rules, such as a credit card number, phone number, or email address.</span></span> <span data-ttu-id="74ff0-135">検証属性は、要件の強制を容易にします。</span><span class="sxs-lookup"><span data-stu-id="74ff0-135">Validation attributes make it easy to enforce requirements.</span></span>

<span data-ttu-id="74ff0-136">ただし、次のコードに示すように、この方法は、MVC コントローラーから呼び出す必要がある Microsoft.AspNetCore.Mvc.ModelState から ModelState.IsValid に対する依存関係を取得するため、非常に煩わしい場合があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-136">However, as shown in the following code, this approach might be too intrusive in a DDD model, because it takes a dependency on ModelState.IsValid from Microsoft.AspNetCore.Mvc.ModelState, which you must call from your MVC controllers.</span></span> <span data-ttu-id="74ff0-137">モデル検証は各コントローラー アクションが呼び出される前に行われます。ModelState.IsValid 呼び出しの結果を検査し、適切に対処するのはコントローラー メソッドの役割です。</span><span class="sxs-lookup"><span data-stu-id="74ff0-137">The model validation occurs prior to each controller action being invoked, and it is the controller method’s responsibility to inspect the result of calling ModelState.IsValid and react appropriately.</span></span> <span data-ttu-id="74ff0-138">これを使用するかどうかは、モデルをそのインフラストラクチャとどの程度緊密に結合させるかによります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-138">The decision to use it depends on how tightly coupled you want the model to be with that infrastructure.</span></span>

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

<span data-ttu-id="74ff0-139">ただし、DDD の観点から、ドメイン モデルはエンティティの動作メソッド内の例外を使用して、または検証規則を強制する仕様パターンと通知パターンを実装することで、リーンに保つことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="74ff0-139">However, from a DDD point of view, the domain model is best kept lean with the use of exceptions in your entity’s behavior methods, or by implementing the Specification and Notification patterns to enforce validation rules.</span></span> <span data-ttu-id="74ff0-140">ASP.NET Core でのデータ注釈のような検証フレームワーク、または FluentValidation のようなその他の検証フレームワークには、アプリケーション フレームワークを呼び出すための要件があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-140">Validation frameworks like data annotations in ASP.NET Core or any other validation frameworks like FluentValidation carry a requirement to invoke the application framework.</span></span> <span data-ttu-id="74ff0-141">たとえば、データ注釈で ModelState.IsValid メソッドを呼び出す場合、ASP.NET コントローラーを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-141">For example, when calling the ModelState.IsValid method in data annotations, you need to invoke ASP.NET controllers.</span></span>

<span data-ttu-id="74ff0-142">UI 層内でモデルの検証を許可するために、入力を受け取る ViewModel クラス内 (ドメイン エンティティではなく) のアプリケーション層でデータ注釈を使用するのは合理的です。</span><span class="sxs-lookup"><span data-stu-id="74ff0-142">It can make sense to use data annotations at the application layer in ViewModel classes (instead of domain entities) that will accept input, to allow for model validation within the UI layer.</span></span> <span data-ttu-id="74ff0-143">ただし、ドメイン モデル内での検証の実行時にはこれを行わないでください。</span><span class="sxs-lookup"><span data-stu-id="74ff0-143">However, this should not be done at the exclusion of validation within the domain model.</span></span>

### <a name="validating-entities-by-implementing-the-specification-pattern-and-the-notification-pattern"></a><span data-ttu-id="74ff0-144">仕様パターンと通知パターンを実装することでエンティティを検証する</span><span class="sxs-lookup"><span data-stu-id="74ff0-144">Validating entities by implementing the Specification pattern and the Notification pattern</span></span>

<span data-ttu-id="74ff0-145">最後に、ドメイン モデルで検証を実装するより複雑な方法は、後述するその他の技術情報の一部で説明されているように、仕様パターンと通知パターンを組み合わせて実装することです。</span><span class="sxs-lookup"><span data-stu-id="74ff0-145">Finally, a more elaborate approach to implementing validations in the domain model is by implementing the Specification pattern in conjunction with the Notification pattern, as explained in some of the additional resources listed later.</span></span>

<span data-ttu-id="74ff0-146">これらのパターンの 1 つだけを使用することもできます。たとえば、コントロール ステートメントを使用して手動で検証していますが、検証エラーの一覧をスタックして返すには通知パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="74ff0-146">It is worth mentioning that you can also use just one of those patterns—for example, validating manually with control statements, but using the Notification pattern to stack and return a list of validation errors.</span></span>

### <a name="using-deferred-validation-in-the-domain"></a><span data-ttu-id="74ff0-147">ドメインで遅延検証を使用する</span><span class="sxs-lookup"><span data-stu-id="74ff0-147">Using deferred validation in the domain</span></span>

<span data-ttu-id="74ff0-148">ドメインで遅延検証に対処するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="74ff0-148">There are various approaches to deal with deferred validations in the domain.</span></span> <span data-ttu-id="74ff0-149">Vaughn Vernon 氏は自身の著書『[Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)』で、検証に関するセクションでこれらについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="74ff0-149">In his book [Implementing Domain-Driven Design](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577), Vaughn Vernon discusses these in the section on validation.</span></span>

### <a name="two-step-validation"></a><span data-ttu-id="74ff0-150">2 段階検証</span><span class="sxs-lookup"><span data-stu-id="74ff0-150">Two-step validation</span></span>

<span data-ttu-id="74ff0-151">2 段階検証も検討してください。</span><span class="sxs-lookup"><span data-stu-id="74ff0-151">Also consider two-step validation.</span></span> <span data-ttu-id="74ff0-152">データ転送オブジェクト (DTO) コマンドにはフィールド レベルの検証を使用し、エンティティ内にはドメイン レベルの検証を使用します。</span><span class="sxs-lookup"><span data-stu-id="74ff0-152">Use field-level validation on your command Data Transfer Objects (DTOs) and domain-level validation inside your entities.</span></span> <span data-ttu-id="74ff0-153">検証エラーを処理しやすくするために、例外の代わりに結果オブジェクトを返すことで、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="74ff0-153">You can do this by returning a result object instead exceptions in order to make it easier to deal with the validation errors.</span></span>

<span data-ttu-id="74ff0-154">たとえば、データ注釈を使用したフィールドの検証を使用している場合、検証定義を複製しないでください。</span><span class="sxs-lookup"><span data-stu-id="74ff0-154">Using field validation with data annotations, for example, you do not duplicate the validation definition.</span></span> <span data-ttu-id="74ff0-155">ただし、DTO の場合、実行はサーバー側とクライアント側の両方で可能です (たとえば、コマンドと ViewModels)。</span><span class="sxs-lookup"><span data-stu-id="74ff0-155">The execution, though, can be both server-side and client-side in the case of DTOs (commands and ViewModels, for instance).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="74ff0-156">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="74ff0-156">Additional resources</span></span>

-   <span data-ttu-id="74ff0-157">**Rachel Appel。ASP.NET Core MVC でのモデル検証の概要**
    [*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span><span class="sxs-lookup"><span data-stu-id="74ff0-157">**Rachel Appel. Introduction to model validation in ASP.NET Core MVC**
[*https://docs.microsoft.com/aspnet/core/mvc/models/validation*](https://docs.microsoft.com/aspnet/core/mvc/models/validation)</span></span>

-   <span data-ttu-id="74ff0-158">**Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="74ff0-158">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

-   <span data-ttu-id="74ff0-159">**Martin Fowler。検証で例外のスローを通知に置き換える**
    [*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span><span class="sxs-lookup"><span data-stu-id="74ff0-159">**Martin Fowler. Replacing Throwing Exceptions with Notification in Validations**
[*https://martinfowler.com/articles/replaceThrowWithNotification.html*](https://martinfowler.com/articles/replaceThrowWithNotification.html)</span></span>

-   <span data-ttu-id="74ff0-160">**仕様と通知のパターン**
    [*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span><span class="sxs-lookup"><span data-stu-id="74ff0-160">**Specification and Notification Patterns**
[*https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns*](https://www.codeproject.com/Tips/790758/Specification-and-Notification-Patterns)</span></span>

-   <span data-ttu-id="74ff0-161">**Lev Gorodinski。ドメイン駆動設計 (DDD) での検証**
    [*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span><span class="sxs-lookup"><span data-stu-id="74ff0-161">**Lev Gorodinski. Validation in Domain-Driven Design (DDD)**
[*http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/*](http://gorodinski.com/blog/2012/05/19/validation-in-domain-driven-design-ddd/)</span></span>

-   <span data-ttu-id="74ff0-162">**Colin Jack。ドメイン モデルの検証**
    [*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span><span class="sxs-lookup"><span data-stu-id="74ff0-162">**Colin Jack. Domain Model Validation**
[*http://colinjack.blogspot.com/2008/03/domain-model-validation.html*](http://colinjack.blogspot.com/2008/03/domain-model-validation.html)</span></span>

-   <span data-ttu-id="74ff0-163">**Jimmy Bogard。DDD 世界での検証**
    [*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span><span class="sxs-lookup"><span data-stu-id="74ff0-163">**Jimmy Bogard. Validation in a DDD world**
[*https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/*](https://lostechies.com/jimmybogard/2009/02/15/validation-in-a-ddd-world/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="74ff0-164">[前へ] (enumeration-classes-over-enum-types.md) [次へ] (client-side-validation.md)</span><span class="sxs-lookup"><span data-stu-id="74ff0-164">[Previous] (enumeration-classes-over-enum-types.md) [Next] (client-side-validation.md)</span></span>

---
title: "クライアント側の検証 (プレゼンテーション層での検証)"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |クライアント側の検証 (プレゼンテーション層での検証)"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: db88a3b5c95afdc8d5a20094105f1f5991483ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="630a4-104">クライアント側の検証 (プレゼンテーション層での検証)</span><span class="sxs-lookup"><span data-stu-id="630a4-104">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="630a4-105">実際のソースは、ドメイン モデルと、最終的にする必要があります検証ドメイン モデル レベルで場合でも検証は、ドメイン モデル レベル (サーバー側) と、クライアント側の両方でまだ処理できます。</span><span class="sxs-lookup"><span data-stu-id="630a4-105">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="630a4-106">クライアント側の検証は、ユーザーにとって非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="630a4-106">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="630a4-107">保存されますがそれ以外の場合に費やす時間のラウンド トリップを待つ妥当性確認エラーを返す可能性のあるサーバーです。</span><span class="sxs-lookup"><span data-stu-id="630a4-107">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="630a4-108">ビジネス用語では、何百もの時間を乗算した値の秒の小数部をもいくつかは、多数の時間、経費、およびストレスへ追加します。</span><span class="sxs-lookup"><span data-stu-id="630a4-108">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="630a4-109">簡単かつ迅速検証より効率的に作業しより優れた品質の入力し、出力を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="630a4-109">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="630a4-110">ビュー モデルとドメイン モデルが異なる場合と同様ビュー モデルの検証およびドメイン モデル可能性がありますのようになりますが、別の目的に使用します。</span><span class="sxs-lookup"><span data-stu-id="630a4-110">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="630a4-111">問題がある場合はドライ (しないことを繰り返さない原則)、ここではコードの再利用には、結合が可能性がありますもと、エンタープライズ アプリケーションにすることがより重要いないドライの原則に従うにより、クライアント側に、サーバー側を結合することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="630a4-111">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="630a4-112">でもクライアント側の検証を使用する場合必要があります常にまたは検証すること、コマンドをサーバー Api が可能な攻撃ベクトルであるために、サーバー コードで dtos の使用を入力します。</span><span class="sxs-lookup"><span data-stu-id="630a4-112">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="630a4-113">通常は、両方を行って、最善の方法のためプロアクティブでき、ユーザーが無効な情報を入力することをお勧め UX の観点からのクライアント アプリケーションがある場合です。</span><span class="sxs-lookup"><span data-stu-id="630a4-113">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="630a4-114">そのため、クライアント側のコードで通常を検証する、ViewModels です。</span><span class="sxs-lookup"><span data-stu-id="630a4-114">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="630a4-115">クライアントを検証することもできます。 サービスに送信する前に、dtos の使用またはコマンドを出力します。</span><span class="sxs-lookup"><span data-stu-id="630a4-115">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="630a4-116">クライアント側の検証の実装は、構築してクライアント アプリケーションの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="630a4-116">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="630a4-117">.NET では、JavaScript または TypeScript でコーディングされていることの検証で SPA web アプリケーション コードのほとんどで web MVC web アプリケーションでデータを検証している場合は別になりますまたはモバイル アプリを Xamarin と C# でコード化された\#です。</span><span class="sxs-lookup"><span data-stu-id="630a4-117">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="630a4-118">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="630a4-118">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="630a4-119">Xamarin のモバイル アプリでの検証</span><span class="sxs-lookup"><span data-stu-id="630a4-119">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="630a4-120">**テキストを入力し、エラーの表示の検証**
    [*https://developer.xamarin.com/recipes/ios/standard\_コントロール]、[テキスト\_フィールド/検証\_入力/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="630a4-120">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="630a4-121">**検証コールバック**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="630a4-121">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="630a4-122">ASP.NET Core アプリでの検証</span><span class="sxs-lookup"><span data-stu-id="630a4-122">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="630a4-123">**Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="630a4-123">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="630a4-124">SPA での検証の Web アプリ (角度 2、TypeScript では、JavaScript)</span><span class="sxs-lookup"><span data-stu-id="630a4-124">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="630a4-125">**Ado Kukic です。Angular 2 フォーム検証** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="630a4-125">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="630a4-126">**検証をフォーム**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="630a4-126">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="630a4-127">**検証します。**</span><span class="sxs-lookup"><span data-stu-id="630a4-127">**Validation.**</span></span> <span data-ttu-id="630a4-128">ドキュメントをとても簡単です。</span><span class="sxs-lookup"><span data-stu-id="630a4-128">Breeze documentation.</span></span>
    [<span data-ttu-id="630a4-129">*http://breeze.github.io/doc-js/validation.html*</span><span class="sxs-lookup"><span data-stu-id="630a4-129">*http://breeze.github.io/doc-js/validation.html*</span></span>](http://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="630a4-130">概要、これらは、検証において最も重要な概念を示します。</span><span class="sxs-lookup"><span data-stu-id="630a4-130">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="630a4-131">エンティティと集計を独自の整合性を適用し、「常に有効な」します。</span><span class="sxs-lookup"><span data-stu-id="630a4-131">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="630a4-132">集計のルートは、同じ集計内で複数のエンティティの整合性を担当します。</span><span class="sxs-lookup"><span data-stu-id="630a4-132">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="630a4-133">エンティティが無効な状態を入力する必要があると思われる場合は、別のオブジェクト モデルを使用することを検討してください: 最後のドメイン エンティティを作成するまでに、一時 DTO をなどを使用します。</span><span class="sxs-lookup"><span data-stu-id="630a4-133">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="630a4-134">する場合に、集計など、いくつかの関連オブジェクトを作成する必要があり、のみ有効なそれらのすべてを作成した後、ファクトリ パターンの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="630a4-134">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="630a4-135">検証フレームワークは最も多く使用プレゼンテーション層またはアプリケーション/サービス レイヤーなど、特定のレイヤーで通常ではなく、ドメイン モデル レイヤー、インフラストラクチャ フレームワークで強力な依存関係を実行する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="630a4-135">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="630a4-136">ほとんどの場合である冗長検証、クライアント側では、適切なアプリケーションを事前に指定できます。</span><span class="sxs-lookup"><span data-stu-id="630a4-136">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="630a4-137">[前](ドメインのモデルのレイヤー-validations.md) [次へ] (ドメインのイベントの設計の implementation.md)</span><span class="sxs-lookup"><span data-stu-id="630a4-137">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>

---
title: クライアント側の検証 (プレゼンテーション層での検証)
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | クライアント側の検証 (プレゼンテーション層での検証)
keywords: Docker, マイクロサービス, ASP.NET, コンテナー
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2057609c7f5c26668eac49cecce522135545e7dd
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a><span data-ttu-id="9016c-104">クライアント側の検証 (プレゼンテーション層での検証)</span><span class="sxs-lookup"><span data-stu-id="9016c-104">Client-side validation (validation in the presentation layers)</span></span>

<span data-ttu-id="9016c-105">実際のソースがドメイン モデルで、最終的にドメイン モデル レベルで検証が必要な場合でも、検証はドメイン モデル レベル (サーバー側) とクライアント側の両方で処理できます。</span><span class="sxs-lookup"><span data-stu-id="9016c-105">Even when the source of truth is the domain model and ultimately you must have validation at the domain model level, validation can still be handled at both the domain model level (server side) and the client side.</span></span>

<span data-ttu-id="9016c-106">クライアント側の検証は、ユーザーにとって非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="9016c-106">Client-side validation is a great convenience for users.</span></span> <span data-ttu-id="9016c-107">他の方法では、検証エラーが返される可能性のあるサーバーへのラウンド トリップを待つために必要な時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="9016c-107">It saves time they would otherwise spend waiting for a round trip to the server that might return validation errors.</span></span> <span data-ttu-id="9016c-108">ビジネス的に表現すると、1 回だけ見ればわずかな時間でも、それが毎日何百回も積み重なると、膨大な時間、費用、フラストレーションになります。</span><span class="sxs-lookup"><span data-stu-id="9016c-108">In business terms, even a few fractions of seconds multiplied hundreds of times each day adds up to a lot of time, expense, and frustration.</span></span> <span data-ttu-id="9016c-109">簡単かつ迅速な検証は、ユーザーの作業をいっそう効率的にし、入力と出力の品質が向上します。</span><span class="sxs-lookup"><span data-stu-id="9016c-109">Straightforward and immediate validation enables users to work more efficiently and produce better quality input and output.</span></span>

<span data-ttu-id="9016c-110">ビュー モデルとドメイン モデルが異なる場合と同様に、ビュー モデルの検証とドメイン モデルの検証は似ていても目的は異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9016c-110">Just as the view model and the domain model are different, view model validation and domain model validation might be similar but serve a different purpose.</span></span> <span data-ttu-id="9016c-111">DRY (Don’t Repeat Yourself) の原則を念頭に置いている場合は、コードの再利用はカップリングを意味することもある点を考慮してください。エンタープライズ アプリケーションでは、DRY 原則に従うよりも、サーバー側とクライアント側をカップリングしないことの方が重要です。</span><span class="sxs-lookup"><span data-stu-id="9016c-111">If you are concerned about DRY (the Don’t Repeat Yourself principle), consider that in this case code reuse might also mean coupling, and in enterprise applications it is more important not to couple the server side to the client side than to follow the DRY principle.</span></span>

<span data-ttu-id="9016c-112">クライアント側の検証を使用する場合でも、サーバー API が攻撃ベクトルになる可能性があるため、サーバー コードに含まれるコマンドまたは入力 DTO を常に検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9016c-112">Even when using client-side validation, you should always validate your commands or input DTOs in server code, because the server APIs are a possible attack vector.</span></span> <span data-ttu-id="9016c-113">通常、両方を実行するのが最善の方法です。なぜなら、クライアント アプリケーションがある場合、UX の観点から、事前対応型にして、ユーザーに無効な情報を入力させない方法が最善のためです。</span><span class="sxs-lookup"><span data-stu-id="9016c-113">Usually, doing both is your best bet because if you have a client application, from a UX perspective, it is best to be proactive and not allow the user to enter invalid information.</span></span>

<span data-ttu-id="9016c-114">したがって、通常、クライアント側のコードでは ViewModel を検証します。</span><span class="sxs-lookup"><span data-stu-id="9016c-114">Therefore, in client-side code you typically validate the ViewModels.</span></span> <span data-ttu-id="9016c-115">サービスに送信する前に、クライアントの出力 DTO またはコマンドを検証することもできます。</span><span class="sxs-lookup"><span data-stu-id="9016c-115">You could also validate the client output DTOs or commands before you send them to the services.</span></span>

<span data-ttu-id="9016c-116">クライアント側の検証の実装は、構築するクライアント アプリケーションの種類によって変わります。</span><span class="sxs-lookup"><span data-stu-id="9016c-116">The implementation of client-side validation depends on what kind of client application you are building.</span></span> <span data-ttu-id="9016c-117">実装は、検証対象のデータが、ほとんどのコードが .NET の Web MVC Web アプリケーションか、検証が JavaScript または TypeScript でコーディングされている SPA Web アプリケーションか、Xamarin と C\# でコーディングされているモバイル アプリかによって変わります。</span><span class="sxs-lookup"><span data-stu-id="9016c-117">It will be different if you are validating data in a web MVC web application with most of the code in .NET, an SPA web application with that validation being coded in JavaScript or TypeScript, or a mobile app coded with Xamarin and C\#.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9016c-118">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9016c-118">Additional resources</span></span>

### <a name="validation-in-xamarin-mobile-apps"></a><span data-ttu-id="9016c-119">Xamarin モバイル アプリの検証</span><span class="sxs-lookup"><span data-stu-id="9016c-119">Validation in Xamarin mobile apps</span></span>

-   <span data-ttu-id="9016c-120">**テキスト入力の検証とエラーの表示**
    [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span><span class="sxs-lookup"><span data-stu-id="9016c-120">**Validate Text Input and Show Errors**
[*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)</span></span>

-   <span data-ttu-id="9016c-121">**検証コールバック**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span><span class="sxs-lookup"><span data-stu-id="9016c-121">**Validation Callback**
[*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)</span></span>

### <a name="validation-in-aspnet-core-apps"></a><span data-ttu-id="9016c-122">ASP.NET Core アプリの検証</span><span class="sxs-lookup"><span data-stu-id="9016c-122">Validation in ASP.NET Core apps</span></span>

-   <span data-ttu-id="9016c-123">**Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span><span class="sxs-lookup"><span data-stu-id="9016c-123">**Rick Anderson. Adding validation**
[*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)</span></span>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a><span data-ttu-id="9016c-124">SPA Web アプリの検証 (Angular 2、TypeScript、JavaScript)</span><span class="sxs-lookup"><span data-stu-id="9016c-124">Validation in SPA Web apps (Angular 2, TypeScript, JavaScript)</span></span>

-   <span data-ttu-id="9016c-125">**Ado Kukic。Angular 2 フォームの検証** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span><span class="sxs-lookup"><span data-stu-id="9016c-125">**Ado Kukic. Angular 2 Form Validation** **
**[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)</span></span>

-   <span data-ttu-id="9016c-126">**フォームの検証**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span><span class="sxs-lookup"><span data-stu-id="9016c-126">**Form Validation**
[*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)</span></span>

-   <span data-ttu-id="9016c-127">**検証。**</span><span class="sxs-lookup"><span data-stu-id="9016c-127">**Validation.**</span></span> <span data-ttu-id="9016c-128">Breeze ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="9016c-128">Breeze documentation.</span></span>
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

<span data-ttu-id="9016c-129">要約すると、検証に関する最も重要な概念は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9016c-129">In summary, these are the most important concepts in regards to validation:</span></span>

-   <span data-ttu-id="9016c-130">エンティティと集計は、独自の一貫性を強制し、"常に有効" である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9016c-130">Entities and aggregates should enforce their own consistency and be "always valid”.</span></span> <span data-ttu-id="9016c-131">集計ルートが、同じ集計内の複数エンティティの一貫性を担います。</span><span class="sxs-lookup"><span data-stu-id="9016c-131">Aggregate roots are responsible for multi-entity consistency within the same aggregate.</span></span>

-   <span data-ttu-id="9016c-132">エンティティで無効な状態を入力する必要があると考えられる場合は、最終的なドメイン エンティティを作成するまで一時的な DTO を使用するなど、別のオブジェクト モデルの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9016c-132">If you think that an entity needs to enter an invalid state, consider using a different object model—for example, using a temporary DTO until you create the final domain entity.</span></span>

-   <span data-ttu-id="9016c-133">集計などの複数の関連オブジェクトを作成する必要があり、すべてのオブジェクトが作成された後にのみ有効になる場合は、ファクトリ パターンの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9016c-133">If you need to create several related objects, such as an aggregate, and they are only valid once all of them have been created, consider using the Factory pattern.</span></span>

-   <span data-ttu-id="9016c-134">検証フレームワークは、プレゼンテーション レイヤーやアプリケーション/サービス レイヤーなどの特定のレイヤーで最もよく使用されますが、インフラストラクチャ フレームワークに強く依存する必要があるため、通常はドメイン モデル レイヤーでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9016c-134">Validation frameworks are best used in specific layers, such as the presentation layer or the application/service layer, but usually not in the domain model layer, because you would need to take a strong dependency on an infrastructure framework.</span></span>

-   <span data-ttu-id="9016c-135">ほとんどの場合、クライアント側で冗長な検証を行うことをお勧めします。これは、アプリケーションを事前対応型にすることができるためです。</span><span class="sxs-lookup"><span data-stu-id="9016c-135">In most of the cases, having redundant validation in the client side is good, because the application can be proactive.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9016c-136">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span><span class="sxs-lookup"><span data-stu-id="9016c-136">[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)</span></span>

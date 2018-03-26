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
ms.openlocfilehash: 273aa0a8ceb7f683999f1074faae0a6aa303f9be
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>クライアント側の検証 (プレゼンテーション層での検証)

実際のソースがドメイン モデルで、最終的にドメイン モデル レベルで検証が必要な場合でも、検証はドメイン モデル レベル (サーバー側) とクライアント側の両方で処理できます。

クライアント側の検証は、ユーザーにとって非常に便利です。 他の方法では、検証エラーが返される可能性のあるサーバーへのラウンド トリップを待つために必要な時間を節約できます。 ビジネス的に表現すると、1 回だけ見ればわずかな時間でも、それが毎日何百回も積み重なると、膨大な時間、費用、フラストレーションになります。 簡単かつ迅速な検証は、ユーザーの作業をいっそう効率的にし、入力と出力の品質が向上します。

ビュー モデルとドメイン モデルが異なる場合と同様に、ビュー モデルの検証とドメイン モデルの検証は似ていても目的は異なる場合があります。 DRY (Don’t Repeat Yourself) の原則を念頭に置いている場合は、コードの再利用はカップリングを意味することもある点を考慮してください。エンタープライズ アプリケーションでは、DRY 原則に従うよりも、サーバー側とクライアント側をカップリングしないことの方が重要です。

クライアント側の検証を使用する場合でも、サーバー API が攻撃ベクトルになる可能性があるため、サーバー コードに含まれるコマンドまたは入力 DTO を常に検証する必要があります。 通常、両方を実行するのが最善の方法です。なぜなら、クライアント アプリケーションがある場合、UX の観点から、事前対応型にして、ユーザーに無効な情報を入力させない方法が最善のためです。

したがって、通常、クライアント側のコードでは ViewModel を検証します。 サービスに送信する前に、クライアントの出力 DTO またはコマンドを検証することもできます。

クライアント側の検証の実装は、構築するクライアント アプリケーションの種類によって変わります。 実装は、検証対象のデータが、ほとんどのコードが .NET の Web MVC Web アプリケーションか、検証が JavaScript または TypeScript でコーディングされている SPA Web アプリケーションか、Xamarin と C\# でコーディングされているモバイル アプリかによって変わります。

## <a name="additional-resources"></a>その他の技術情報

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin モバイル アプリの検証

-   **テキストを入力し、エラーの表示の検証**
    [*https://developer.xamarin.com/recipes/ios/standard\_コントロール]、[テキスト\_フィールド/検証\_入力/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **検証コールバック**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core アプリの検証

-   **Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA Web アプリの検証 (Angular 2、TypeScript、JavaScript)

-   **Ado Kukic。角度の 2 つのフォーム検証** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **フォーム検証**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **検証。** Breeze ドキュメント。
    [*http://breeze.github.io/doc-js/validation.html*](http://breeze.github.io/doc-js/validation.html)

要約すると、検証に関する最も重要な概念は次のとおりです。

-   エンティティと集計は、独自の一貫性を強制し、"常に有効" である必要があります。 集計ルートが、同じ集計内の複数エンティティの一貫性を担います。

-   エンティティで無効な状態を入力する必要があると考えられる場合は、最終的なドメイン エンティティを作成するまで一時的な DTO を使用するなど、別のオブジェクト モデルの使用を検討してください。

-   集計などの複数の関連オブジェクトを作成する必要があり、すべてのオブジェクトが作成された後にのみ有効になる場合は、ファクトリ パターンの使用を検討してください。

-   検証フレームワークは、プレゼンテーション レイヤーやアプリケーション/サービス レイヤーなどの特定のレイヤーで最もよく使用されますが、インフラストラクチャ フレームワークに強く依存する必要があるため、通常はドメイン モデル レイヤーでは使用されません。

-   ほとんどの場合、クライアント側で冗長な検証を行うことをお勧めします。これは、アプリケーションを事前対応型にすることができるためです。


>[!div class="step-by-step"]
[Previous] (domain-model-layer-validations.md) [Next] (domain-events-design-implementation.md)

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
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>クライアント側の検証 (プレゼンテーション層での検証)

実際のソースは、ドメイン モデルと、最終的にする必要があります検証ドメイン モデル レベルで場合でも検証は、ドメイン モデル レベル (サーバー側) と、クライアント側の両方でまだ処理できます。

クライアント側の検証は、ユーザーにとって非常に便利です。 保存されますがそれ以外の場合に費やす時間のラウンド トリップを待つ妥当性確認エラーを返す可能性のあるサーバーです。 ビジネス用語では、何百もの時間を乗算した値の秒の小数部をもいくつかは、多数の時間、経費、およびストレスへ追加します。 簡単かつ迅速検証より効率的に作業しより優れた品質の入力し、出力を生成することができます。

ビュー モデルとドメイン モデルが異なる場合と同様ビュー モデルの検証およびドメイン モデル可能性がありますのようになりますが、別の目的に使用します。 問題がある場合はドライ (しないことを繰り返さない原則)、ここではコードの再利用には、結合が可能性がありますもと、エンタープライズ アプリケーションにすることがより重要いないドライの原則に従うにより、クライアント側に、サーバー側を結合することを検討してください。

でもクライアント側の検証を使用する場合必要があります常にまたは検証すること、コマンドをサーバー Api が可能な攻撃ベクトルであるために、サーバー コードで dtos の使用を入力します。 通常は、両方を行って、最善の方法のためプロアクティブでき、ユーザーが無効な情報を入力することをお勧め UX の観点からのクライアント アプリケーションがある場合です。

そのため、クライアント側のコードで通常を検証する、ViewModels です。 クライアントを検証することもできます。 サービスに送信する前に、dtos の使用またはコマンドを出力します。

クライアント側の検証の実装は、構築してクライアント アプリケーションの種類によって異なります。 .NET では、JavaScript または TypeScript でコーディングされていることの検証で SPA web アプリケーション コードのほとんどで web MVC web アプリケーションでデータを検証している場合は別になりますまたはモバイル アプリを Xamarin と C# でコード化された\#です。

## <a name="additional-resources"></a>その他の技術情報

### <a name="validation-in-xamarin-mobile-apps"></a>Xamarin のモバイル アプリでの検証

-   **テキストを入力し、エラーの表示の検証**
    [*https://developer.xamarin.com/recipes/ios/standard\_コントロール]、[テキスト\_フィールド/検証\_入力/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **検証コールバック**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>ASP.NET Core アプリでの検証

-   **Rick Anderson の 検証の追加**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>SPA での検証の Web アプリ (角度 2、TypeScript では、JavaScript)

-   **Ado Kukic です。Angular 2 フォーム検証** **
     ** [ *https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **検証をフォーム**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **検証します。** ドキュメントをとても簡単です。
    [*http://breeze.github.io/doc-js/validation.html*](http://breeze.github.io/doc-js/validation.html)

概要、これらは、検証において最も重要な概念を示します。

-   エンティティと集計を独自の整合性を適用し、「常に有効な」します。 集計のルートは、同じ集計内で複数のエンティティの整合性を担当します。

-   エンティティが無効な状態を入力する必要があると思われる場合は、別のオブジェクト モデルを使用することを検討してください: 最後のドメイン エンティティを作成するまでに、一時 DTO をなどを使用します。

-   する場合に、集計など、いくつかの関連オブジェクトを作成する必要があり、のみ有効なそれらのすべてを作成した後、ファクトリ パターンの使用を検討してください。

-   検証フレームワークは最も多く使用プレゼンテーション層またはアプリケーション/サービス レイヤーなど、特定のレイヤーで通常ではなく、ドメイン モデル レイヤー、インフラストラクチャ フレームワークで強力な依存関係を実行する必要があるためです。

-   ほとんどの場合である冗長検証、クライアント側では、適切なアプリケーションを事前に指定できます。


>[!div class="step-by-step"]
[前](ドメインのモデルのレイヤー-validations.md) [次へ] (ドメインのイベントの設計の implementation.md)

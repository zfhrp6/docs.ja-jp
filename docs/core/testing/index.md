---
title: ".NET Core での単体テスト"
description: "単体テストがさらに容易になりました。 .NET Core と .NET Standard プロジェクトでの単体テストの使用方法をご覧ください。"
keywords: ".NET, .NET Core, .NET Standard, 単体テスト"
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.openlocfilehash: 9f6a70598f3a0c0e3f479a25171e1deb6abffa33
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>.NET Core と .NET Standard の単体テスト

.NET Core は、アプリケーションの単体テストを従来よりも簡単に作成できるように、テストの容易性を考慮して設計されています。 この記事では、単体テスト (およびその他の種類のテストとの違い) について簡単に紹介します。 リンクされたリソースでは、テスト プロジェクトをソリューションに追加してから、コマンド ラインまたは Visual Studio を使用して単体テストを実行する方法を説明します。

.NET Core 2.0 は [.NET Standard 2.0](../../standard/net-standard.md) をサポートしています。 このセクションで単体テストの説明に使用するライブラリは .NET Standard に依存しており、他のプロジェクト タイプでも機能します。

.NET Core 2.0 以降では、Visual Basic 、F# および C# 用の単体テスト プロジェクト テンプレートが用意されています。

## <a name="getting-started-with-testing"></a>テストの概要

自動テストのスイートを備えることは、ソフトウェア アプリケーションが作成者の意図どおりに動作することを確認する最良の方法の 1 つです。 ソフトウェア アプリケーション用のテストには、統合テスト、Web テスト、ロード テストなど、さまざまな種類があります。 最下位レベルには、個々のソフトウェア コンポーネントまたはメソッドをテストする単体テストがあります。 単体テストでは、開発者のコントロール内のコードのみをテストし、データベース、ファイル システム、ネットワーク リソースなどのインフラストラクチャ上の問題はテストしません。 単体テストは、[テスト駆動開発 (TDD)](http://deviq.com/test-driven-development/) を使用して記述することも、既存のコードに追加してその正確性を確認することもできます。 いずれの場合にも、プロジェクトの共有コード リポジトリに変更をプッシュする前に数百もの単体テストを実行できることが理想的なため、単体テストは小規模で高速、かつ適切な名前が付けられている必要があります。

> [!NOTE]
> 多くの場合、開発者はテストのクラスやメソッドに適した名前を考え出すのに苦心します。 開始点として、ASP.NET 製品チームは[これらの規則](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)に従います。

単体テストを記述するときは、インフラストラクチャに対する依存関係を誤って導入しないように注意してください。 これらを導入すると、テストが低速で不安定になるので、統合テスト用に残しておく必要があります。 アプリケーション コードでこれらの非表示の依存関係を回避するには、[明示的な依存関係の原則](http://deviq.com/explicit-dependencies-principle/)に従い、[依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)を使用して、フレームワークに依存関係を要求します。 また、統合テストとは別個のプロジェクト内に単体テストを保持し、単体テスト プロジェクトがインフラストラクチャ パッケージへの参照または依存関係を確実に含まないようにできます。

.NET Core プロジェクトでの単体テストの詳細については、次を参照してください。

.NET Core の単体テスト プロジェクトは [C#](../../csharp/index.md)、[F#](../../fsharp/index.md)、[Visual Basic](../../visual-basic/index.md) でサポートされています。 また、[xUnit](http://xunit.github.io) か [MSTest](https://github.com/Microsoft/vstest-docs) を選択することもできます。

これらの組み合わせについては以下のチュートリアルで確認できます。

* [*XUnit* と *C#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-with-dotnet-test.md)。
* [*MSTest* と *C#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-with-mstest.md)。
* [*XUnit* と *F#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-fsharp-with-dotnet-test.md)。
* [*MSTest* と *F#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-fsharp-with-mstest.md)。
* [*XUnit* と *Visual Basic* を使用して .NET Core CLI で単体テストを作成する](unit-testing-visual-basic-with-dotnet-test.md)。
* [*MSTest* と *Visual Basic* を使用して .NET Core CLI で単体テストを作成する](unit-testing-visual-basic-with-mstest.md)。

使用するクラス ライブラリと単体テスト ライブラリには、さまざまな言語を選択できます。 先述のチュートリアルをうまく組み合わせることで、使用方法を学習できます。

* Visual Studio を使用する場合は、[.NET Core での Live Unit Testing](/visualstudio/test/live-unit-testing) に関するページをご覧ください。
* 選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[選択的単体テストの実行](selective-unit-tests.md)」のページ、または [Visual Studio を使用したテストの組み込みと除外](/visualstudio/test/live-unit-testing#including-and-excluding-test-projects-and-test-methods)に関するトピックをご覧ください。
* XUnit チームは、書き込みが [.NET Core および Visual Studio で xUnit を使用する方法](http://xunit.github.io/docs/getting-started-dotnet-core.html)を示すチュートリアルを作成しました。

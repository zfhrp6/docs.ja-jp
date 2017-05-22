---
title: ".NET Core での単体テスト"
description: ".NET Core での単体テスト"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.translationtype: Human Translation
ms.sourcegitcommit: ae036cfcad341ffc859336a7ab2a49feec145715
ms.openlocfilehash: 1bef3c8b36218d0cb228e85ef2ccdffd9a2a1bd7
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---

# <a name="unit-testing-in-net-core"></a>.NET Core での単体テスト

.NET Core は、アプリケーションの単体テストを従来よりも簡単に作成できるように、テストの容易性を考慮して設計されています。 この記事では、単体テスト (およびその他の種類のテストとの違い) について簡単に紹介します。 リンクされたリソースは、テスト プロジェクトをソリューションに追加してから、コマンドラインまたは Visual Studio を使用して単体テストを実行する方法を示します。

## <a name="getting-started-with-testing"></a>テストの概要
 
自動テストのスイートを備えることは、ソフトウェア アプリケーションが作成者の意図どおりに動作することを確認する最良の方法の 1 つです。 統合テスト、Web テスト、ロード テスト、その他の多くのテストを含め、ソフトウェア アプリケーション用のテストにはさまざまな種類があります。 最下位レベルには、個々のソフトウェア コンポーネントまたはメソッドをテストする単体テストがあります。 単体テストでは、開発者のコントロール内のコードのみをテストし、データベース、ファイル システム、ネットワーク リソースなどのインフラストラクチャ上の問題はテストしません。 単体テストは、[テスト駆動開発 (TDD)](http://deviq.com/test-driven-development/) を使用して記述することも、既存のコードに追加してその正確性を確認することもできます。 いずれの場合にも、プロジェクトの共有コード リポジトリに変更をプッシュする前に数百もの単体テストを実行できることが理想的なので、単体テストは小規模で高速かつ名前が適切である必要があります。

> [!NOTE]
> 多くの場合、開発者はテストのクラスやメソッドに適した名前を考え出すのに苦心します。 開始点として、ASP.NET 製品チームは[これらの規則](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)に従います。

単体テストを記述するときは、インフラストラクチャに対する依存関係を誤って導入しないように注意してください。 これらを導入すると、テストが低速で不安定になるので、統合テスト用に残しておく必要があります。 アプリケーション コードでこれらの非表示の依存関係を回避するには、[明示的な依存関係の原則](http://deviq.com/explicit-dependencies-principle/)に従い、[依存関係の挿入](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection)を使用して、フレームワークに依存関係を要求します。 また、統合テストとは別個のプロジェクト内に単体テストを保持し、単体テスト プロジェクトがインフラストラクチャ パッケージへの参照または依存関係を確実に含まないようにできます。

.NET Core プロジェクトでの単体テストの詳細については、次を参照してください。

* この [xUnit と .NET CLI による単体テストの作成チュートリアル](unit-testing-with-dotnet-test.md)を試してみてください。 
* XUnit チームは、書き込みが [.NET Core および Visual Studio で xUnit を使用する方法](http://xunit.github.io/docs/getting-started-dotnet-core.html)を示すチュートリアルを作成しました。
* MSTest を使用する場合は、[MSTest と .NET CLI を使用して単体テストを作成する方法のチュートリアル](unit-testing-with-mstest.md)を試してください。
* 選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。


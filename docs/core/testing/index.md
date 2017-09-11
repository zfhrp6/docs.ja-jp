---
title: ".NET Core での単体テスト"
description: "単体テストがさらに容易になりました。 .NET Core プロジェクトでの単体テストの使用方法を参照してください。"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 22647a9ad7723bbfcf0d54530b3c0538198e7c35
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="unit-testing-in-net-core"></a><span data-ttu-id="20b28-105">.NET Core での単体テスト</span><span class="sxs-lookup"><span data-stu-id="20b28-105">Unit Testing in .NET Core</span></span>

<span data-ttu-id="20b28-106">.NET Core は、アプリケーションの単体テストを従来よりも簡単に作成できるように、テストの容易性を考慮して設計されています。</span><span class="sxs-lookup"><span data-stu-id="20b28-106">.NET Core has been designed with testability in mind, so that creating unit tests for your applications is easier than ever before.</span></span> <span data-ttu-id="20b28-107">この記事では、単体テスト (およびその他の種類のテストとの違い) について簡単に紹介します。</span><span class="sxs-lookup"><span data-stu-id="20b28-107">This article briefly introduces unit tests (and how they differ from other kinds of tests).</span></span> <span data-ttu-id="20b28-108">リンクされたリソースは、テスト プロジェクトをソリューションに追加してから、コマンドラインまたは Visual Studio を使用して単体テストを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="20b28-108">Linked resources demonstrates how to add a test project to your solution and then run unit tests using either the command line or Visual Studio.</span></span>

## <a name="getting-started-with-testing"></a><span data-ttu-id="20b28-109">テストの概要</span><span class="sxs-lookup"><span data-stu-id="20b28-109">Getting Started with Testing</span></span>
 
<span data-ttu-id="20b28-110">自動テストのスイートを備えることは、ソフトウェア アプリケーションが作成者の意図どおりに動作することを確認する最良の方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="20b28-110">Having a suite of automated tests is one of the best ways to ensure a software application does what its authors intended it to do.</span></span> <span data-ttu-id="20b28-111">統合テスト、Web テスト、ロード テスト、その他の多くのテストを含め、ソフトウェア アプリケーション用のテストにはさまざまな種類があります。</span><span class="sxs-lookup"><span data-stu-id="20b28-111">There are many different kinds of tests for software applications, including integration tests, web tests, load tests, and many others.</span></span> <span data-ttu-id="20b28-112">最下位レベルには、個々のソフトウェア コンポーネントまたはメソッドをテストする単体テストがあります。</span><span class="sxs-lookup"><span data-stu-id="20b28-112">At the lowest level are unit tests, which test individual software components or methods.</span></span> <span data-ttu-id="20b28-113">単体テストでは、開発者のコントロール内のコードのみをテストし、データベース、ファイル システム、ネットワーク リソースなどのインフラストラクチャ上の問題はテストしません。</span><span class="sxs-lookup"><span data-stu-id="20b28-113">Unit tests should only test code within the developer’s control, and should not test infrastructure concerns, like databases, file systems, or network resources.</span></span> <span data-ttu-id="20b28-114">単体テストは、[テスト駆動開発 (TDD)](http://deviq.com/test-driven-development/) を使用して記述することも、既存のコードに追加してその正確性を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="20b28-114">Unit tests may be written using [Test Driven Development (TDD)](http://deviq.com/test-driven-development/), or they can be added to existing code to confirm its correctness.</span></span> <span data-ttu-id="20b28-115">いずれの場合にも、プロジェクトの共有コード リポジトリに変更をプッシュする前に数百もの単体テストを実行できることが理想的なので、単体テストは小規模で高速かつ名前が適切である必要があります。</span><span class="sxs-lookup"><span data-stu-id="20b28-115">In either case, they should be small, well-named, and fast, since ideally you will want to be able to run hundreds of them before pushing your changes into the project’s shared code repository.</span></span>

> [!NOTE]
> <span data-ttu-id="20b28-116">多くの場合、開発者はテストのクラスやメソッドに適した名前を考え出すのに苦心します。</span><span class="sxs-lookup"><span data-stu-id="20b28-116">Developers often struggle with coming up with good names for their test classes and methods.</span></span> <span data-ttu-id="20b28-117">開始点として、ASP.NET 製品チームは[これらの規則](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)に従います。</span><span class="sxs-lookup"><span data-stu-id="20b28-117">As a starting point, the ASP.NET product team follows [these conventions](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).</span></span>

<span data-ttu-id="20b28-118">単体テストを記述するときは、インフラストラクチャに対する依存関係を誤って導入しないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="20b28-118">When writing unit tests, be careful you don’t accidentally introduce dependencies on infrastructure.</span></span> <span data-ttu-id="20b28-119">これらを導入すると、テストが低速で不安定になるので、統合テスト用に残しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="20b28-119">These tend to make tests slower and more brittle, and thus should be reserved for integration tests.</span></span> <span data-ttu-id="20b28-120">アプリケーション コードでこれらの非表示の依存関係を回避するには、[明示的な依存関係の原則](http://deviq.com/explicit-dependencies-principle/)に従い、[依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)を使用して、フレームワークに依存関係を要求します。</span><span class="sxs-lookup"><span data-stu-id="20b28-120">You can avoid these hidden dependencies in your application code by following the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/) and using [Dependency Injection](/aspnet/core/fundamentals/dependency-injection) to request your dependencies from the framework.</span></span> <span data-ttu-id="20b28-121">また、統合テストとは別個のプロジェクト内に単体テストを保持し、単体テスト プロジェクトがインフラストラクチャ パッケージへの参照または依存関係を確実に含まないようにできます。</span><span class="sxs-lookup"><span data-stu-id="20b28-121">You can also keep your unit tests in a separate project from your integration tests, and ensure your unit test project doesn’t have references to or dependencies on infrastructure packages.</span></span>

<span data-ttu-id="20b28-122">.NET Core プロジェクトでの単体テストの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20b28-122">Learn more about unit testing in .NET Core projects:</span></span>

* <span data-ttu-id="20b28-123">この [xUnit と .NET Core CLI による単体テストの作成チュートリアル](unit-testing-with-dotnet-test.md)を試してください。</span><span class="sxs-lookup"><span data-stu-id="20b28-123">Try this [walkthrough creating unit tests with xUnit and the .NET Core CLI](unit-testing-with-dotnet-test.md).</span></span> 
* <span data-ttu-id="20b28-124">XUnit チームは、書き込みが [.NET Core および Visual Studio で xUnit を使用する方法](http://xunit.github.io/docs/getting-started-dotnet-core.html)を示すチュートリアルを作成しました。</span><span class="sxs-lookup"><span data-stu-id="20b28-124">The XUnit team has written a tutorial that shows [how to use xUnit with .NET Core and Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).</span></span>
* <span data-ttu-id="20b28-125">MSTest を使用する場合は、[MSTest と .NET Core CLI を使用して単体テストを作成する方法のチュートリアル](unit-testing-with-mstest.md)を試してください。</span><span class="sxs-lookup"><span data-stu-id="20b28-125">If you prefer using MSTest, try the [walkthrough creating unit tests with MSTest and the .NET Core CLI](unit-testing-with-mstest.md).</span></span>
* <span data-ttu-id="20b28-126">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[Running selective unit tests (選択的単体テストの実行)](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="20b28-126">For a additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>


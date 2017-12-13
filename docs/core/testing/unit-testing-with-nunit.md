---
title: "NUnit と .NET Core による単体テスト C#"
description: "dotnet テストおよび NUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、C# および .NET Core の単体テストの概念について説明します。"
keywords: NUnit, .NET, .NET Core
author: rprouse
ms.date: 12/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.openlocfilehash: ad410497adc641e89bd9845ed69c063692ad2f73
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a><span data-ttu-id="a0679-104">NUnit と .NET Core による単体テスト C#</span><span class="sxs-lookup"><span data-stu-id="a0679-104">Unit testing C# with NUnit and .NET Core</span></span>

<span data-ttu-id="a0679-105">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="a0679-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="a0679-106">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/)してください。</span><span class="sxs-lookup"><span data-stu-id="a0679-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/) before you begin.</span></span> <span data-ttu-id="a0679-107">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0679-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="a0679-108">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a0679-108">Creating the source project</span></span>

<span data-ttu-id="a0679-109">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="a0679-109">Open a shell window.</span></span> <span data-ttu-id="a0679-110">ソリューションを保存するための *unit-testing-using-nunit* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-110">Create a directory called *unit-testing-using-nunit* to hold the solution.</span></span> <span data-ttu-id="a0679-111">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、クラス ライブラリとテスト プロジェクト用の新しいソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-111">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="a0679-112">次に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-112">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="a0679-113">現時点のディレクトリとファイルの構造は次のアウトラインのようになっています。</span><span class="sxs-lookup"><span data-stu-id="a0679-113">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

<span data-ttu-id="a0679-114">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="a0679-115">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="a0679-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="a0679-116">テスト駆動開発 (TDD) を行うには、`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

<span data-ttu-id="a0679-117">*unit-testing-using-nunit* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="a0679-117">Change the directory back to the *unit-testing-using-nunit* directory.</span></span> <span data-ttu-id="a0679-118">[`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a0679-118">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="a0679-119">NUnit プロジェクト テンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="a0679-119">Install the NUnit project template</span></span>

<span data-ttu-id="a0679-120">NUnit テストのプロジェクト テンプレートは、テスト プロジェクトを作成する前にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0679-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="a0679-121">これは、新しい NUnit プロジェクトを作成する開発者の各コンピューターで 1 回だけ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0679-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="a0679-122">NUnit テンプレートをインストールするには、[`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0679-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a><span data-ttu-id="a0679-123">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="a0679-123">Creating the test project</span></span>

<span data-ttu-id="a0679-124">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="a0679-125">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="a0679-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="a0679-126">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new nunit`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="a0679-127">dotnet new コマンドによって、テスト ライブラリとして NUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a0679-127">The dotnet new command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="a0679-128">生成されたテンプレートで、*PrimeServiceTests.csproj* ファイルのテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="a0679-128">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="a0679-129">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0679-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="a0679-130">前の手順の `dotnet new` では Microsoft テスト SDK、NUnit テスト フレームワーク、NUnit テスト アダプターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="a0679-130">`dotnet new` in the previous step added the Microsoft test SDK, the NUnit test framework, and the NUnit test adapter.</span></span> <span data-ttu-id="a0679-131">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="a0679-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="a0679-132">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0679-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="a0679-133">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="a0679-133">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="a0679-134">ソリューションの最終的なレイアウトは次のアウトラインのようになります。</span><span class="sxs-lookup"><span data-stu-id="a0679-134">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="a0679-135">*unit-testing-using-dotnet-test* ディレクトリで [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0679-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="a0679-136">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="a0679-136">Creating the first test</span></span>

<span data-ttu-id="a0679-137">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a0679-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="a0679-138">*PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。コンテンツは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a0679-138">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="a0679-139">`[TestFixture]` 属性は、単体テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="a0679-139">The `[TestFixture]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="a0679-140">`[Test]` 属性は、メソッドがテスト メソッドであることを表します。</span><span class="sxs-lookup"><span data-stu-id="a0679-140">The `[Test]` attribute indicates a method is a test method.</span></span>

<span data-ttu-id="a0679-141">このファイルを保存し、[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドしてから、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0679-141">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="a0679-142">NUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0679-142">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="a0679-143">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="a0679-143">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="a0679-144">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="a0679-144">Your test fails.</span></span> <span data-ttu-id="a0679-145">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="a0679-145">You haven't created the implementation yet.</span></span> <span data-ttu-id="a0679-146">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="a0679-146">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

<span data-ttu-id="a0679-147">*unit-testing-using-nunit* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0679-147">In the *unit-testing-using-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="a0679-148">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a0679-148">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="a0679-149">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a0679-149">After building both projects, it runs this single test.</span></span> <span data-ttu-id="a0679-150">成功します。</span><span class="sxs-lookup"><span data-stu-id="a0679-150">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="a0679-151">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="a0679-151">Adding more features</span></span>

<span data-ttu-id="a0679-152">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="a0679-152">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="a0679-153">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="a0679-153">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="a0679-154">`[Test]` 属性を使用すると新しいテストを追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="a0679-154">You could add new tests with the `[Test]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="a0679-155">一連の類似のテストを記述できるようになる、他の NUnit 属性があります。</span><span class="sxs-lookup"><span data-stu-id="a0679-155">There are other NUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="a0679-156">`[TestCase]` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a0679-156">A `[TestCase]` attribute is used to create a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="a0679-157">`[TestCase]` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a0679-157">You can use the `[TestCase]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="a0679-158">新しいテストを作成するのではなく、この属性を適用することで 1 つのデータ駆動テストを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0679-158">Instead of creating new tests, apply this attribute to create a single data driven test.</span></span> <span data-ttu-id="a0679-159">そのデータ駆動テストとは、複数の 2 未満の値を調べて、最も小さい素数を特定するという手法です。</span><span class="sxs-lookup"><span data-stu-id="a0679-159">The data driven test is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="a0679-160">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="a0679-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="a0679-161">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="a0679-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="a0679-162">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="a0679-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="a0679-163">[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs)ができ、[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="a0679-163">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="a0679-164">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="a0679-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="a0679-165">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="a0679-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="a0679-166">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="a0679-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

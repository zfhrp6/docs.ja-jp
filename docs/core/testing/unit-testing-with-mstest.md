---
title: MSTest と .NET Core による単体テスト C#
description: dotnet テストおよび MSTest を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、C# および .NET Core の単体テストの概念について説明します。
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: b76e577d3950dd13b038f47c1b133e3529867c38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a><span data-ttu-id="1d712-103">MSTest と .NET Core による単体テスト C#</span><span class="sxs-lookup"><span data-stu-id="1d712-103">Unit testing C# with MSTest and .NET Core</span></span>

<span data-ttu-id="1d712-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="1d712-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="1d712-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/)してください。</span><span class="sxs-lookup"><span data-stu-id="1d712-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="1d712-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d712-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="1d712-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1d712-107">Creating the source project</span></span>

<span data-ttu-id="1d712-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="1d712-108">Open a shell window.</span></span> <span data-ttu-id="1d712-109">ソリューションを保持するための *unit-testing-using-dotnet-test* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="1d712-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、クラス ライブラリとテスト プロジェクト用の新しいソリューション ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution file for the class library and the test project.</span></span> <span data-ttu-id="1d712-111">次に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-111">Next, create a *PrimeService* directory.</span></span> <span data-ttu-id="1d712-112">現時点のディレクトリとファイルの構造は次のアウトラインのようになっています。</span><span class="sxs-lookup"><span data-stu-id="1d712-112">The following outline shows the directory and file structure thus far:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

<span data-ttu-id="1d712-113">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="1d712-114">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="1d712-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="1d712-115">テスト駆動開発 (TDD) を行うには、`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-115">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="1d712-116">*unit-testing-using-mstest* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1d712-116">Change the directory back to the *unit-testing-using-mstest* directory.</span></span> <span data-ttu-id="1d712-117">[`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="1d712-117">Run [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span> 

### <a name="creating-the-test-project"></a><span data-ttu-id="1d712-118">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1d712-118">Creating the test project</span></span>

<span data-ttu-id="1d712-119">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-119">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="1d712-120">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="1d712-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="1d712-121">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new mstest`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d712-121">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="1d712-122">dotnet new コマンドによって、テスト ライブラリとして MStest を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1d712-122">The dotnet new command creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="1d712-123">生成されたテンプレートで、*PrimeServiceTests.csproj* ファイルのテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="1d712-123">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="1d712-124">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="1d712-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="1d712-125">前の手順の `dotnet new` により、MSTest SDK、MSTest テスト フレームワーク、MSTest ランナーが追加されました。</span><span class="sxs-lookup"><span data-stu-id="1d712-125">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="1d712-126">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="1d712-126">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="1d712-127">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1d712-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="1d712-128">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="1d712-128">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="1d712-129">ソリューションの最終的なレイアウトは次のアウトラインのようになります。</span><span class="sxs-lookup"><span data-stu-id="1d712-129">The following outline shows the final solution layout:</span></span>

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="1d712-130">*unit-testing-using-dotnet-test* ディレクトリで [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="1d712-130">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="1d712-131">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="1d712-131">Creating the first test</span></span>

<span data-ttu-id="1d712-132">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1d712-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="1d712-133">*PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。コンテンツは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1d712-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="1d712-134">`[TestClass]` 属性は、単体テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="1d712-134">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="1d712-135">`[TestMethod]` 属性は、メソッドがテスト メソッドであることを表します。</span><span class="sxs-lookup"><span data-stu-id="1d712-135">The `[TestMethod]` attribute indicates a method is a test method.</span></span> 

<span data-ttu-id="1d712-136">このファイルを保存し、[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドしてから、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d712-136">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="1d712-137">MSTest テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1d712-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="1d712-138">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1d712-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="1d712-139">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="1d712-139">Your test fails.</span></span> <span data-ttu-id="1d712-140">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="1d712-140">You haven't created the implementation yet.</span></span> <span data-ttu-id="1d712-141">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストが成功するようにします。</span><span class="sxs-lookup"><span data-stu-id="1d712-141">Make this test pass by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="1d712-142">*unit-testing-using-mstest* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="1d712-142">In the *unit-testing-using-mstest* directory, run `dotnet test` again.</span></span> <span data-ttu-id="1d712-143">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d712-143">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="1d712-144">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="1d712-144">After building both projects, it runs this single test.</span></span> <span data-ttu-id="1d712-145">成功します。</span><span class="sxs-lookup"><span data-stu-id="1d712-145">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="1d712-146">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="1d712-146">Adding more features</span></span>

<span data-ttu-id="1d712-147">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="1d712-147">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="1d712-148">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="1d712-148">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="1d712-149">`[TestMethod]` 属性を使用すると新しいテストを追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="1d712-149">You could add new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="1d712-150">一連の類似のテストを記述できるようになる、他の MSTest 属性があります。</span><span class="sxs-lookup"><span data-stu-id="1d712-150">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="1d712-151">`[DataTestMethod]` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="1d712-151">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="1d712-152">`[DataRow]` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="1d712-152">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="1d712-153">新しいテストを作成するのではなく、この 2 つの属性を適用することで 1 つのデータ駆動テストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1d712-153">Instead of creating new tests, apply these two attributes to create a single data driven test.</span></span> <span data-ttu-id="1d712-154">そのデータ駆動テストとは、複数の 2 未満の値を調べて、もっとも小さい素数を特定するという手法です。</span><span class="sxs-lookup"><span data-stu-id="1d712-154">The data driven test is a method that tests several values less than two, which is the lowest prime number: :</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="1d712-155">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="1d712-155">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="1d712-156">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="1d712-156">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="1d712-157">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="1d712-157">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="1d712-158">[テストの最終版](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)ができ、[ライブラリの完全な実装](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1d712-158">You have the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="1d712-159">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="1d712-159">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="1d712-160">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="1d712-160">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="1d712-161">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="1d712-161">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

---
title: "dotnet テストと xUnit を使用した .NET Core での単体テスト C# コード"
description: "dotnet テストおよび xUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、C# および .NET Core の単体テストの概念について説明します。"
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6e986e89d47ba4de9b8563f1a95cb1ae89accc89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="3faaa-103">dotnet テストと xUnit を使用した .NET Core での単体テスト C#</span><span class="sxs-lookup"><span data-stu-id="3faaa-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="3faaa-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3faaa-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)してください。</span><span class="sxs-lookup"><span data-stu-id="3faaa-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="3faaa-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3faaa-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3faaa-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3faaa-107">Creating the source project</span></span>

<span data-ttu-id="3faaa-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-108">Open a shell window.</span></span> <span data-ttu-id="3faaa-109">ソリューションを保持するための *unit-testing-using-dotnet-test* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span>
<span data-ttu-id="3faaa-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、ソリューションを新たに作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="3faaa-111">こうすることで、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="3faaa-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="3faaa-112">ソリューションのディレクトリ内で、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="3faaa-113">現時点のディレクトリとファイルの構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="3faaa-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

<span data-ttu-id="3faaa-114">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-114">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="3faaa-115">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-115">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="3faaa-116">テスト駆動開発 (TDD) を使用するため、`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-116">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

<span data-ttu-id="3faaa-117">*unit-testing-using-dotnet-test* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3faaa-117">Change the directory back to the *unit-testing-using-dotnet-test* directory.</span></span> <span data-ttu-id="3faaa-118">[`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-118">Run [`dotnet sln add .\PrimeService\PrimeService.csproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="3faaa-119">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3faaa-119">Creating the test project</span></span>

<span data-ttu-id="3faaa-120">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-120">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="3faaa-121">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="3faaa-121">The following outline shows the directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="3faaa-122">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new xunit`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-122">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="3faaa-123">これで、テスト ライブラリとして xUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-123">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="3faaa-124">生成されたテンプレートで、*PrimeServiceTests.csproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-124">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="3faaa-125">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="3faaa-125">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3faaa-126">前の手順の `dotnet new` によって、xUnit と xUnit ランナーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="3faaa-126">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="3faaa-127">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-127">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="3faaa-128">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-128">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="3faaa-129">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-129">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="3faaa-130">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3faaa-130">The following shows the final solution layout:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

<span data-ttu-id="3faaa-131">*unit-testing-using-dotnet-test* ディレクトリで [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-131">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) in the *unit-testing-using-dotnet-test* directory.</span></span> 

## <a name="creating-the-first-test"></a><span data-ttu-id="3faaa-132">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="3faaa-132">Creating the first test</span></span>

<span data-ttu-id="3faaa-133">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="3faaa-134">*PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs*.</span></span> <span data-ttu-id="3faaa-135">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-135">Add the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="3faaa-136">`[Fact]` 属性は、テスト ランナーによって実行されるテスト メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-136">The `[Fact]` attribute indicates a test method that is run by the test runner.</span></span> <span data-ttu-id="3faaa-137">*unit-testing-using-dotnet-test* で [`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-137">From the *unit-testing-using-dotnet-test*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3faaa-138">xUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3faaa-138">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3faaa-139">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-139">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3faaa-140">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-140">Your test fails.</span></span> <span data-ttu-id="3faaa-141">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="3faaa-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="3faaa-142">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-142">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

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

<span data-ttu-id="3faaa-143">*unit-testing-using-dotnet-test* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-143">In the *unit-testing-using-dotnet-test* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3faaa-144">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="3faaa-145">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3faaa-146">成功します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="3faaa-147">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="3faaa-147">Adding more features</span></span>

<span data-ttu-id="3faaa-148">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3faaa-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3faaa-149">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="3faaa-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="3faaa-150">`[Fact]` 属性を使用すると、これらの例を新しいテストとして追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="3faaa-150">You could add those cases as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="3faaa-151">一連の類似のテストを記述できるようになる、他の xUnit 属性があります。</span><span class="sxs-lookup"><span data-stu-id="3faaa-151">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="3faaa-152">`[Theory]` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-152">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="3faaa-153">`[InlineData]` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-153">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="3faaa-154">新しいテストを作成するのではなく、この 2 つの属性を適用することで 1 つの理論を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-154">Instead of creating new tests, apply these two attributes to create a single theory.</span></span> <span data-ttu-id="3faaa-155">その理論とは、複数の 2 未満の値を調べて、もっとも小さい素数を特定するという手法です。</span><span class="sxs-lookup"><span data-stu-id="3faaa-155">The theory is a method that tests several values less than two, which is the lowest prime number:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="3faaa-156">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="3faaa-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="3faaa-157">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="3faaa-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="3faaa-158">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="3faaa-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="3faaa-159">[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)ができ、[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3faaa-159">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3faaa-160">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="3faaa-160">Additional resources</span></span>

[<span data-ttu-id="3faaa-161">ASP.NET Core でのテスト コント ローラー ロジック</span><span class="sxs-lookup"><span data-stu-id="3faaa-161">Testing controller logic in ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

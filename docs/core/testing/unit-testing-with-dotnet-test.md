---
title: "dotnet テストと xUnit を使用した .NET Core での単体テスト"
description: ".NET テストおよび xUnit を使用するサンプル ソリューションを手順を追って構築する対話型エクスペリエンスを通じて、.NET Core の単体テストの概念について説明します。"
author: ardalis
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.translationtype: HT
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: d989ee731d7ffd0439bac69afe1458e2aa10733a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="unit-testing-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="49a3b-103">dotnet テストと xUnit を使用した .NET Core での単体テスト</span><span class="sxs-lookup"><span data-stu-id="49a3b-103">Unit testing in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="49a3b-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="49a3b-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/)してください。</span><span class="sxs-lookup"><span data-stu-id="49a3b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) before you begin.</span></span> <span data-ttu-id="49a3b-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49a3b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="49a3b-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="49a3b-107">Creating the source project</span></span>

<span data-ttu-id="49a3b-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-108">Open a shell window.</span></span> <span data-ttu-id="49a3b-109">ソリューションを保持するための *unit-testing-using-dotnet-test* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-109">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="49a3b-110">この新しいディレクトリ内に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-110">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="49a3b-111">現時点のディレクトリ構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="49a3b-111">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
```

<span data-ttu-id="49a3b-112">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-112">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="49a3b-113">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-113">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="49a3b-114">テスト駆動開発 (TDD) を使用するため、`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-114">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

## <a name="creating-the-test-project"></a><span data-ttu-id="49a3b-115">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="49a3b-115">Creating the test project</span></span>

<span data-ttu-id="49a3b-116">*unit-testing-using-dotnet-test* ディレクトリに戻り、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-116">Change the directory back to the *unit-testing-using-dotnet-test* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="49a3b-117">ディレクトリ構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49a3b-117">The directory structure is shown below:</span></span>

```
/unit-testing-using-dotnet-test
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="49a3b-118">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new xunit`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-118">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new xunit`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="49a3b-119">これで、テスト ライブラリとして xUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-119">This creates a test project that uses xUnit as the test library.</span></span> <span data-ttu-id="49a3b-120">生成されたテンプレートで、*PrimeServiceTests.csproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-120">The generated template configures the test runner in the *PrimeServiceTests.csproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

<span data-ttu-id="49a3b-121">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="49a3b-121">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="49a3b-122">前の手順の `dotnet new` によって、xUnit と xUnit ランナーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="49a3b-122">`dotnet new` in the previous step added xUnit and the xUnit runner.</span></span> <span data-ttu-id="49a3b-123">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-123">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="49a3b-124">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-124">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="49a3b-125">*PrimeService.Tests.csproj* ファイルを編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-125">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="49a3b-126">最初の `<ItemGroup>` ノードの下で直接、ライブラリ プロジェクトを参照する別の `<ItemGroup>` ノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-126">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="49a3b-127">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-127">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="49a3b-128">最終的なソリューションのレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49a3b-128">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="49a3b-129">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="49a3b-129">Creating the first test</span></span>

<span data-ttu-id="49a3b-130">ライブラリまたはテストを構築する前に、*PrimeService.Tests* ディレクトリで [`dotnet restore`](../tools/dotnet-restore.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-130">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="49a3b-131">このコマンドにより、各プロジェクトの必要なすべての NuGet パッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-131">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="49a3b-132">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="49a3b-133">*PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。コンテンツは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49a3b-133">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

            Assert.False(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="49a3b-134">`[Fact]` 属性は、単一のテストとしてメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-134">The `[Fact]` attribute denotes a method as a single test.</span></span> <span data-ttu-id="49a3b-135">[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドしてから、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-135">Execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="49a3b-136">xUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="49a3b-136">The xUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="49a3b-137">`dotnet test` がテスト ランナーを開始し、テストを含むアセンブリを示すテスト ランナーにコマンド ライン引数を提供します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-137">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="49a3b-138">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-138">Your test fails.</span></span> <span data-ttu-id="49a3b-139">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="49a3b-139">You haven't created the implementation yet.</span></span> <span data-ttu-id="49a3b-140">このテストを成功させるための最も簡単なコードを `PrimeService` クラスに記述します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-140">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

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

<span data-ttu-id="49a3b-141">*PrimeService.Tests* ディレクトリで、`dotnet test` をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-141">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="49a3b-142">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-142">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="49a3b-143">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-143">After building both projects, it runs this single test.</span></span> <span data-ttu-id="49a3b-144">成功します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-144">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="49a3b-145">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="49a3b-145">Adding more features</span></span>

<span data-ttu-id="49a3b-146">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="49a3b-146">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="49a3b-147">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="49a3b-147">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="49a3b-148">これらは `[Fact]` 属性を使用して新しいテストとして追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="49a3b-148">You could add those as new tests with the `[Fact]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="49a3b-149">一連の類似のテストを記述できるようになる、他の xUnit 属性があります。</span><span class="sxs-lookup"><span data-stu-id="49a3b-149">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="49a3b-150">`[Theory]` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-150">A `[Theory]` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="49a3b-151">`[InlineData]` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-151">You can use the `[InlineData]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="49a3b-152">新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストする理論を 1 つ作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="49a3b-152">Instead of creating new tests, leverage these two attributes to create a single theory that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="49a3b-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="49a3b-153">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="49a3b-154">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="49a3b-154">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="49a3b-155">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-155">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="49a3b-156">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="49a3b-156">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="49a3b-157">[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs)と[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)により終了します。</span><span class="sxs-lookup"><span data-stu-id="49a3b-157">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="49a3b-158">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="49a3b-158">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="49a3b-159">新しいパッケージとテストの追加がシームレスになり、アプリケーションの目標を解決するためにほとんどの時間と労力を注げるようにソリューションを構成しました。</span><span class="sxs-lookup"><span data-stu-id="49a3b-159">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>


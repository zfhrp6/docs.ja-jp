---
title: "MSTest と .NET Core による単体テスト"
description: "MSTest と .NET Core を使用する方法"
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 03/21/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d1cb9f6667e1317e74d246988ef1257d0712c431
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="unit-testing-with-mstest-and-net-core"></a><span data-ttu-id="d0062-104">MSTest と .NET Core による単体テスト</span><span class="sxs-lookup"><span data-stu-id="d0062-104">Unit testing with MSTest and .NET Core</span></span>

<span data-ttu-id="d0062-105">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="d0062-105">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="d0062-106">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/)してください。</span><span class="sxs-lookup"><span data-stu-id="d0062-106">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/) before you begin.</span></span> <span data-ttu-id="d0062-107">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0062-107">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="creating-the-source-project"></a><span data-ttu-id="d0062-108">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="d0062-108">Creating the source project</span></span>

<span data-ttu-id="d0062-109">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0062-109">Open a shell window.</span></span> <span data-ttu-id="d0062-110">ソリューションを保持するための *unit-testing-using-dotnet-test* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0062-110">Create a directory called *unit-testing-using-dotnet-test* to hold the solution.</span></span> <span data-ttu-id="d0062-111">この新しいディレクトリ内に、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0062-111">Inside this new directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="d0062-112">現時点のディレクトリ構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="d0062-112">The directory structure thus far is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
```

<span data-ttu-id="d0062-113">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0062-113">Make *PrimeService* the current directory and run [`dotnet new classlib`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="d0062-114">*Class1.cs* の名前を *PrimeService.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="d0062-114">Rename *Class1.cs* to *PrimeService.cs*.</span></span> <span data-ttu-id="d0062-115">テスト駆動開発 (TDD) を使用するため、`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="d0062-115">To use test-driven development (TDD), you'll create a failing implementation of the `PrimeService` class:</span></span>

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

### <a name="creating-the-test-project"></a><span data-ttu-id="d0062-116">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="d0062-116">Creating the test project</span></span>

<span data-ttu-id="d0062-117">*unit-testing-using-mstest* ディレクトリに戻り、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0062-117">Change the directory back to the *unit-testing-using-mstest* directory and create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="d0062-118">ディレクトリ構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d0062-118">The directory structure is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

<span data-ttu-id="d0062-119">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new mstest`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0062-119">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new mstest`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="d0062-120">これにより、テスト ライブラリとして MStest を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d0062-120">This creates a test project that uses MStest as the test library.</span></span> <span data-ttu-id="d0062-121">生成されたテンプレートで、*PrimeServiceTests.csproj* ファイルのテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="d0062-121">The generated template configures the test runner in the *PrimeServiceTests.csproj* file:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.11" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11" />
</ItemGroup>
```

<span data-ttu-id="d0062-122">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="d0062-122">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="d0062-123">前の手順の `dotnet new` により、MSTest SDK、MSTest テスト フレームワーク、MSTest ランナーが追加されました。</span><span class="sxs-lookup"><span data-stu-id="d0062-123">`dotnet new` in the previous step added the MSTest SDK, the MSTest test framework, and the MSTest runner.</span></span> <span data-ttu-id="d0062-124">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0062-124">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="d0062-125">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0062-125">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

<span data-ttu-id="d0062-126">*PrimeService.Tests.csproj* ファイルを編集することもできます。</span><span class="sxs-lookup"><span data-stu-id="d0062-126">Another option is to edit the *PrimeService.Tests.csproj* file.</span></span> <span data-ttu-id="d0062-127">最初の `<ItemGroup>` ノードの下で直接、ライブラリ プロジェクトを参照する別の `<ItemGroup>` ノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="d0062-127">Directly under the first `<ItemGroup>` node, add another `<ItemGroup>` node with a reference to the library project:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\PrimeService\PrimeService.csproj" />
</ItemGroup>
```

<span data-ttu-id="d0062-128">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="d0062-128">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) on GitHub.</span></span>

<span data-ttu-id="d0062-129">最終的なソリューションのレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d0062-129">The final solution layout is shown below:</span></span>

```
/unit-testing-using-mstest
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService
        PrimeServiceTests.csproj
```

## <a name="creating-the-first-test"></a><span data-ttu-id="d0062-130">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="d0062-130">Creating the first test</span></span>

<span data-ttu-id="d0062-131">ライブラリまたはテストを構築する前に、*PrimeService.Tests* ディレクトリで [`dotnet restore`](../tools/dotnet-restore.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="d0062-131">Before building the library or the tests, execute [`dotnet restore`](../tools/dotnet-restore.md) in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="d0062-132">このコマンドにより、各プロジェクトの必要なすべての NuGet パッケージが復元されます。</span><span class="sxs-lookup"><span data-stu-id="d0062-132">This command restores all the necessary NuGet packages for each project.</span></span>

<span data-ttu-id="d0062-133">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d0062-133">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="d0062-134">*PrimeService.Tests* ディレクトリから *UnitTest1.cs* を削除し、*PrimeService_IsPrimeShould.cs* という名前の新しい C# ファイルを作成します。コンテンツは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d0062-134">Remove *UnitTest1.cs* from the *PrimeService.Tests* directory and create a new C# file named *PrimeService_IsPrimeShould.cs* with the following content:</span></span>

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

            Assert.IsFalse(result, $"1 should not be prime");
        }
    }
}
```

<span data-ttu-id="d0062-135">`[TestClass]` 属性は、単体テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="d0062-135">The `[TestClass]` attribute denotes a class that contains unit tests.</span></span> <span data-ttu-id="d0062-136">`[TestMethod]` 属性は、単一のテストとしてメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="d0062-136">The `[TestMethod]` attribute denotes a method as a single test.</span></span> 

<span data-ttu-id="d0062-137">このファイルを保存し、[`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドしてから、テストを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0062-137">Save this file and execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="d0062-138">MSTest テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d0062-138">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="d0062-139">`dotnet test` がテスト ランナーを開始し、テストを含むアセンブリを示すテスト ランナーにコマンド ライン引数を提供します。</span><span class="sxs-lookup"><span data-stu-id="d0062-139">`dotnet test` starts the test runner and provides a command-line argument to the test runner indicating the assembly that contains your tests.</span></span>

<span data-ttu-id="d0062-140">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="d0062-140">Your test fails.</span></span> <span data-ttu-id="d0062-141">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="d0062-141">You haven't created the implementation yet.</span></span> <span data-ttu-id="d0062-142">このテストを成功させるための最も簡単なコードを `PrimeService` クラスに記述します。</span><span class="sxs-lookup"><span data-stu-id="d0062-142">Write the simplest code in the `PrimeService` class to make this test pass:</span></span>

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

<span data-ttu-id="d0062-143">*PrimeService.Tests* ディレクトリで、`dotnet test` をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="d0062-143">In the *PrimeService.Tests* directory, run `dotnet test` again.</span></span> <span data-ttu-id="d0062-144">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0062-144">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="d0062-145">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="d0062-145">After building both projects, it runs this single test.</span></span> <span data-ttu-id="d0062-146">成功します。</span><span class="sxs-lookup"><span data-stu-id="d0062-146">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="d0062-147">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="d0062-147">Adding more features</span></span>

<span data-ttu-id="d0062-148">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="d0062-148">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="d0062-149">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="d0062-149">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="d0062-150">これらは `[TestMethod]` 属性を使用して新しいテストとして追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="d0062-150">You could add those as new tests with the `[TestMethod]` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="d0062-151">一連の類似のテストを記述できるようになる、他の MSTest 属性があります。</span><span class="sxs-lookup"><span data-stu-id="d0062-151">There are other MSTest attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="d0062-152">`[DataTestMethod]` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="d0062-152">A `[DataTestMethod]`attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="d0062-153">`[DataRow]` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d0062-153">You can use the `[DataRow]` attribute to specify values for those inputs.</span></span> 
 
<span data-ttu-id="d0062-154">新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストするデータ テスト メソッドを 1 つ作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="d0062-154">Instead of creating new tests, leverage these two attributes to create a single data test method that tests several values less than two, which is the lowest prime number:</span></span>

<span data-ttu-id="d0062-155">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span><span class="sxs-lookup"><span data-stu-id="d0062-155">[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]</span></span>

<span data-ttu-id="d0062-156">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="d0062-156">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="d0062-157">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="d0062-157">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```csharp
if (candidate < 2)
```

<span data-ttu-id="d0062-158">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="d0062-158">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="d0062-159">[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs)と[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs)により終了します。</span><span class="sxs-lookup"><span data-stu-id="d0062-159">You'll end up with the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="d0062-160">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="d0062-160">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="d0062-161">新しいパッケージとテストの追加がシームレスになり、アプリケーションの目標を解決するためにほとんどの時間と労力を注げるようにソリューションを構成しました。</span><span class="sxs-lookup"><span data-stu-id="d0062-161">You've structured the solution so that adding new packages and tests is seamless, and you can concentrate most of your time and effort on solving the goals of the applicaiton.</span></span>


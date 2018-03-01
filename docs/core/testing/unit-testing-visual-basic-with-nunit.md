---
title: "dotnet テストと NUnit を使用した .NET Core での単体テスト Visual Basic"
description: "NUnit を使用した Visual Basic ソリューションのサンプルを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core の単体テストの概念について説明します。"
author: rprouse
ms.date: 12/01/2017
ms.topic: article
dev_langs:
- vb
ms.prod: .net-core
ms.openlocfilehash: 2166da36fe9d0297f03e7c38249135d281b9a5d6
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a><span data-ttu-id="3fc94-103">dotnet テストと NUnit を使用した Visual Basic .NET Core ライブラリでの単体テスト</span><span class="sxs-lookup"><span data-stu-id="3fc94-103">Unit testing Visual Basic .NET Core libraries using dotnet test and NUnit</span></span>

<span data-ttu-id="3fc94-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="3fc94-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/)してください。</span><span class="sxs-lookup"><span data-stu-id="3fc94-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-vb-nunit/) before you begin.</span></span> <span data-ttu-id="3fc94-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc94-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="3fc94-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3fc94-107">Creating the source project</span></span>

<span data-ttu-id="3fc94-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-108">Open a shell window.</span></span> <span data-ttu-id="3fc94-109">ソリューションを保存するための *unit-testing-vb-nunit* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-109">Create a directory called *unit-testing-vb-nunit* to hold the solution.</span></span> <span data-ttu-id="3fc94-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、ソリューションを新たに作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="3fc94-111">こうすることで、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-111">This practice makes it easier to manage both the class library and the unit test project.</span></span> <span data-ttu-id="3fc94-112">ソリューションのディレクトリ内で、*PrimeService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-112">Inside the solution directory, create a *PrimeService* directory.</span></span> <span data-ttu-id="3fc94-113">現時点のディレクトリとファイルの構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="3fc94-113">You have the following directory and file structure thus far:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

<span data-ttu-id="3fc94-114">*PrimeService* を現在のディレクトリにし、[`dotnet new classlib -lang VB`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-114">Make *PrimeService* the current directory and run [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) to create the source project.</span></span> <span data-ttu-id="3fc94-115">*Class1.VB* の名前を *PrimeService.VB* に変更します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-115">Rename *Class1.VB* to *PrimeService.VB*.</span></span> <span data-ttu-id="3fc94-116">テスト駆動開発 (TDD) を行うには、`PrimeService` クラスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-116">To use test-driven development (TDD), you create a failing implementation of the `PrimeService` class:</span></span>

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

<span data-ttu-id="3fc94-117">*unit-testing-vb-using-stest* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-117">Change the directory back to the *unit-testing-vb-using-stest* directory.</span></span> <span data-ttu-id="3fc94-118">[`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-118">Run [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="3fc94-119">NUnit プロジェクト テンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="3fc94-119">Install the NUnit project template</span></span>

<span data-ttu-id="3fc94-120">NUnit テストのプロジェクト テンプレートは、テスト プロジェクトを作成する前にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-120">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="3fc94-121">これは、新しい NUnit プロジェクトを作成する開発者の各コンピューターで 1 回だけ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-121">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="3fc94-122">NUnit テンプレートをインストールするには、[`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-122">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="3fc94-123">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3fc94-123">Creating the test project</span></span>

<span data-ttu-id="3fc94-124">次に、*PrimeService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-124">Next, create the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="3fc94-125">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="3fc94-125">The following outline shows the directory structure:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

<span data-ttu-id="3fc94-126">*PrimeService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new nunit -lang VB`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-126">Make the *PrimeService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang VB`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="3fc94-127">このコマンドによって、テスト ライブラリとして NUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-127">This command creates a test project that uses NUnit as the test library.</span></span> <span data-ttu-id="3fc94-128">生成されたテンプレートで、*PrimeServiceTests.vbproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-128">The generated template configures the test runner in the *PrimeServiceTests.vbproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="3fc94-129">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="3fc94-129">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="3fc94-130">前の手順の `dotnet new` では、NUnit と NUnit のテスト アダプターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="3fc94-130">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="3fc94-131">ここで、プロジェクトに別の依存関係として `PrimeService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-131">Now, add the `PrimeService` class library as another dependency to the project.</span></span> <span data-ttu-id="3fc94-132">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-132">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

<span data-ttu-id="3fc94-133">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-133">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) on GitHub.</span></span>

<span data-ttu-id="3fc94-134">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-134">You have the following final solution layout:</span></span>

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

<span data-ttu-id="3fc94-135">*unit-testing-vb-nunit* ディレクトリで [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-135">Execute [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) in the *unit-testing-vb-nunit* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="3fc94-136">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="3fc94-136">Creating the first test</span></span>

<span data-ttu-id="3fc94-137">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-137">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="3fc94-138">*PrimeService.Tests* ディレクトリから *UnitTest1.vb* を削除し、*PrimeService_IsPrimeShould.VB* という名前の新しい Visual Basic ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-138">Remove *UnitTest1.vb* from the *PrimeService.Tests* directory and create a new Visual Basic file named *PrimeService_IsPrimeShould.VB*.</span></span> <span data-ttu-id="3fc94-139">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-139">Add the following code:</span></span>

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

<span data-ttu-id="3fc94-140">`<TestFixture>` 属性は、テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-140">The `<TestFixture>` attribute indicates a class that contains tests.</span></span> <span data-ttu-id="3fc94-141">`<Test>` 属性は、テスト ランナーによって実行されるメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-141">The `<Test>` attribute denotes a method that is run by the test runner.</span></span> <span data-ttu-id="3fc94-142">*unit-testing-vb-nunit* で [`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-142">From the *unit-testing-vb-nunit*, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="3fc94-143">NUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3fc94-143">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="3fc94-144">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-144">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="3fc94-145">テストが失敗します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-145">Your test fails.</span></span> <span data-ttu-id="3fc94-146">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="3fc94-146">You haven't created the implementation yet.</span></span> <span data-ttu-id="3fc94-147">最も単純な動作のコードを `PrimeService` クラスに記述して、このテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-147">Make this test by writing the simplest code in the `PrimeService` class that works:</span></span>

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

<span data-ttu-id="3fc94-148">*unit-testing-vb-nunit* ディレクトリで `dotnet test` をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-148">In the *unit-testing-vb-nunit* directory, run `dotnet test` again.</span></span> <span data-ttu-id="3fc94-149">`dotnet test` コマンドは `PrimeService` プロジェクトのビルドを実行してから、`PrimeService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-149">The `dotnet test` command runs a build for the `PrimeService` project and then for the `PrimeService.Tests` project.</span></span> <span data-ttu-id="3fc94-150">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-150">After building both projects, it runs this single test.</span></span> <span data-ttu-id="3fc94-151">成功します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-151">It passes.</span></span>

## <a name="adding-more-features"></a><span data-ttu-id="3fc94-152">他の機能の追加</span><span class="sxs-lookup"><span data-stu-id="3fc94-152">Adding more features</span></span>

<span data-ttu-id="3fc94-153">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="3fc94-153">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="3fc94-154">素数に関する、いくつかの単純なケースが他にもあります (0、-1)。</span><span class="sxs-lookup"><span data-stu-id="3fc94-154">There are a few other simple cases for prime numbers: 0, -1.</span></span> <span data-ttu-id="3fc94-155">`<Test>` 属性を使用すると、これらの例を新しいテストとして追加できますが、すぐに煩雑になります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-155">You could add those cases as new tests with the `<Test>` attribute, but that quickly becomes tedious.</span></span> <span data-ttu-id="3fc94-156">一連の類似のテストを記述できるようになる、他の xUnit 属性があります。</span><span class="sxs-lookup"><span data-stu-id="3fc94-156">There are other xUnit attributes that enable you to write a suite of similar tests.</span></span>  <span data-ttu-id="3fc94-157">`<TestCase>` 属性は同じコードを実行するものの、異なる入力引数が含まれる一連のテストを表します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-157">A `<TestCase>` attribute represents a suite of tests that execute the same code but have different input arguments.</span></span> <span data-ttu-id="3fc94-158">`<TestCase>` 属性を使用して、そのような入力の値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-158">You can use the `<TestCase>` attribute to specify values for those inputs.</span></span>

<span data-ttu-id="3fc94-159">新しいテストを作成する代わりに、この 2 つの属性を活用して、最も小さな素数である 2 未満の複数の値をテストする一連のテストを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="3fc94-159">Instead of creating new tests, apply these two attributes to create a series of tests that test several values less than two, which is the lowest prime number:</span></span>

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

<span data-ttu-id="3fc94-160">`dotnet test` を実行して、これらの 2 つのテストが失敗したとします。</span><span class="sxs-lookup"><span data-stu-id="3fc94-160">Run `dotnet test`, and two of these tests fail.</span></span> <span data-ttu-id="3fc94-161">すべてのテストを成功させるために、メソッドの先頭にある `if` 句を変更します。</span><span class="sxs-lookup"><span data-stu-id="3fc94-161">To make all of the tests pass, change the `if` clause at the beginning of the method:</span></span>

```vb
if candidate < 2
```

<span data-ttu-id="3fc94-162">他のテスト、理論、コードをメイン ライブラリに追加して、反復を続けます。</span><span class="sxs-lookup"><span data-stu-id="3fc94-162">Continue to iterate by adding more tests, more theories, and more code in the main library.</span></span> <span data-ttu-id="3fc94-163">[テストの最終版](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb)ができ、[ライブラリの完全な実装](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3fc94-163">You have the [finished version of the tests](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) and the [complete implementation of the library](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).</span></span>

<span data-ttu-id="3fc94-164">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="3fc94-164">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="3fc94-165">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="3fc94-165">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="3fc94-166">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="3fc94-166">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

---
title: dotnet テストと NUnit を使用した .NET Core での単体テスト F# ライブラリ
description: dotnet テストおよび NUnit を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core における F# の単体テストの概念について説明します。
author: rprouse
ms.date: 12/01/2017
dev_langs:
- fsharp
ms.openlocfilehash: c5653463ce43ab8660753aa03ef79ba10f339fac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215757"
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-nunit"></a><span data-ttu-id="9050f-103">dotnet テストと NUnit を使用した .NET Core での単体テスト F# ライブラリ</span><span class="sxs-lookup"><span data-stu-id="9050f-103">Unit testing F# libraries in .NET Core using dotnet test and NUnit</span></span>

<span data-ttu-id="9050f-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="9050f-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="9050f-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/)してください。</span><span class="sxs-lookup"><span data-stu-id="9050f-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-with-fsharp-nunit/) before you begin.</span></span> <span data-ttu-id="9050f-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9050f-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="9050f-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="9050f-107">Creating the source project</span></span>

<span data-ttu-id="9050f-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9050f-108">Open a shell window.</span></span> <span data-ttu-id="9050f-109">ソリューションを保存するための *unit-testing-with-fsharp* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="9050f-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、ソリューションを新たに作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="9050f-111">こうすることで、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="9050f-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="9050f-112">ソリューションのディレクトリ内で、*MathService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="9050f-113">現時点のディレクトリとファイルの構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="9050f-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="9050f-114">*MathService* を現在のディレクトリにし、[`dotnet new classlib -lang F#`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="9050f-115">テスト駆動開発 (TDD) を行うには、計算サービスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let squaresOfOdds xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="9050f-116">*unit-testing-with-fsharp* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="9050f-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="9050f-117">[`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="9050f-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="install-the-nunit-project-template"></a><span data-ttu-id="9050f-118">NUnit プロジェクト テンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="9050f-118">Install the NUnit project template</span></span>

<span data-ttu-id="9050f-119">NUnit テストのプロジェクト テンプレートは、テスト プロジェクトを作成する前にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9050f-119">The NUnit test project templates need to be installed before creating a test project.</span></span> <span data-ttu-id="9050f-120">これは、新しい NUnit プロジェクトを作成する開発者の各コンピューターで 1 回だけ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9050f-120">This only needs to be done once on each developer machine where you'll create new NUnit projects.</span></span> <span data-ttu-id="9050f-121">NUnit テンプレートをインストールするには、[`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="9050f-121">Run [`dotnet new -i NUnit3.DotNetNew.Template`](../tools/dotnet-new.md) to install the NUnit templates.</span></span>

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a><span data-ttu-id="9050f-122">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="9050f-122">Creating the test project</span></span>

<span data-ttu-id="9050f-123">次に、*MathService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-123">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="9050f-124">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="9050f-124">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="9050f-125">*MathService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new nunit -lang F#`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-125">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new nunit -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="9050f-126">これにより、テスト フレームワークとして NUnit を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9050f-126">This creates a test project that uses NUnit as the test framework.</span></span> <span data-ttu-id="9050f-127">生成されたテンプレートで、*MathServiceTests.fsproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="9050f-127">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

<span data-ttu-id="9050f-128">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="9050f-128">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="9050f-129">前の手順の `dotnet new` では、NUnit と NUnit のテスト アダプターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="9050f-129">`dotnet new` in the previous step added NUnit and the NUnit test adapter.</span></span> <span data-ttu-id="9050f-130">ここで、プロジェクトに別の依存関係として `MathService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="9050f-130">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="9050f-131">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9050f-131">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="9050f-132">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="9050f-132">You can see the entire file in the [samples repository](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="9050f-133">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9050f-133">You have the following final solution layout:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
        Test Source Files
        MathServiceTests.fsproj
```

<span data-ttu-id="9050f-134">*unit-testing-with-fsharp* ディレクトリで [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="9050f-134">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="9050f-135">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="9050f-135">Creating the first test</span></span>

<span data-ttu-id="9050f-136">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="9050f-136">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="9050f-137">*Tests.fs* を開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9050f-137">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open NUnit.Framework
open MathService

[<TestFixture>]
type TestClass () =

    [<Test>]
    member this.TestMethodPassing() =
        Assert.True(true)

    [<Test>]
     member this.FailEveryTime() = Assert.True(false)
```

<span data-ttu-id="9050f-138">`[<TestFixture>]` 属性は、テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="9050f-138">The `[<TestFixture>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="9050f-139">`[<Test>]` 属性は、テスト ランナーによって実行されるテスト メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="9050f-139">The `[<Test>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="9050f-140">*unit-testing-with-fsharp* ディレクトリで [`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="9050f-140">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="9050f-141">NUnit テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9050f-141">The NUnit test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="9050f-142">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="9050f-142">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="9050f-143">この 2 つのテストは、最も基本的な成功テストと失敗テストです。</span><span class="sxs-lookup"><span data-stu-id="9050f-143">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="9050f-144">`My test` は成功し、`Fail every time` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9050f-144">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="9050f-145">今度は `squaresOfOdds` メソッドのテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-145">Now, create a test for the `squaresOfOdds` method.</span></span> <span data-ttu-id="9050f-146">`squaresOfOdds` メソッドは、入力シーケンスに含まれるすべての奇数の整数値を 2 乗した値のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="9050f-146">The `squaresOfOdds` method returns a sequence of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="9050f-147">これらの関数をすべて一度に書き込むのではなく、機能を検証するテストを繰り返し作成することができます。</span><span class="sxs-lookup"><span data-stu-id="9050f-147">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="9050f-148">各テストを成功させることで、メソッドに必要な機能を作成することになります。</span><span class="sxs-lookup"><span data-stu-id="9050f-148">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="9050f-149">最も簡単に記述できるテストは、すべて偶数である数字を `squaresOfOdds` に渡して呼び出すことです。このテストの結果は、整数の空のシーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="9050f-149">The simplest test we can write is to call `squaresOfOdds` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="9050f-150">次に示すのがそのテストです。</span><span class="sxs-lookup"><span data-stu-id="9050f-150">Here's that test:</span></span>

```fsharp
[<Test>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int>
    let actual = MyMath.squaresOfOdds [2; 4; 6; 8; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="9050f-151">`expected` シーケンスがリストに変換されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9050f-151">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="9050f-152">NUnit ライブラリは、標準的な .NET 型の多くに依存しています。</span><span class="sxs-lookup"><span data-stu-id="9050f-152">The NUnit framework relies on many standard .NET types.</span></span> <span data-ttu-id="9050f-153">この依存関係は、お使いのパブリック インターフェイスおよび期待される結果が、<xref:System.Collections.IEnumerable> でなく <xref:System.Collections.ICollection> をサポートしていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9050f-153">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="9050f-154">テストを実行すると、失敗することがわかります。</span><span class="sxs-lookup"><span data-stu-id="9050f-154">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="9050f-155">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="9050f-155">You haven't created the implementation yet.</span></span> <span data-ttu-id="9050f-156">最も単純な動作のコードを `Mathservice` クラスに記述して、このテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="9050f-156">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let squaresOfOdds xs =
    Seq.empty<int>
```

<span data-ttu-id="9050f-157">*unit-testing-with-fsharp* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="9050f-157">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="9050f-158">`dotnet test` コマンドは `MathService` プロジェクトのビルドを実行してから、`MathService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9050f-158">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="9050f-159">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9050f-159">After building both projects, it runs this single test.</span></span> <span data-ttu-id="9050f-160">成功します。</span><span class="sxs-lookup"><span data-stu-id="9050f-160">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="9050f-161">要件の完成</span><span class="sxs-lookup"><span data-stu-id="9050f-161">Completing the requirements</span></span>

<span data-ttu-id="9050f-162">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="9050f-162">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="9050f-163">次の単純な例は、奇数は `1` のみが含まれるシーケンスで機能します。</span><span class="sxs-lookup"><span data-stu-id="9050f-163">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="9050f-164">数値の 1 は簡単です。なぜなら 1 の 2 乗は 1 になるためです。</span><span class="sxs-lookup"><span data-stu-id="9050f-164">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="9050f-165">次のテストを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9050f-165">Here's that next test:</span></span>

```fsharp
[<Test>]
member public this.TestOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.squaresOfOdds [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="9050f-166">`dotnet test` を実行すると、新しいテストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="9050f-166">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="9050f-167">新しいテストに対応するには `squaresOfOdds` メソッドを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9050f-167">You must update the `squaresOfOdds` method to handle this new test.</span></span> <span data-ttu-id="9050f-168">このテストを成功させるには、フィルター処理でシーケンスからすべての偶数を除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9050f-168">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="9050f-169">小さなフィルター関数を記述し、`Seq.filter` を使用することで実現できます。</span><span class="sxs-lookup"><span data-stu-id="9050f-169">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
```

<span data-ttu-id="9050f-170">`Seq.toList` を呼び出していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9050f-170">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="9050f-171">これにより、<xref:System.Collections.ICollection> インターフェイスを実装するリストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9050f-171">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="9050f-172">実施する手順がもう一つあります。各奇数を 2 乗します。</span><span class="sxs-lookup"><span data-stu-id="9050f-172">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="9050f-173">テストを新たに記述するところから始めます。</span><span class="sxs-lookup"><span data-stu-id="9050f-173">Start by writing a new test:</span></span>

```fsharp
[<Test>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.squaresOfOdds [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.That(actual, Is.EqualTo(expected))
```

<span data-ttu-id="9050f-174">テストを修正するには、フィルター処理したシーケンスをパイプでつなぎ、各奇数の 2 乗を計算するマップ操作をします。</span><span class="sxs-lookup"><span data-stu-id="9050f-174">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let squaresOfOdds xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
```

<span data-ttu-id="9050f-175">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="9050f-175">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="9050f-176">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="9050f-176">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="9050f-177">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="9050f-177">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

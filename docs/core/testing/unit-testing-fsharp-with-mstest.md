---
title: "dotnet テストと MSTest を使用した .NET Core での単体テスト F# ライブラリ"
description: "dotnet テストおよび MSTest を使用したサンプル ソリューションを段階的に構築していく対話型エクスペリエンスを通じて、.NET Core における F# の単体テストの概念について説明します。"
author: billwagner
ms.author: wiwagn
ms.date: 08/30/2017
ms.topic: article
dev_langs: fsharp
ms.prod: .net-core
ms.openlocfilehash: ad869d6b66ad5d966037a3ef38154fadcfa5978b
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2017
---
# <a name="unit-testing-f-libraries-in-net-core-using-dotnet-test-and-mstest"></a><span data-ttu-id="0394b-103">dotnet テストと MSTest を使用した .NET Core での単体テスト F# ライブラリ</span><span class="sxs-lookup"><span data-stu-id="0394b-103">Unit testing F# libraries in .NET Core using dotnet test and MSTest</span></span>

<span data-ttu-id="0394b-104">このチュートリアルでは、単体テストの概念について学習するためにサンプル ソリューションを段階的に構築する対話型のエクスペリエンスを示します。</span><span class="sxs-lookup"><span data-stu-id="0394b-104">This tutorial takes you through an interactive experience building a sample solution step-by-step to learn unit testing concepts.</span></span> <span data-ttu-id="0394b-105">構築済みのソリューションを使用してチュートリアルに従う場合は、開始する前に[サンプル コードを参照またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/)してください。</span><span class="sxs-lookup"><span data-stu-id="0394b-105">If you prefer to follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-with-fsharp-mstest/) before you begin.</span></span> <span data-ttu-id="0394b-106">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0394b-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="creating-the-source-project"></a><span data-ttu-id="0394b-107">ソース プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="0394b-107">Creating the source project</span></span>

<span data-ttu-id="0394b-108">シェル ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="0394b-108">Open a shell window.</span></span> <span data-ttu-id="0394b-109">ソリューションを保存するための *unit-testing-with-fsharp* というディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-109">Create a directory called *unit-testing-with-fsharp* to hold the solution.</span></span>
<span data-ttu-id="0394b-110">この新しいディレクトリ内で [`dotnet new sln`](../tools/dotnet-new.md) を実行して、ソリューションを新たに作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-110">Inside this new directory, run [`dotnet new sln`](../tools/dotnet-new.md) to create a new solution.</span></span> <span data-ttu-id="0394b-111">こうすることで、クラス ライブラリと単体テスト プロジェクトの両方を管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="0394b-111">This makes it easier to manage both the class library and the unit test project.</span></span>
<span data-ttu-id="0394b-112">ソリューションのディレクトリ内で、*MathService* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-112">Inside the solution directory, create a *MathService* directory.</span></span> <span data-ttu-id="0394b-113">現時点のディレクトリとファイルの構造は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="0394b-113">The directory and file structure thus far is shown below:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
```

<span data-ttu-id="0394b-114">*MathService* を現在のディレクトリにし、[`dotnet new classlib -lang F#`](../tools/dotnet-new.md) を実行してソース プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-114">Make *MathService* the current directory and run [`dotnet new classlib -lang F#`](../tools/dotnet-new.md) to create the source project.</span></span>  <span data-ttu-id="0394b-115">テスト駆動開発 (TDD) を行うには、計算サービスのエラーが発生する実装を作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-115">To use test-driven development (TDD), you'll create a failing implementation of the math service:</span></span>

```fsharp
module MyMath =
    let sumOfSquares xs = raise (System.NotImplementedException("You haven't written a test yet!"))
```

<span data-ttu-id="0394b-116">*unit-testing-with-fsharp* ディレクトリに戻ります。</span><span class="sxs-lookup"><span data-stu-id="0394b-116">Change the directory back to the *unit-testing-with-fsharp* directory.</span></span> <span data-ttu-id="0394b-117">[`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) を実行して、クラス ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="0394b-117">Run [`dotnet sln add .\MathService\MathService.fsproj`](../tools/dotnet-sln.md) to add the class library project to the solution.</span></span>

## <a name="creating-the-test-project"></a><span data-ttu-id="0394b-118">テスト プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="0394b-118">Creating the test project</span></span>

<span data-ttu-id="0394b-119">次に、*MathService.Tests* ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-119">Next, create the *MathService.Tests* directory.</span></span> <span data-ttu-id="0394b-120">次の一覧はディレクトリ構造を示したものです。</span><span class="sxs-lookup"><span data-stu-id="0394b-120">The following outline shows the directory structure:</span></span>

```
/unit-testing-with-fsharp
    unit-testing-with-fsharp.sln
    /MathService
        Source Files
        MathService.fsproj
    /MathService.Tests
```

<span data-ttu-id="0394b-121">*MathService.Tests* ディレクトリを現在のディレクトリにし、[`dotnet new mstest -lang F#`](../tools/dotnet-new.md) を使用して新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-121">Make the *MathService.Tests* directory the current directory and create a new project using [`dotnet new mstest -lang F#`](../tools/dotnet-new.md).</span></span> <span data-ttu-id="0394b-122">これにより、テスト フレームワークとして MSTest を使用するテスト プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0394b-122">This creates a test project that uses MSTest as the test framework.</span></span> <span data-ttu-id="0394b-123">生成されたテンプレートで、*MathServiceTests.fsproj* のテスト ランナーが構成されます。</span><span class="sxs-lookup"><span data-stu-id="0394b-123">The generated template configures the test runner in the *MathServiceTests.fsproj*:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

<span data-ttu-id="0394b-124">テスト プロジェクトには、単体テストを作成して実行するための、他のパッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="0394b-124">The test project requires other packages to create and run unit tests.</span></span> <span data-ttu-id="0394b-125">前の手順の `dotnet new` によって、MSTest と MSTest ランナーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="0394b-125">`dotnet new` in the previous step added MSTest and the MSTest runner.</span></span> <span data-ttu-id="0394b-126">ここで、プロジェクトに別の依存関係として `MathService` クラス ライブラリを追加します。</span><span class="sxs-lookup"><span data-stu-id="0394b-126">Now, add the `MathService` class library as another dependency to the project.</span></span> <span data-ttu-id="0394b-127">次の [`dotnet add reference`](../tools/dotnet-add-reference.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0394b-127">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```
dotnet add reference ../MathService/MathService.fsproj
```

<span data-ttu-id="0394b-128">全体のファイルは GitHub の[サンプル リポジトリ](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="0394b-128">You can see the entire file in the [samples repository](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-with-fsharp/MathService.Tests/MathService.Tests.fsproj) on GitHub.</span></span>

<span data-ttu-id="0394b-129">ソリューションの最終的なレイアウトは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0394b-129">You have the following final solution layout:</span></span>

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

<span data-ttu-id="0394b-130">*unit-testing-with-fsharp* ディレクトリで [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) を実行します。</span><span class="sxs-lookup"><span data-stu-id="0394b-130">Execute [`dotnet sln add .\MathService.Tests\MathService.Tests.fsproj`](../tools/dotnet-sln.md) in the *unit-testing-with-fsharp* directory.</span></span>

## <a name="creating-the-first-test"></a><span data-ttu-id="0394b-131">最初のテストの作成</span><span class="sxs-lookup"><span data-stu-id="0394b-131">Creating the first test</span></span>

<span data-ttu-id="0394b-132">TDD のアプローチでは、失敗するテストを 1 つ記述することを要求し、それを渡して、プロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="0394b-132">The TDD approach calls for writing one failing test, making it pass, then repeating the process.</span></span> <span data-ttu-id="0394b-133">*Tests.fs* を開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0394b-133">Open *Tests.fs* and add the following code:</span></span>

```fsharp
namespace MathService.Tests

open System
open Microsoft.VisualStudio.TestTools.UnitTesting
open MathService

[<TestClass>]
type TestClass () =

    [<TestMethod>]
    member this.TestMethodPassing() =
        Assert.IsTrue(true)

    [<TestMethod>]
     member this.FailEveryTime() = Assert.IsTrue(false)
```

<span data-ttu-id="0394b-134">`[<TestClass>]` 属性は、テストを含むクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="0394b-134">The `[<TestClass>]` attribute denotes a class that contains tests.</span></span> <span data-ttu-id="0394b-135">`[<TestMethod>]` 属性は、テスト ランナーによって実行されるテスト メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="0394b-135">The `[<TestMethod>]` attribute denotes a test method that is run by the test runner.</span></span> <span data-ttu-id="0394b-136">*unit-testing-with-fsharp* ディレクトリで [`dotnet test`](../tools/dotnet-test.md) を実行してテストとクラス ライブラリをビルドし、それからテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="0394b-136">From the *unit-testing-with-fsharp* directory, execute [`dotnet test`](../tools/dotnet-test.md) to build the tests and the class library and then run the tests.</span></span> <span data-ttu-id="0394b-137">MSTest テスト ランナーには、テストを実行するためのプログラムのエントリ ポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0394b-137">The MSTest test runner contains the program entry point to run your tests.</span></span> <span data-ttu-id="0394b-138">`dotnet test` を実行すると、作成した単体テスト プロジェクトを使用してテスト ランナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="0394b-138">`dotnet test` starts the test runner using the unit test project you've created.</span></span>

<span data-ttu-id="0394b-139">この 2 つのテストは、最も基本的な成功テストと失敗テストです。</span><span class="sxs-lookup"><span data-stu-id="0394b-139">These two tests show the most basic passing and failing tests.</span></span> <span data-ttu-id="0394b-140">`My test` は成功し、`Fail every time` は失敗します。</span><span class="sxs-lookup"><span data-stu-id="0394b-140">`My test` passes, and `Fail every time` fails.</span></span> <span data-ttu-id="0394b-141">今度は `sumOfSquares` メソッドのテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-141">Now, create a test for the `sumOfSquares` method.</span></span> <span data-ttu-id="0394b-142">`sumOfSquares` メソッドは、入力シーケンスに含まれるすべての奇数の整数値を 2 乗して合計した値を返します。</span><span class="sxs-lookup"><span data-stu-id="0394b-142">The `sumOfSquares` method returns the sum of the squares of all odd integer values that are part of the input sequence.</span></span> <span data-ttu-id="0394b-143">これらの関数をすべて一度に書き込むのではなく、機能を検証するテストを繰り返し作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0394b-143">Rather than trying to write all of those functions at once, you can iteratively create tests that validate the functionality.</span></span> <span data-ttu-id="0394b-144">各テストを成功させることで、メソッドに必要な機能を作成することになります。</span><span class="sxs-lookup"><span data-stu-id="0394b-144">Making each test pass means creating the necessary functionality for the method.</span></span>

<span data-ttu-id="0394b-145">最も簡単に記述できるテストは、すべて偶数である数字を `sumOfSquares` に渡して呼び出すことです。このテストの結果は、整数の空のシーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="0394b-145">The simplest test we can write is to call `sumOfSquares` with all even numbers, where the result should be an empty sequence of integers.</span></span>  <span data-ttu-id="0394b-146">次に示すのがそのテストです。</span><span class="sxs-lookup"><span data-stu-id="0394b-146">Here's that test:</span></span>

```fsharp
[<TestMethod>]
member this.TestEvenSequence() =
    let expected = Seq.empty<int> |> Seq.toList
    let actual = MyMath.sumOfSquares [2; 4; 6; 8; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="0394b-147">`expected` シーケンスがリストに変換されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0394b-147">Notice that the `expected` sequence has been converted to a list.</span></span> <span data-ttu-id="0394b-148">MSTest ライブラリは、標準的な .NET 型の多くに依存しています。</span><span class="sxs-lookup"><span data-stu-id="0394b-148">The MSTest library relies on many standard .NET types.</span></span> <span data-ttu-id="0394b-149">この依存関係は、お使いのパブリック インターフェイスおよび期待される結果が、<xref:System.Collections.IEnumerable> でなく <xref:System.Collections.ICollection> をサポートしていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0394b-149">That dependency means that your public interface and expected results support <xref:System.Collections.ICollection> rather than <xref:System.Collections.IEnumerable>.</span></span>

<span data-ttu-id="0394b-150">テストを実行すると、失敗することがわかります。</span><span class="sxs-lookup"><span data-stu-id="0394b-150">When you run the test, you see that your test fails.</span></span> <span data-ttu-id="0394b-151">実装はまだ作成していません。</span><span class="sxs-lookup"><span data-stu-id="0394b-151">You haven't created the implementation yet.</span></span> <span data-ttu-id="0394b-152">最も単純な動作のコードを `Mathservice` クラスに記述して、このテストを作成します。</span><span class="sxs-lookup"><span data-stu-id="0394b-152">Make this test by writing the simplest code in the `Mathservice` class that works:</span></span>

```csharp
let sumOfSquares xs =
    Seq.empty<int> |> Seq.toList
```

<span data-ttu-id="0394b-153">*unit-testing-with-fsharp* ディレクトリで、もう一度 `dotnet test` を実行します。</span><span class="sxs-lookup"><span data-stu-id="0394b-153">In the *unit-testing-with-fsharp* directory, run `dotnet test` again.</span></span> <span data-ttu-id="0394b-154">`dotnet test` コマンドは `MathService` プロジェクトのビルドを実行してから、`MathService.Tests` プロジェクトのビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0394b-154">The `dotnet test` command runs a build for the `MathService` project and then for the `MathService.Tests` project.</span></span> <span data-ttu-id="0394b-155">両方のプロジェクトをビルドすると、この単一テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0394b-155">After building both projects, it runs this single test.</span></span> <span data-ttu-id="0394b-156">成功します。</span><span class="sxs-lookup"><span data-stu-id="0394b-156">It passes.</span></span>

## <a name="completing-the-requirements"></a><span data-ttu-id="0394b-157">要件の完成</span><span class="sxs-lookup"><span data-stu-id="0394b-157">Completing the requirements</span></span>

<span data-ttu-id="0394b-158">テストが成功したので、他のテストも記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="0394b-158">Now that you've made one test pass, it's time to write more.</span></span> <span data-ttu-id="0394b-159">次の単純な例は、奇数は `1` のみが含まれるシーケンスで機能します。</span><span class="sxs-lookup"><span data-stu-id="0394b-159">The next simple case works with a sequence whose only odd number is `1`.</span></span> <span data-ttu-id="0394b-160">数値の 1 は簡単です。なぜなら 1 の 2 乗は 1 になるためです。</span><span class="sxs-lookup"><span data-stu-id="0394b-160">The number 1 is easier because the square of 1 is 1.</span></span> <span data-ttu-id="0394b-161">次のテストを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="0394b-161">Here's that next test:</span></span>

```fsharp
[<TestMethod>]
member public this.SumOnesAndEvens() =
    let expected = [1; 1; 1; 1]
    let actual = MyMath.sumOfSquares [2; 1; 4; 1; 6; 1; 8; 1; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="0394b-162">`dotnet test` を実行すると、新しいテストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="0394b-162">Executing `dotnet test` fails the new test.</span></span> <span data-ttu-id="0394b-163">新しいテストに対応するには `sumOfSquares` メソッドを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0394b-163">You must update the `sumOfSquares` method to handle this new test.</span></span> <span data-ttu-id="0394b-164">このテストを成功させるには、フィルター処理でシーケンスからすべての偶数を除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0394b-164">You must filter all the even numbers out of the sequence to make this test pass.</span></span> <span data-ttu-id="0394b-165">小さなフィルター関数を記述し、`Seq.filter` を使用することで実現できます。</span><span class="sxs-lookup"><span data-stu-id="0394b-165">You can do that by writing a small filter function and using `Seq.filter`:</span></span>

```fsharp
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd |> Seq.toList
```

<span data-ttu-id="0394b-166">`Seq.toList` を呼び出していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0394b-166">Notice the call to `Seq.toList`.</span></span> <span data-ttu-id="0394b-167">これにより、<xref:System.Collections.ICollection> インターフェイスを実装するリストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0394b-167">That creates a list, which implements the <xref:System.Collections.ICollection> interface.</span></span>

<span data-ttu-id="0394b-168">実施する手順がもう一つあります。各奇数を 2 乗します。</span><span class="sxs-lookup"><span data-stu-id="0394b-168">There's one more step to go: square each of the odd numbers.</span></span> <span data-ttu-id="0394b-169">テストを新たに記述するところから始めます。</span><span class="sxs-lookup"><span data-stu-id="0394b-169">Start by writing a new test:</span></span>

```fsharp
[<TestMethod>]
member public this.TestSquaresOfOdds() =
    let expected = [1; 9; 25; 49; 81]
    let actual = MyMath.sumOfSquares [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
    Assert.AreEqual(expected, actual)
```

<span data-ttu-id="0394b-170">テストを修正するには、フィルター処理したシーケンスをパイプでつなぎ、各奇数の 2 乗を計算するマップ操作をします。</span><span class="sxs-lookup"><span data-stu-id="0394b-170">You can fix the test by piping the filtered sequence through a map operation to compute the square of each odd number:</span></span>

```fsharp
let private square x = x * x
let private isOdd x = x % 2 <> 0

let sumOfSquares xs =
    xs
    |> Seq.filter isOdd
    |> Seq.map square
    |> Seq.toList
```

<span data-ttu-id="0394b-171">これで、小さなライブラリとそのライブラリの単体テストのセットが構築されました。</span><span class="sxs-lookup"><span data-stu-id="0394b-171">You've built a small library and a set of unit tests for that library.</span></span> <span data-ttu-id="0394b-172">ソリューションを構築したことで、新しいパッケージとテストの追加が通常のワークフローに組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="0394b-172">You've structured the solution so that adding new packages and tests is part of the normal workflow.</span></span> <span data-ttu-id="0394b-173">アプリケーションの目標を達成することに時間と労力の多くを割き、集中して取り組みました。</span><span class="sxs-lookup"><span data-stu-id="0394b-173">You've concentrated most of your time and effort on solving the goals of the application.</span></span>

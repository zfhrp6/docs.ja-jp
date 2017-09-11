---
title: "ローカル関数とラムダ式の比較"
description: "ローカル関数がラムダ式よりも適した選択肢となり得る理由について。"
keywords: "C#, .NET, .NET Core, 最新の機能, 新機能, ローカル関数, ラムダ式"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: 9bb17207ba72bb22f5d6db55e9d1bd77e3013445
ms.openlocfilehash: 0730e7b7d6e3ef7b5c534d16baacde6a7dafacfc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/25/2017

---
# <a name="local-functions-compared-to-lambda-expressions"></a><span data-ttu-id="63185-104">ローカル関数とラムダ式の比較</span><span class="sxs-lookup"><span data-stu-id="63185-104">Local functions compared to Lambda expressions</span></span>

<span data-ttu-id="63185-105">一見したところ、[ローカル関数](programming-guide/classes-and-structs/local-functions.md)と[ラムダ式](lambda-expressions.md)は、非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="63185-105">At first glance, [local functions](programming-guide/classes-and-structs/local-functions.md) and [lambda expressions](lambda-expressions.md) are very similar.</span></span>
<span data-ttu-id="63185-106">ローカル関数は、必要に応じてより使いやすく、単純なソリューションにすることができます。</span><span class="sxs-lookup"><span data-stu-id="63185-106">Depending on your needs, local functions may be a much better and simpler solution.</span></span>

<span data-ttu-id="63185-107">階乗アルゴリズムのローカル関数とラムダ式の実装の違いについて見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="63185-107">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="63185-108">まずは、ローカル関数を使用するバージョンです。</span><span class="sxs-lookup"><span data-stu-id="63185-108">First the version using a local function:</span></span>

<span data-ttu-id="63185-109">[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "ローカル関数を使用する再帰的階乗、")]</span><span class="sxs-lookup"><span data-stu-id="63185-109">[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]</span></span>

<span data-ttu-id="63185-110">ラムダ式を使用するバージョンの実装と比較します。</span><span class="sxs-lookup"><span data-stu-id="63185-110">Contrast that implementation with a version that uses lambda expressions:</span></span>

<span data-ttu-id="63185-111">[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "ラムダ式を使用する再帰的階乗、")]</span><span class="sxs-lookup"><span data-stu-id="63185-111">[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]</span></span>

<span data-ttu-id="63185-112">最初に、ラムダ式は、デリゲートをインスタンス化して、そのデリゲートを呼び出すことで実装されます。</span><span class="sxs-lookup"><span data-stu-id="63185-112">First, lambda expressions are implemented by instantiating a delegate and invoking that delegate.</span></span> <span data-ttu-id="63185-113">ローカル関数は、メソッド呼び出しとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="63185-113">Local functions are implemented as method calls.</span></span>
<span data-ttu-id="63185-114">ラムダ式に必要なインスタンス化では、余分なメモリの割り当てが必要となり、タイム クリティカルなコード パスに影響を与えるパフォーマンス因子となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="63185-114">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time critical code paths.</span></span>
<span data-ttu-id="63185-115">ローカル関数では、このオーバーヘッドは発生しません。</span><span class="sxs-lookup"><span data-stu-id="63185-115">Local functions do not incur this overhead.</span></span> <span data-ttu-id="63185-116">上記の例では、ローカル関数のバージョンは、ラムダ式のバージョンよりも割り当てが 2 つ少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="63185-116">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

<span data-ttu-id="63185-117">この再帰メソッドは十分に単純で、ローカル関数がコンパイラによって生成された名前のプライベート メソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="63185-117">This recursive method is simple enough that the local function is implemented as a private method with a compiler generated name.</span></span> <span data-ttu-id="63185-118">他のプライベート メソッドとの唯一の違いは、外側の関数内に意味的な範囲が指定されていることです。</span><span class="sxs-lookup"><span data-stu-id="63185-118">Its only difference from other private methods is that it is semantically scoped inside the outer function.</span></span>

<span data-ttu-id="63185-119">第 2 に、ローカル関数は、定義の前でも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="63185-119">Second, local functions can be called before they are defined.</span></span> <span data-ttu-id="63185-120">ラムダ式は、定義の前に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63185-120">Lambda expressions must be declared before they are defined.</span></span> <span data-ttu-id="63185-121">つまり、先に示したように、ローカル関数は再帰的なアルゴリズムで使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="63185-121">This means local functions are easier to use in recursive algorithms, as shown above.</span></span>

<span data-ttu-id="63185-122">ラムダ式を使用したバージョンでは、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="63185-122">Notice that the version using the lambda expression must declare and initialize the lambda expression, `nthFactorial` before defining it.</span></span> <span data-ttu-id="63185-123">その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="63185-123">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>
<span data-ttu-id="63185-124">再帰的なアルゴリズムの作成は、ローカル関数を使用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="63185-124">Recursive algorithms are easier to create using local functions.</span></span>

<span data-ttu-id="63185-125">第 3 に、ラムダ式の場合、コンパイラで匿名クラスとそのクラスのインスタンスを作成し、クロージャによってキャプチャされたすべての変数を常に格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63185-125">Third, for lambda expressions, the compiler must always create an anonymous class and an instance of that class to store any variables captured by the closure.</span></span> <span data-ttu-id="63185-126">次の非同期の例について考えます。</span><span class="sxs-lookup"><span data-stu-id="63185-126">Consider this async example:</span></span>

<span data-ttu-id="63185-127">[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "ラムダ式を使用するメソッドを返すタスク、")]</span><span class="sxs-lookup"><span data-stu-id="63185-127">[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]</span></span>

<span data-ttu-id="63185-128">このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。</span><span class="sxs-lookup"><span data-stu-id="63185-128">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="63185-129">ローカル関数の場合、クロージャを実装するオブジェクトが `struct` になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="63185-129">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="63185-130">その場合、割り当てが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="63185-130">That would save on an allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="63185-131">このメソッドのローカル関数と同等のものも、同じクロージャのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="63185-131">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="63185-132">ローカル関数のクロージャが `class` として実装される場合でも、実装の詳細が `struct` である場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="63185-132">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="63185-133">ローカル関数は `struct` を使用する場合がありますが、ラムダは常に `class` を使用します。</span><span class="sxs-lookup"><span data-stu-id="63185-133">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

<span data-ttu-id="63185-134">[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "ローカル関数を持つメソッドを返すタスク")]</span><span class="sxs-lookup"><span data-stu-id="63185-134">[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]</span></span>

<span data-ttu-id="63185-135">この例では説明しませんが、最後の 1 つの利点は値のシーケンスを生成するために `yield return` 構文を使用して、ローカル関数を反復子として実装できることです。</span><span class="sxs-lookup"><span data-stu-id="63185-135">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span>

<span data-ttu-id="63185-136">ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。</span><span class="sxs-lookup"><span data-stu-id="63185-136">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span>
<span data-ttu-id="63185-137">ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。</span><span class="sxs-lookup"><span data-stu-id="63185-137">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>


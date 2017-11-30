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
ms.openlocfilehash: 20312b58a24dc991791edad4bb92d3a8ca6d501a
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="local-functions-compared-to-lambda-expressions"></a><span data-ttu-id="a7644-104">ラムダ式と比較して、ローカル関数</span><span class="sxs-lookup"><span data-stu-id="a7644-104">Local functions compared to lambda expressions</span></span>

<span data-ttu-id="a7644-105">一見したところ、[ローカル関数](programming-guide/classes-and-structs/local-functions.md)と[ラムダ式](lambda-expressions.md)は、非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="a7644-105">At first glance, [local functions](programming-guide/classes-and-structs/local-functions.md) and [lambda expressions](lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="a7644-106">多くの場合は、ラムダ式とローカル関数を使用して、選択は、スタイルと各ユーザーの好みの問題です。</span><span class="sxs-lookup"><span data-stu-id="a7644-106">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="a7644-107">ただし、どちらか一方を認識しておく必要がありますを使用する実際の相違があります。</span><span class="sxs-lookup"><span data-stu-id="a7644-107">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="a7644-108">階乗アルゴリズムのローカル関数とラムダ式の実装の違いについて見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="a7644-108">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="a7644-109">まずは、ローカル関数を使用するバージョンです。</span><span class="sxs-lookup"><span data-stu-id="a7644-109">First the version using a local function:</span></span>

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

<span data-ttu-id="a7644-110">ラムダ式を使用するバージョンの実装と比較します。</span><span class="sxs-lookup"><span data-stu-id="a7644-110">Contrast that implementation with a version that uses lambda expressions:</span></span>

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

<span data-ttu-id="a7644-111">ローカルの関数名であります。</span><span class="sxs-lookup"><span data-stu-id="a7644-111">The local functions have names.</span></span> <span data-ttu-id="a7644-112">ラムダ式には、匿名メソッド、変数に割り当てられている`Func`または`Action`型です。</span><span class="sxs-lookup"><span data-stu-id="a7644-112">The lambda expressions are anonymous methods that are assigned to variables that are `Func` or `Action` types.</span></span> <span data-ttu-id="a7644-113">ローカル関数を宣言するときに、引数の型と戻り値の型には、関数の宣言の一部です。</span><span class="sxs-lookup"><span data-stu-id="a7644-113">When you declare a local function, the argument types and return type are part of the function declaration.</span></span> <span data-ttu-id="a7644-114">ラムダの本体の一部ではなく式では、引数の型と戻り値の型は、ラムダ式の変数の型宣言の一部です。</span><span class="sxs-lookup"><span data-stu-id="a7644-114">Instead of being part of the body of the lambda expression, the argument types and return type are part of the lambda expression's variable type declaration.</span></span> <span data-ttu-id="a7644-115">これら 2 つの違いは、わかりやすいコードがあります。</span><span class="sxs-lookup"><span data-stu-id="a7644-115">Those two differences may result in clearer code.</span></span>

<span data-ttu-id="a7644-116">ローカル関数は、ラムダ式よりも確実な割り当てのルールを設定します。</span><span class="sxs-lookup"><span data-stu-id="a7644-116">Local functions have different rules for definite assignment than lambda expressions.</span></span> <span data-ttu-id="a7644-117">ローカル関数宣言は、スコープ内にある任意のコードの場所から参照できます。</span><span class="sxs-lookup"><span data-stu-id="a7644-117">A local function declaration can be referenced from any code location where it is in scope.</span></span> <span data-ttu-id="a7644-118">ラムダ式は、アクセス (したりできる、ラムダ式を参照している delgate を通じて呼び出されます。) 前に、デリゲート変数に割り当てる必要があります。ラムダ式を使用したバージョンでは、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7644-118">A lambda expression must be assigned to a delegate variable before it can be accessed (or called through the delgate referencing the lambda expression.) Notice that the version using the lambda expression must declare and initialize the lambda expression, `nthFactorial` before defining it.</span></span> <span data-ttu-id="a7644-119">その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a7644-119">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span>
<span data-ttu-id="a7644-120">これらの相違点は、再帰的なアルゴリズムは簡単にローカル関数を使用して作成することを意味します。</span><span class="sxs-lookup"><span data-stu-id="a7644-120">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="a7644-121">宣言し、それ自体を呼び出すローカル関数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a7644-121">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="a7644-122">ラムダ式は、宣言、および同じラムダ式を参照する本文に再割り当てできるようにするには、既定値を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7644-122">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

<span data-ttu-id="a7644-123">確実な代入規則では、ローカル関数またはラムダ epression によってキャプチャされたすべての変数にも影響します。</span><span class="sxs-lookup"><span data-stu-id="a7644-123">Definite assignment rules also affect any variables that are captured by the local function or lamdba epression.</span></span> <span data-ttu-id="a7644-124">ローカル関数とラムダ式の規則の両方、キャプチャされた変数は間違いなく割り当てられている時点でローカル関数またはラムダ式をデリゲートに変換するときを要求します。</span><span class="sxs-lookup"><span data-stu-id="a7644-124">Both local functions and lambda expression rules demand that any captured variables are definitely assigned at the point when the local function or lambda expression is converted to a delegate.</span></span> <span data-ttu-id="a7644-125">違いは、宣言する場合、ラムダ式をデリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="a7644-125">The difference is that lambda expressions are converted to delegates when they are declared.</span></span> <span data-ttu-id="a7644-126">ローカル関数は、代理人として使用する場合にのみ、デリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="a7644-126">Local functions are converted to delegates only when used as a delegate.</span></span> <span data-ttu-id="a7644-127">ローカル関数宣言をのみ、メソッドのように呼び出すことによって参照する場合は、デリゲートに変換されません。</span><span class="sxs-lookup"><span data-stu-id="a7644-127">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span> <span data-ttu-id="a7644-128">その規則では、その外側のスコープ内の任意の便利な場所でローカル関数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="a7644-128">That rule enables you to declare a local function at any convenient location in its enclosing scope.</span></span> <span data-ttu-id="a7644-129">すべての return ステートメントの後に、親メソッドの末尾にローカル関数を宣言する通常はします。</span><span class="sxs-lookup"><span data-stu-id="a7644-129">It's common to declare local functions at the end of the parent method, after any return statements.</span></span>

<span data-ttu-id="a7644-130">3 番目に、コンパイラを確実に外側のスコープでキャプチャされた変数を代入するローカル関数を有効にする静的な分析を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a7644-130">Third, the compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="a7644-131">次の例について考えます。</span><span class="sxs-lookup"><span data-stu-id="a7644-131">Consider this example:</span></span>

```csharp
bool M()
{
    int y;
    Local();
    return y;

    void Local() => y = 0;
}
```

<span data-ttu-id="a7644-132">コンパイラが判別されること`Local`確実割り当てます`y`呼び出されたときにします。</span><span class="sxs-lookup"><span data-stu-id="a7644-132">The compiler can determine that `Local` definitely assigns `y` when called.</span></span> <span data-ttu-id="a7644-133">`Local`前に呼び出されます、`return`ステートメントでは、 `y` definitiely はで割り当てられている、`return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="a7644-133">Because `Local` is called before the `return` statement, `y` is definitiely assigned at the `return` statement.</span></span>

<span data-ttu-id="a7644-134">その分析を有効にする分析では、4 番目の相違点を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7644-134">The analysis that enables that analysis enables the fourth difference.</span></span>
<span data-ttu-id="a7644-135">使用によってローカル関数は常にラムダ式用に必要なヒープ割り当てを回避できます。</span><span class="sxs-lookup"><span data-stu-id="a7644-135">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="a7644-136">ローカル関数は、デリゲートに変換されていない場合、その他の形式のラムダまたはデリゲートに変換されるローカル関数によってキャプチャされるローカル関数によってキャプチャされる変数のいずれも、コンパイラは、ヒープ割り当てを回避できます。</span><span class="sxs-lookup"><span data-stu-id="a7644-136">If a local function is never converted to a delegate, and none of the variables captured by the local function is captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span> 

<span data-ttu-id="a7644-137">次の非同期の例について考えます。</span><span class="sxs-lookup"><span data-stu-id="a7644-137">Consider this async example:</span></span>

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

<span data-ttu-id="a7644-138">このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。</span><span class="sxs-lookup"><span data-stu-id="a7644-138">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="a7644-139">ローカル関数の場合、クロージャを実装するオブジェクトが `struct` になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7644-139">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="a7644-140">その構造体の型は、ローカル関数への参照によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="a7644-140">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="a7644-141">この実装の違いが、割り当てに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a7644-141">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="a7644-142">ラムダ式のために必要なインスタンス化では、余分なメモリの割り当ては、タイム クリティカルなコード パスでのパフォーマンス要因となる可能性がありますを意味します。</span><span class="sxs-lookup"><span data-stu-id="a7644-142">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span>
<span data-ttu-id="a7644-143">ローカル関数では、このオーバーヘッドは発生しません。</span><span class="sxs-lookup"><span data-stu-id="a7644-143">Local functions do not incur this overhead.</span></span> <span data-ttu-id="a7644-144">上記の例では、ローカル関数のバージョンは、ラムダ式のバージョンよりも割り当てが 2 つ少なくなっています。</span><span class="sxs-lookup"><span data-stu-id="a7644-144">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

> [!NOTE]
> <span data-ttu-id="a7644-145">このメソッドのローカル関数と同等のものも、同じクロージャのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7644-145">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="a7644-146">ローカル関数のクロージャが `class` として実装される場合でも、実装の詳細が `struct` である場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="a7644-146">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="a7644-147">ローカル関数は `struct` を使用する場合がありますが、ラムダは常に `class` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a7644-147">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

<span data-ttu-id="a7644-148">この例では説明しませんが、最後の 1 つの利点は値のシーケンスを生成するために `yield return` 構文を使用して、ローカル関数を反復子として実装できることです。</span><span class="sxs-lookup"><span data-stu-id="a7644-148">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span> <span data-ttu-id="a7644-149">`yield return`ステートメントがラムダ式で許可されていません。</span><span class="sxs-lookup"><span data-stu-id="a7644-149">The `yield return` statement is not allowed in lambda expressions.</span></span>

<span data-ttu-id="a7644-150">ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。</span><span class="sxs-lookup"><span data-stu-id="a7644-150">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span>
<span data-ttu-id="a7644-151">ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a7644-151">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

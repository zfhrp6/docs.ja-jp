---
title: ラムダ式
description: 引数として渡すことができる実行可能コード ブロックであるラムダ式の使用方法について説明します。
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: e37f0e72ee02915d16509fb2ff48bd114e8ad466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lambda-expressions"></a><span data-ttu-id="2427b-103">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="2427b-103">Lambda expressions</span></span> #

<span data-ttu-id="2427b-104">"*ラムダ式*" は、オブジェクトとして扱われるコード ブロック (式またはステートメント ブロック) です。</span><span class="sxs-lookup"><span data-stu-id="2427b-104">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="2427b-105">これは、引数としてメソッドに渡すことができるほか、メソッドの呼び出しによって返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2427b-105">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="2427b-106">ラムダ式は、次の処理によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="2427b-106">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="2427b-107"><xref:System.Threading.Tasks.Task.Run(System.Action)> など、非同期メソッドに対して実行されるコードを渡す。</span><span class="sxs-lookup"><span data-stu-id="2427b-107">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="2427b-108">[LINQ クエリ式](linq/index.md)を記述する。</span><span class="sxs-lookup"><span data-stu-id="2427b-108">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="2427b-109">[式ツリー](expression-trees-building.md)を作成する。</span><span class="sxs-lookup"><span data-stu-id="2427b-109">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="2427b-110">ラムダ式は、デリゲート、またはデリゲートにコンパイルされる式ツリーとして表現できるコードです。</span><span class="sxs-lookup"><span data-stu-id="2427b-110">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="2427b-111">ラムダ式の特定のデリゲート型は、パラメーターや戻り値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2427b-111">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="2427b-112">値を返さないラムダ式は、そのパラメーター数に応じて、特定の `Action` デリゲートに対応します。</span><span class="sxs-lookup"><span data-stu-id="2427b-112">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="2427b-113">値を返すラムダ式は、そのパラメーター数に応じて、特定の `Func` デリゲートに対応します。</span><span class="sxs-lookup"><span data-stu-id="2427b-113">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="2427b-114">たとえば、2 つのパラメーターがあっても値を返さないラムダ式は、<xref:System.Action%602> デリゲートに対応します。</span><span class="sxs-lookup"><span data-stu-id="2427b-114">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="2427b-115">パラメーターが 1 つあり、値を返すラムダ式は、<xref:System.Func%602> デリゲートに対応します。</span><span class="sxs-lookup"><span data-stu-id="2427b-115">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="2427b-116">ラムダ式は、`=>` ([ラムダ宣言演算子](language-reference/operators/lambda-operator.md)) を使用して、ラムダのパラメーター リストを実行可能コードから分離します。</span><span class="sxs-lookup"><span data-stu-id="2427b-116">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="2427b-117">ラムダ式を作成するには、ラムダ演算子の左側に入力パラメーター (ある場合) を指定し、反対側に式またはステートメント ブロックを置きます。</span><span class="sxs-lookup"><span data-stu-id="2427b-117">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="2427b-118">たとえば、1 行のラムダ式 `x => x * x` は、`x` という名前のパラメーターを指定し、`x` を 2 乗した値を返します。</span><span class="sxs-lookup"><span data-stu-id="2427b-118">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="2427b-119">次の例に示すように、この式をデリゲート型に割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="2427b-119">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="2427b-120">また、メソッドの引数として直接渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2427b-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="2427b-121">式形式のラムダ</span><span class="sxs-lookup"><span data-stu-id="2427b-121">Expression lambdas</span></span> ##

 <span data-ttu-id="2427b-122">=> 演算子の右辺に式があるラムダ式を "*式形式のラムダ*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="2427b-122">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="2427b-123">式形式のラムダは、[式ツリー](expression-trees.md)の構築に幅広く使用されます。</span><span class="sxs-lookup"><span data-stu-id="2427b-123">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="2427b-124">式形式のラムダは式の結果を返します。基本的な形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2427b-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="2427b-125">かっこはラムダの入力パラメーターが 1 つの場合のみ省略可能で、それ以外の場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="2427b-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="2427b-126">入力パラメーターがないことを指定するには、次のように空のかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="2427b-126">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="2427b-127">入力パラメーターが 2 つ以上ある場合は、かっこで囲んで各パラメーターをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="2427b-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="2427b-128">通常、コンパイラは、パラメーターの型を判定する際に型の推定を使用します。</span><span class="sxs-lookup"><span data-stu-id="2427b-128">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="2427b-129">ただし、コンパイラが入力の型を推定するのが困難または不可能な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2427b-129">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="2427b-130">このような場合は、次の例に示すように、型を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="2427b-130">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="2427b-131">この例では、式形式のラムダの本体をメソッド呼び出しで構成できることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="2427b-131">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="2427b-132">ただし、SQL Server や Entity Framework (EF) など、.NET Framework の外部で評価される式ツリーを作成する場合は、ラムダ式内でメソッド呼び出しを使用することを控える必要があります。これは、.NET 実装のコンテキストの外部では、これらのメソッドが通用しない可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="2427b-132">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="2427b-133">この状況でメソッド呼び出しを使用する場合は、メソッド呼び出しを正常に解決できるように必ず徹底的にテストしてください。</span><span class="sxs-lookup"><span data-stu-id="2427b-133">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfuly resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="2427b-134">ステートメント形式のラムダ</span><span class="sxs-lookup"><span data-stu-id="2427b-134">Statement lambdas</span></span> ##

<span data-ttu-id="2427b-135">ステートメント形式のラムダは式形式のラムダに似ていますが、ステートメントが中かっこで囲まれる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="2427b-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="2427b-136">ステートメント形式のラムダの本体は任意の数のステートメントで構成できますが、実際面では通常、2、3 個以下にします。</span><span class="sxs-lookup"><span data-stu-id="2427b-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="2427b-137">匿名メソッドと同様、ステートメント形式のラムダを使用して式ツリーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="2427b-137">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="2427b-138">非同期ラムダ</span><span class="sxs-lookup"><span data-stu-id="2427b-138">Async lambdas</span></span> ##

<span data-ttu-id="2427b-139">[async](language-reference/keywords/async.md) キーワードと [await](language-reference/keywords/await.md) キーワードを使用すると、非同期処理を組み込んだラムダ式およびステートメントを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="2427b-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="2427b-140">たとえば、この例では、非同期に実行される `ShowSquares` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2427b-140">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="2427b-141">非同期メソッドの作成および使用方法の詳細については、「[Async および Await を使用した非同期プログラミング](programming-guide/concepts/async/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2427b-141">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="2427b-142">ラムダ式とタプル</span><span class="sxs-lookup"><span data-stu-id="2427b-142">Lambda expressions and tuples</span></span> ##

<span data-ttu-id="2427b-143">C# 7.0 以降、C# 言語はタプルの組み込みサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="2427b-143">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="2427b-144">タプルは、ラムダ式への引数として指定できるほか、ラムダ式で返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2427b-144">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="2427b-145">場合によっては、C# コンパイラは、型の推定を使用して、タプル コンポーネントの型を判定することもあります。</span><span class="sxs-lookup"><span data-stu-id="2427b-145">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span> 

<span data-ttu-id="2427b-146">タプルを定義するには、そのコンポーネントのコンマ区切りリストをかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="2427b-146">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="2427b-147">次の例では、5 つのコンポーネントを持つタプルを使用して、ラムダ式に連続した数値を渡します。このラムダ式により、各値が 2 倍になり、乗算の結果を格納する 5 つのコンポーネントを持つタプルが返されます。</span><span class="sxs-lookup"><span data-stu-id="2427b-147">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="2427b-148">通常、タプルのフィールド名は `Item1`、`Item2` のようになります。ただし、次の例のとおり、名前付きのコンポーネントを持つタプルを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="2427b-148">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="2427b-149">C# におけるタプルのサポートの詳細については、「[C# Tuple types (C# のタプル型)](tuples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2427b-149">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="2427b-150">標準クエリ演算子を使用したラムダ</span><span class="sxs-lookup"><span data-stu-id="2427b-150">Lambdas with the standard query operators</span></span> ##

<span data-ttu-id="2427b-151">いくつかある実装の中で特に、LINQ to Objects は、汎用デリゲートの <xref:System.Func%601> ファミリに属する型の入力パラメーターを持ちます。</span><span class="sxs-lookup"><span data-stu-id="2427b-151">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="2427b-152">これらのデリゲートは、型パラメーターを使用して、入力パラメーターの数と型に加え、デリゲートの戻り値の型を定義します。</span><span class="sxs-lookup"><span data-stu-id="2427b-152">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="2427b-153">`Func` デリゲートは、ソース データのセット内の各要素に適用されるユーザー定義の式をカプセル化する場合に非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="2427b-153">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="2427b-154">たとえば、<xref:System.Func%601> デリゲートを考えてみます。この構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2427b-154">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="2427b-155">このデリゲートのインスタンスは、次のようなコードを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="2427b-155">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="2427b-156">この場合、`int` は入力パラメーター、`bool` は戻り値です。</span><span class="sxs-lookup"><span data-stu-id="2427b-156">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="2427b-157">戻り値は必ず最後の型パラメーターで指定されます。</span><span class="sxs-lookup"><span data-stu-id="2427b-157">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="2427b-158">次の `Func` デリゲートを呼び出すと、入力パラメーターが 5 に等しいかどうかを示す true または false が返されます。</span><span class="sxs-lookup"><span data-stu-id="2427b-158">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="2427b-159">たとえば、<xref:System.Linq.Queryable> 型で定義された標準クエリ演算子において、引数型が <xref:System.Linq.Expressions.Expression%601> の場合もラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2427b-159">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="2427b-160"><xref:System.Linq.Expressions.Expression%601> 引数を指定すると、ラムダは式ツリーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="2427b-160">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="2427b-161">次の例では、[System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) 標準クエリ演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="2427b-161">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="2427b-162">入力パラメーターの型はコンパイラが推論できますが、明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2427b-162">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="2427b-163">この特定のラムダ式は、2 で除算したときに剰余が 1 になる整数 (`n`) をカウントします。</span><span class="sxs-lookup"><span data-stu-id="2427b-163">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="2427b-164">次の例では、`numbers` 配列内で 9 より前にある要素をすべて含むシーケンスを作成します。これは、9 がシーケンス内で条件を満たさない最初の数値であるためです。</span><span class="sxs-lookup"><span data-stu-id="2427b-164">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="2427b-165">次の例では、複数の入力パラメーターをかっこで囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="2427b-165">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="2427b-166">このメソッドは、値が numbers 配列内のその位置を表す序数よりも小さい数値が出現するまで、その配列に含まれるすべての要素を返します。</span><span class="sxs-lookup"><span data-stu-id="2427b-166">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="2427b-167">ラムダ式の型の推定</span><span class="sxs-lookup"><span data-stu-id="2427b-167">Type inference in lambda expressions</span></span> ##

<span data-ttu-id="2427b-168">ラムダを記述する際、多くの場合は入力パラメーターの型を指定する必要はありません。これは、ラムダ本体やパラメーターの型など C# 言語仕様に記述されている要素に基づいて、コンパイラが型を推定できるためです。</span><span class="sxs-lookup"><span data-stu-id="2427b-168">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="2427b-169">ほとんどの標準クエリ演算子では、最初の入力がソース シーケンス内の要素の型です。</span><span class="sxs-lookup"><span data-stu-id="2427b-169">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="2427b-170">`IEnumerable<Customer>` を問い合わせると、入力変数は `Customer` オブジェクトであると推論されます。これは、そのメソッドとプロパティにアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2427b-170">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="2427b-171">ラムダの型の推定の一般規則は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2427b-171">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="2427b-172">ラムダにはデリゲート型と同じ数のパラメーターが含まれていなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2427b-172">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="2427b-173">ラムダに含まれる各入力引数は、対応するデリゲート パラメーターに暗黙的に変換できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2427b-173">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="2427b-174">ラムダの戻り値 (ある場合) は、デリゲートの戻り値の型に暗黙的に変換できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2427b-174">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="2427b-175">共通型システムには "ラムダ式" の概念が組み込まれていないため、ラムダ式自体は型を持ちません。</span><span class="sxs-lookup"><span data-stu-id="2427b-175">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="2427b-176">しかし、変則的ではあってもラムダ式の "型" を表現できると都合が良い場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2427b-176">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="2427b-177">このような場合の型は、ラムダ式の変換後のデリゲート型または <xref:System.Linq.Expressions.Expression> 型を指します。</span><span class="sxs-lookup"><span data-stu-id="2427b-177">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="2427b-178">ラムダ式における変数のスコープ</span><span class="sxs-lookup"><span data-stu-id="2427b-178">Variable Scope in Lambda Expressions</span></span> ##

<span data-ttu-id="2427b-179">ラムダは、"*外部変数*" を参照できます (「[匿名メソッド](programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照)。外部変数とは、ラムダ関数を定義するメソッド内のスコープ、またはラムダ式を含む型のスコープに存在する変数のことです。</span><span class="sxs-lookup"><span data-stu-id="2427b-179">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="2427b-180">こうして取り込まれた変数は、ラムダ式で使用するために格納されます。これは、変数がスコープ外に出てガベージ コレクトされる場合でも変わりません。</span><span class="sxs-lookup"><span data-stu-id="2427b-180">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="2427b-181">外部変数は、ラムダ式で使用される前に明示的に代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2427b-181">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="2427b-182">次の例は、こうした規則を示しています。</span><span class="sxs-lookup"><span data-stu-id="2427b-182">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="2427b-183">ラムダ式における変数のスコープには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2427b-183">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="2427b-184">取り込まれた変数は、その変数を参照するデリゲートがガベージ コレクションの対象になるまでガベージ コレクトされません。</span><span class="sxs-lookup"><span data-stu-id="2427b-184">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="2427b-185">ラムダ式内に導入された変数は、外側のメソッドでは参照できません。</span><span class="sxs-lookup"><span data-stu-id="2427b-185">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="2427b-186">ラムダ式は、外側のメソッドの `in`、`ref`、`out` パラメーターを直接取り込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="2427b-186">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="2427b-187">ラムダ式に含まれる return ステートメントで外側のメソッドを戻すことはありません。</span><span class="sxs-lookup"><span data-stu-id="2427b-187">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="2427b-188">ラムダ式には、 `goto` ステートメント、 `break` ステートメント、およびジャンプ ステートメントのジャンプ先がブロック外である場合はラムダ式の内部にある `continue` ステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="2427b-188">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="2427b-189">また、ジャンプ先がブロックの内部にある場合は、ラムダ式の外部でジャンプ ステートメントを使用するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="2427b-189">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="2427b-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="2427b-190">See also</span></span> ##

<span data-ttu-id="2427b-191">[LINQ (統合言語クエリ)](../standard/using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="2427b-191">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span></span>  
<span data-ttu-id="2427b-192">[匿名メソッド](programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="2427b-192">[Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
[<span data-ttu-id="2427b-193">式ツリー</span><span class="sxs-lookup"><span data-stu-id="2427b-193">Expression trees</span></span>](expression-trees.md)

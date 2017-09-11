---
title: "式ツリーの実行"
description: "式ツリーの実行について説明します。式ツリーを実行可能な中間言語 (IL) 命令に変換します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4ca87c8410a04e9198e9dd6c379760e7b6596585
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="executing-expression-trees"></a><span data-ttu-id="35bb6-104">式ツリーの実行</span><span class="sxs-lookup"><span data-stu-id="35bb6-104">Executing Expression Trees</span></span>

[<span data-ttu-id="35bb6-105">前へ -- 式ツリーをサポートするフレームワークの型</span><span class="sxs-lookup"><span data-stu-id="35bb6-105">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="35bb6-106">*式ツリー*はコードを表すデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="35bb6-106">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="35bb6-107">式ツリーはコンパイル済みの実行可能なコードではありません。</span><span class="sxs-lookup"><span data-stu-id="35bb6-107">It is not compiled and executable code.</span></span> <span data-ttu-id="35bb6-108">式ツリーで表される .NET コードを実行する場合は、実行可能な IL 命令に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-108">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="35bb6-109">ラムダ式から関数への変換</span><span class="sxs-lookup"><span data-stu-id="35bb6-109">Lambda Expressions to Functions</span></span>
<span data-ttu-id="35bb6-110">すべての LambdaExpression、または LambdaExpression の派生型は、実行可能な IL に変換できます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-110">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="35bb6-111">その他の式の型は直接コードに変換できません。</span><span class="sxs-lookup"><span data-stu-id="35bb6-111">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="35bb6-112">実際には、この制限はほとんど影響がありません。</span><span class="sxs-lookup"><span data-stu-id="35bb6-112">This restriction has little effect in practice.</span></span> <span data-ttu-id="35bb6-113">ラムダ式は、実行可能な中間言語 (IL) に変換して実行する唯一の式の型です。</span><span class="sxs-lookup"><span data-stu-id="35bb6-113">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="35bb6-114">(直接 `ConstantExpression` を実行することにどのような意味があるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="35bb6-114">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="35bb6-115">何かに役立つでしょうか。)`LamdbaExpression` である式ツリー、または `LambdaExpression` の派生型はすべて IL に変換できます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-115">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="35bb6-116">式の型 `Expression<TDelegate>` は .NET Core ライブラリで唯一の具体的な例です。</span><span class="sxs-lookup"><span data-stu-id="35bb6-116">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="35bb6-117">この型は任意のデリゲート型にマップされる式を表すのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-117">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="35bb6-118">この型はデリゲート型にマップされるため、.NET で式を検証し、ラムダ式のシグネチャと一致する適切なデリゲートの IL を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-118">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="35bb6-119">通常、これによって式とそれに対応するデリゲートの間で単純なマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-119">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="35bb6-120">たとえば、`Expression<Func<int>>` によって表される式ツリーは、`Func<int>` 型のデリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-120">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="35bb6-121">任意の戻り値の型と引数リストをもつラムダ式の場合、そのラムダ式によって表される実行可能コードのターゲット型となるデリゲート型が存在します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-121">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="35bb6-122">`LamdbaExpression` 型には、式ツリーを実行可能コードに変換するために使用する `Compile` と `CompileToMethod` メンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-122">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="35bb6-123">`Compile` メソッドはデリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-123">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="35bb6-124">`ConmpileToMethod` メソッドは、式ツリーのコンパイル済み出力を表す IL によって `MethodBuilder` オブジェクトを更新します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-124">The `ConmpileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="35bb6-125">なお、`CompileToMethod` は完全なデスクトップ フレームワークでのみ利用可能で、.NET Core framework では利用できません。</span><span class="sxs-lookup"><span data-stu-id="35bb6-125">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="35bb6-126">必要に応じて、生成されたデリゲート オブジェクトのシンボル デバッグ情報を受け取る `DebugInfoGenerator` を用意することもできます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-126">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="35bb6-127">これにより、式ツリーをデリゲート オブジェクトに変換し、生成されたデリゲートの完全なデバッグ情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-127">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="35bb6-128">次のコードを使用して、式をデリゲートに変換します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-128">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="35bb6-129">デリゲート型は式の型が基になっています。</span><span class="sxs-lookup"><span data-stu-id="35bb6-129">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="35bb6-130">厳密に型指定された方法でデリゲート オブジェクトを使用する場合は、戻り値の型および引数リストを把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-130">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="35bb6-131">`LambdaExpression.Compile()` メソッドは `Delegate` 型を返します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-131">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="35bb6-132">コンパイル時ツールを使用して、戻り値の型の引数リストを確認するには、適切なデリゲート型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-132">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="35bb6-133">実行と有効期間</span><span class="sxs-lookup"><span data-stu-id="35bb6-133">Execution and Lifetimes</span></span>

<span data-ttu-id="35bb6-134">`LamdbaExpression.Compile()` を呼び出したときに作成されたデリゲートを呼び出して、コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-134">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="35bb6-135">上の例の `add.Compile()` がデリゲートを返す部分に、これが表示されています。</span><span class="sxs-lookup"><span data-stu-id="35bb6-135">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="35bb6-136">`func()` を呼び出して、デリゲートを呼び出すことにより、コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-136">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="35bb6-137">そのデリゲートは式ツリーのコードを表します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-137">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="35bb6-138">そのデリゲートのハンドルを保持して、後で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-138">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="35bb6-139">デリゲートが表すコードを実行するたびに、式ツリーをコンパイルする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35bb6-139">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="35bb6-140">(式ツリーは不変であるため、あとで同じ式ツリーをコンパイルしても、同じコードを実行するデリゲートが作成されます。)</span><span class="sxs-lookup"><span data-stu-id="35bb6-140">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="35bb6-141">より高度なキャッシュ機構を作成して、不要なコンパイルの呼び出しを回避することで、パフォーマンスを向上させようとしないように気を付けてください。</span><span class="sxs-lookup"><span data-stu-id="35bb6-141">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="35bb6-142">また、2 つの任意の式ツリーを比較して、同じアルゴリズムを表しているかどうかを確認することも、実行に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-142">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="35bb6-143">`LambdaExpression.Compile()` への余分な呼び出しを回避して、コンピューティング時間を削減しても、2 つの異なる式ツリーから同じ実行可能コードが得られることを確認するコードを実行するのにもっと多くの時間がかかってしまいます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-143">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="35bb6-144">注意事項</span><span class="sxs-lookup"><span data-stu-id="35bb6-144">Caveats</span></span>

<span data-ttu-id="35bb6-145">ラムダ式をデリゲートにコンパイルして、そのデリゲートを呼び出すのは、式ツリーで実行する最も単純な操作の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="35bb6-145">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="35bb6-146">ただし、この簡単な操作にも気をつけるべき点があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-146">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="35bb6-147">ラムダ式は、式で参照される任意のローカル変数に対するクロージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-147">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="35bb6-148">デリゲートの一部となる任意の変数は、`Compile` を呼び出す場所で使用でき、得られたデリゲートを実行するときに使用できるように保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-148">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="35bb6-149">通常は、このことが true であることをコンパイラが確認します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-149">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="35bb6-150">しかし、式が `IDisposable` を実装する変数にアクセスする場合、式ツリーでオブジェクトが保持されている一方で、コードがオブジェクトを破棄する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-150">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="35bb6-151">たとえば、次のコードは `int` が `IDisposable` を実装しないため、正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-151">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="35bb6-152">デリゲートはローカル変数 `constant` への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-152">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="35bb6-153">`CreateBoundFunc` によって返される関数をあとで実行するとき、その変数はいつでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-153">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="35bb6-154">しかし、次の `IDisposable` を実装するクラス (かなり不自然です) はどうでしょうか。</span><span class="sxs-lookup"><span data-stu-id="35bb6-154">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="35bb6-155">下記に示す式で使用する場合、`Resource.Argument`プロパティによって参照されるコードを実行すると、`ObjectDisposedException` が得られます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-155">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="35bb6-156">このメソッドから返されたデリゲートは、`constant` オブジェクトを捕捉しますが、このオブジェクトはすでに破棄されています。</span><span class="sxs-lookup"><span data-stu-id="35bb6-156">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="35bb6-157">(オブジェクトは `using` ステートメントで宣言されたため、破棄されています。)</span><span class="sxs-lookup"><span data-stu-id="35bb6-157">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="35bb6-158">このため、このメソッドから返されたデリゲートを実行すると、実行時に `ObjecctDisposedException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-158">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="35bb6-159">コンパイル時の構成要素を表す実行時エラーが発生するのは変だと思うかもしれませんが、式ツリーを扱う場合はそういうものです。</span><span class="sxs-lookup"><span data-stu-id="35bb6-159">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="35bb6-160">この問題はさまざまなバリエーションがあるため、これを回避する一般的なガイダンスを提供することは困難です。</span><span class="sxs-lookup"><span data-stu-id="35bb6-160">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="35bb6-161">式を定義するときにローカル変数へのアクセスに注意するとともに、パブリック API によって返される可能性がある式ツリーを作成する場合、(`this` によって表される) 現在のオブジェクトでのアクセス状態に注意してください。</span><span class="sxs-lookup"><span data-stu-id="35bb6-161">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="35bb6-162">式のコードが他のアセンブリのメソッドまたはプロパティを参照する場合があります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-162">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="35bb6-163">そのアセンブリには、式の定義時、式のコンパイル時、得られたデリゲートの呼び出し時にアクセスが必要になります。</span><span class="sxs-lookup"><span data-stu-id="35bb6-163">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="35bb6-164">アセンブリが存在しない場合、`ReferencedAssemblyNotFoundException` が発生します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-164">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="35bb6-165">まとめ</span><span class="sxs-lookup"><span data-stu-id="35bb6-165">Summary</span></span>

<span data-ttu-id="35bb6-166">ラムダ式を表す式ツリーをコンパイルすると、実行可能なデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="35bb6-166">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="35bb6-167">この方法は、式ツリーが表すコードを実行するメカニズムの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="35bb6-167">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="35bb6-168">式ツリーは、作成した任意の構成要素を実行するコードを表わしています。</span><span class="sxs-lookup"><span data-stu-id="35bb6-168">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="35bb6-169">コードをコンパイルして実行する環境が、式を作成する環境と一致している限り、すべてが期待どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="35bb6-169">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="35bb6-170">環境が一致していない場合、エラーが確実に予想されます。このエラーは、式ツリーを使用するコードを最初にテストする段階で発見されるはずです。</span><span class="sxs-lookup"><span data-stu-id="35bb6-170">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="35bb6-171">次へ -- 式の解釈</span><span class="sxs-lookup"><span data-stu-id="35bb6-171">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)


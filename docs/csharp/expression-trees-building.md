---
title: "式ツリーの構築"
description: "式ツリーを構築するためのテクニックについて説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c0d7bcf6e07f4a49e15e6f6f4e028eebfe82d8bf
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="building-expression-trees"></a><span data-ttu-id="44a33-104">式ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="44a33-104">Building Expression Trees</span></span>

[<span data-ttu-id="44a33-105">前回 -- 式の解釈</span><span class="sxs-lookup"><span data-stu-id="44a33-105">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="44a33-106">これまでに説明した式ツリーは、いずれも C# コンパイラで作成したものです。</span><span class="sxs-lookup"><span data-stu-id="44a33-106">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="44a33-107">`Expression<Func<T>>` や他の同様の型として型指定された変数に割り当てるラムダ式を作成するだけの手順でしたが、</span><span class="sxs-lookup"><span data-stu-id="44a33-107">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="44a33-108">式ツリーを作成する方法は他にもあります。</span><span class="sxs-lookup"><span data-stu-id="44a33-108">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="44a33-109">実行時にメモリ内で式を構築する必要があるというシナリオはよくあります。</span><span class="sxs-lookup"><span data-stu-id="44a33-109">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="44a33-110">式ツリーは不変なので、式ツリーの構築は複雑です。</span><span class="sxs-lookup"><span data-stu-id="44a33-110">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="44a33-111">不変とは、リーフからルートにいたるまでツリーを構築する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="44a33-111">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="44a33-112">式ツリーの構築に使用する API がこれを反映しています。ノードの構築に使用するメソッドは、そのすべての子を引数として取得します。</span><span class="sxs-lookup"><span data-stu-id="44a33-112">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="44a33-113">いくつかの例を挙げながら手法を説明します。</span><span class="sxs-lookup"><span data-stu-id="44a33-113">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="44a33-114">ノードの作成</span><span class="sxs-lookup"><span data-stu-id="44a33-114">Creating Nodes</span></span>

<span data-ttu-id="44a33-115">比較的単純な例から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="44a33-115">Let's start relatively simply again.</span></span> <span data-ttu-id="44a33-116">これまでに使用してきた加算式を使用します。</span><span class="sxs-lookup"><span data-stu-id="44a33-116">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="44a33-117">式ツリーを構築するには、リーフ ノードを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44a33-117">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="44a33-118">リーフ ノードは定数なので、`Expression.Constant` メソッドを使用してノードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="44a33-118">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="44a33-119">次に、加算式を構築します。</span><span class="sxs-lookup"><span data-stu-id="44a33-119">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="44a33-120">加算式を構築したら、ラムダ式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="44a33-120">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lamdba = Expression.Lambda(addition);
```

<span data-ttu-id="44a33-121">引数がないので、これはとても単純な LambdaExpression です。</span><span class="sxs-lookup"><span data-stu-id="44a33-121">This is a very simple LambdaExpression, because it contains no arguments.</span></span>
<span data-ttu-id="44a33-122">このセクションの後半では、引数をパラメーターにマップし、より複雑な式を構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="44a33-122">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="44a33-123">この例のように単純な式の場合、すべての呼び出しを 1 つのステートメントにまとめることもできます。</span><span class="sxs-lookup"><span data-stu-id="44a33-123">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="44a33-124">ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="44a33-124">Building a Tree</span></span>

<span data-ttu-id="44a33-125">メモリ内に式ツリーを構築する基本的な方法です。</span><span class="sxs-lookup"><span data-stu-id="44a33-125">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="44a33-126">一般的に、複雑なツリーの場合はノードの種類が多く、ツリー内のノード数も多くなります。</span><span class="sxs-lookup"><span data-stu-id="44a33-126">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="44a33-127">もう 1 つの例を使って、式ツリーを作成するときに一般的に構築する 2 つのノードについて説明します。引数ノードとメソッド呼び出しノードです。</span><span class="sxs-lookup"><span data-stu-id="44a33-127">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="44a33-128">式ツリーを構築して次の式を作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="44a33-128">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="44a33-129">まず `x` と `y` のパラメーター式を作成します。</span><span class="sxs-lookup"><span data-stu-id="44a33-129">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="44a33-130">乗算式と加算式の作成方法は、これまでに説明したパターンどおりです。</span><span class="sxs-lookup"><span data-stu-id="44a33-130">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="44a33-131">次に、`Math.Sqrt` の呼び出しのために、メソッド呼び出し式を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44a33-131">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="44a33-132">最後に、メソッド呼び出しをラムダ式に組み込み、忘れずにラムダ式の引数を定義します。</span><span class="sxs-lookup"><span data-stu-id="44a33-132">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="44a33-133">このやや複雑な例では、式ツリーの作成に必要になることが多い手法がいくつか見られます。</span><span class="sxs-lookup"><span data-stu-id="44a33-133">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="44a33-134">まず、パラメーターまたはローカル変数を表すオブジェクトは、使用前に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="44a33-134">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="44a33-135">オブジェクトの作成後は、式ツリーのどこでも必要な場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="44a33-135">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="44a33-136">次に、`MethodInfo` オブジェクトを作成するには、リフレクション API の一部を使用する必要があります。これは、そのメソッドにアクセスする式ツリーを作成できるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="44a33-136">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="44a33-137">使用するリフレクション API は、.NET Core プラットフォームで使用できるものに限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44a33-137">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="44a33-138">繰り返しになりますが、こうした手法は他の式ツリーにも応用されます。</span><span class="sxs-lookup"><span data-stu-id="44a33-138">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="44a33-139">コードの構築の詳細</span><span class="sxs-lookup"><span data-stu-id="44a33-139">Building Code In Depth</span></span>

<span data-ttu-id="44a33-140">このような API を使用して構築できるものに制限はありませんが、</span><span class="sxs-lookup"><span data-stu-id="44a33-140">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="44a33-141">構築する式ツリーが複雑になるほど、コードの管理と読み取りが困難になります。</span><span class="sxs-lookup"><span data-stu-id="44a33-141">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="44a33-142">このコードと同じ式ツリーを構築してみましょう。</span><span class="sxs-lookup"><span data-stu-id="44a33-142">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="44a33-143">上の例では、式ツリーを構築せず、デリゲートのみを構築しました。</span><span class="sxs-lookup"><span data-stu-id="44a33-143">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="44a33-144">`Expression` クラスを使用して、ステートメント形式のラムダを構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="44a33-144">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="44a33-145">同じ機能を構築するために必要なコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="44a33-145">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="44a33-146">この例が複雑なのは、`while` ループを構築する API がなく、条件テストを含むループと、ループを抜けるためのラベル ターゲットを構築する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="44a33-146">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="44a33-147">階乗関数の式ツリーを構築するコードは、かなり長く複雑になります。また、通常のコーディング作業では避けたいラベルや break ステートメントなどの要素が多くなってしまいます。</span><span class="sxs-lookup"><span data-stu-id="44a33-147">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="44a33-148">このセクションでは、この式ツリーのすべてのノードにアクセスするビジター コードも更新し、このサンプルで作成したノードに関する情報を書き出しました。</span><span class="sxs-lookup"><span data-stu-id="44a33-148">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="44a33-149">GitHub の dotnet/docs レポジトリで、[サンプル コードを表示またはダウンロード](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees)することができます。</span><span class="sxs-lookup"><span data-stu-id="44a33-149">You can [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="44a33-150">自分でサンプルをビルドし、実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="44a33-150">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="44a33-151">ダウンロード方法については、「[サンプルおよびチュートリアル](../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44a33-151">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="44a33-152">API の確認</span><span class="sxs-lookup"><span data-stu-id="44a33-152">Examining the APIs</span></span>

<span data-ttu-id="44a33-153">.NET Core では、式ツリーの API をたどることがやや難しくはありますが、問題ありません。</span><span class="sxs-lookup"><span data-stu-id="44a33-153">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="44a33-154">その目的は、実行時にコードを生成するコードを作成するという、かなり複雑な作業だからです。</span><span class="sxs-lookup"><span data-stu-id="44a33-154">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="44a33-155">C# 言語で使用できるすべてのコントロール構造体をサポートしながら、API のアクセス領域をできるだけ少なくするバランスを取るため、必然的に複雑な作業になります。</span><span class="sxs-lookup"><span data-stu-id="44a33-155">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="44a33-156">このバランスとは、多くのコントロール構造体は、C# コンストラクトではなく、上位のコンストラクトからコンパイラが生成する基のロジックを示すコンストラクトで表されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="44a33-156">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="44a33-157">また、現時点では、`Expression` クラス メソッドを使用して直接構築できない C# 式があります。</span><span class="sxs-lookup"><span data-stu-id="44a33-157">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="44a33-158">一般的に、C# 5 と C# 6 で追加された最新の演算子と式です</span><span class="sxs-lookup"><span data-stu-id="44a33-158">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="44a33-159">(たとえば、`async` は構築できず、新しい `?.` 演算子は直接作成できません)。</span><span class="sxs-lookup"><span data-stu-id="44a33-159">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="44a33-160">次回 -- 式の変換</span><span class="sxs-lookup"><span data-stu-id="44a33-160">Next -- Translating Expressions</span></span>](expression-trees-translating.md)


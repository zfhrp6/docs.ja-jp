---
title: "式ツリーをサポートするフレームワークの型"
description: "式ツリーをサポートするフレームワークの型、式ツリーの作成、式ツリー API の操作テクニックについて説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ed89b286eee9b4c2e11bb27d18e50f777f94f33e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="b507d-104">式ツリーをサポートするフレームワークの型</span><span class="sxs-lookup"><span data-stu-id="b507d-104">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="b507d-105">前へ -- 式ツリーの説明</span><span class="sxs-lookup"><span data-stu-id="b507d-105">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="b507d-106">式ツリーを使用する .NET Core framework には、多くのクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="b507d-106">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="b507d-107">クラスの全リストは[ここ](/dotnet/core/api/System.Linq.Expressions)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="b507d-107">You can see the full list [here](/dotnet/core/api/System.Linq.Expressions).</span></span>
<span data-ttu-id="b507d-108">ここでは、リストのすべてを説明するのではなく、フレームワークのクラスがどう設計されているかを把握します。</span><span class="sxs-lookup"><span data-stu-id="b507d-108">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="b507d-109">言語設計の観点から言えば、式は、評価して値を返すコードの本体です。</span><span class="sxs-lookup"><span data-stu-id="b507d-109">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="b507d-110">式はごく単純な場合があります。定数式 `1` は定数値 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="b507d-110">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="b507d-111">式が複雑になる場合もあります。式 `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` は二次方程式の 1 つの解を返します (式に解がある場合)。</span><span class="sxs-lookup"><span data-stu-id="b507d-111">They may be more complicated: The expression `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="b507d-112">すべては System.Linq.Expression から始まる</span><span class="sxs-lookup"><span data-stu-id="b507d-112">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="b507d-113">式ツリーの使用が複雑になる理由の 1 つは、プログラムの多くの場所でさまざまな種類の式が有効になることです。</span><span class="sxs-lookup"><span data-stu-id="b507d-113">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="b507d-114">代入式を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="b507d-114">Consider an assignment expression.</span></span> <span data-ttu-id="b507d-115">代入式の右側には、定数値、変数、メソッドの呼び出し式、その他を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b507d-115">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="b507d-116">言語に柔軟性があるため、式ツリーをたどっていくと、ツリーのノードのあらゆる場所でさまざまな式の型が使用されていることに気づくはずです。</span><span class="sxs-lookup"><span data-stu-id="b507d-116">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="b507d-117">そのため、基本の式の型を使用して作業できるのであれば、それが最も簡単な操作方法になります。</span><span class="sxs-lookup"><span data-stu-id="b507d-117">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="b507d-118">しかし、場合によっては、それ以上の知識が必要です。</span><span class="sxs-lookup"><span data-stu-id="b507d-118">However, sometimes you need to know more.</span></span>
<span data-ttu-id="b507d-119">このために、基本の式クラスに `NodeType` プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b507d-119">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="b507d-120">このプロパティは、あり得る式の型の列挙型である `ExpressionType` を返します。</span><span class="sxs-lookup"><span data-stu-id="b507d-120">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="b507d-121">ノードの型がわかれば、その型にキャストし、式ノードの型を識別する特定のアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b507d-121">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="b507d-122">特定の型のノードを検索し、その種類の式が持つ特定のプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b507d-122">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="b507d-123">たとえば、次のコードでは変数アクセス式の変数名を出力します。</span><span class="sxs-lookup"><span data-stu-id="b507d-123">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="b507d-124">ここでは、ノードの型を確認し、次に変数アクセス式にキャストして、特定の式の型のプロパティを確認するという手順で進めています。</span><span class="sxs-lookup"><span data-stu-id="b507d-124">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="b507d-125">式ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="b507d-125">Creating Expression Trees</span></span>

<span data-ttu-id="b507d-126">`System.Linq.Expression` クラスには、式を作成する静的メソッドも数多く含まれています。</span><span class="sxs-lookup"><span data-stu-id="b507d-126">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="b507d-127">これらのメソッドは、その子に指定された引数を使用して式ノードを作成します。</span><span class="sxs-lookup"><span data-stu-id="b507d-127">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="b507d-128">このようにしてリーフ ノードから式を作成します。</span><span class="sxs-lookup"><span data-stu-id="b507d-128">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="b507d-129">たとえば、次のコードは Add 式を作成します。</span><span class="sxs-lookup"><span data-stu-id="b507d-129">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="b507d-130">この簡単な例からわかるように、さまざまな型が式ツリーの作成と操作に関わっています。</span><span class="sxs-lookup"><span data-stu-id="b507d-130">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="b507d-131">C# 言語が備える豊富な語彙が提供する機能を発揮するには、こうした複雑さが必要になります。</span><span class="sxs-lookup"><span data-stu-id="b507d-131">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="b507d-132">API の操作</span><span class="sxs-lookup"><span data-stu-id="b507d-132">Navigating the APIs</span></span>
<span data-ttu-id="b507d-133">ほぼすべての C# 言語の構文要素に対してマップされる式ノード型がそれぞれ存在します。</span><span class="sxs-lookup"><span data-stu-id="b507d-133">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="b507d-134">各型には、その型の言語要素に特有のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="b507d-134">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="b507d-135">一度に覚えておくべきことがたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="b507d-135">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="b507d-136">ここではすべてを記憶しようとするのではなく、式ツリーを操作するときにふだん使うテクニックを紹介します。</span><span class="sxs-lookup"><span data-stu-id="b507d-136">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="b507d-137">`ExpressionType` 列挙型のメンバーを調べて、検証するノードを特定します。</span><span class="sxs-lookup"><span data-stu-id="b507d-137">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="b507d-138">式ツリーをたどって理解するときに、この方法が実に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b507d-138">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="b507d-139">`Expression` クラスの静的メンバーを調べて、式を作成します。</span><span class="sxs-lookup"><span data-stu-id="b507d-139">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="b507d-140">これらのメソッドでは、その子ノードから任意の式の型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="b507d-140">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="b507d-141">`ExpressionVisitor` クラスを調べて、変更された式ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b507d-141">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="b507d-142">これら 3 つの部分をそれぞれ調べれば、さらに多くのことがわかります。</span><span class="sxs-lookup"><span data-stu-id="b507d-142">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="b507d-143">これら 3 つのステップのいずれかを実行すれば、必要なことが必ず見つかります。</span><span class="sxs-lookup"><span data-stu-id="b507d-143">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="b507d-144">次へ -- 式ツリーの実行</span><span class="sxs-lookup"><span data-stu-id="b507d-144">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 


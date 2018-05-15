---
title: 式ツリーの変換
description: 式ツリーの各ノードにアクセスし、その式ツリーに変更を加えたコピーを構築する方法について説明します。
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 9483cbe75b4bf5a38dd791633c852eb0b8473944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="translating-expression-trees"></a><span data-ttu-id="4a027-103">式ツリーの変換</span><span class="sxs-lookup"><span data-stu-id="4a027-103">Translating Expression Trees</span></span>

[<span data-ttu-id="4a027-104">前回 -- 式の構築</span><span class="sxs-lookup"><span data-stu-id="4a027-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="4a027-105">この最終セクションでは、式ツリーの各ノードにアクセスし、その式ツリーに変更を加えたコピーを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a027-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="4a027-106">これらの手法は、2 つの重要なシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4a027-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="4a027-107">1 つ目は、別の環境に変換するために、式ツリーで表現されるアルゴリズムを理解する場合です。</span><span class="sxs-lookup"><span data-stu-id="4a027-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="4a027-108">2 つ目は、作成したアルゴリズムを変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="4a027-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="4a027-109">この目的として、ログ記録の追加、メソッド呼び出しの取得と追跡などがあります。</span><span class="sxs-lookup"><span data-stu-id="4a027-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="4a027-110">変換はアクセスすること</span><span class="sxs-lookup"><span data-stu-id="4a027-110">Translating is Visiting</span></span>

<span data-ttu-id="4a027-111">式ツリーを変換するために構築するコードは、既に説明した、ツリーのすべてのノードにアクセスする式です。</span><span class="sxs-lookup"><span data-stu-id="4a027-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="4a027-112">式ツリーを変換するときに、すべてのノードにアクセスします。また、アクセスしながら新しいツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="4a027-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="4a027-113">新しいツリーには、元のノードの参照や、ツリーに配置した新しいノードが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4a027-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="4a027-114">それでは、実際に式ツリーにアクセスし、ノードの置き換えを含む新しいツリーを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a027-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="4a027-115">この例では、定数を 10 倍大きい定数に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4a027-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="4a027-116">それ以外に式ツリーの変更はありません。</span><span class="sxs-lookup"><span data-stu-id="4a027-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="4a027-117">定数の値を読み取って新しい定数で置き換えるのではなく、定数ノードを、乗算を実行する新しいノードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4a027-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="4a027-118">ここで定数ノードを見つけたら、子が元の定数である新しい乗算ノードと定数 `10` を作成します。</span><span class="sxs-lookup"><span data-stu-id="4a027-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="4a027-119">元のノードを置き換えるには、変更を含む新しいツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="4a027-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="4a027-120">置き換えたツリーをコンパイルし、実行して確認することができます。</span><span class="sxs-lookup"><span data-stu-id="4a027-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="4a027-121">新しいツリーの構築は、既存のツリー内のノードへのアクセスと、新しいノードの作成とツリーへの挿入を組み合わせた操作です。</span><span class="sxs-lookup"><span data-stu-id="4a027-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="4a027-122">この例は、式ツリーが不変である重要性を示しています。</span><span class="sxs-lookup"><span data-stu-id="4a027-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="4a027-123">上の作成した新しいツリーには、新しく作成したノード、既存のツリーのノードが混在しています。</span><span class="sxs-lookup"><span data-stu-id="4a027-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="4a027-124">既存のツリーのノードは変更できないので、安全です。</span><span class="sxs-lookup"><span data-stu-id="4a027-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="4a027-125">また、メモリ効率も大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="4a027-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="4a027-126">同じノードを 1 つのツリー全体、または複数の式ツリーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a027-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="4a027-127">ノードは変更できないので、必要に応じていつでも同じノードを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="4a027-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="4a027-128">加算の走査と実行</span><span class="sxs-lookup"><span data-stu-id="4a027-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="4a027-129">加算ノードのツリーをたどり、結果を計算する 2 つ目のビジターを構築して、このことを検証してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a027-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="4a027-130">そのために、これまでに見てきたビジターに何点か変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="4a027-130">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="4a027-131">この新しいバージョンでは、この時点までの加算演算の部分的な合計が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a027-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="4a027-132">定数式の場合、これは単に定数式の値です。</span><span class="sxs-lookup"><span data-stu-id="4a027-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="4a027-133">加算式の場合、ツリーの走査が完了すると、結果は左右のオペランドの合計になります。</span><span class="sxs-lookup"><span data-stu-id="4a027-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it 
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="4a027-134">長いコードですが、概念はとてもわかりやすいものです。</span><span class="sxs-lookup"><span data-stu-id="4a027-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="4a027-135">このコードでは、深さ優先検索で子にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4a027-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="4a027-136">定数ノードが検出されると、ビジターから定数値が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a027-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="4a027-137">ビジターが両方の子にアクセスすると、それらの子のサブツリーの合計が計算されます。</span><span class="sxs-lookup"><span data-stu-id="4a027-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="4a027-138">加算ノードで、合計を計算できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4a027-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="4a027-139">式ツリー内のすべてのノードがアクセスされると、合計が計算されます。</span><span class="sxs-lookup"><span data-stu-id="4a027-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="4a027-140">実行をトレースするには、デバッガーでサンプルを実行して実行をトレースします。</span><span class="sxs-lookup"><span data-stu-id="4a027-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="4a027-141">ツリーを走査して、ノードを分析し、合計を計算する方法を簡単にしてみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a027-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="4a027-142">大量のトレース情報を含む更新版の Aggregate メソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4a027-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="4a027-143">同じ式に対して実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4a027-143">Running it on the same expression yields the following output:</span></span>

```
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="4a027-144">出力をトレースし、上のコードの手順を確認します。</span><span class="sxs-lookup"><span data-stu-id="4a027-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="4a027-145">コードがツリーをたどって合計を見つけるときに、各ノードにアクセスし、合計を計算する方法を理解できます。</span><span class="sxs-lookup"><span data-stu-id="4a027-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="4a027-146">次に、`sum1` が指定された式を使用して、別の実行処理を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a027-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="4a027-147">この式の実行の出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4a027-147">Here's the output from examining this expression:</span></span>

```
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="4a027-148">最終的な答えは同じですが、ツリーの走査はまったく異なります。</span><span class="sxs-lookup"><span data-stu-id="4a027-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="4a027-149">ノードは別の順序で走査されます。これは、優先する演算が異なるツリーが構成されていたためです。</span><span class="sxs-lookup"><span data-stu-id="4a027-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="4a027-150">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4a027-150">Learning More</span></span>

<span data-ttu-id="4a027-151">このサンプルは、式ツリーで表されるアルゴリズムを走査し、解釈するために構築するコードのごく一部です。</span><span class="sxs-lookup"><span data-stu-id="4a027-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="4a027-152">式ツリーを別の言語に変換する汎用的なライブラリを構築するために必要なすべての作業の説明については、Matt Warren の[このシリーズ](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a027-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="4a027-153">式ツリーに含まれる任意のコードを変換する方法について、詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="4a027-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="4a027-154">式ツリーの真の力がおわかりいただけたでしょうか。</span><span class="sxs-lookup"><span data-stu-id="4a027-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="4a027-155">コードのセットを確認し、そのコードに必要な変更を加え、変更されたバージョンを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="4a027-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="4a027-156">式ツリーは不変なので、既存のツリーのコンポーネントを使用して新しいツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4a027-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="4a027-157">その結果、変更した式ツリーの作成に必要なメモリ量が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="4a027-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="4a027-158">次回 -- まとめ</span><span class="sxs-lookup"><span data-stu-id="4a027-158">Next -- Summing up</span></span>](expression-trees-summary.md)

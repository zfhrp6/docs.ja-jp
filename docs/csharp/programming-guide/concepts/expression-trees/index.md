---
title: "式ツリー (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: be37183163a3747f861cbda7fd7867640ba382a2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="expression-trees-c"></a><span data-ttu-id="ca960-102">式ツリー (C#)</span><span class="sxs-lookup"><span data-stu-id="ca960-102">Expression Trees (C#)</span></span>
<span data-ttu-id="ca960-103">式ツリーでは、コードがツリー状のデータ構造で表示されます。各ノードは 1 つの式に対応しています。たとえば、メソッドの呼び出しや `x < y` のような二項演算などです。</span><span class="sxs-lookup"><span data-stu-id="ca960-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="ca960-104">式ツリーで表されるコードはコンパイルおよび実行できます。</span><span class="sxs-lookup"><span data-stu-id="ca960-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="ca960-105">これによって、実行可能なコードの動的な変更、さまざまなデータベースでの LINQ クエリの実行、および動的クエリの作成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="ca960-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="ca960-106">LINQ の式ツリーの詳細については、「[How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)」 (方法: 式ツリーを使用して動的クエリをビルドする (C#)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca960-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="ca960-107">また、式ツリーを動的言語ランタイム (DLR) に使用することで、動的言語と .NET Framework 間の相互運用性が実現し、コンパイラ ライターで Microsoft Intermediate language (MSIL) ではなく式ツリーを出力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ca960-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="ca960-108">DLR の詳細については、「[動的言語ランタイムの概要](https://msdn.microsoft.com/library/dd233052)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca960-108">For more information about the DLR, see [Dynamic Language Runtime Overview](https://msdn.microsoft.com/library/dd233052).</span></span>  
  
 <span data-ttu-id="ca960-109">匿名のラムダ式に基づいて、C# と Visual Basic コンパイラで式ツリーを作成できます。または、<xref:System.Linq.Expressions> 名前空間を使用して手動で式ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ca960-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="ca960-110">ラムダ式からの式ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="ca960-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="ca960-111">ラムダ式が <xref:System.Linq.Expressions.Expression%601> 型の変数に割り当てられている場合、コンパイラはラムダ式を表す式ツリーを構築するコードを出力します。</span><span class="sxs-lookup"><span data-stu-id="ca960-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="ca960-112">C# コンパイラは、式形式のラムダ (つまり単一行のラムダ) からのみ式ツリーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ca960-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="ca960-113">ステートメント形式のラムダ (つまり複数行のラムダ) は解析できません。</span><span class="sxs-lookup"><span data-stu-id="ca960-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="ca960-114">C# のラムダ式の詳細については、「[ラムダ式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca960-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="ca960-115">次のコード例は、ラムダ式 `num => num < 5` を表す式ツリーを C# コンパイラで作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca960-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="ca960-116">API を使用した式ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="ca960-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="ca960-117">API を使用して式ツリーを作成するには、<xref:System.Linq.Expressions.Expression> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ca960-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="ca960-118">このクラスには、特定の型を持つ式ツリー ノードを作成する静的ファクトリ メソッドが含まれます。たとえば、変数またはパラメーターを表す <xref:System.Linq.Expressions.ParameterExpression> や、メソッドの呼び出しを表す <xref:System.Linq.Expressions.MethodCallExpression> などです。</span><span class="sxs-lookup"><span data-stu-id="ca960-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="ca960-119"><xref:System.Linq.Expressions.ParameterExpression>、<xref:System.Linq.Expressions.MethodCallExpression> などの式固有の型も、<xref:System.Linq.Expressions> 名前空間で定義されます。</span><span class="sxs-lookup"><span data-stu-id="ca960-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="ca960-120">これらの型は、<xref:System.Linq.Expressions.Expression> 抽象型から派生したものです。</span><span class="sxs-lookup"><span data-stu-id="ca960-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="ca960-121">次のコード例は、API を使用して、ラムダ式 `num => num < 5` を表す式ツリーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca960-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for   
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="ca960-122">.NET Framework 4 以降の式ツリー API は、割り当て式、制御フロー式 (ループ、条件ブロック)、および `try-catch` ブロックもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="ca960-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="ca960-123">API を使用すると、C# コンパイラのラムダ式から作成できる式ツリーよりも複雑な式ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ca960-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="ca960-124">次の例は、数値の階乗を計算する式ツリーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca960-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.   
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="ca960-125">詳細については、「[Generating Dynamic Methods with Expression Trees in Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513) (Visual Studio 2010 での式ツリーによる動的メソッドの生成)」を参照し、Visual Studio 2010 以降のバージョンについても同じ方法を適用してください。</span><span class="sxs-lookup"><span data-stu-id="ca960-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="ca960-126">式ツリーの解析</span><span class="sxs-lookup"><span data-stu-id="ca960-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="ca960-127">次のコード例は、ラムダ式 `num => num < 5` を表す式ツリーを各部分に分解する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca960-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="ca960-128">式ツリーの不変性</span><span class="sxs-lookup"><span data-stu-id="ca960-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="ca960-129">式ツリーは変更できません。</span><span class="sxs-lookup"><span data-stu-id="ca960-129">Expression trees should be immutable.</span></span> <span data-ttu-id="ca960-130">つまり、式ツリーを変更するには、既存の式ツリーをコピーしてツリー内のノードを置き換えることで、新しい式ツリーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca960-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="ca960-131">式ツリー ビジターを使用して、既存の式ツリーを走査することができます。</span><span class="sxs-lookup"><span data-stu-id="ca960-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="ca960-132">詳細については、「[方法: 式ツリーを変更する (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca960-132">For more information, see [How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="ca960-133">式ツリーのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ca960-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="ca960-134"><xref:System.Linq.Expressions.Expression%601> 型に含まれる <xref:System.Linq.Expressions.Expression%601.Compile%2A> メソッドにより、式ツリーが表すコードを実行可能なデリゲートにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ca960-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="ca960-135">次のコード例は、式ツリーをコンパイルして結果のコードを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca960-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="ca960-136">詳細については、「[方法: 式ツリーを実行する (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca960-136">For more information, see [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca960-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca960-137">See Also</span></span>  
 <span data-ttu-id="ca960-138"><xref:System.Linq.Expressions></span><span class="sxs-lookup"><span data-stu-id="ca960-138"><xref:System.Linq.Expressions></span></span>   
 <span data-ttu-id="ca960-139">[方法 : 式ツリーを実行する (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="ca960-139">[How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
 <span data-ttu-id="ca960-140">[方法: 式ツリーを変更する (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="ca960-140">[How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md) </span></span>  
 <span data-ttu-id="ca960-141">[ラムダ式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="ca960-141">[Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
 <span data-ttu-id="ca960-142">[動的言語ランタイムの概要](https://msdn.microsoft.com/library/dd233052) </span><span class="sxs-lookup"><span data-stu-id="ca960-142">[Dynamic Language Runtime Overview](https://msdn.microsoft.com/library/dd233052) </span></span>  
 [<span data-ttu-id="ca960-143">プログラミングの概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="ca960-143">Programming Concepts (C#)</span></span>](../../../../csharp/programming-guide/concepts/index.md)


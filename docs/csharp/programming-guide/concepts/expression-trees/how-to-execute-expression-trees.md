---
title: "方法: 式ツリーを実行する (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
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
ms.openlocfilehash: d230adee877c214dfef0f60ae2c6e7547fedb869
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="bb9a6-102">方法: 式ツリーを実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="bb9a6-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="bb9a6-103">このトピックでは、式ツリーを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="bb9a6-104">式ツリーを実行すると値が返される場合がありますが、メソッドの呼び出しなどの処理が実行されるだけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="bb9a6-105">実行できるのは、ラムダ式を表す式ツリーのみです。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="bb9a6-106">ラムダ式を表す式ツリーの型は、<xref:System.Linq.Expressions.LambdaExpression> または <xref:System.Linq.Expressions.Expression%601> です。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="bb9a6-107">このような式ツリーを実行するには、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A> メソッドを呼び出して実行可能なデリゲートを作成した後、そのデリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb9a6-108">デリゲートの型が不明な場合、つまり、ラムダ式が <xref:System.Linq.Expressions.LambdaExpression> 型であり <xref:System.Linq.Expressions.Expression%601> 型ではない場合には、デリゲートを直接呼び出さずに、デリゲートに対して <xref:System.Delegate.DynamicInvoke%2A> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="bb9a6-109">式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> メソッドを呼び出すことで、元の式ツリーを本体に含む新しいラムダ式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="bb9a6-110">その後、このセクションの説明のとおりにラムダ式を実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb9a6-111">例</span><span class="sxs-lookup"><span data-stu-id="bb9a6-111">Example</span></span>  
 <span data-ttu-id="bb9a6-112">次のコード例は、ラムダ式を作成して実行することで数値の累乗を表す式ツリーの実行方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="bb9a6-113">このコードを実行すると、累乗された数値を表す結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb9a6-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bb9a6-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="bb9a6-115">System.Core.dll がまだ参照されていない場合は、System.Core.dll へのプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="bb9a6-116">System.Linq.Expressions 名前空間をインクルードします。</span><span class="sxs-lookup"><span data-stu-id="bb9a6-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9a6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb9a6-117">See Also</span></span>  
 <span data-ttu-id="bb9a6-118">[式ツリー (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb9a6-118">[Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md) </span></span>  
 [<span data-ttu-id="bb9a6-119">方法: 式ツリーを変更する (C#)</span><span class="sxs-lookup"><span data-stu-id="bb9a6-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)


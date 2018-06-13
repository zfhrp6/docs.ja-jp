---
title: '方法: 式ツリー (Visual Basic) を実行'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 5fbd9ea2842a87a941a1b572acadc93b0a7d2e11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643654"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="89171-102">方法: 式ツリー (Visual Basic) を実行</span><span class="sxs-lookup"><span data-stu-id="89171-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="89171-103">このトピックでは、式ツリーを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="89171-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="89171-104">式ツリーを実行すると値が返される場合がありますが、メソッドの呼び出しなどの処理が実行されるだけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="89171-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="89171-105">実行できるのは、ラムダ式を表す式ツリーのみです。</span><span class="sxs-lookup"><span data-stu-id="89171-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="89171-106">ラムダ式を表す式ツリーの型は、<xref:System.Linq.Expressions.LambdaExpression> または <xref:System.Linq.Expressions.Expression%601> です。</span><span class="sxs-lookup"><span data-stu-id="89171-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="89171-107">このような式ツリーを実行するには、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A> メソッドを呼び出して実行可能なデリゲートを作成した後、そのデリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="89171-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89171-108">デリゲートの型が不明な場合、つまり、ラムダ式が <xref:System.Linq.Expressions.LambdaExpression> 型であり <xref:System.Linq.Expressions.Expression%601> 型ではない場合には、デリゲートを直接呼び出さずに、デリゲートに対して <xref:System.Delegate.DynamicInvoke%2A> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="89171-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="89171-109">式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> メソッドを呼び出すことで、元の式ツリーを本体に含む新しいラムダ式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="89171-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="89171-110">その後、このセクションの説明のとおりにラムダ式を実行できます。</span><span class="sxs-lookup"><span data-stu-id="89171-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89171-111">例</span><span class="sxs-lookup"><span data-stu-id="89171-111">Example</span></span>  
 <span data-ttu-id="89171-112">次のコード例は、ラムダ式を作成して実行することで数値の累乗を表す式ツリーの実行方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="89171-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="89171-113">このコードを実行すると、累乗された数値を表す結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="89171-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89171-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="89171-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="89171-115">System.Core.dll がまだ参照されていない場合は、System.Core.dll へのプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="89171-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="89171-116">System.Linq.Expressions 名前空間をインクルードします。</span><span class="sxs-lookup"><span data-stu-id="89171-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89171-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="89171-117">See Also</span></span>  
 [<span data-ttu-id="89171-118">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89171-118">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="89171-119">方法: 式ツリー (Visual Basic) を変更</span><span class="sxs-lookup"><span data-stu-id="89171-119">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)

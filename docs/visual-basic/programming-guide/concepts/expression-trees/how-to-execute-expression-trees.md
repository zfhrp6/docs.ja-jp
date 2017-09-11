---
title: "方法: 式ツリー (Visual Basic) を実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4cc2c9890c1f5efbc4036d94eef1adb05094ae40
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="423c7-102">方法: 式ツリー (Visual Basic) を実行</span><span class="sxs-lookup"><span data-stu-id="423c7-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="423c7-103">このトピックでは、式ツリーを実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="423c7-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="423c7-104">式ツリーの実行で、値を返すことがありますか、メソッドの呼び出しなど、アクションをのみ実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="423c7-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="423c7-105">ラムダ式を表す式ツリーのみを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="423c7-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="423c7-106">型<xref:System.Linq.Expressions.LambdaExpression>または<xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601></xref:System.Linq.Expressions.LambdaExpression>のラムダ式を表す式ツリーが、します。</span><span class="sxs-lookup"><span data-stu-id="423c7-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="423c7-107">これらの式ツリーを実行するを呼び出し、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A>を実行可能なデリゲートを作成し、デリゲートを呼び出すメソッド</xref:System.Linq.Expressions.LambdaExpression.Compile%2A>。</span><span class="sxs-lookup"><span data-stu-id="423c7-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="423c7-108">デリゲートの型が不明の場合、ラムダ式は型の<xref:System.Linq.Expressions.LambdaExpression>および not <xref:System.Linq.Expressions.Expression%601>、呼び出す必要があります、<xref:System.Delegate.DynamicInvoke%2A>メソッドを直接呼び出す場合の代わりにデリゲートします</xref:System.Delegate.DynamicInvoke%2A></xref:System.Linq.Expressions.Expression%601></xref:System.Linq.Expressions.LambdaExpression>。</span><span class="sxs-lookup"><span data-stu-id="423c7-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="423c7-109">呼び出すことによって、本文として元の式ツリーを持つ新しいラムダ式を作成する式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>メソッド</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>。</span><span class="sxs-lookup"><span data-stu-id="423c7-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="423c7-110">次に、このセクションで説明したとおりに、ラムダ式を実行できます。</span><span class="sxs-lookup"><span data-stu-id="423c7-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="423c7-111">例</span><span class="sxs-lookup"><span data-stu-id="423c7-111">Example</span></span>  
 <span data-ttu-id="423c7-112">次のコード例では、ラムダ式を作成して実行することで累乗する数値を累乗を表す式ツリーを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="423c7-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="423c7-113">電源に数値の累乗を表す、結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="423c7-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="423c7-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="423c7-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="423c7-115">参照されていない場合は、System.Core.dll へのプロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="423c7-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="423c7-116">System.Linq.Expressions 名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="423c7-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423c7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="423c7-117">See Also</span></span>  
 <span data-ttu-id="423c7-118">[式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="423c7-118">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="423c7-119"> [方法: 式ツリー (Visual Basic) を変更](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="423c7-119"> [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)</span></span>

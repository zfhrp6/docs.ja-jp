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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e12c45b417310f097d597561b2652ee793a4b2c0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-execute-expression-trees-visual-basic"></a>方法: 式ツリー (Visual Basic) を実行
このトピックでは、式ツリーを実行する方法を説明します。 式ツリーの実行で、値を返すことがありますか、メソッドの呼び出しなど、アクションをのみ実行することがあります。  
  
 ラムダ式を表す式ツリーのみを実行することができます。 型<xref:System.Linq.Expressions.LambdaExpression>または<xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601></xref:System.Linq.Expressions.LambdaExpression>のラムダ式を表す式ツリーが、します。 これらの式ツリーを実行するを呼び出し、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A>を実行可能なデリゲートを作成し、デリゲートを呼び出すメソッド</xref:System.Linq.Expressions.LambdaExpression.Compile%2A>。  
  
> [!NOTE]
>  デリゲートの型が不明の場合、ラムダ式は型の<xref:System.Linq.Expressions.LambdaExpression>および not <xref:System.Linq.Expressions.Expression%601>、呼び出す必要があります、<xref:System.Delegate.DynamicInvoke%2A>メソッドを直接呼び出す場合の代わりにデリゲートします</xref:System.Delegate.DynamicInvoke%2A></xref:System.Linq.Expressions.Expression%601></xref:System.Linq.Expressions.LambdaExpression>。  
  
 呼び出すことによって、本文として元の式ツリーを持つ新しいラムダ式を作成する式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>メソッド</xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>。 次に、このセクションで説明したとおりに、ラムダ式を実行できます。  
  
## <a name="example"></a>例  
 次のコード例では、ラムダ式を作成して実行することで累乗する数値を累乗を表す式ツリーを実行する方法を示します。 電源に数値の累乗を表す、結果が表示されます。  
  
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
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   参照されていない場合は、System.Core.dll へのプロジェクト参照を追加します。  
  
-   System.Linq.Expressions 名前空間が含まれます。  
  
## <a name="see-also"></a>関連項目  
 [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [方法: 式ツリー (Visual Basic) を変更](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)

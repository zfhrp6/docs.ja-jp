---
title: "方法: 式ツリー (Visual Basic) を変更"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28a79a2dc8817a3fc6c7f3e2e01c1270d2981334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>方法: 式ツリー (Visual Basic) を変更
このトピックでは、式ツリーを変更する方法について説明します。 式ツリーは変更不可であるため、直接変更を加えることができません。 式ツリーを変更するには、既存の式ツリーのコピーを作成する必要があります。コピーを作成する際に、必要な変更を加えます。 <xref:System.Linq.Expressions.ExpressionVisitor> クラスを使用して、既存の式ツリーを走査し、走査した各ノードをコピーすることができます。  
  
### <a name="to-modify-an-expression-tree"></a>式ツリーを変更するには  
  
1.  新しい**コンソール アプリケーション** プロジェクトを作成します。  
  
2.  追加、`Imports`ステートメントについては、ファイルを`System.Linq.Expressions`名前空間。  
  
3.  `AndAlsoModifier` クラスをプロジェクトに追加します。  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     このクラスは、`AND` 条件演算を表す式を変更するための特別なクラスで、<xref:System.Linq.Expressions.ExpressionVisitor> クラスを継承します。 このクラスによって条件 `AND` が条件 `OR` に変更されます。 そのために、クラスは基本データ型の <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> メソッドをオーバーライドします。`AND` 条件式は二項式で表されるためです。 `VisitBinary` メソッドでは、渡される式が `AND` 条件演算を表す場合、`AND` 条件演算子ではなく `OR` 条件演算子を含む新しい式がコードによって作成されます。 `VisitBinary` に渡される式が `AND` 条件演算を表さない場合は、基底クラスの実装が延期されます。 基底クラスのメソッドによって、渡された式ツリーに似たノードが作成されますが、そのノードのサブツリーは、ビジターによって再帰的に作成される式ツリーに置き換えられます。  
  
4.  追加、`Imports`ステートメントについては、ファイルを`System.Linq.Expressions`名前空間。  
  
5.  コードを追加して、 `Main` Module1.vb ファイルを式ツリーを作成し、そのメソッドに渡すことでメソッドが変更されます。  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     次のコードは、`AND` 条件演算を含む式を作成し、 `AndAlsoModifier` クラスのインスタンスを作成して、このクラスの `Modify` メソッドにその式を渡します。 元の式ツリーと変更された式ツリーの両方が出力され、変更内容が表示されます。  
  
6.  アプリケーションをコンパイルして実行します。  
  
## <a name="see-also"></a>関連項目  
 [方法: 式ツリー (Visual Basic) を実行](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)

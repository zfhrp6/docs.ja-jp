---
title: "方法: 式ツリー (Visual Basic) を変更 |Microsoft ドキュメント"
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
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fb4e818eed7d6547e091c914d40b3ce87af59512
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a>方法: 式ツリー (Visual Basic) を変更
このトピックでは、式ツリーを変更する方法を示します。 式ツリーは変更できません、つまり、変更が直接であることはできません。 式ツリーを変更するには、既存の式ツリーのコピーを作成し、コピーを作成するときに、必要な変更を加える必要があります。 使用することができます、<xref:System.Linq.Expressions.ExpressionVisitor>クラスを既存の式ツリーを走査し、走査の各ノードをコピーする</xref:System.Linq.Expressions.ExpressionVisitor>。  
  
### <a name="to-modify-an-expression-tree"></a>式ツリーを変更するには  
  
1.  新しい**コンソール アプリケーション**プロジェクトです。  
  
2.  追加、`Imports`ステートメント用にファイルを`System.Linq.Expressions`名前空間。  
  
3.  追加、`AndAlsoModifier`クラスをプロジェクトにします。  
  
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
  
     このクラスは継承、<xref:System.Linq.Expressions.ExpressionVisitor>クラスし、条件を表す式を変更する特殊な`AND`操作</xref:System.Linq.Expressions.ExpressionVisitor>。 これらの操作を変更する条件付きから`AND`する条件付きに`OR`します。 このクラスのオーバーライドを行うには、 <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>、基本データ型のメソッド、条件付き`AND`式はバイナリ式として表されます</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>。 `VisitBinary`メソッドに渡された式が条件を表す場合`AND`操作の場合、コードは、条件式を含む新しい式を構築します。`OR`演算子、条件式ではなく`AND`演算子。 場合に渡される式`VisitBinary`する条件付きを表さない`AND`操作、メソッドが基本クラスの実装に従います。 基本クラスのメソッドが、渡される式ツリーのようなノードが作成、ノードがある、式ツリーによる置き換えのサブツリーには、再帰的に、ユーザーによってが生成されます。  
  
4.  追加、`Imports`ステートメント用にファイルを`System.Linq.Expressions`名前空間。  
  
5.  コードを追加して、`Main`式ツリーを作成し、そのメソッドに渡すことに、Module1.vb ファイル内のメソッドが変更されます。  
  
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
  
     コード条件を含む式を作成する`AND`操作します。 インスタンスを作成し、`AndAlsoModifier`クラスし、する式を渡す、`Modify`このクラスのメソッドです。 変更を表示するのには、元と変更後の式ツリーの両方が出力されます。  
  
6.  アプリケーションをコンパイルして実行します。  
  
## <a name="see-also"></a>関連項目  
 [方法: 式ツリー (Visual Basic) を実行](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)

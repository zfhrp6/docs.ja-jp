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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2f0d383cbac639212519177fb1825875682f6233
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="edba6-102">方法: 式ツリー (Visual Basic) を変更</span><span class="sxs-lookup"><span data-stu-id="edba6-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="edba6-103">このトピックでは、式ツリーを変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="edba6-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="edba6-104">式ツリーは変更できません、つまり、変更が直接であることはできません。</span><span class="sxs-lookup"><span data-stu-id="edba6-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="edba6-105">式ツリーを変更するには、既存の式ツリーのコピーを作成し、コピーを作成するときに、必要な変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="edba6-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="edba6-106">使用することができます、<xref:System.Linq.Expressions.ExpressionVisitor>クラスを既存の式ツリーを走査し、走査の各ノードをコピーする</xref:System.Linq.Expressions.ExpressionVisitor>。</span><span class="sxs-lookup"><span data-stu-id="edba6-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="edba6-107">式ツリーを変更するには</span><span class="sxs-lookup"><span data-stu-id="edba6-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="edba6-108">新しい**コンソール アプリケーション**プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="edba6-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="edba6-109">追加、`Imports`ステートメント用にファイルを`System.Linq.Expressions`名前空間。</span><span class="sxs-lookup"><span data-stu-id="edba6-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="edba6-110">追加、`AndAlsoModifier`クラスをプロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="edba6-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="edba6-111">このクラスは継承、<xref:System.Linq.Expressions.ExpressionVisitor>クラスし、条件を表す式を変更する特殊な`AND`操作</xref:System.Linq.Expressions.ExpressionVisitor>。</span><span class="sxs-lookup"><span data-stu-id="edba6-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="edba6-112">これらの操作を変更する条件付きから`AND`する条件付きに`OR`します。</span><span class="sxs-lookup"><span data-stu-id="edba6-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="edba6-113">このクラスのオーバーライドを行うには、 <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>、基本データ型のメソッド、条件付き`AND`式はバイナリ式として表されます</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>。</span><span class="sxs-lookup"><span data-stu-id="edba6-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="edba6-114">`VisitBinary`メソッドに渡された式が条件を表す場合`AND`操作の場合、コードは、条件式を含む新しい式を構築します。`OR`演算子、条件式ではなく`AND`演算子。</span><span class="sxs-lookup"><span data-stu-id="edba6-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="edba6-115">場合に渡される式`VisitBinary`する条件付きを表さない`AND`操作、メソッドが基本クラスの実装に従います。</span><span class="sxs-lookup"><span data-stu-id="edba6-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="edba6-116">基本クラスのメソッドが、渡される式ツリーのようなノードが作成、ノードがある、式ツリーによる置き換えのサブツリーには、再帰的に、ユーザーによってが生成されます。</span><span class="sxs-lookup"><span data-stu-id="edba6-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="edba6-117">追加、`Imports`ステートメント用にファイルを`System.Linq.Expressions`名前空間。</span><span class="sxs-lookup"><span data-stu-id="edba6-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="edba6-118">コードを追加して、`Main`式ツリーを作成し、そのメソッドに渡すことに、Module1.vb ファイル内のメソッドが変更されます。</span><span class="sxs-lookup"><span data-stu-id="edba6-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="edba6-119">コード条件を含む式を作成する`AND`操作します。</span><span class="sxs-lookup"><span data-stu-id="edba6-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="edba6-120">インスタンスを作成し、`AndAlsoModifier`クラスし、する式を渡す、`Modify`このクラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="edba6-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="edba6-121">変更を表示するのには、元と変更後の式ツリーの両方が出力されます。</span><span class="sxs-lookup"><span data-stu-id="edba6-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="edba6-122">アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="edba6-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edba6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="edba6-123">See Also</span></span>  
 <span data-ttu-id="edba6-124">[方法: 式ツリー (Visual Basic) を実行](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="edba6-124">[How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
<span data-ttu-id="edba6-125"> [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span><span class="sxs-lookup"><span data-stu-id="edba6-125"> [Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span></span>

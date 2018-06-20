---
title: '方法: LINQ (Visual Basic) で ArrayList を照会します。'
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: 24865842d073dbd4cbb60fe4a228520e98010f4d
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207247"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="164ec-102">方法: LINQ (Visual Basic) で ArrayList を照会します。</span><span class="sxs-lookup"><span data-stu-id="164ec-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>
<span data-ttu-id="164ec-103">LINQ を使用して <xref:System.Collections.ArrayList> などの非ジェネリックの <xref:System.Collections.IEnumerable> コレクションをクエリする場合、範囲変数の型を明示的に宣言して、オブジェクトの特定の型をコレクションに反映させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="164ec-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="164ec-104">ある場合など、<xref:System.Collections.ArrayList>の`Student`、オブジェクト、 [From 句](../../../../visual-basic/language-reference/queries/from-clause.md)は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="164ec-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 <span data-ttu-id="164ec-105">範囲変数の型を指定することで、<xref:System.Collections.ArrayList> 内の各項目を `Student` にキャストします。</span><span class="sxs-lookup"><span data-stu-id="164ec-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="164ec-106">明示的に型指定された範囲変数をクエリ式で使用すると、<xref:System.Linq.Enumerable.Cast%2A> メソッドを呼び出した場合と同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="164ec-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="164ec-107">指定したキャストを実行できない場合、<xref:System.Linq.Enumerable.Cast%2A> は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="164ec-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="164ec-108"><xref:System.Linq.Enumerable.Cast%2A> および <xref:System.Linq.Enumerable.OfType%2A> は、非ジェネリックの <xref:System.Collections.IEnumerable> 型で動作する、2 つの標準クエリ演算子メソッドです。</span><span class="sxs-lookup"><span data-stu-id="164ec-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="164ec-109">Visual basic で明示的に呼び出す必要があります、<xref:System.Linq.Enumerable.Cast%2A>メソッドをデータ ソースを特定の範囲変数の型を確認します。</span><span class="sxs-lookup"><span data-stu-id="164ec-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="164ec-110">詳細については、次を参照してください。[クエリ操作 (Visual Basic) での型の関係](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="164ec-110">For more information, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="164ec-111">例</span><span class="sxs-lookup"><span data-stu-id="164ec-111">Example</span></span>  
 <span data-ttu-id="164ec-112">次の例では、<xref:System.Collections.ArrayList> に対して単純なクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="164ec-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="164ec-113">この例では、コードが <xref:System.Collections.ArrayList.Add%2A> メソッドを呼び出すときにオブジェクト初期化子を使用していますが、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="164ec-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a><span data-ttu-id="164ec-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="164ec-114">See Also</span></span>  
 [<span data-ttu-id="164ec-115">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="164ec-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

---
title: "方法: LINQ (Visual Basic) で ArrayList を照会 |Microsoft ドキュメント"
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
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
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
ms.openlocfilehash: f48b06c23b1e28fccb953638954a8d9afefe574e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>方法: クエリ、LINQ で ArrayList を (Visual Basic)
LINQ を使用してクエリの非ジェネリックする<xref:System.Collections.IEnumerable>などコレクション<xref:System.Collections.ArrayList>、コレクション内のオブジェクトの特定の種類を反映するように範囲変数の型を明示的に宣言する必要があります</xref:System.Collections.ArrayList></xref:System.Collections.IEnumerable>。 ある場合など、<xref:System.Collections.ArrayList>の`Student`オブジェクト、 [From 句](../../../../visual-basic/language-reference/queries/from-clause.md)次のようになります:</xref:System.Collections.ArrayList>  
  
```  
  
Dim query = From student As Student In arrList   
...  
  
```  
  
 内の各項目のキャストの範囲変数の型を指定することによって、<xref:System.Collections.ArrayList>に、 `Student`</xref:System.Collections.ArrayList> 。  
  
 クエリ式で明示的に型指定された範囲変数の使用は呼び出すことと同じ、<xref:System.Linq.Enumerable.Cast%2A>メソッド</xref:System.Linq.Enumerable.Cast%2A>。 <xref:System.Linq.Enumerable.Cast%2A>指定されたキャストは実行できない場合は、例外をスローします。</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A><xref:System.Linq.Enumerable.OfType%2A>非ジェネリックで動作する&2; つの標準クエリ演算子メソッドを<xref:System.Collections.IEnumerable>の種類</xref:System.Collections.IEnumerable></xref:System.Linq.Enumerable.OfType%2A>。</xref:System.Linq.Enumerable.Cast%2A> Visual basic で明示的に呼び出す必要があります、<xref:System.Linq.Enumerable.Cast%2A>メソッドをデータ ソースを特定の範囲変数の型を確認します</xref:System.Linq.Enumerable.Cast%2A>。 詳細については、次を参照してください。[クエリ操作 (Visual Basic) での型の関係](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)します。  
  
## <a name="example"></a>例  
 次の例は、 <xref:System.Collections.ArrayList>。</xref:System.Collections.ArrayList>経由で簡単なクエリを示します この例では、コードを呼び出すときに、オブジェクト初期化子が使用して、メモ、<xref:System.Collections.ArrayList.Add%2A>メソッドが、これは必須ではありません</xref:System.Collections.ArrayList.Add%2A>。  
  
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
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

---
title: "(Visual Basic) のジェネリック コレクションに対するインターフェイスの分散の使用 |Microsoft ドキュメント"
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
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
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
ms.openlocfilehash: 86184c7de3fe16148bf954b16d703ca682216337
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>(Visual Basic) のジェネリック コレクションに対するインターフェイスの分散の使用
共変のインターフェイスは、インターフェイスで指定されている以上の派生型を返すメソッドを使用します。 反変のインターフェイスは、インターフェイスで指定された値よりも弱い派生型のパラメーターを受け取るには、そのメソッドを許可します。  
  
 .NET Framework 4 ではいくつかの既存のインターフェイスが共変と反変です。 <xref:System.Collections.Generic.IEnumerable%601>および<xref:System.IComparable%601>。</xref:System.IComparable%601></xref:System.Collections.Generic.IEnumerable%601>が含まれます これにより、派生型のコレクションの基本型のジェネリック コレクションを操作するメソッドを再利用できます。  
  
 .NET Framework のバリアントのインターフェイスの一覧は、次を参照してください。[ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)します。  
  
## <a name="converting-generic-collections"></a>ジェネリック コレクションの変換  
 次の例では、ジェネリックの共変性でのサポートの特典、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。 `PrintFullName`メソッドのコレクションを受け取る、`IEnumerable(Of Person)`型をパラメーターとして。 ただし、再利用できますのコレクションを`IEnumerable(Of Person)`ために、入力`Employee`継承`Person`します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="comparing-generic-collections"></a>ジェネリック コレクションの比較  
 次の例では、反変性でのサポートの特典、<xref:System.Collections.Generic.IComparer%601>インターフェイス</xref:System.Collections.Generic.IComparer%601>。 `PersonComparer` クラスは、`IComparer(Of Person)` インターフェイスを実装します。 ただし、このクラスのオブジェクトのシーケンスを比較するを再利用する、`Employee`ために、入力`Employee`継承`Person`します。  
  
```vb  
' Simple hierarhcy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
' The custom comparer for the Person type  
' with standard implementations of Equals()  
' and GetHashCode() methods.  
Class PersonComparer  
    Implements IEqualityComparer(Of Person)  
  
    Public Function Equals1(  
        ByVal x As Person,  
        ByVal y As Person) As Boolean _  
        Implements IEqualityComparer(Of Person).Equals  
  
        If x Is y Then Return True  
        If x Is Nothing OrElse y Is Nothing Then Return False  
        Return (x.FirstName = y.FirstName) AndAlso  
            (x.LastName = y.LastName)  
    End Function  
    Public Function GetHashCode1(  
        ByVal person As Person) As Integer _  
        Implements IEqualityComparer(Of Person).GetHashCode  
  
        If person Is Nothing Then Return 0  
        Dim hashFirstName =  
            If(person.FirstName Is Nothing,  
            0, person.FirstName.GetHashCode())  
        Dim hashLastName = person.LastName.GetHashCode()  
        Return hashFirstName Xor hashLastName  
    End Function  
End Class  
  
Sub Main()  
    Dim employees = New List(Of Employee) From {  
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},  
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}  
    }  
  
    ' You can pass PersonComparer,   
    ' which implements IEqualityComparer(Of Person),  
    ' although the method expects IEqualityComparer(Of Employee)  
  
    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())  
  
    For Each employee In noduplicates  
        Console.WriteLine(employee.FirstName & " " & employee.LastName)  
    Next  
End Sub  
```  
  
## <a name="see-also"></a>関連項目  
 [ジェネリック インターフェイス (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)

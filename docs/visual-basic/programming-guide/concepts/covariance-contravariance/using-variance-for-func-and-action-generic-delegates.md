---
title: "Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用 |Microsoft ドキュメント"
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
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
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
ms.openlocfilehash: b4dc4a162d3562b218a448653cb51473fff4165a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="04cf1-102">Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用</span><span class="sxs-lookup"><span data-stu-id="04cf1-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="04cf1-103">これらの例は、共変性と反変性を使用する方法をデモンストレーション、`Func`と`Action`メソッドの再利用を有効にして、コード内の柔軟性を提供する汎用デリゲート。</span><span class="sxs-lookup"><span data-stu-id="04cf1-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="04cf1-104">ジェネリックの共変性と反変性の詳細については、次を参照してください。[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)します。</span><span class="sxs-lookup"><span data-stu-id="04cf1-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="04cf1-105">共変の型パラメーターを持つデリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="04cf1-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="04cf1-106">次の例では、ジェネリックの共分散のサポートの特典`Func`デリゲート。</span><span class="sxs-lookup"><span data-stu-id="04cf1-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="04cf1-107">`FindByTitle`メソッドのパラメーターを受け取る、`String`を入力し、オブジェクトを返します、`Employee`型です。</span><span class="sxs-lookup"><span data-stu-id="04cf1-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="04cf1-108">ただし、このメソッドを割り当てることができます、`Func(Of String, Person)`ので委任`Employee`継承`Person`します。</span><span class="sxs-lookup"><span data-stu-id="04cf1-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class Finder  
    Public Shared Function FindByTitle(  
        ByVal title As String) As Employee  
        ' This is a stub for a method that returns  
        ' an employee that has the specified title.  
        Return New Employee  
    End Function  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim findEmployee As Func(Of String, Employee) =  
            AddressOf FindByTitle  
  
        ' The delegate expects a method to return Person,  
        ' but you can assign it a method that returns Employee.  
        Dim findPerson As Func(Of String, Person) =  
            AddressOf FindByTitle  
  
        ' You can also assign a delegate   
        ' that returns a more derived type to a delegate   
        ' that returns a less derived type.  
        findPerson = findEmployee  
    End Sub  
End Class  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="04cf1-109">反変の型パラメーターを持つデリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="04cf1-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="04cf1-110">次の例では、ジェネリックの反変性のサポートの特典`Action`デリゲート。</span><span class="sxs-lookup"><span data-stu-id="04cf1-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="04cf1-111">`AddToContacts`メソッドのパラメーターを受け取る、`Person`型です。</span><span class="sxs-lookup"><span data-stu-id="04cf1-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="04cf1-112">ただし、このメソッドを割り当てることができます、`Action(Of Employee)`ので委任`Employee`継承`Person`します。</span><span class="sxs-lookup"><span data-stu-id="04cf1-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
```vb  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class AddressBook  
    Shared Sub AddToContacts(ByVal person As Person)  
        ' This method adds a Person object  
        ' to a contact list.  
    End Sub  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim addPersonToContacts As Action(Of Person) =  
            AddressOf AddToContacts  
  
        ' The Action delegate expects   
        ' a method that has an Employee parameter,  
        ' but you can assign it a method that has a Person parameter  
        ' because Employee derives from Person.  
        Dim addEmployeeToContacts As Action(Of Employee) =  
            AddressOf AddToContacts  
  
        ' You can also assign a delegate   
        ' that accepts a less derived parameter   
        ' to a delegate that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="04cf1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="04cf1-113">See Also</span></span>  
 <span data-ttu-id="04cf1-114">[ジェネリックの共変性と反変性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/covariance-and-contravariance.md) </span><span class="sxs-lookup"><span data-stu-id="04cf1-114">[Covariance and Contravariance (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/covariance-and-contravariance.md) </span></span>  
<span data-ttu-id="04cf1-115"> [ジェネリック](https://msdn.microsoft.com/library/ms172192)</span><span class="sxs-lookup"><span data-stu-id="04cf1-115"> [Generics](https://msdn.microsoft.com/library/ms172192)</span></span>

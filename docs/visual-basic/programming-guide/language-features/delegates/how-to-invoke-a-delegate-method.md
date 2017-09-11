---
title: "方法: デリゲート メソッド (Visual Basic) を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 060a60da16a0032850b0a45822c8fd24b4622b83
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="29b70-102">方法: デリゲート メソッドを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29b70-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="29b70-103">この例では、メソッドをデリゲートに関連付け、デリゲートによってメソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="29b70-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="29b70-104">デリゲートと一致する手順を作成します。</span><span class="sxs-lookup"><span data-stu-id="29b70-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="29b70-105">という名前のデリゲートを作成する`MySubDelegate`です。</span><span class="sxs-lookup"><span data-stu-id="29b70-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="29b70-106">デリゲートと同じシグネチャを持つメソッドを含むクラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="29b70-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="29b70-107">デリゲートのインスタンスを作成し、組み込みを呼び出すことによって、デリゲートに関連付けられているメソッドを呼び出し、メソッドを定義`Invoke`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="29b70-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29b70-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="29b70-108">See Also</span></span>  
 <span data-ttu-id="29b70-109">[Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="29b70-109">[Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="29b70-110"> [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="29b70-110"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="29b70-111"> [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="29b70-111"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="29b70-112"> [マルチスレッド アプリケーション](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)</span><span class="sxs-lookup"><span data-stu-id="29b70-112"> [Multithreaded Applications](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)</span></span>

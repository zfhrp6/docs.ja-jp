---
title: "デリゲート (Visual Basic) の分散の使用 |Microsoft ドキュメント"
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
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
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
ms.openlocfilehash: 620fd61000e42d68f566e441d023d73a036000ae
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="4bfc9-102">デリゲート (Visual Basic) の分散の使用</span><span class="sxs-lookup"><span data-stu-id="4bfc9-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="4bfc9-103">デリゲートにメソッドを割り当てるときに*共変性*と*反変性*メソッド シグネチャを持つデリゲート型に一致する柔軟性を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="4bfc9-104">ジェネリックの共変性は、メソッドのデリゲートで定義されているよりも強い派生は、戻り値の型を許可します。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="4bfc9-105">反変性により、デリゲート型の場合よりも弱い派生パラメーター型を持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="4bfc9-106">例 1: 共変性</span><span class="sxs-lookup"><span data-stu-id="4bfc9-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="4bfc9-107">説明</span><span class="sxs-lookup"><span data-stu-id="4bfc9-107">Description</span></span>  
 <span data-ttu-id="4bfc9-108">この例では、デリゲート シグネチャの戻り値の型から派生した戻り値の型の方法でデリゲートを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="4bfc9-109">によって返されるデータ型`DogsHandler`型`Dogs`から派生した、`Mammals`デリゲートで定義されている型。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4bfc9-110">コード</span><span class="sxs-lookup"><span data-stu-id="4bfc9-110">Code</span></span>  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="4bfc9-111">例 2: 反変性</span><span class="sxs-lookup"><span data-stu-id="4bfc9-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="4bfc9-112">説明</span><span class="sxs-lookup"><span data-stu-id="4bfc9-112">Description</span></span>  
 <span data-ttu-id="4bfc9-113">この例では、デリゲート シグネチャのパラメーターの型の基本型である型のパラメーターを持つメソッドでデリゲートを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="4bfc9-114">反変性により、複数のハンドラーではなく&1; つのイベント ハンドラーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="4bfc9-115">受け取るイベント ハンドラーを作成するなど、`EventArgs`パラメーターを入力し、それを使用、`Button.MouseClick`イベントを送信する、`MouseEventArgs`型をパラメーターとして、さらに、`TextBox.KeyDown`イベントを送信する、`KeyEventArgs`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="4bfc9-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4bfc9-116">コード</span><span class="sxs-lookup"><span data-stu-id="4bfc9-116">Code</span></span>  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bfc9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bfc9-117">See Also</span></span>  
 <span data-ttu-id="4bfc9-118">[デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="4bfc9-118">[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span></span>  
<span data-ttu-id="4bfc9-119"> [Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="4bfc9-119"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>

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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5bd3e60031eac713cee3dee1399af8c6b83e6656
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a>デリゲート (Visual Basic) の分散の使用
デリゲートにメソッドを割り当てるときに*共変性*と*反変性*メソッド シグネチャを持つデリゲート型に一致する柔軟性を提供します。 ジェネリックの共変性は、メソッドのデリゲートで定義されているよりも強い派生は、戻り値の型を許可します。 反変性により、デリゲート型の場合よりも弱い派生パラメーター型を持つメソッドです。  
  
## <a name="example-1-covariance"></a>例 1: 共変性  
  
### <a name="description"></a>説明  
 この例では、デリゲート シグネチャの戻り値の型から派生した戻り値の型の方法でデリゲートを使用する方法を示します。 によって返されるデータ型`DogsHandler`型`Dogs`から派生した、`Mammals`デリゲートで定義されている型。  
  
### <a name="code"></a>コード  
  
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
  
## <a name="example-2-contravariance"></a>例 2: 反変性  
  
### <a name="description"></a>説明  
 この例では、デリゲート シグネチャのパラメーターの型の基本型である型のパラメーターを持つメソッドでデリゲートを使用する方法を示します。 反変性により、複数のハンドラーではなく&1; つのイベント ハンドラーを使用することができます。 受け取るイベント ハンドラーを作成するなど、`EventArgs`パラメーターを入力し、それを使用、`Button.MouseClick`イベントを送信する、`MouseEventArgs`型をパラメーターとして、さらに、`TextBox.KeyDown`イベントを送信する、`KeyEventArgs`パラメーター。  
  
### <a name="code"></a>コード  
  
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
  
## <a name="see-also"></a>関連項目  
 [デリゲート (Visual Basic) の分散](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)   
 [Func および Action 汎用デリゲート (Visual Basic) に対する分散の使用](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

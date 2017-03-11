---
title: "How to: Invoke a Delegate Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# How to: Invoke a Delegate Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

この例では、メソッドとデリゲートを関連付け、デリゲートによってメソッドを呼び出す方法について説明します。  
  
### デリゲートおよび一致プロシージャの作成  
  
1.  `MySubDelegate` という名前のデリゲートを作成します。  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  デリゲートと同じシグネチャを持つメソッドが含まれるクラスを宣言します。  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  デリゲートのインスタンスが作成されるメソッドを定義し、組み込みの `Invoke` メソッドを呼び出して、デリゲートに関連付けられたメソッドを呼び出します。  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## 参照  
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [マルチスレッド アプリケーション](../Topic/Multithreaded%20Applications%20\(C%23%20and%20Visual%20Basic\).md)
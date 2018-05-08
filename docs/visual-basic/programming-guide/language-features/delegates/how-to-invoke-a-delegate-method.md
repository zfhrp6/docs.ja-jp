---
title: '方法: デリゲート メソッドを呼び出す (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: aca87dd9fa1990d44c99aab7753f2fd7d508adc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>方法: デリゲート メソッドを呼び出す (Visual Basic)
この例では、デリゲートにメソッドを関連付けるし、デリゲートからメソッドを呼び出す方法を示します。  
  
### <a name="create-the-delegate-and-matching-procedures"></a>デリゲートと一致するプロシージャを作成します。  
  
1.  という名前のデリゲートを作成する`MySubDelegate`です。  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  デリゲートと同じシグネチャを持つメソッドを含むクラスを宣言します。  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  デリゲートのインスタンスを作成し、組み込みを呼び出すことによって、デリゲートに関連付けられているメソッドを呼び出すメソッドを定義`Invoke`メソッドです。  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [マルチスレッド アプリケーション](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)

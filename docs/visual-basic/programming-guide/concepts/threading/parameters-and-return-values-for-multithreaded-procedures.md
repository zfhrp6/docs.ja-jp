---
title: パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 039e9be6f174148995a83c842a442806b9409a3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648100"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)
マルチスレッド アプリケーションでの値の受け渡しは複雑です。それは、引数を受け取らず値を返さないプロシージャへの参照をスレッド クラスのコンストラクターに渡す必要があるためです。 以下のセクションでは、異なるスレッドのプロシージャからパラメーターを指定して値を返す単純な方法を示します。  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>マルチスレッド プロシージャのパラメーターの指定  
 マルチスレッド メソッドの呼び出しにパラメーターを指定する最良の方法は、クラスにターゲット メソッドをラップし、新規スレッドのパラメーターとして機能するフィールドをそのクラスに対して定義することです。 この方法の利点は、新規スレッドを開始するたびに独自のパラメーターでクラスの新規インスタンスを作成できることです。 たとえば、次のコードに示すように三角形の面積を計算する関数があるとします。  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 次に示すように、`CalcArea` 関数をラップして入力パラメーターを格納するフィールドを作成するクラスを記述できます。  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 `AreaClass` を使用するには、次のコードに示すように `AreaClass` オブジェクトを作成し、`Base` プロパティと `Height` プロパティを設定します。  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 `TestArea` プロシージャは `CalcArea` メソッドの呼び出し後に `Area` フィールドの値を確認しないことに注意してください。 `CalcArea` は別のスレッドで実行されるため、`Thread.Start` を呼び出した直後に確認する場合は、`Area` フィールドが設定されているとは限りません。 次のセクションでは、マルチスレッド プロシージャから値を返す適切な方法について説明します。  
  
## <a name="returning-values-from-multithreaded-procedures"></a>マルチスレッド プロシージャから値を返す  
 異なるスレッドで実行されるプロシージャの場合、値を返す動作は複雑になります。プロシージャは関数にすることができず、`ByRef` 引数を使用できないからです。 値を返す最も簡単な方法は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使ってスレッドを管理し、タスクが完了したときにイベントを生成し、結果をイベント ハンドラーで処理することです。  
  
 次の例では、別のスレッドで実行中のプロシージャからイベントを発生させて値を返します。  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 スレッド プールのスレッドにパラメーターと戻り値を提供するには、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用します。 スレッド タイマーのスレッドもこの目的で状態オブジェクトをサポートしています。 スレッド プールおよびスレッド タイマーについては、次を参照してください。[スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[スレッド プール](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)と[スレッド タイマー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [マルチスレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [コンポーネントのマルチスレッド](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)

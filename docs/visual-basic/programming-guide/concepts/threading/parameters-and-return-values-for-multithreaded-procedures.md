---
title: "パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5d8adde531d31aa6bf353f53bd4cfecc084f515
ms.lasthandoff: 03/13/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)
スレッド クラスのコンス トラクターは、引数を使用しないと、値を返さないプロシージャへの参照を渡す必要があるためにを提供し、マルチ スレッド アプリケーションで値を返すには、複雑なです。 次のセクションでは、パラメーターを指定して、個別のスレッドでプロシージャから値を返す単純な方法を示します。  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>マルチ スレッド プロシージャのパラメーターの指定  
 マルチ スレッドのメソッド呼び出しのパラメーターを指定する最善の方法では、クラスで、対象のメソッドをラップし、その新しいスレッドへのパラメーターとして使用するクラスのフィールドを定義します。 このアプローチの利点は、新しいスレッドを開始するたびに、独自のパラメーターを使用して、クラスの新しいインスタンスを作成します。 たとえば、次のコードのように、三角形の面積を計算する関数があるとします。  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 ラップするクラスを作成できますが、`CalcArea`機能し、次のように入力パラメーターを格納するフィールドを作成します。  
  
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
  
 使用する、 `AreaClass`、作成することができます、`AreaClass`オブジェクトし、設定、`Base`と`Height`次のコードに示すようにプロパティ。  
  
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
  
 注意して、`TestArea`プロシージャがの値をチェックしていない、`Area`フィールド呼び出した後、`CalcArea`メソッドです。 `CalcArea`別のスレッドで実行される、`Area`を呼び出した後すぐに確認する場合に設定するフィールドは保証されません`Thread.Start`します。 次のセクションでは、マルチ スレッド プロシージャから値を返す方について説明します。  
  
## <a name="returning-values-from-multithreaded-procedures"></a>マルチ スレッド プロシージャから値を返す  
 個別のスレッドで実行されるプロシージャからの戻り値は複雑にするという事実の手順は、関数には使用できません`ByRef`引数。 値を返す最も簡単な方法は、使用する、 <xref:System.ComponentModel.BackgroundWorker>、スレッドを管理およびタスクを完了すると、イベントを発生させるイベント ハンドラーを持つ結果を処理するコンポーネント</xref:System.ComponentModel.BackgroundWorker>。  
  
 次の例では、別のスレッドで実行中のプロシージャからのイベントを発生させることによって、値を返します。  
  
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
  
 パラメーターを指定し、オプションのパラメーターを使用して、スレッド プールのスレッドに値を返す`ByVal`の状態オブジェクト変数、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>メソッド</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>。 スレッド タイマー スレッドは、この目的でも、状態オブジェクトをサポートします。 詳細については、スレッド プールとスレッド タイマーは、次を参照してください。[スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[スレッド プール](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)と[スレッド タイマー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)   
 [スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)   
 [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [マルチ スレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [コンポーネントのマルチ スレッド](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)

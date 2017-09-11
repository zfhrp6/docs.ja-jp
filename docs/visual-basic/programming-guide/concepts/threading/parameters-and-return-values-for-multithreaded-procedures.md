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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6d1eb53454b6e0d964be15df2e320ce189e7d875
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="5ee01-102">パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ee01-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="5ee01-103">スレッド クラスのコンス トラクターは、引数を使用しないと、値を返さないプロシージャへの参照を渡す必要があるためにを提供し、マルチ スレッド アプリケーションで値を返すには、複雑なです。</span><span class="sxs-lookup"><span data-stu-id="5ee01-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="5ee01-104">次のセクションでは、パラメーターを指定して、個別のスレッドでプロシージャから値を返す単純な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="5ee01-105">マルチ スレッド プロシージャのパラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="5ee01-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="5ee01-106">マルチ スレッドのメソッド呼び出しのパラメーターを指定する最善の方法では、クラスで、対象のメソッドをラップし、その新しいスレッドへのパラメーターとして使用するクラスのフィールドを定義します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="5ee01-107">このアプローチの利点は、新しいスレッドを開始するたびに、独自のパラメーターを使用して、クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="5ee01-108">たとえば、次のコードのように、三角形の面積を計算する関数があるとします。</span><span class="sxs-lookup"><span data-stu-id="5ee01-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="5ee01-109">ラップするクラスを作成できますが、`CalcArea`機能し、次のように入力パラメーターを格納するフィールドを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="5ee01-110">使用する、 `AreaClass`、作成することができます、`AreaClass`オブジェクトし、設定、`Base`と`Height`次のコードに示すようにプロパティ。</span><span class="sxs-lookup"><span data-stu-id="5ee01-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="5ee01-111">注意して、`TestArea`プロシージャがの値をチェックしていない、`Area`フィールド呼び出した後、`CalcArea`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5ee01-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="5ee01-112">`CalcArea`別のスレッドで実行される、`Area`を呼び出した後すぐに確認する場合に設定するフィールドは保証されません`Thread.Start`します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="5ee01-113">次のセクションでは、マルチ スレッド プロシージャから値を返す方について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="5ee01-114">マルチ スレッド プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="5ee01-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="5ee01-115">個別のスレッドで実行されるプロシージャからの戻り値は複雑にするという事実の手順は、関数には使用できません`ByRef`引数。</span><span class="sxs-lookup"><span data-stu-id="5ee01-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="5ee01-116">値を返す最も簡単な方法は、使用する、 <xref:System.ComponentModel.BackgroundWorker>、スレッドを管理およびタスクを完了すると、イベントを発生させるイベント ハンドラーを持つ結果を処理するコンポーネント</xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="5ee01-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="5ee01-117">次の例では、別のスレッドで実行中のプロシージャからのイベントを発生させることによって、値を返します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="5ee01-118">パラメーターを指定し、オプションのパラメーターを使用して、スレッド プールのスレッドに値を返す`ByVal`の状態オブジェクト変数、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>メソッド</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="5ee01-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="5ee01-119">スレッド タイマー スレッドは、この目的でも、状態オブジェクトをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5ee01-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="5ee01-120">詳細については、スレッド プールとスレッド タイマーは、次を参照してください。[スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[スレッド プール](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)と[スレッド タイマー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)します。</span><span class="sxs-lookup"><span data-stu-id="5ee01-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee01-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee01-121">See Also</span></span>  
 <span data-ttu-id="5ee01-122">[チュートリアル: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span><span class="sxs-lookup"><span data-stu-id="5ee01-122">[Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span></span>  
<span data-ttu-id="5ee01-123"> [スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span><span class="sxs-lookup"><span data-stu-id="5ee01-123"> [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span></span>  
<span data-ttu-id="5ee01-124"> [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="5ee01-124"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
<span data-ttu-id="5ee01-125"> [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ee01-125"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="5ee01-126"> [マルチ スレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="5ee01-126"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="5ee01-127"> [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ee01-127"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="5ee01-128"> [コンポーネントのマルチ スレッド](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)</span><span class="sxs-lookup"><span data-stu-id="5ee01-128"> [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)</span></span>

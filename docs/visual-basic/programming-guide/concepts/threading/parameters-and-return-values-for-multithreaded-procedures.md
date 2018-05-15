---
title: パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 039e9be6f174148995a83c842a442806b9409a3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="94a83-102">パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a83-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="94a83-103">マルチスレッド アプリケーションでの値の受け渡しは複雑です。それは、引数を受け取らず値を返さないプロシージャへの参照をスレッド クラスのコンストラクターに渡す必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="94a83-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="94a83-104">以下のセクションでは、異なるスレッドのプロシージャからパラメーターを指定して値を返す単純な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="94a83-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="94a83-105">マルチスレッド プロシージャのパラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="94a83-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="94a83-106">マルチスレッド メソッドの呼び出しにパラメーターを指定する最良の方法は、クラスにターゲット メソッドをラップし、新規スレッドのパラメーターとして機能するフィールドをそのクラスに対して定義することです。</span><span class="sxs-lookup"><span data-stu-id="94a83-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="94a83-107">この方法の利点は、新規スレッドを開始するたびに独自のパラメーターでクラスの新規インスタンスを作成できることです。</span><span class="sxs-lookup"><span data-stu-id="94a83-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="94a83-108">たとえば、次のコードに示すように三角形の面積を計算する関数があるとします。</span><span class="sxs-lookup"><span data-stu-id="94a83-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="94a83-109">次に示すように、`CalcArea` 関数をラップして入力パラメーターを格納するフィールドを作成するクラスを記述できます。</span><span class="sxs-lookup"><span data-stu-id="94a83-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="94a83-110">`AreaClass` を使用するには、次のコードに示すように `AreaClass` オブジェクトを作成し、`Base` プロパティと `Height` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="94a83-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="94a83-111">`TestArea` プロシージャは `CalcArea` メソッドの呼び出し後に `Area` フィールドの値を確認しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="94a83-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="94a83-112">`CalcArea` は別のスレッドで実行されるため、`Thread.Start` を呼び出した直後に確認する場合は、`Area` フィールドが設定されているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="94a83-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="94a83-113">次のセクションでは、マルチスレッド プロシージャから値を返す適切な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94a83-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="94a83-114">マルチスレッド プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="94a83-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="94a83-115">異なるスレッドで実行されるプロシージャの場合、値を返す動作は複雑になります。プロシージャは関数にすることができず、`ByRef` 引数を使用できないからです。</span><span class="sxs-lookup"><span data-stu-id="94a83-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="94a83-116">値を返す最も簡単な方法は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使ってスレッドを管理し、タスクが完了したときにイベントを生成し、結果をイベント ハンドラーで処理することです。</span><span class="sxs-lookup"><span data-stu-id="94a83-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="94a83-117">次の例では、別のスレッドで実行中のプロシージャからイベントを発生させて値を返します。</span><span class="sxs-lookup"><span data-stu-id="94a83-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="94a83-118">スレッド プールのスレッドにパラメーターと戻り値を提供するには、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="94a83-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="94a83-119">スレッド タイマーのスレッドもこの目的で状態オブジェクトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="94a83-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="94a83-120">スレッド プールおよびスレッド タイマーについては、次を参照してください。[スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[スレッド プール](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)と[スレッド タイマー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)です。</span><span class="sxs-lookup"><span data-stu-id="94a83-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a83-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="94a83-121">See Also</span></span>  
 [<span data-ttu-id="94a83-122">チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a83-122">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="94a83-123">スレッド プール (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a83-123">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="94a83-124">スレッドの同期 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a83-124">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="94a83-125">イベント</span><span class="sxs-lookup"><span data-stu-id="94a83-125">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="94a83-126">マルチスレッド アプリケーション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94a83-126">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="94a83-127">デリゲート</span><span class="sxs-lookup"><span data-stu-id="94a83-127">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="94a83-128">コンポーネントのマルチスレッド</span><span class="sxs-lookup"><span data-stu-id="94a83-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)

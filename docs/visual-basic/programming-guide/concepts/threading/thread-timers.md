---
title: スレッド タイマー (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
ms.openlocfilehash: 019b8372be63b9a9fdbcee134834a34f6bef2b74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="thread-timers-visual-basic"></a><span data-ttu-id="3d3b7-102">スレッド タイマー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d3b7-102">Thread Timers (Visual Basic)</span></span>
<span data-ttu-id="3d3b7-103"><xref:System.Threading.Timer?displayProperty=nameWithType> クラスは、タスクを別々のスレッドで定期的に実行するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="3d3b7-103">The <xref:System.Threading.Timer?displayProperty=nameWithType> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="3d3b7-104">たとえば、スレッド タイマーを使用すると、データベースのステータスと整合性をチェックしたり、重要なファイルをバックアップしたりできます。</span><span class="sxs-lookup"><span data-stu-id="3d3b7-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="3d3b7-105">スレッド タイマーの例</span><span class="sxs-lookup"><span data-stu-id="3d3b7-105">Thread Timer Example</span></span>  
 <span data-ttu-id="3d3b7-106">2 秒ごとにタスクを起動し、フラグを使用して <xref:System.IDisposable.Dispose%2A> メソッドを開始し、タイマーを停止する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d3b7-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="3d3b7-107">この例は、ステータスを出力ウィンドウに出力します。</span><span class="sxs-lookup"><span data-stu-id="3d3b7-107">This example posts status to the output window.</span></span>  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="3d3b7-108">スレッド タイマーは、コンソール アプリケーションを開発するときなど、<xref:System.Windows.Forms.Timer?displayProperty=nameWithType> オブジェクトを使用できないときに特に有効です。</span><span class="sxs-lookup"><span data-stu-id="3d3b7-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3b7-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d3b7-109">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="3d3b7-110">マルチスレッド アプリケーション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d3b7-110">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)

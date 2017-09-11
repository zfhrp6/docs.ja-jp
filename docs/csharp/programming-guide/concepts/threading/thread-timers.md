---
title: "スレッド タイマー (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 52ed71e8-4fd9-43a4-ae40-04cce7cff23f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 30037b5b6d798796e7f76fa045f882b7f335e0d7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="thread-timers-c"></a><span data-ttu-id="a72cf-102">スレッド タイマー (C#)</span><span class="sxs-lookup"><span data-stu-id="a72cf-102">Thread Timers (C#)</span></span>
<span data-ttu-id="a72cf-103"><xref:System.Threading.Timer?displayProperty=fullName> クラスは、タスクを別々のスレッドで定期的に実行するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="a72cf-103">The <xref:System.Threading.Timer?displayProperty=fullName> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="a72cf-104">たとえば、スレッド タイマーを使用すると、データベースのステータスと整合性をチェックしたり、重要なファイルをバックアップしたりできます。</span><span class="sxs-lookup"><span data-stu-id="a72cf-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="a72cf-105">スレッド タイマーの例</span><span class="sxs-lookup"><span data-stu-id="a72cf-105">Thread Timer Example</span></span>  
 <span data-ttu-id="a72cf-106">2 秒ごとにタスクを起動し、フラグを使用して <xref:System.IDisposable.Dispose%2A> メソッドを開始し、タイマーを停止する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a72cf-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="a72cf-107">この例は、ステータスを出力ウィンドウに出力します。</span><span class="sxs-lookup"><span data-stu-id="a72cf-107">This example posts status to the output window.</span></span>  
  
```csharp  
private class StateObjClass  
{  
    // Used to hold parameters for calls to TimerTask.  
    public int SomeValue;  
    public System.Threading.Timer TimerReference;  
    public bool TimerCanceled;  
}  
  
public void RunTimer()  
{  
    StateObjClass StateObj = new StateObjClass();  
    StateObj.TimerCanceled = false;  
    StateObj.SomeValue = 1;  
    System.Threading.TimerCallback TimerDelegate =  
        new System.Threading.TimerCallback(TimerTask);  
  
    // Create a timer that calls a procedure every 2 seconds.  
    // Note: There is no Start method; the timer starts running as soon as   
    // the instance is created.  
    System.Threading.Timer TimerItem =  
        new System.Threading.Timer(TimerDelegate, StateObj, 2000, 2000);  
  
    // Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem;    
  
    // Run for ten loops.  
    while (StateObj.SomeValue < 10)   
    {  
        // Wait one second.  
        System.Threading.Thread.Sleep(1000);    
    }  
  
    // Request Dispose of the timer object.  
    StateObj.TimerCanceled = true;    
}  
  
private void TimerTask(object StateObj)  
{  
    StateObjClass State = (StateObjClass)StateObj;  
    // Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(ref State.SomeValue);  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " + DateTime.Now.ToString());  
    if (State.TimerCanceled)      
    // Dispose Requested.  
    {  
        State.TimerReference.Dispose();  
        System.Diagnostics.Debug.WriteLine("Done  " + DateTime.Now.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="a72cf-108">スレッド タイマーは、コンソール アプリケーションを開発するときなど、<xref:System.Windows.Forms.Timer?displayProperty=fullName> オブジェクトを使用できないときに特に有効です。</span><span class="sxs-lookup"><span data-stu-id="a72cf-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=fullName> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a72cf-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="a72cf-109">See Also</span></span>  
 <span data-ttu-id="a72cf-110"><xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="a72cf-110"><xref:System.Threading></span></span>   
 [<span data-ttu-id="a72cf-111">マルチスレッド アプリケーション (C#)</span><span class="sxs-lookup"><span data-stu-id="a72cf-111">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)


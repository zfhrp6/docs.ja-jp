---
title: スレッドの破棄
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e6eff0caa76349ce441a662428e37e25e2a6518
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="destroying-threads"></a><span data-ttu-id="32d24-102">スレッドの破棄</span><span class="sxs-lookup"><span data-stu-id="32d24-102">Destroying Threads</span></span>
<span data-ttu-id="32d24-103">マネージ スレッドを完全に停止するには、<xref:System.Threading.Thread.Abort%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="32d24-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="32d24-104"><xref:System.Threading.Thread.Abort%2A> を呼び出すと、共通言語ランタイムが対象スレッドで <xref:System.Threading.ThreadAbortException> をスローし、対象スレッドはそれをキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="32d24-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="32d24-105">詳細については、「<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32d24-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32d24-106">スレッドが <xref:System.Threading.Thread.Abort%2A> メソッドの呼び出し時にアンマネージ コードを実行する場合、ランタイムはそれを <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> としてマークします。</span><span class="sxs-lookup"><span data-stu-id="32d24-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="32d24-107">スレッドがマネージ コードに戻ると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="32d24-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="32d24-108">スレッドが中止されると、再起動することはできません。</span><span class="sxs-lookup"><span data-stu-id="32d24-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="32d24-109">対象スレッドが <xref:System.Threading.ThreadAbortException> をキャッチし、`finally` ブロック内の任意の量のコードを実行できるため、<xref:System.Threading.Thread.Abort%2A> メソッドにより、スレッドがすぐに中止されることはありません。</span><span class="sxs-lookup"><span data-stu-id="32d24-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="32d24-110">スレッドが終了するまで待機する必要がある場合は、<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="32d24-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="32d24-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> は、スレッドが実際に実行を停止するか、オプションのタイムアウト間隔が経過するまで返されないブロック呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="32d24-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="32d24-112">中止されたスレッドは <xref:System.Threading.Thread.ResetAbort%2A> メソッドを呼び出したり、`finally` ブロックで無制限処理を実行したりすることができるため、タイムアウトを指定しない場合、終了するまで待機するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="32d24-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="32d24-113"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> メソッドへの呼び出しを待機しているスレッドは、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> を呼び出す他のスレッドで中断することができます。</span><span class="sxs-lookup"><span data-stu-id="32d24-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="32d24-114">ThreadAbortException の処理</span><span class="sxs-lookup"><span data-stu-id="32d24-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="32d24-115">独自のコードからの <xref:System.Threading.Thread.Abort%2A> の呼び出しの結果、またはスレッドが実行中のアプリケーション ドメインのアンロード (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> が <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を使用してスレッドを終了する) の結果として、スレッドが中止されることが予想される場合、スレッドは <xref:System.Threading.ThreadAbortException> を処理し、以下のコードに示すように、`finally` 句で最終処理を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32d24-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="32d24-116">クリーンアップ コードは `catch` 句または `finally` 句にある必要があります。これは、<xref:System.Threading.ThreadAbortException> が `finally` 句の最後、または `catch` 句の最後 (`finally` 句がない場合) にシステムによって再スローされるためです。</span><span class="sxs-lookup"><span data-stu-id="32d24-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="32d24-117"><xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> メソッドを呼び出して、システムが例外を再スローしないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="32d24-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="32d24-118">ただし、この操作は独自のコードにより <xref:System.Threading.ThreadAbortException> が発生した場合にのみ行ってください。</span><span class="sxs-lookup"><span data-stu-id="32d24-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d24-119">参照</span><span class="sxs-lookup"><span data-stu-id="32d24-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="32d24-120">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="32d24-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

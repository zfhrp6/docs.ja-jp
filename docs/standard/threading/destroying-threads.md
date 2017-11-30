---
title: "スレッドの破棄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a><span data-ttu-id="fe37f-102">スレッドの破棄</span><span class="sxs-lookup"><span data-stu-id="fe37f-102">Destroying Threads</span></span>
<span data-ttu-id="fe37f-103"><xref:System.Threading.Thread.Abort%2A>マネージ スレッドを完全に停止するメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe37f-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="fe37f-104">呼び出すと<xref:System.Threading.Thread.Abort%2A>、共通言語ランタイムをスロー、<xref:System.Threading.ThreadAbortException>対象のスレッドにキャッチできる対象のスレッドにします。</span><span class="sxs-lookup"><span data-stu-id="fe37f-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="fe37f-105">詳細については、「<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe37f-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe37f-106">スレッドが実行されている場合は、アンマネージ コードの場合にその<xref:System.Threading.Thread.Abort%2A>メソッドが呼び出されると、ランタイムのマークが付け<xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fe37f-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe37f-107">スレッドがマネージ コードに戻ると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fe37f-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="fe37f-108">スレッドが中止されると、一度を再起動することはできません。</span><span class="sxs-lookup"><span data-stu-id="fe37f-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="fe37f-109"><xref:System.Threading.Thread.Abort%2A>メソッドは行われません、スレッドが、すぐに中止する対象のスレッドにキャッチできるため、<xref:System.Threading.ThreadAbortException>内のコードの任意の量を実行し、`finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="fe37f-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="fe37f-110">呼び出すことができます<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>スレッドが終了するまで待機する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="fe37f-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="fe37f-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>ブロッキング呼び出しではスレッドの実行が実際に停止されるまで返されないか、オプションのタイムアウト間隔が経過しました。</span><span class="sxs-lookup"><span data-stu-id="fe37f-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="fe37f-112">中止されたスレッドを呼び出すことが、<xref:System.Threading.Thread.ResetAbort%2A>メソッドで無限の処理を実行したり、`finally`ブロックにあるため、タイムアウト時間を指定しないと場合、待機が終了とは限りません。</span><span class="sxs-lookup"><span data-stu-id="fe37f-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="fe37f-113">呼び出しで待機しているスレッド、<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>メソッドを呼び出す他のスレッドを中断できる<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="fe37f-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="fe37f-114">ThreadAbortException の処理</span><span class="sxs-lookup"><span data-stu-id="fe37f-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="fe37f-115">呼び出しの結果として、中止するスレッドが予想される場合<xref:System.Threading.Thread.Abort%2A>またはスレッドが実行されているアプリケーション ドメインをアンロードした結果として、自分のコードから (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>使用<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>スレッドを終了する)、スレッドを処理する必要があります<xref:System.Threading.ThreadAbortException>での最終処理を実行し、`finally`句、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="fe37f-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="fe37f-116">クリーンアップ コードがである必要があります、`catch`句または`finally`句、ため、<xref:System.Threading.ThreadAbortException>の最後に、システムによって再スロー、`finally`句、またはの最後に、`catch`句がある場合にない`finally`句。</span><span class="sxs-lookup"><span data-stu-id="fe37f-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="fe37f-117">システムから呼び出すことによって、例外を再スローすることができなくことができます、<xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fe37f-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe37f-118">ただし、行う必要がある場合のみ、この独自のコードの原因となった、<xref:System.Threading.ThreadAbortException>です。</span><span class="sxs-lookup"><span data-stu-id="fe37f-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe37f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe37f-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="fe37f-120">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="fe37f-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)

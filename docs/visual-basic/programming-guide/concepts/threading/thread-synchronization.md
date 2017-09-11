---
title: "スレッドの同期 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 240937905254120f777ce140049084279c35005c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="thread-synchronization-visual-basic"></a><span data-ttu-id="3ff58-102">スレッドの同期 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff58-102">Thread Synchronization (Visual Basic)</span></span>
<span data-ttu-id="3ff58-103">次のセクションでは、機能とマルチ スレッド アプリケーションのリソースへのアクセスを同期するために使用されるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-103">The following sections describe features and classes that can be used to synchronize access to resources in multithreaded applications.</span></span>  
  
 <span data-ttu-id="3ff58-104">アプリケーションで複数のスレッドを使用する利点の&1; つは、各スレッドが非同期的に実行することです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-104">One of the benefits of using multiple threads in an application is that each thread executes asynchronously.</span></span> <span data-ttu-id="3ff58-105">Windows アプリケーションは、これにより、アプリケーション ウィンドウの中にバック グラウンドで実行する時間のかかるタスクし、コントロールの応答性を維持します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-105">For Windows applications, this allows time-consuming tasks to be performed in the background while the application window and controls remain responsive.</span></span> <span data-ttu-id="3ff58-106">サーバーには、アプリケーション、マルチ スレッドは、別のスレッドで受信された各要求を処理する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-106">For server applications, multithreading provides the ability to handle each incoming request with a different thread.</span></span> <span data-ttu-id="3ff58-107">それ以外の場合、完全には満足できましたが、前回の要求まで新しい要求が処理されないとを取得します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-107">Otherwise, each new request would not get serviced until the previous request had been fully satisfied.</span></span>  
  
 <span data-ttu-id="3ff58-108">ただし、非同期の特質がファイル ハンドル、ネットワーク接続、およびメモリなどのリソースにアクセスするスレッドの場合は、調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ff58-108">However, the asynchronous nature of threads means that access to resources such as file handles, network connections, and memory must be coordinated.</span></span> <span data-ttu-id="3ff58-109">それ以外の場合、2 つまたは複数のスレッドは、同じリソースに同時に、それぞれの動作を認識しないアクセスでした。</span><span class="sxs-lookup"><span data-stu-id="3ff58-109">Otherwise, two or more threads could access the same resource at the same time, each unaware of the other's actions.</span></span> <span data-ttu-id="3ff58-110">予期しないデータの破損になります。</span><span class="sxs-lookup"><span data-stu-id="3ff58-110">The result is unpredictable data corruption.</span></span>  
  
 <span data-ttu-id="3ff58-111">整数の数値データ型に対する単純な操作は、スレッドの同期で実現できる<xref:System.Threading.Interlocked>クラス</xref:System.Threading.Interlocked>のメンバー</span><span class="sxs-lookup"><span data-stu-id="3ff58-111">For simple operations on integral numeric data types, synchronizing threads can be accomplished with members of the <xref:System.Threading.Interlocked> class.</span></span> <span data-ttu-id="3ff58-112">その他のすべてのデータ型および非スレッド セーフであるリソース、マルチ スレッドのみ安全に実行できますこのトピックの構成要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-112">For all other data types and non thread-safe resources, multithreading can only be safely performed using the constructs in this topic.</span></span>  
  
 <span data-ttu-id="3ff58-113">マルチ スレッド プログラミングの基礎知識についてを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ff58-113">For background information on multithreaded programming, see:</span></span>  
  
-   [<span data-ttu-id="3ff58-114">マネージ スレッド処理の基礎</span><span class="sxs-lookup"><span data-stu-id="3ff58-114">Managed Threading Basics</span></span>](http://msdn.microsoft.com/library/b2944911-0e8f-427d-a8bb-077550618935)  
  
-   [<span data-ttu-id="3ff58-115">スレッドを使用して、スレッド処理</span><span class="sxs-lookup"><span data-stu-id="3ff58-115">Using Threads and Threading</span></span>](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)  
  
-   [<span data-ttu-id="3ff58-116">マネージ スレッド処理のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="3ff58-116">Managed Threading Best Practices</span></span>](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557)  
  
## <a name="the-lock-and-synclock-keywords"></a><span data-ttu-id="3ff58-117">ロックおよび SyncLock キーワード</span><span class="sxs-lookup"><span data-stu-id="3ff58-117">The lock and SyncLock Keywords</span></span>  
 <span data-ttu-id="3ff58-118">Visual Basic`SyncLock`他のスレッドによって中断されることがなく完了するまでのコード ブロックが実行できるようにするステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ff58-118">The Visual Basic `SyncLock` statement can be used to ensure that a block of code runs to completion without interruption by other threads.</span></span> <span data-ttu-id="3ff58-119">これは、コード ブロックの中から特定のオブジェクト相互排他ロックを取得することによって行います。</span><span class="sxs-lookup"><span data-stu-id="3ff58-119">This is accomplished by obtaining a mutual-exclusion lock for a given object for the duration of the code block.</span></span>  
  
 <span data-ttu-id="3ff58-120">A`SyncLock`ステートメントが、引数としてオブジェクトが指定され、一度に&1; つのスレッドによって実行されるコード ブロックが続きます。</span><span class="sxs-lookup"><span data-stu-id="3ff58-120">A `SyncLock` statement is given an object as an argument, and is followed by a code block that is to be executed by only one thread at a time.</span></span> <span data-ttu-id="3ff58-121">例:</span><span class="sxs-lookup"><span data-stu-id="3ff58-121">For example:</span></span>  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="3ff58-122">渡される引数、`SyncLock`キーワードが参照型に基づくオブジェクトである必要があり、ロックのスコープを定義するために使用します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-122">The argument provided to the `SyncLock` keyword must be an object based on a reference type, and is used to define the scope of the lock.</span></span> <span data-ttu-id="3ff58-123">上記の例で、ロックのスコープはこの関数に限定されているため、オブジェクトへの参照`lockThis`関数の外部に存在します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-123">In the example above, the lock scope is limited to this function because no references to the object `lockThis` exist outside the function.</span></span> <span data-ttu-id="3ff58-124">このような参照が存在すると場合、そのオブジェクトにロックのスコープを拡張します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-124">If such a reference did exist, lock scope would extend to that object.</span></span> <span data-ttu-id="3ff58-125">厳密に言えば、指定されたオブジェクトは任意のクラス インスタンスにするために複数のスレッド間で共有されるリソースを一意に識別するためだけに使用します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-125">Strictly speaking, the object provided is used solely to uniquely identify the resource being shared among multiple threads, so it can be an arbitrary class instance.</span></span> <span data-ttu-id="3ff58-126">実際にこのオブジェクト通常は、スレッドの同期が必要なリソースです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-126">In practice, however, this object usually represents the resource for which thread synchronization is necessary.</span></span> <span data-ttu-id="3ff58-127">たとえば、コンテナー オブジェクトを複数のスレッドで使用する場合は、し、ロックするには、コンテナーを渡すことができ、ロックの後、同期されたコード ブロックは、コンテナーへのアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3ff58-127">For example, if a container object is to be used by multiple threads, then the container can be passed to lock, and the synchronized code block following the lock would access the container.</span></span> <span data-ttu-id="3ff58-128">上の他のスレッドをロックしている限り、アクセスする前に含む同じし、オブジェクトへのアクセスを安全に同期します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-128">As long as other threads locks on the same contain before accessing it, then access to the object is safely synchronized.</span></span>  
  
 <span data-ttu-id="3ff58-129">一般をロックしないことをお勧め、`public`の種類や、アプリケーション処理の対象外のオブジェクト インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3ff58-129">Generally, it is best to avoid locking on a `public` type, or on object instances beyond the control of your application.</span></span> <span data-ttu-id="3ff58-130">たとえば、`lockThis`は問題となるインスタンスがパブリックにアクセスできる場合もオブジェクトにユーザーが制御できないコードがロックされることがあるためです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-130">For example, `lockThis` can be problematic if the instance can be accessed publicly, because code beyond your control may lock on the object as well.</span></span> <span data-ttu-id="3ff58-131">これにより、デッドロックが&2; つまたは複数のスレッドが同じオブジェクトの解放を待機が作成する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3ff58-131">This could create deadlock situations where two or more threads wait for the release of the same object.</span></span> <span data-ttu-id="3ff58-132">オブジェクトではなく、パブリックなデータ型をロックすると、同じ理由で問題が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="3ff58-132">Locking on a public data type, as opposed to an object, can cause problems for the same reason.</span></span> <span data-ttu-id="3ff58-133">リテラル文字列はリテラル文字列のロックは特に危険*インターン*共通言語ランタイム (CLR) によってです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-133">Locking on literal strings is especially risky because literal strings are *interned* by the common language runtime (CLR).</span></span> <span data-ttu-id="3ff58-134">つまり、すべての文字列の&1; つのインスタンスがあるプログラム全体のリテラル、まったく同じオブジェクトがすべてのリテラルを表すすべてのスレッドでアプリケーション ドメインを実行します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-134">This means that there is one instance of any given string literal for the entire program, the exact same object represents the literal in all running application domains, on all threads.</span></span> <span data-ttu-id="3ff58-135">その結果をロックと同じ内容の文字列に任意の場所アプリケーション プロセスのロックのアプリケーションでは、その文字列のすべてのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3ff58-135">As a result, a lock placed on a string with the same contents anywhere in the application process locks all instances of that string in the application.</span></span> <span data-ttu-id="3ff58-136">その結果、隔離されていないプライベートまたはプロテクト メンバーをロックすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3ff58-136">As a result, it is best to lock a private or protected member that is not interned.</span></span> <span data-ttu-id="3ff58-137">一部のクラスは、ロック専用のメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-137">Some classes provide members specifically for locking.</span></span> <span data-ttu-id="3ff58-138"><xref:System.Array>型、たとえばに<xref:System.Array.SyncRoot%2A>。</xref:System.Array.SyncRoot%2A>が用意されています</xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="3ff58-138">The <xref:System.Array> type, for example, provides <xref:System.Array.SyncRoot%2A>.</span></span> <span data-ttu-id="3ff58-139">多くのコレクション型には、`SyncRoot`メンバーもします。</span><span class="sxs-lookup"><span data-stu-id="3ff58-139">Many collection types provide a `SyncRoot` member as well.</span></span>  
  
 <span data-ttu-id="3ff58-140">詳細については、`SyncLock`ステートメントでは、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ff58-140">For more information about the `SyncLock` statement, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3ff58-141">SyncLock ステートメント</span><span class="sxs-lookup"><span data-stu-id="3ff58-141">SyncLock Statement</span></span>](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a><span data-ttu-id="3ff58-142">モニター</span><span class="sxs-lookup"><span data-stu-id="3ff58-142">Monitors</span></span>  
 <span data-ttu-id="3ff58-143">ように、`SyncLock`キーワード、モニターは、複数のスレッドが同時に実行からのコード ブロックを防ぐためです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-143">Like the `SyncLock` keyword, monitors prevent blocks of code from simultaneous execution by multiple threads.</span></span> <span data-ttu-id="3ff58-144"><xref:System.Threading.Monitor.Enter%2A>メソッドを使用して、次のステートメントに続行する、1 つのスレッドは実行中のスレッドが<xref:System.Threading.Monitor.Exit%2A>。</xref:System.Threading.Monitor.Exit%2A>を呼び出すまで、他のすべてのスレッドがブロックされます。</xref:System.Threading.Monitor.Enter%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-144">The <xref:System.Threading.Monitor.Enter%2A> method allows one and only one thread to proceed into the following statements; all other threads are blocked until the executing thread calls <xref:System.Threading.Monitor.Exit%2A>.</span></span> <span data-ttu-id="3ff58-145">これを使用するよう、`SyncLock`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-145">This is just like using the `SyncLock` keyword.</span></span> <span data-ttu-id="3ff58-146">例:</span><span class="sxs-lookup"><span data-stu-id="3ff58-146">For example:</span></span>  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 <span data-ttu-id="3ff58-147">これと同じです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-147">This is equivalent to:</span></span>  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 <span data-ttu-id="3ff58-148">使用して、`SyncLock`を使用するキーワードは、通常の優先、<xref:System.Threading.Monitor>クラスを直接両方ため`SyncLock`はより簡潔なので、`SyncLock`基になっているモニターが離されたことを保証する場合でも、保護されているコードが例外をスローします</xref:System.Threading.Monitor>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-148">Using the `SyncLock` keyword is generally preferred over using the <xref:System.Threading.Monitor> class directly, both because `SyncLock` is more concise, and because `SyncLock` insures that the underlying monitor is released, even if the protected code throws an exception.</span></span> <span data-ttu-id="3ff58-149">これを行うと、`Finally`キーワードで、例外をスローするかどうかに関係なく、関連するコード ブロックを実行します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-149">This is accomplished with the `Finally` keyword, which executes its associated code block regardless of whether an exception is thrown.</span></span>  
  
## <a name="synchronization-events-and-wait-handles"></a><span data-ttu-id="3ff58-150">同期イベントと待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="3ff58-150">Synchronization Events and Wait Handles</span></span>  
 <span data-ttu-id="3ff58-151">ロックまたはモニターの使用は、コードのスレッドに依存したブロックを同時に実行を防止するために役立ちますが、これらの構成要素には、1 つのスレッドにイベントを別の通信にはできません。</span><span class="sxs-lookup"><span data-stu-id="3ff58-151">Using a lock or monitor is useful for preventing the simultaneous execution of thread-sensitive blocks of code, but these constructs do not allow one thread to communicate an event to another.</span></span> <span data-ttu-id="3ff58-152">これが必要です*同期イベント*、これは、2 つの状態の&1; つを持つオブジェクトをアクティブ化し、スレッドを中断に使用するシグナルと非シグナル状態であります。</span><span class="sxs-lookup"><span data-stu-id="3ff58-152">This requires *synchronization events*, which are objects that have one of two states, signaled and un-signaled, that can be used to activate and suspend threads.</span></span> <span data-ttu-id="3ff58-153">スレッドは、シグナル、同期イベントを待機させることによって中断されることができますあり、イベントの状態をシグナル状態に変更することによってアクティブ化されることができます。</span><span class="sxs-lookup"><span data-stu-id="3ff58-153">Threads can be suspended by being made to wait on a synchronization event that is unsignaled, and can be activated by changing the event state to signaled.</span></span> <span data-ttu-id="3ff58-154">スレッドは、イベントがシグナルを待機しようとする場合は、遅延なしに実行、スレッドが続行します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-154">If a thread attempts to wait on an event that is already signaled, then the thread continues to execute without delay.</span></span>  
  
 <span data-ttu-id="3ff58-155">同期イベントの&2; つの種類があります: <xref:System.Threading.AutoResetEvent>、 <xref:System.Threading.ManualResetEvent>.</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent></span><span class="sxs-lookup"><span data-stu-id="3ff58-155">There are two kinds of synchronization events: <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="3ff58-156">のみが異なりますを<xref:System.Threading.AutoResetEvent>から変更シグナル状態にシグナルを自動的に時間がいずれかのスレッドがアクティブになります</xref:System.Threading.AutoResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-156">They differ only in that <xref:System.Threading.AutoResetEvent> changes from signaled to unsignaled automatically any time it activates a thread.</span></span> <span data-ttu-id="3ff58-157">逆に、<xref:System.Threading.ManualResetEvent>のシグナルの状態によってアクティブ化するスレッドの任意の数を使用し、シグナルに戻りますのみ状態のときにその<xref:System.Threading.EventWaitHandle.Reset%2A>メソッドが呼び出されます</xref:System.Threading.EventWaitHandle.Reset%2A></xref:System.Threading.ManualResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-157">Conversely, a <xref:System.Threading.ManualResetEvent> allows any number of threads to be activated by its signaled state, and will only revert to an unsignaled state when its <xref:System.Threading.EventWaitHandle.Reset%2A> method is called.</span></span>  
  
 <span data-ttu-id="3ff58-158">待機メソッドの&1; つを呼び出してなどのイベントを待機するスレッドができる<xref:System.Threading.WaitHandle.WaitOne%2A>、 <xref:System.Threading.WaitHandle.WaitAny%2A>、または<xref:System.Threading.WaitHandle.WaitAll%2A>.</xref:System.Threading.WaitHandle.WaitAll%2A> </xref:System.Threading.WaitHandle.WaitAny%2A> </xref:System.Threading.WaitHandle.WaitOne%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-158">Threads can be made to wait on events by calling one of the wait methods, such as <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, or <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span> <span data-ttu-id="3ff58-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>1 つのイベントがシグナル状態になるまで待機するスレッド<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>1 つ以上の指定されたイベントがシグナル状態になるまで、スレッドをブロックし、<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>すべて指定されたイベントのシグナル状態になるまで、スレッドをブロックします</xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName></xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>。</xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3ff58-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> causes the thread to wait until a single event becomes signaled, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> blocks a thread until one or more indicated events become signaled, and <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> blocks the thread until all of the indicated events become signaled.</span></span> <span data-ttu-id="3ff58-160">イベントがシグナル状態とその<xref:System.Threading.EventWaitHandle.Set%2A>メソッドが呼び出されます</xref:System.Threading.EventWaitHandle.Set%2A>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-160">An event becomes signaled when its <xref:System.Threading.EventWaitHandle.Set%2A> method is called.</span></span>  
  
 <span data-ttu-id="3ff58-161">スレッドの作成および開始で次の例では、`Main`関数です。</span><span class="sxs-lookup"><span data-stu-id="3ff58-161">In the following example, a thread is created and started by the `Main` function.</span></span> <span data-ttu-id="3ff58-162">イベントを使用して、新しいスレッドが待機する、<xref:System.Threading.WaitHandle.WaitOne%2A>メソッド</xref:System.Threading.WaitHandle.WaitOne%2A>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-162">The new thread waits on an event using the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span> <span data-ttu-id="3ff58-163">実行しているプライマリ スレッドによってイベントがシグナル状態になるまでスレッドが中断、`Main`関数です。</span><span class="sxs-lookup"><span data-stu-id="3ff58-163">The thread is suspended until the event becomes signaled by the primary thread that is executing the `Main` function.</span></span> <span data-ttu-id="3ff58-164">補助的なスレッドが戻るイベントがシグナル状態になります。</span><span class="sxs-lookup"><span data-stu-id="3ff58-164">Once the event becomes signaled, the auxiliary thread returns.</span></span> <span data-ttu-id="3ff58-165">この場合、イベントがのみ使用されるための&1; つのスレッドのアクティブ化するか、<xref:System.Threading.AutoResetEvent>または<xref:System.Threading.ManualResetEvent>クラスを使用できます</xref:System.Threading.ManualResetEvent></xref:System.Threading.AutoResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-165">In this case, because the event is only used for one thread activation, either the <xref:System.Threading.AutoResetEvent> or <xref:System.Threading.ManualResetEvent> classes could be used.</span></span>  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
```  
  
## <a name="mutex-object"></a><span data-ttu-id="3ff58-166">ミュー テックス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="3ff58-166">Mutex Object</span></span>  
 <span data-ttu-id="3ff58-167">A*ミュー テックス*モニターのようなことにより、コードのブロックを同時に実行スレッドは&1; つ以上の一度にします。</span><span class="sxs-lookup"><span data-stu-id="3ff58-167">A *mutex* is similar to a monitor; it prevents the simultaneous execution of a block of code by more than one thread at a time.</span></span> <span data-ttu-id="3ff58-168">実際には、「相互に排他的です」という用語の短縮形は、名前「ミュー テックス」</span><span class="sxs-lookup"><span data-stu-id="3ff58-168">In fact, the name "mutex" is a shortened form of the term "mutually exclusive."</span></span> <span data-ttu-id="3ff58-169">モニターとは異なり、ミュー テックスできますプロセス間でスレッドを同期します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-169">Unlike monitors, however, a mutex can be used to synchronize threads across processes.</span></span> <span data-ttu-id="3ff58-170">ミュー テックスが<xref:System.Threading.Mutex>クラス</xref:System.Threading.Mutex>によって表される</span><span class="sxs-lookup"><span data-stu-id="3ff58-170">A mutex is represented by the <xref:System.Threading.Mutex> class.</span></span>  
  
 <span data-ttu-id="3ff58-171">ミュー テックスと呼ばれるプロセス間の同期に使用する場合、*名前付きミュー テックス*別のアプリケーションで使用するのには、グローバルまたは静的変数を使用ため共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="3ff58-171">When used for inter-process synchronization, a mutex is called a *named mutex* because it is to be used in another application, and therefore it cannot be shared by means of a global or static variable.</span></span> <span data-ttu-id="3ff58-172">これは、必要があります名前を指定する両方のアプリケーションが同じミュー テックス オブジェクトにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="3ff58-172">It must be given a name so that both applications can access the same mutex object.</span></span>  
  
 <span data-ttu-id="3ff58-173">使用して、ミュー テックスを使用して、プロセス間のスレッドの同期化できますが、<xref:System.Threading.Monitor>が一般に推奨されるモニターが向けに .NET Framework とはそのためのリソースを活用して行っています</xref:System.Threading.Monitor>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-173">Although a mutex can be used for intra-process thread synchronization, using <xref:System.Threading.Monitor> is generally preferred, because monitors were designed specifically for the .NET Framework and therefore make better use of resources.</span></span> <span data-ttu-id="3ff58-174">これに対し、<xref:System.Threading.Mutex>クラスは、Win32 コンストラクトにラッパー</xref:System.Threading.Mutex> 。</span><span class="sxs-lookup"><span data-stu-id="3ff58-174">In contrast, the <xref:System.Threading.Mutex> class is a wrapper to a Win32 construct.</span></span> <span data-ttu-id="3ff58-175">ミュー テックスがより負荷の大きい<xref:System.Threading.Monitor>クラス</xref:System.Threading.Monitor>で必要なものである相互運用機能の遷移を必要とモニターよりも強力ですが、</span><span class="sxs-lookup"><span data-stu-id="3ff58-175">While it is more powerful than a monitor, a mutex requires interop transitions that are more computationally expensive than those required by the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="3ff58-176">ミュー テックスを使用しての例は、次を参照してください。[ミュー テックス](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-176">For an example of using a mutex, see [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).</span></span>  
  
## <a name="interlocked-class"></a><span data-ttu-id="3ff58-177">Interlocked クラス</span><span class="sxs-lookup"><span data-stu-id="3ff58-177">Interlocked Class</span></span>  
 <span data-ttu-id="3ff58-178">メソッドを使用する、<xref:System.Threading.Interlocked>複数のスレッドが同時に更新または同じ値と比較を試みるときに発生する問題を防止するクラス</xref:System.Threading.Interlocked>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-178">You can use the methods of the <xref:System.Threading.Interlocked> class to prevent problems that can occur when multiple threads attempt to simultaneously update or compare the same value.</span></span> <span data-ttu-id="3ff58-179">このクラスのメソッドを使用する安全なインクリメント、デクリメント、交換、および任意のスレッドからの値を比較します。</span><span class="sxs-lookup"><span data-stu-id="3ff58-179">The methods of this class let you safely increment, decrement, exchange, and compare values from any thread.</span></span>  
  
## <a name="readerwriter-locks"></a><span data-ttu-id="3ff58-180">ReaderWriter ロック</span><span class="sxs-lookup"><span data-stu-id="3ff58-180">ReaderWriter Locks</span></span>  
 <span data-ttu-id="3ff58-181">場合によっては、データが書き込まれている場合にのみ、リソースをロックし、複数のクライアントにデータが更新されていないときにデータの同時読み取りを許可するのにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="3ff58-181">In some cases, you may want to lock a resource only when data is being written and permit multiple clients to simultaneously read data when data is not being updated.</span></span> <span data-ttu-id="3ff58-182"><xref:System.Threading.ReaderWriterLock>クラスは、スレッドが、リソースを変更するは、リソースの読み取り時に非排他的なアクセスが許可されているときに、リソースへの排他アクセスを強制します</xref:System.Threading.ReaderWriterLock>。</span><span class="sxs-lookup"><span data-stu-id="3ff58-182">The <xref:System.Threading.ReaderWriterLock> class enforces exclusive access to a resource while a thread is modifying the resource, but it allows non-exclusive access when reading the resource.</span></span> <span data-ttu-id="3ff58-183">ReaderWriter ロックは、待機もとそれらのスレッドする必要はありませんデータを更新するには、他のスレッド排他ロックの代わりにします。</span><span class="sxs-lookup"><span data-stu-id="3ff58-183">ReaderWriter locks are a useful alternative to exclusive locks, which cause other threads to wait, even when those threads do not need to update data.</span></span>  
  
## <a name="deadlocks"></a><span data-ttu-id="3ff58-184">デッドロック</span><span class="sxs-lookup"><span data-stu-id="3ff58-184">Deadlocks</span></span>  
 <span data-ttu-id="3ff58-185">スレッドの同期はマルチ スレッド アプリケーションで役に立つが、常に作成する危険性がある、 `deadlock`」複数のスレッドが互いを待機しているし、アプリケーションが停止するものです。</span><span class="sxs-lookup"><span data-stu-id="3ff58-185">Thread synchronization is invaluable in multithreaded applications, but there is always the danger of creating a `deadlock`, where multiple threads are waiting for each other and the application comes to a halt.</span></span> <span data-ttu-id="3ff58-186">デッドロックは、車が&4; 方向の位置で停止されたして移動するその他の各ユーザーが待機しているのと似ています。</span><span class="sxs-lookup"><span data-stu-id="3ff58-186">A deadlock is analogous to a situation in which cars are stopped at a four-way stop and each person is waiting for the other to go.</span></span> <span data-ttu-id="3ff58-187">デッドロックを避けることが重要です。綿密な計画が重要です。</span><span class="sxs-lookup"><span data-stu-id="3ff58-187">Avoiding deadlocks is important; the key is careful planning.</span></span> <span data-ttu-id="3ff58-188">多くの場合、コーディングを開始する前に、マルチ スレッド アプリケーションを図式化でデッドロックが発生を予測できます。</span><span class="sxs-lookup"><span data-stu-id="3ff58-188">You can often predict deadlock situations by diagramming multithreaded applications before you start coding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff58-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ff58-189">See Also</span></span>  
 <span data-ttu-id="3ff58-190"><xref:System.Threading.Thread></xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="3ff58-190"><xref:System.Threading.Thread></span></span>   
 <span data-ttu-id="3ff58-191"><xref:System.Threading.WaitHandle.WaitOne%2A></xref:System.Threading.WaitHandle.WaitOne%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-191"><xref:System.Threading.WaitHandle.WaitOne%2A></span></span>   
 <span data-ttu-id="3ff58-192"><xref:System.Threading.WaitHandle.WaitAny%2A></xref:System.Threading.WaitHandle.WaitAny%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-192"><xref:System.Threading.WaitHandle.WaitAny%2A></span></span>   
 <span data-ttu-id="3ff58-193"><xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-193"><xref:System.Threading.WaitHandle.WaitAll%2A></span></span>   
 <span data-ttu-id="3ff58-194"><xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-194"><xref:System.Threading.Thread.Join%2A></span></span>   
 <span data-ttu-id="3ff58-195"><xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-195"><xref:System.Threading.Thread.Start%2A></span></span>   
 <span data-ttu-id="3ff58-196"><xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-196"><xref:System.Threading.Thread.Sleep%2A></span></span>   
 <span data-ttu-id="3ff58-197"><xref:System.Threading.Monitor></xref:System.Threading.Monitor></span><span class="sxs-lookup"><span data-stu-id="3ff58-197"><xref:System.Threading.Monitor></span></span>   
 <span data-ttu-id="3ff58-198"><xref:System.Threading.Mutex></xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="3ff58-198"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="3ff58-199"><xref:System.Threading.AutoResetEvent></xref:System.Threading.AutoResetEvent></span><span class="sxs-lookup"><span data-stu-id="3ff58-199"><xref:System.Threading.AutoResetEvent></span></span>   
 <span data-ttu-id="3ff58-200"><xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent></span><span class="sxs-lookup"><span data-stu-id="3ff58-200"><xref:System.Threading.ManualResetEvent></span></span>   
 <span data-ttu-id="3ff58-201"><xref:System.Threading.Interlocked></xref:System.Threading.Interlocked></span><span class="sxs-lookup"><span data-stu-id="3ff58-201"><xref:System.Threading.Interlocked></span></span>   
 <span data-ttu-id="3ff58-202"><xref:System.Threading.WaitHandle></xref:System.Threading.WaitHandle></span><span class="sxs-lookup"><span data-stu-id="3ff58-202"><xref:System.Threading.WaitHandle></span></span>   
 <span data-ttu-id="3ff58-203"><xref:System.Threading.EventWaitHandle></xref:System.Threading.EventWaitHandle></span><span class="sxs-lookup"><span data-stu-id="3ff58-203"><xref:System.Threading.EventWaitHandle></span></span>   
 <span data-ttu-id="3ff58-204"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="3ff58-204"><xref:System.Threading></span></span>   
 <span data-ttu-id="3ff58-205"><xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A></span><span class="sxs-lookup"><span data-stu-id="3ff58-205"><xref:System.Threading.EventWaitHandle.Set%2A></span></span>   
<span data-ttu-id="3ff58-206"> [マルチ スレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="3ff58-206"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="3ff58-207"> [SyncLock ステートメント](../../../../visual-basic/language-reference/statements/synclock-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3ff58-207"> [SyncLock Statement](../../../../visual-basic/language-reference/statements/synclock-statement.md) </span></span>  
<span data-ttu-id="3ff58-208"> [ミュー テックス](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2) </span><span class="sxs-lookup"><span data-stu-id="3ff58-208"> [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2) </span></span>  
 @System.Threading.Monitor   
<span data-ttu-id="3ff58-209"> [インタロックされた操作](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b) </span><span class="sxs-lookup"><span data-stu-id="3ff58-209"> [Interlocked Operations](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b) </span></span>  
<span data-ttu-id="3ff58-210"> [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18) </span><span class="sxs-lookup"><span data-stu-id="3ff58-210"> [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18) </span></span>  
<span data-ttu-id="3ff58-211"> [データを同期するマルチ スレッド](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)</span><span class="sxs-lookup"><span data-stu-id="3ff58-211"> [Synchronizing Data for Multithreading](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)</span></span>

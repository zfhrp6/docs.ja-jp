---
title: "スレッドの同期 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b51775eac5221ec8c723d89323d1f4f542d2453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="thread-synchronization-c"></a><span data-ttu-id="2e579-102">スレッドの同期 (C#)</span><span class="sxs-lookup"><span data-stu-id="2e579-102">Thread Synchronization (C#)</span></span>
<span data-ttu-id="2e579-103">次のセクションでは、マルチスレッド アプリケーションでリソースへのアクセスを同期するために使用できる機能とクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2e579-103">The following sections describe features and classes that can be used to synchronize access to resources in multithreaded applications.</span></span>  
  
 <span data-ttu-id="2e579-104">アプリケーションで複数のスレッドを使用する利点の 1 つは、各スレッドを非同期的に実行できる点にあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-104">One of the benefits of using multiple threads in an application is that each thread executes asynchronously.</span></span> <span data-ttu-id="2e579-105">Windows アプリケーションでは、これによって、アプリケーションのウィンドウやコントロールを応答可能な状態に維持しつつ、時間のかかるタスクをバックグラウンドで実行することができます。</span><span class="sxs-lookup"><span data-stu-id="2e579-105">For Windows applications, this allows time-consuming tasks to be performed in the background while the application window and controls remain responsive.</span></span> <span data-ttu-id="2e579-106">サーバー アプリケーションでは、マルチスレッドを使用することで、受け取った各要求を別個のスレッドで処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2e579-106">For server applications, multithreading provides the ability to handle each incoming request with a different thread.</span></span> <span data-ttu-id="2e579-107">マルチスレッドを使用しない場合、前の要求が完全に満たされるまで、新しい要求はサービスを受けることができません。</span><span class="sxs-lookup"><span data-stu-id="2e579-107">Otherwise, each new request would not get serviced until the previous request had been fully satisfied.</span></span>  
  
 <span data-ttu-id="2e579-108">ただし、スレッドでの処理が非同期であるために、ファイル ハンドル、ネットワーク接続、およびメモリなどのリソースへのアクセスを調整する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="2e579-108">However, the asynchronous nature of threads means that access to resources such as file handles, network connections, and memory must be coordinated.</span></span> <span data-ttu-id="2e579-109">調整が行われないと、互いに別のスレッドの動作が認識できず、複数のスレッドが同時に同じリソースにアクセスしてしまうことになります。</span><span class="sxs-lookup"><span data-stu-id="2e579-109">Otherwise, two or more threads could access the same resource at the same time, each unaware of the other's actions.</span></span> <span data-ttu-id="2e579-110">その結果、予測できないデータ破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="2e579-110">The result is unpredictable data corruption.</span></span>  
  
 <span data-ttu-id="2e579-111">整数の数値データ型に対する単純な演算の場合は、<xref:System.Threading.Interlocked> クラスのメンバーを使用することにより、スレッドの同期を実現できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-111">For simple operations on integral numeric data types, synchronizing threads can be accomplished with members of the <xref:System.Threading.Interlocked> class.</span></span> <span data-ttu-id="2e579-112">その他のすべてのデータ型やスレッド セーフではないリソースについては、このトピックで説明する構成要素を使用しない限り、マルチスレッド処理を安全に実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="2e579-112">For all other data types and non thread-safe resources, multithreading can only be safely performed using the constructs in this topic.</span></span>  
  
 <span data-ttu-id="2e579-113">マルチスレッド プログラミングの背景情報については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e579-113">For background information on multithreaded programming, see:</span></span>  
  
-   [<span data-ttu-id="2e579-114">マネージ スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="2e579-114">Managed Threading Basics</span></span>](../../../../standard/threading/managed-threading-basics.md)  
  
-   [<span data-ttu-id="2e579-115">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="2e579-115">Using Threads and Threading</span></span>](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [<span data-ttu-id="2e579-116">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="2e579-116">Managed Threading Best Practices</span></span>](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a><span data-ttu-id="2e579-117">lock キーワード</span><span class="sxs-lookup"><span data-stu-id="2e579-117">The lock Keyword</span></span>  
 <span data-ttu-id="2e579-118">C# `lock` ステートメントを使用すると、他のスレッドからの割り込みを受けることなくコード ブロックを確実に最後まで実行できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-118">The C# `lock` statement can be used to ensure that a block of code runs to completion without interruption by other threads.</span></span> <span data-ttu-id="2e579-119">これは、コード ブロックの実行中に、特定のオブジェクトに対して同時に使用できないロックを取得することで実現されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-119">This is accomplished by obtaining a mutual-exclusion lock for a given object for the duration of the code block.</span></span>  
  
 <span data-ttu-id="2e579-120">`lock` ステートメントには引数としてオブジェクトが渡され、その後に、一度に 1 つのスレッドだけが実行するコード ブロックが続きます。</span><span class="sxs-lookup"><span data-stu-id="2e579-120">A `lock` statement is given an object as an argument, and is followed by a code block that is to be executed by only one thread at a time.</span></span> <span data-ttu-id="2e579-121">例:</span><span class="sxs-lookup"><span data-stu-id="2e579-121">For example:</span></span>  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="2e579-122">`lock` キーワードに渡される引数は、参照型に基づくオブジェクトである必要があり、ロックのスコープを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-122">The argument provided to the `lock` keyword must be an object based on a reference type, and is used to define the scope of the lock.</span></span> <span data-ttu-id="2e579-123">前の例では、関数の外部にオブジェクト `lockThis` への参照が存在しないため、ロックのスコープはこの関数に限定されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-123">In the example above, the lock scope is limited to this function because no references to the object `lockThis` exist outside the function.</span></span> <span data-ttu-id="2e579-124">この参照が存在していたら、ロックのスコープはそのオブジェクトまで拡張されていました。</span><span class="sxs-lookup"><span data-stu-id="2e579-124">If such a reference did exist, lock scope would extend to that object.</span></span> <span data-ttu-id="2e579-125">厳密には、渡されるオブジェクトは、複数のスレッドで共有されるリソースを一意に識別するためだけに使用されるので、任意のクラスのインスタンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-125">Strictly speaking, the object provided is used solely to uniquely identify the resource being shared among multiple threads, so it can be an arbitrary class instance.</span></span> <span data-ttu-id="2e579-126">ただし、実際には、このオブジェクトは、スレッドの同期が必要なリソースを表すのが普通です。</span><span class="sxs-lookup"><span data-stu-id="2e579-126">In practice, however, this object usually represents the resource for which thread synchronization is necessary.</span></span> <span data-ttu-id="2e579-127">たとえば、複数のスレッドがコンテナー オブジェクトを使用する場合、そのコンテナーを lock に渡すと、lock に続く、同期されたコード ブロックがそのコンテナーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="2e579-127">For example, if a container object is to be used by multiple threads, then the container can be passed to lock, and the synchronized code block following the lock would access the container.</span></span> <span data-ttu-id="2e579-128">他のスレッドが同じコンテナーにアクセスする前にコンテナーをロックすると、このオブジェクトへのアクセスを安全に同期できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-128">As long as other threads locks on the same contain before accessing it, then access to the object is safely synchronized.</span></span>  
  
 <span data-ttu-id="2e579-129">一般に、`public` 型や、アプリケーションの制御が及ばないオブジェクト インスタンスはロックしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2e579-129">Generally, it is best to avoid locking on a `public` type, or on object instances beyond the control of your application.</span></span> <span data-ttu-id="2e579-130">たとえば、インスタンスにパブリックにアクセスできる場合、`lock(this)` は問題となることがあります。ユーザーの制御が及ばないコードによってもこのオブジェクトがロックされる可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="2e579-130">For example, `lock(this)` can be problematic if the instance can be accessed publicly, because code beyond your control may lock on the object as well.</span></span> <span data-ttu-id="2e579-131">この場合、複数のスレッドが同じオブジェクトの解放を待機しているような場合にはデッドロック状態が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-131">This could create deadlock situations where two or more threads wait for the release of the same object.</span></span> <span data-ttu-id="2e579-132">オブジェクトではなく、パブリックなデータ型をロックした場合も同じ理由から問題が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-132">Locking on a public data type, as opposed to an object, can cause problems for the same reason.</span></span> <span data-ttu-id="2e579-133">リテラル文字列は共通言語ランタイム (CLR) の*インターン プールに存在*しているため、リテラル文字列をロックすることは特に危険です。</span><span class="sxs-lookup"><span data-stu-id="2e579-133">Locking on literal strings is especially risky because literal strings are *interned* by the common language runtime (CLR).</span></span> <span data-ttu-id="2e579-134">つまり、プログラム全体では任意のリテラル文字列のインスタンスは 1 つしか存在しませんが、まったく同じオブジェクトが、実行中のすべてのアプリケーション ドメインのすべてのスレッド上のリテラルを表すためです。</span><span class="sxs-lookup"><span data-stu-id="2e579-134">This means that there is one instance of any given string literal for the entire program, the exact same object represents the literal in all running application domains, on all threads.</span></span> <span data-ttu-id="2e579-135">この結果、アプリケーション プロセスの任意の場所で同じ内容を持つ文字列をロックした場合、アプリケーション内のその文字列のすべてのインスタンスがロックされてしまいます。</span><span class="sxs-lookup"><span data-stu-id="2e579-135">As a result, a lock placed on a string with the same contents anywhere in the application process locks all instances of that string in the application.</span></span> <span data-ttu-id="2e579-136">したがって、インターン プールに存在しないプライベート メンバーまたはプロテクト メンバーをロックすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2e579-136">As a result, it is best to lock a private or protected member that is not interned.</span></span> <span data-ttu-id="2e579-137">クラスによっては、ロック専用のメンバーを提供するものもあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-137">Some classes provide members specifically for locking.</span></span> <span data-ttu-id="2e579-138">たとえば、<xref:System.Array> 型では <xref:System.Array.SyncRoot%2A> が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-138">The <xref:System.Array> type, for example, provides <xref:System.Array.SyncRoot%2A>.</span></span> <span data-ttu-id="2e579-139">多くのコレクション型でも、`SyncRoot` メンバーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-139">Many collection types provide a `SyncRoot` member as well.</span></span>  
  
 <span data-ttu-id="2e579-140">`lock` ステートメントの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e579-140">For more information about the `lock` statement, see the following topics:</span></span>  
  
-   [<span data-ttu-id="2e579-141">lock ステートメント</span><span class="sxs-lookup"><span data-stu-id="2e579-141">lock Statement</span></span>](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a><span data-ttu-id="2e579-142">モニター</span><span class="sxs-lookup"><span data-stu-id="2e579-142">Monitors</span></span>  
 <span data-ttu-id="2e579-143">`lock` キーワードと同様、モニターも複数のスレッドによるコード ブロックの同時実行を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="2e579-143">Like the `lock` keyword, monitors prevent blocks of code from simultaneous execution by multiple threads.</span></span> <span data-ttu-id="2e579-144"><xref:System.Threading.Monitor.Enter%2A> メソッドは 1 つのスレッドにのみ後続のステートメントに進むことを許可します。他のすべてのスレッドは、実行中のスレッドが <xref:System.Threading.Monitor.Exit%2A> を呼び出すまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="2e579-144">The <xref:System.Threading.Monitor.Enter%2A> method allows one and only one thread to proceed into the following statements; all other threads are blocked until the executing thread calls <xref:System.Threading.Monitor.Exit%2A>.</span></span> <span data-ttu-id="2e579-145">これは `lock` キーワードを使用した場合とまったく同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="2e579-145">This is just like using the `lock` keyword.</span></span> <span data-ttu-id="2e579-146">例:</span><span class="sxs-lookup"><span data-stu-id="2e579-146">For example:</span></span>  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 <span data-ttu-id="2e579-147">このようにすると、次の記述と同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="2e579-147">This is equivalent to:</span></span>  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 <span data-ttu-id="2e579-148">通常は、<xref:System.Threading.Monitor> クラスを直接使用するよりも `lock` キーワードを使用することをお勧めします。`lock` の方が簡潔であり、また、`lock` を使用すると、保護されたコードが例外をスローした場合でも基になるモニターが確実に解放されるためです。</span><span class="sxs-lookup"><span data-stu-id="2e579-148">Using the `lock` keyword is generally preferred over using the <xref:System.Threading.Monitor> class directly, both because `lock` is more concise, and because `lock` insures that the underlying monitor is released, even if the protected code throws an exception.</span></span> <span data-ttu-id="2e579-149">モニターを確実に解放するには、`finally` キーワードを使用します。このキーワードを使用することにより、例外がスローされたかどうかに関係なく、関連付けられているコード ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-149">This is accomplished with the `finally` keyword, which executes its associated code block regardless of whether an exception is thrown.</span></span>  
  
## <a name="synchronization-events-and-wait-handles"></a><span data-ttu-id="2e579-150">同期イベントと待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="2e579-150">Synchronization Events and Wait Handles</span></span>  
 <span data-ttu-id="2e579-151">スレッド依存のコード ブロックが同時に実行されないようにするためにロックやモニターを使用することは有効ですが、このような構成要素だけでは、スレッド間でイベントをやりとりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2e579-151">Using a lock or monitor is useful for preventing the simultaneous execution of thread-sensitive blocks of code, but these constructs do not allow one thread to communicate an event to another.</span></span> <span data-ttu-id="2e579-152">そこで、*同期イベント*が必要になります。これは、シグナル状態と非シグナル状態という 2 つの状態を持つオブジェクトで、これを使用することにより、スレッドをアクティブにしたり中断したりできます。</span><span class="sxs-lookup"><span data-stu-id="2e579-152">This requires *synchronization events*, which are objects that have one of two states, signaled and un-signaled, that can be used to activate and suspend threads.</span></span> <span data-ttu-id="2e579-153">非シグナル状態の同期イベントを待機させることによってスレッドを中断できます。また、イベントの状態をシグナル状態に変更することにより、スレッドをアクティブにできます。</span><span class="sxs-lookup"><span data-stu-id="2e579-153">Threads can be suspended by being made to wait on a synchronization event that is unsignaled, and can be activated by changing the event state to signaled.</span></span> <span data-ttu-id="2e579-154">既にシグナル状態にあるイベントをスレッドが待機している場合、スレッドは遅延なしに実行され続けます。</span><span class="sxs-lookup"><span data-stu-id="2e579-154">If a thread attempts to wait on an event that is already signaled, then the thread continues to execute without delay.</span></span>  
  
 <span data-ttu-id="2e579-155">同期イベントには、<xref:System.Threading.AutoResetEvent> と <xref:System.Threading.ManualResetEvent> の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="2e579-155">There are two kinds of synchronization events: <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span> <span data-ttu-id="2e579-156">この 2 つで唯一違うのは、<xref:System.Threading.AutoResetEvent> の場合、1 つのスレッドをアクティブにするたびに自動的にシグナル状態から非シグナル状態に変わるという点です。</span><span class="sxs-lookup"><span data-stu-id="2e579-156">They differ only in that <xref:System.Threading.AutoResetEvent> changes from signaled to unsignaled automatically any time it activates a thread.</span></span> <span data-ttu-id="2e579-157">逆に <xref:System.Threading.ManualResetEvent> では、そのシグナル状態で任意の数のスレッドをアクティブにでき、<xref:System.Threading.EventWaitHandle.Reset%2A> メソッドが呼び出された場合にのみ、非シグナル状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="2e579-157">Conversely, a <xref:System.Threading.ManualResetEvent> allows any number of threads to be activated by its signaled state, and will only revert to an unsignaled state when its <xref:System.Threading.EventWaitHandle.Reset%2A> method is called.</span></span>  
  
 <span data-ttu-id="2e579-158"><xref:System.Threading.WaitHandle.WaitOne%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A>、<xref:System.Threading.WaitHandle.WaitAll%2A> などの待機メソッドのいずれかを呼び出すことによって、スレッドにイベントを待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="2e579-158">Threads can be made to wait on events by calling one of the wait methods, such as <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, or <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span> <span data-ttu-id="2e579-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> は、単一のイベントがシグナル状態になるまでスレッドを待機させます。<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> は、指定した 1 つ以上のイベントがシグナル状態になるまでスレッドをブロックします。<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> は、指定したすべてのイベントがシグナル状態になるまでスレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="2e579-159"><xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> causes the thread to wait until a single event becomes signaled, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> blocks a thread until one or more indicated events become signaled, and <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> blocks the thread until all of the indicated events become signaled.</span></span> <span data-ttu-id="2e579-160">イベントは、その <xref:System.Threading.EventWaitHandle.Set%2A> メソッドが呼び出されると、シグナル状態になります。</span><span class="sxs-lookup"><span data-stu-id="2e579-160">An event becomes signaled when its <xref:System.Threading.EventWaitHandle.Set%2A> method is called.</span></span>  
  
 <span data-ttu-id="2e579-161">次の例では、`Main` 関数によってスレッドが作成され開始されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-161">In the following example, a thread is created and started by the `Main` function.</span></span> <span data-ttu-id="2e579-162">新しいスレッドは <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを使用してイベントを待機します。</span><span class="sxs-lookup"><span data-stu-id="2e579-162">The new thread waits on an event using the <xref:System.Threading.WaitHandle.WaitOne%2A> method.</span></span> <span data-ttu-id="2e579-163">このスレッドは、`Main` 関数を実行しているプライマリ スレッドによってイベントがシグナル状態になるまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-163">The thread is suspended until the event becomes signaled by the primary thread that is executing the `Main` function.</span></span> <span data-ttu-id="2e579-164">イベントがシグナル状態になると、この補助スレッドに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="2e579-164">Once the event becomes signaled, the auxiliary thread returns.</span></span> <span data-ttu-id="2e579-165">この場合は 1 つのスレッドだけをアクティブにするためにイベントを使用しているので、<xref:System.Threading.AutoResetEvent> クラスまたは <xref:System.Threading.ManualResetEvent> クラスのいずれも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-165">In this case, because the event is only used for one thread activation, either the <xref:System.Threading.AutoResetEvent> or <xref:System.Threading.ManualResetEvent> classes could be used.</span></span>  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a><span data-ttu-id="2e579-166">ミューテックス オブジェクト</span><span class="sxs-lookup"><span data-stu-id="2e579-166">Mutex Object</span></span>  
 <span data-ttu-id="2e579-167">*ミューテックス*は、複数のスレッドによってコード ブロックが同時に実行されるのを防ぐという点でモニターに似ています。</span><span class="sxs-lookup"><span data-stu-id="2e579-167">A *mutex* is similar to a monitor; it prevents the simultaneous execution of a block of code by more than one thread at a time.</span></span> <span data-ttu-id="2e579-168">実際、"mutex (ミューテックス)" という名前は、"mutually exclusive (相互に排他的)" という用語の短縮形です。</span><span class="sxs-lookup"><span data-stu-id="2e579-168">In fact, the name "mutex" is a shortened form of the term "mutually exclusive."</span></span> <span data-ttu-id="2e579-169">ただし、モニターとは違って、ミューテックスを使用するとプロセス間でスレッドを同期できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-169">Unlike monitors, however, a mutex can be used to synchronize threads across processes.</span></span> <span data-ttu-id="2e579-170">ミューテックスは、<xref:System.Threading.Mutex> クラスで表されます。</span><span class="sxs-lookup"><span data-stu-id="2e579-170">A mutex is represented by the <xref:System.Threading.Mutex> class.</span></span>  
  
 <span data-ttu-id="2e579-171">プロセス間の同期に使用されるミューテックスは、*名前付きミューテックス*と呼ばれます。このようなミューテックスは別のアプリケーションで使用される可能性があるため、グローバル変数や静的変数を使用して共有できないからです。</span><span class="sxs-lookup"><span data-stu-id="2e579-171">When used for inter-process synchronization, a mutex is called a *named mutex* because it is to be used in another application, and therefore it cannot be shared by means of a global or static variable.</span></span> <span data-ttu-id="2e579-172">したがって、両方のアプリケーションから同じミューテックス オブジェクトにアクセスできるように、名前を付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e579-172">It must be given a name so that both applications can access the same mutex object.</span></span>  
  
 <span data-ttu-id="2e579-173">ミューテックスを使用するとプロセス間でスレッドを同期できますが、通常は <xref:System.Threading.Monitor> の使用をお勧めします。その理由は、モニターが .NET Framework 専用にデザインされているため、より適切にリソースを利用できる点にあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-173">Although a mutex can be used for intra-process thread synchronization, using <xref:System.Threading.Monitor> is generally preferred, because monitors were designed specifically for the .NET Framework and therefore make better use of resources.</span></span> <span data-ttu-id="2e579-174">一方、<xref:System.Threading.Mutex> クラスは Win32 の構成要素のラッパーです。</span><span class="sxs-lookup"><span data-stu-id="2e579-174">In contrast, the <xref:System.Threading.Mutex> class is a wrapper to a Win32 construct.</span></span> <span data-ttu-id="2e579-175">ミューテックスはモニターよりも強力ですが、<xref:System.Threading.Monitor> クラスよりも相互運用機能の遷移に必要な計算上の負荷が大きくなってしまいます。</span><span class="sxs-lookup"><span data-stu-id="2e579-175">While it is more powerful than a monitor, a mutex requires interop transitions that are more computationally expensive than those required by the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="2e579-176">ミューテックスの使用例については、「[ミューテックス](../../../../standard/threading/mutexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e579-176">For an example of using a mutex, see [Mutexes](../../../../standard/threading/mutexes.md).</span></span>  
  
## <a name="interlocked-class"></a><span data-ttu-id="2e579-177">Interlocked クラス</span><span class="sxs-lookup"><span data-stu-id="2e579-177">Interlocked Class</span></span>  
 <span data-ttu-id="2e579-178"><xref:System.Threading.Interlocked> クラスのメソッドを使用すると、複数のスレッドが同じ値を同時に更新または比較しようとしたときに発生する可能性のある問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-178">You can use the methods of the <xref:System.Threading.Interlocked> class to prevent problems that can occur when multiple threads attempt to simultaneously update or compare the same value.</span></span> <span data-ttu-id="2e579-179">このクラスのメソッドによって、どのスレッドの値も安全にインクリメント、デクリメント、交換、比較することができます。</span><span class="sxs-lookup"><span data-stu-id="2e579-179">The methods of this class let you safely increment, decrement, exchange, and compare values from any thread.</span></span>  
  
## <a name="readerwriter-locks"></a><span data-ttu-id="2e579-180">ReaderWriter ロック</span><span class="sxs-lookup"><span data-stu-id="2e579-180">ReaderWriter Locks</span></span>  
 <span data-ttu-id="2e579-181">場合によっては、データを書き込むときだけリソースをロックし、データが更新されないときには複数のクライアントにデータの同時読み取りを許可することがあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-181">In some cases, you may want to lock a resource only when data is being written and permit multiple clients to simultaneously read data when data is not being updated.</span></span> <span data-ttu-id="2e579-182"><xref:System.Threading.ReaderWriterLock> クラスを使用すると、スレッドがリソースを変更する間はリソースに排他アクセスを適用し、リソースを読み取るときには排他的でないアクセスを許可できます。</span><span class="sxs-lookup"><span data-stu-id="2e579-182">The <xref:System.Threading.ReaderWriterLock> class enforces exclusive access to a resource while a thread is modifying the resource, but it allows non-exclusive access when reading the resource.</span></span> <span data-ttu-id="2e579-183">ReaderWriter ロックは、データの更新が必要ないときでも、他のスレッドを待機させる方法として、排他ロックに代わる有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="2e579-183">ReaderWriter locks are a useful alternative to exclusive locks, which cause other threads to wait, even when those threads do not need to update data.</span></span>  
  
## <a name="deadlocks"></a><span data-ttu-id="2e579-184">デッドロック</span><span class="sxs-lookup"><span data-stu-id="2e579-184">Deadlocks</span></span>  
 <span data-ttu-id="2e579-185">スレッドの同期は、マルチスレッド アプリケーションにとって非常に大切ですが、`deadlock` を生じさせてしまう危険性が常にあります。つまり、複数のスレッドが互いに待機しあって、アプリケーションが中断してしまう状態になります。</span><span class="sxs-lookup"><span data-stu-id="2e579-185">Thread synchronization is invaluable in multithreaded applications, but there is always the danger of creating a `deadlock`, where multiple threads are waiting for each other and the application comes to a halt.</span></span> <span data-ttu-id="2e579-186">デッドロックは、たとえるなら四方向が一時停止の交差点で停止した車どうしが、相手の車を先に行かせるよう互いに譲り合い、誰もが動けなくなっている状態に似ています。</span><span class="sxs-lookup"><span data-stu-id="2e579-186">A deadlock is analogous to a situation in which cars are stopped at a four-way stop and each person is waiting for the other to go.</span></span> <span data-ttu-id="2e579-187">デッドロックを防ぐことは重要です。その鍵となるのは、綿密なプランです。</span><span class="sxs-lookup"><span data-stu-id="2e579-187">Avoiding deadlocks is important; the key is careful planning.</span></span> <span data-ttu-id="2e579-188">コーディングを始める前にマルチスレッド アプリケーションを図式化すると、デッドロック状態を予想できることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="2e579-188">You can often predict deadlock situations by diagramming multithreaded applications before you start coding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e579-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e579-189">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="2e579-190">マルチスレッド アプリケーション (C#)</span><span class="sxs-lookup"><span data-stu-id="2e579-190">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="2e579-191">lock ステートメント</span><span class="sxs-lookup"><span data-stu-id="2e579-191">lock Statement</span></span>](../../../../csharp/language-reference/keywords/lock-statement.md)  
 [<span data-ttu-id="2e579-192">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="2e579-192">Mutexes</span></span>](../../../../standard/threading/mutexes.md)  
 [<span data-ttu-id="2e579-193">インタロックされた操作</span><span class="sxs-lookup"><span data-stu-id="2e579-193">Interlocked Operations</span></span>](../../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="2e579-194">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="2e579-194">AutoResetEvent</span></span>](../../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="2e579-195">マルチスレッド処理のためのデータの同期</span><span class="sxs-lookup"><span data-stu-id="2e579-195">Synchronizing Data for Multithreading</span></span>](../../../../standard/threading/synchronizing-data-for-multithreading.md)

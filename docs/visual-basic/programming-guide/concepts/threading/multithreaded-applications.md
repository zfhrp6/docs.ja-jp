---
title: マルチ スレッド アプリケーション (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
ms.openlocfilehash: ab4b8d1c77ae75aee6f2cf459258766f88d86abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="multithreaded-applications-visual-basic"></a><span data-ttu-id="8ea9b-102">マルチ スレッド アプリケーション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea9b-102">Multithreaded Applications (Visual Basic)</span></span>
<span data-ttu-id="8ea9b-103">Visual Basic では、同時に複数のタスクを実行するアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-103">With Visual Basic, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="8ea9b-104">他のタスクを止める可能性があるタスクは個別のスレッドで実行できます。これは*マルチスレッド*や*フリー スレッド*と呼ばれているプロセスです。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="8ea9b-105">マルチスレッドを利用するアプリケーションはユーザーの入力に対する応答性が良くなります。プロセッサを集中的に利用するタスクが個別のスレッドで実行されるため、ユーザー インターフェイスの動作が妨げられません。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="8ea9b-106">マルチスレッドはまた、スケーラブルなアプリケーションの開発にも便利です。ワークロードが増えたとき、スレッドを追加できるからです。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="8ea9b-107">スレッドを作成し、使用する</span><span class="sxs-lookup"><span data-stu-id="8ea9b-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="8ea9b-108">アプリケーションのスレッドの動作をさらに細かく制御するには、スレッドを自分で管理します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="8ea9b-109">しかしながら、正しく機能するマルチスレッド アプリケーションは記述が難しいことを知ってください。競合状態になり、応答が停止したり、一時的なエラーが発生したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="8ea9b-110">詳しくは、「[スレッドセーフ コンポーネント](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="8ea9b-111">新しいスレッドを作成します。<xref:System.Threading.Thread> 型の変数を宣言し、コンストラクターを呼び出し、新しいスレッドで実行するプロシージャまたはメソッドの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="8ea9b-112">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-112">The following code provides an example.</span></span>  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="8ea9b-113">スレッドの開始と停止</span><span class="sxs-lookup"><span data-stu-id="8ea9b-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="8ea9b-114">新しいスレッドの実行を開始するには、次のコードにあるように、<xref:System.Threading.Thread.Start%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```vb  
newThread.Start()  
```  
  
 <span data-ttu-id="8ea9b-115">スレッドの実行を停止するには、次のコードにあるように、<xref:System.Threading.Thread.Abort%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```vb  
newThread.Abort()  
```  
  
 <span data-ttu-id="8ea9b-116">スレッドの開始と停止に加え、スレッドを中断することもできます。<xref:System.Threading.Thread.Sleep%2A> または <xref:System.Threading.Thread.Suspend%2A> を呼び出します。中断しているスレッドを再開するには、<xref:System.Threading.Thread.Resume%2A> メソッドを使用します。スレッドを破棄するには <xref:System.Threading.Thread.Abort%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="8ea9b-117">スレッド メソッド</span><span class="sxs-lookup"><span data-stu-id="8ea9b-117">Thread Methods</span></span>  
 <span data-ttu-id="8ea9b-118">次の表は、個々のスレッドを制御できるメソッドをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="8ea9b-119">メソッド</span><span class="sxs-lookup"><span data-stu-id="8ea9b-119">Method</span></span>|<span data-ttu-id="8ea9b-120">アクション</span><span class="sxs-lookup"><span data-stu-id="8ea9b-120">Action</span></span>|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|<span data-ttu-id="8ea9b-121">スレッドの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-121">Causes a thread to start to run.</span></span>|  
|<xref:System.Threading.Thread.Sleep%2A>|<span data-ttu-id="8ea9b-122">指定した時間だけスレッドを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-122">Pauses a thread for a specified time.</span></span>|  
|<xref:System.Threading.Thread.Suspend%2A>|<span data-ttu-id="8ea9b-123">セーフ ポイントに到達するとスレッドを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-123">Pauses a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Abort%2A>|<span data-ttu-id="8ea9b-124">セーフ ポイントに到達するとスレッドを停止します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-124">Stops a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Resume%2A>|<span data-ttu-id="8ea9b-125">一時停止になっているスレッドを再開します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-125">Restarts a suspended thread</span></span>|  
|<xref:System.Threading.Thread.Join%2A>|<span data-ttu-id="8ea9b-126">別のスレッドが完了するまで現在のスレッドに待機させます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-126">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="8ea9b-127">タイムアウト値と併用すると、このメソッドは、割り当てられた時間でスレッドが完了した場合、`True` を返します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-127">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="8ea9b-128">セーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="8ea9b-128">Safe Points</span></span>  
 <span data-ttu-id="8ea9b-129">以上のメソッドのほとんどは名前を見ればその機能が明らかですが、*セーフ ポイント*は初めて耳にする概念かもしれません。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-129">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="8ea9b-130">セーフ ポイントとは、共通言語ランタイムが自動*ガベージ コレクション*を安全に実行できる (コード内の) 場所です。ガベージ コレクションは、未使用の変数とメモリを解放するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-130">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="8ea9b-131">スレッドの <xref:System.Threading.Thread.Abort%2A> または <xref:System.Threading.Thread.Suspend%2A> メソッドを呼び出すと、共通言語ランタイムはコードを分析し、スレッドが実行を停止する場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-131">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="8ea9b-132">スレッド プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ea9b-132">Thread Properties</span></span>  
 <span data-ttu-id="8ea9b-133">スレッドには、便利なプロパティもあります。次の表をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-133">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="8ea9b-134">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ea9b-134">Property</span></span>|<span data-ttu-id="8ea9b-135">[値]</span><span class="sxs-lookup"><span data-stu-id="8ea9b-135">Value</span></span>|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|<span data-ttu-id="8ea9b-136">スレッドがアクティブな場合、値 `True` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-136">Contains the value `True` if a thread is active.</span></span>|  
|<xref:System.Threading.Thread.IsBackground%2A>|<span data-ttu-id="8ea9b-137">スレッドがバックグラウンド スレッドかどうか、あるいはバックグラウンド スレッドにする必要があるかどうかを示すブール値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-137">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="8ea9b-138">バックグラウンド スレッドはフォアグラウンド スレッドに似ていますが、プロセスの停止を阻止しません。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-138">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="8ea9b-139">あるプロセスに属するフォアグラウンド スレッドがすべて停止すると、共通言語ランタイムは、アライブ状態のバックグラウンド スレッドで <xref:System.Threading.Thread.Abort%2A> メソッドを呼び出し、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-139">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<xref:System.Threading.Thread.Name%2A>|<span data-ttu-id="8ea9b-140">スレッドの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-140">Gets or sets the name of a thread.</span></span> <span data-ttu-id="8ea9b-141">デバッグ時、個々のスレッドを検出するために頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-141">Most frequently used to discover individual threads when you debug.</span></span>|  
|<xref:System.Threading.Thread.Priority%2A>|<span data-ttu-id="8ea9b-142">オペレーティング システムがスレッド スケジュールに優先順位を設定するために使用する値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-142">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<xref:System.Threading.Thread.ThreadState%2A>|<span data-ttu-id="8ea9b-143">スレッドの状態を説明する値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-143">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="8ea9b-144">スレッドの優先順位</span><span class="sxs-lookup"><span data-stu-id="8ea9b-144">Thread Priorities</span></span>  
 <span data-ttu-id="8ea9b-145">すべてのスレッドに優先順位が与えられます。その優先順位により、スレッドが実行するプロセッサのタイム スライスの大小が決定されます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-145">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="8ea9b-146">オペレーティング システムは、優先順位の高いスレッドに長いタイム スライスを割り当て、優先順位の低いスレッドに短いタイム スライスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-146">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="8ea9b-147">新しいスレッドは値 `Normal` で作成されますが、<xref:System.Threading.Thread.Priority%2A> プロパティを <xref:System.Threading.ThreadPriority> 列挙の任意の値に変更できます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-147">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="8ea9b-148">さまざまなスレッド優先順位の詳細については、「<xref:System.Threading.ThreadPriority>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-148">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="8ea9b-149">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="8ea9b-149">Foreground and Background Threads</span></span>  
 <span data-ttu-id="8ea9b-150">*フォアグラウンド スレッド*は無期限で実行されます。*バックグラウンド スレッド*は、最後のフォアグラウンド スレッドが停止した直後に停止します。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-150">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="8ea9b-151"><xref:System.Threading.Thread.IsBackground%2A> プロパティを利用し、スレッドのバックグラウンド状態を確認したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="8ea9b-151">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea9b-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ea9b-152">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="8ea9b-153">スレッドの同期 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea9b-153">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="8ea9b-154">マルチスレッド プロシージャのパラメーターと戻り値 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea9b-154">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)  
 [<span data-ttu-id="8ea9b-155">スレッド処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea9b-155">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)

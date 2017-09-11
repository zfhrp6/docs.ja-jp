---
title: "マルチスレッド アプリケーション (C#)"
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
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
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
ms.openlocfilehash: dfe0f9c6e911295270df8464d1070a524412466d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="multithreaded-applications-c"></a><span data-ttu-id="a4c16-102">マルチスレッド アプリケーション (C#)</span><span class="sxs-lookup"><span data-stu-id="a4c16-102">Multithreaded Applications (C#)</span></span>
<span data-ttu-id="a4c16-103">C# では、複数のタスクを同時に実行するアプリケーションを記述できます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-103">With C#, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="a4c16-104">他のタスクを止める可能性があるタスクは個別のスレッドで実行できます。これは*マルチスレッド*や*フリー スレッド*と呼ばれているプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a4c16-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="a4c16-105">マルチスレッドを利用するアプリケーションはユーザーの入力に対する応答性が良くなります。プロセッサを集中的に利用するタスクが個別のスレッドで実行されるため、ユーザー インターフェイスの動作が妨げられません。</span><span class="sxs-lookup"><span data-stu-id="a4c16-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="a4c16-106">マルチスレッドはまた、スケーラブルなアプリケーションの開発にも便利です。ワークロードが増えたとき、スレッドを追加できるからです。</span><span class="sxs-lookup"><span data-stu-id="a4c16-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="a4c16-107">スレッドを作成し、使用する</span><span class="sxs-lookup"><span data-stu-id="a4c16-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="a4c16-108">アプリケーションのスレッドの動作をさらに細かく制御するには、スレッドを自分で管理します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="a4c16-109">しかしながら、正しく機能するマルチスレッド アプリケーションは記述が難しいことを知ってください。競合状態になり、応答が停止したり、一時的なエラーが発生したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="a4c16-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="a4c16-110">詳しくは、「[スレッドセーフ コンポーネント](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c16-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="a4c16-111">新しいスレッドを作成します。<xref:System.Threading.Thread> 型の変数を宣言し、コンストラクターを呼び出し、新しいスレッドで実行するプロシージャまたはメソッドの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="a4c16-112">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-112">The following code provides an example.</span></span>  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="a4c16-113">スレッドの開始と停止</span><span class="sxs-lookup"><span data-stu-id="a4c16-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="a4c16-114">新しいスレッドの実行を開始するには、次のコードにあるように、<xref:System.Threading.Thread.Start%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Start();  
```  
  
 <span data-ttu-id="a4c16-115">スレッドの実行を停止するには、次のコードにあるように、<xref:System.Threading.Thread.Abort%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```csharp  
newThread.Abort();  
```  
  
 <span data-ttu-id="a4c16-116">スレッドの開始と停止に加え、スレッドを中断することもできます。<xref:System.Threading.Thread.Sleep%2A> または <xref:System.Threading.Thread.Suspend%2A> を呼び出します。中断しているスレッドを再開するには、<xref:System.Threading.Thread.Resume%2A> メソッドを使用します。スレッドを破棄するには <xref:System.Threading.Thread.Abort%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="a4c16-117">スレッド メソッド</span><span class="sxs-lookup"><span data-stu-id="a4c16-117">Thread Methods</span></span>  
 <span data-ttu-id="a4c16-118">次の表は、個々のスレッドを制御できるメソッドをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="a4c16-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="a4c16-119">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4c16-119">Method</span></span>|<span data-ttu-id="a4c16-120">アクション</span><span class="sxs-lookup"><span data-stu-id="a4c16-120">Action</span></span>|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|<span data-ttu-id="a4c16-121">スレッドの実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-121">Causes a thread to start to run.</span></span>|  
|<xref:System.Threading.Thread.Sleep%2A>|<span data-ttu-id="a4c16-122">指定した時間だけスレッドを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-122">Pauses a thread for a specified time.</span></span>|  
|<xref:System.Threading.Thread.Suspend%2A>|<span data-ttu-id="a4c16-123">セーフ ポイントに到達するとスレッドを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-123">Pauses a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Abort%2A>|<span data-ttu-id="a4c16-124">セーフ ポイントに到達するとスレッドを停止します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-124">Stops a thread when it reaches a safe point.</span></span>|  
|<xref:System.Threading.Thread.Resume%2A>|<span data-ttu-id="a4c16-125">一時停止になっているスレッドを再開します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-125">Restarts a suspended thread</span></span>|  
|<xref:System.Threading.Thread.Join%2A>|<span data-ttu-id="a4c16-126">別のスレッドが完了するまで現在のスレッドに待機させます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-126">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="a4c16-127">タイムアウト値と併用すると、このメソッドは、割り当てられた時間でスレッドが完了した場合、`True` を返します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-127">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="a4c16-128">セーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="a4c16-128">Safe Points</span></span>  
 <span data-ttu-id="a4c16-129">以上のメソッドのほとんどは名前を見ればその機能が明らかですが、*セーフ ポイント*は初めて耳にする概念かもしれません。</span><span class="sxs-lookup"><span data-stu-id="a4c16-129">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="a4c16-130">セーフ ポイントとは、共通言語ランタイムが自動*ガベージ コレクション*を安全に実行できる (コード内の) 場所です。ガベージ コレクションは、未使用の変数とメモリを解放するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a4c16-130">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="a4c16-131">スレッドの <xref:System.Threading.Thread.Abort%2A> または <xref:System.Threading.Thread.Suspend%2A> メソッドを呼び出すと、共通言語ランタイムはコードを分析し、スレッドが実行を停止する場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-131">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="a4c16-132">スレッド プロパティ</span><span class="sxs-lookup"><span data-stu-id="a4c16-132">Thread Properties</span></span>  
 <span data-ttu-id="a4c16-133">スレッドには、便利なプロパティもあります。次の表をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a4c16-133">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="a4c16-134">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a4c16-134">Property</span></span>|<span data-ttu-id="a4c16-135">値</span><span class="sxs-lookup"><span data-stu-id="a4c16-135">Value</span></span>|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|<span data-ttu-id="a4c16-136">スレッドがアクティブな場合、値 `True` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-136">Contains the value `True` if a thread is active.</span></span>|  
|<xref:System.Threading.Thread.IsBackground%2A>|<span data-ttu-id="a4c16-137">スレッドがバックグラウンド スレッドかどうか、あるいはバックグラウンド スレッドにする必要があるかどうかを示すブール値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-137">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="a4c16-138">バックグラウンド スレッドはフォアグラウンド スレッドに似ていますが、プロセスの停止を阻止しません。</span><span class="sxs-lookup"><span data-stu-id="a4c16-138">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="a4c16-139">あるプロセスに属するフォアグラウンド スレッドがすべて停止すると、共通言語ランタイムは、アライブ状態のバックグラウンド スレッドで <xref:System.Threading.Thread.Abort%2A> メソッドを呼び出し、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-139">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<xref:System.Threading.Thread.Name%2A>|<span data-ttu-id="a4c16-140">スレッドの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-140">Gets or sets the name of a thread.</span></span> <span data-ttu-id="a4c16-141">デバッグ時、個々のスレッドを検出するために頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-141">Most frequently used to discover individual threads when you debug.</span></span>|  
|<xref:System.Threading.Thread.Priority%2A>|<span data-ttu-id="a4c16-142">オペレーティング システムがスレッド スケジュールに優先順位を設定するために使用する値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-142">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<xref:System.Threading.Thread.ThreadState%2A>|<span data-ttu-id="a4c16-143">スレッドの状態を説明する値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-143">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="a4c16-144">スレッドの優先順位</span><span class="sxs-lookup"><span data-stu-id="a4c16-144">Thread Priorities</span></span>  
 <span data-ttu-id="a4c16-145">すべてのスレッドに優先順位が与えられます。その優先順位により、スレッドが実行するプロセッサのタイム スライスの大小が決定されます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-145">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="a4c16-146">オペレーティング システムは、優先順位の高いスレッドに長いタイム スライスを割り当て、優先順位の低いスレッドに短いタイム スライスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-146">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="a4c16-147">新しいスレッドは値 `Normal` で作成されますが、<xref:System.Threading.Thread.Priority%2A> プロパティを <xref:System.Threading.ThreadPriority> 列挙の任意の値に変更できます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-147">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="a4c16-148">さまざまなスレッド優先順位の詳細については、「<xref:System.Threading.ThreadPriority>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4c16-148">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="a4c16-149">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="a4c16-149">Foreground and Background Threads</span></span>  
 <span data-ttu-id="a4c16-150">*フォアグラウンド スレッド*は無期限で実行されます。*バックグラウンド スレッド*は、最後のフォアグラウンド スレッドが停止した直後に停止します。</span><span class="sxs-lookup"><span data-stu-id="a4c16-150">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="a4c16-151"><xref:System.Threading.Thread.IsBackground%2A> プロパティを利用し、スレッドのバックグラウンド状態を確認したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="a4c16-151">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c16-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4c16-152">See Also</span></span>  
 <span data-ttu-id="a4c16-153"><xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="a4c16-153"><xref:System.Threading.Thread></span></span>   
 <span data-ttu-id="a4c16-154">[スレッドの同期 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="a4c16-154">[Thread Synchronization (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
 <span data-ttu-id="a4c16-155">[マルチスレッド プロシージャのパラメーターと戻り値 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a4c16-155">[Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span></span>  
 [<span data-ttu-id="a4c16-156">スレッド処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="a4c16-156">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)


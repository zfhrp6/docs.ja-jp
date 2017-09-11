---
title: "マルチ スレッド アプリケーション (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
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
ms.openlocfilehash: 8b68104fbc5eb0e0eb0f46401f3fcef0d3c4d023
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="multithreaded-applications-visual-basic"></a><span data-ttu-id="d176c-102">マルチ スレッド アプリケーション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d176c-102">Multithreaded Applications (Visual Basic)</span></span>
<span data-ttu-id="d176c-103">Visual basic では、同時に複数のタスクを実行するアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d176c-103">With Visual Basic, you can write applications that perform multiple tasks at the same time.</span></span> <span data-ttu-id="d176c-104">その他のタスクを停止させる可能性のあるタスク別のスレッドでと呼ばれるプロセスとの実行のできます*マルチ スレッド*または*フリー スレッド*します。</span><span class="sxs-lookup"><span data-stu-id="d176c-104">Tasks with the potential of holding up other tasks can execute on separate threads, a process known as *multithreading* or *free threading*.</span></span>  
  
 <span data-ttu-id="d176c-105">マルチ スレッドを使用、プロセッサ集中型のタスクを個別のスレッドで実行すると、ユーザー インターフェイスがアクティブに保たれるためのユーザーに応答性を向上するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="d176c-105">Applications that use multithreading are more responsive to user input because the user interface stays active as processor-intensive tasks execute on separate threads.</span></span> <span data-ttu-id="d176c-106">マルチ スレッドも役立ちます、スケーラブルなアプリケーションを作成するときにワークロードが増加すると、スレッドを追加できるためです。</span><span class="sxs-lookup"><span data-stu-id="d176c-106">Multithreading is also useful when you create scalable applications, because you can add threads as the workload increases.</span></span>  
  
## <a name="creating-and-using-threads"></a><span data-ttu-id="d176c-107">作成して、スレッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d176c-107">Creating and Using Threads</span></span>  
 <span data-ttu-id="d176c-108">アプリケーションのスレッドの動作をより詳細に制御する場合は、できるスレッドは、自分で管理します。</span><span class="sxs-lookup"><span data-stu-id="d176c-108">If you need more control over the behavior of your application's threads, you can manage the threads yourself.</span></span> <span data-ttu-id="d176c-109">ただし、正しいマルチ スレッド アプリケーションを作成することは困難を実現します。 アプリケーションの応答を停止または競合状態によって発生する一時的なエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d176c-109">However, realize that writing correct multithreaded applications can be difficult: Your application may stop responding or experience transient errors caused by race conditions.</span></span> <span data-ttu-id="d176c-110">詳細については、次を参照してください。[スレッド セーフなコンポーネント](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)します。</span><span class="sxs-lookup"><span data-stu-id="d176c-110">For more information, see [Thread-Safe Components](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).</span></span>  
  
 <span data-ttu-id="d176c-111">型の変数を宣言することで、新しいスレッドを作成する<xref:System.Threading.Thread>プロシージャまたは新しいスレッド上で実行するメソッドの名前を指定するコンス トラクターを呼び出すとします</xref:System.Threading.Thread>。</span><span class="sxs-lookup"><span data-stu-id="d176c-111">You create a new thread by declaring a variable of type <xref:System.Threading.Thread> and calling the constructor, providing the name of the procedure or method that you want to execute on the new thread.</span></span> <span data-ttu-id="d176c-112">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="d176c-112">The following code provides an example.</span></span>  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a><span data-ttu-id="d176c-113">開始と停止のスレッド</span><span class="sxs-lookup"><span data-stu-id="d176c-113">Starting and Stopping Threads</span></span>  
 <span data-ttu-id="d176c-114">新しいスレッドの実行を開始するを使用して、<xref:System.Threading.Thread.Start%2A>メソッドを次のコードに示すようにします</xref:System.Threading.Thread.Start%2A>。</span><span class="sxs-lookup"><span data-stu-id="d176c-114">To start the execution of a new thread, use the <xref:System.Threading.Thread.Start%2A> method, as shown in the following code.</span></span>  
  
```vb  
newThread.Start()  
```  
  
 <span data-ttu-id="d176c-115">スレッドの実行を停止するを使用して、<xref:System.Threading.Thread.Abort%2A>メソッドを次のコードに示すようにします</xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="d176c-115">To stop the execution of a thread, use the <xref:System.Threading.Thread.Abort%2A> method, as shown in the following code.</span></span>  
  
```vb  
newThread.Abort()  
```  
  
 <span data-ttu-id="d176c-116">開始ほかのスレッドが停止するも一時停止することのスレッドを呼び出して、<xref:System.Threading.Thread.Sleep%2A>または<xref:System.Threading.Thread.Suspend%2A>メソッドを使用して中断されたスレッドを再開、<xref:System.Threading.Thread.Resume%2A>メソッド、および<xref:System.Threading.Thread.Abort%2A>メソッド</xref:System.Threading.Thread.Abort%2A>を使用してスレッドを破棄</xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-116">Besides starting and stopping threads, you can also pause threads by calling the <xref:System.Threading.Thread.Sleep%2A> or <xref:System.Threading.Thread.Suspend%2A> method, resume a suspended thread by using the <xref:System.Threading.Thread.Resume%2A> method, and destroy a thread by using the <xref:System.Threading.Thread.Abort%2A> method</span></span>  
  
### <a name="thread-methods"></a><span data-ttu-id="d176c-117">スレッドのメソッド</span><span class="sxs-lookup"><span data-stu-id="d176c-117">Thread Methods</span></span>  
 <span data-ttu-id="d176c-118">次の表は、個別のスレッドを制御に使用できるメソッドの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="d176c-118">The following table shows some of the methods that you can use to control individual threads.</span></span>  
  
|<span data-ttu-id="d176c-119">メソッド</span><span class="sxs-lookup"><span data-stu-id="d176c-119">Method</span></span>|<span data-ttu-id="d176c-120">操作</span><span class="sxs-lookup"><span data-stu-id="d176c-120">Action</span></span>|  
|------------|------------|  
|<span data-ttu-id="d176c-121"><xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-121"><xref:System.Threading.Thread.Start%2A></span></span>|<span data-ttu-id="d176c-122">スレッド実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="d176c-122">Causes a thread to start to run.</span></span>|  
|<span data-ttu-id="d176c-123"><xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-123"><xref:System.Threading.Thread.Sleep%2A></span></span>|<span data-ttu-id="d176c-124">スレッドを指定した時間一時停止します。</span><span class="sxs-lookup"><span data-stu-id="d176c-124">Pauses a thread for a specified time.</span></span>|  
|<span data-ttu-id="d176c-125"><xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Suspend%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-125"><xref:System.Threading.Thread.Suspend%2A></span></span>|<span data-ttu-id="d176c-126">セーフ ポイントに達すると、スレッドを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="d176c-126">Pauses a thread when it reaches a safe point.</span></span>|  
|<span data-ttu-id="d176c-127"><xref:System.Threading.Thread.Abort%2A></xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-127"><xref:System.Threading.Thread.Abort%2A></span></span>|<span data-ttu-id="d176c-128">セーフ ポイントに達すると、スレッドを停止します。</span><span class="sxs-lookup"><span data-stu-id="d176c-128">Stops a thread when it reaches a safe point.</span></span>|  
|<span data-ttu-id="d176c-129"><xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Resume%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-129"><xref:System.Threading.Thread.Resume%2A></span></span>|<span data-ttu-id="d176c-130">中断されたスレッドを再開します。</span><span class="sxs-lookup"><span data-stu-id="d176c-130">Restarts a suspended thread</span></span>|  
|<span data-ttu-id="d176c-131"><xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-131"><xref:System.Threading.Thread.Join%2A></span></span>|<span data-ttu-id="d176c-132">によって現在のスレッドが別のスレッドが完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="d176c-132">Causes the current thread to wait for another thread to finish.</span></span> <span data-ttu-id="d176c-133">タイムアウト値を持つ場合、このメソッドが戻る`True`割り当てられた時間内に、スレッドが終了した場合。</span><span class="sxs-lookup"><span data-stu-id="d176c-133">If used with a time-out value, this method returns `True` if the thread finishes in the allocated time.</span></span>|  
  
### <a name="safe-points"></a><span data-ttu-id="d176c-134">セーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="d176c-134">Safe Points</span></span>  
 <span data-ttu-id="d176c-135">これらのメソッドのほとんどは見ればわかるので、その概念の*セーフ ポイント*に新しい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d176c-135">Most of these methods are self-explanatory, but the concept of *safe points* may be new to you.</span></span> <span data-ttu-id="d176c-136">セーフ ポイントとは、安全では、共通言語ランタイムを自動実行するコード内の場所*ガベージ コレクション*、使用されていない変数を解放して、メモリを再利用のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d176c-136">Safe points are locations in code where it is safe for the common language runtime to perform automatic *garbage collection*, the process of releasing unused variables and reclaiming memory.</span></span> <span data-ttu-id="d176c-137">呼び出すと、<xref:System.Threading.Thread.Abort%2A>または<xref:System.Threading.Thread.Suspend%2A>、共通言語ランタイムのスレッドのメソッドは、コードを分析し、スレッドの実行を停止するための適切な場所の場所を決定します</xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="d176c-137">When you call the <xref:System.Threading.Thread.Abort%2A> or <xref:System.Threading.Thread.Suspend%2A> method of a thread, the common language runtime analyzes the code and determines the location of an appropriate location for the thread to stop running.</span></span>  
  
### <a name="thread-properties"></a><span data-ttu-id="d176c-138">スレッド プロパティ</span><span class="sxs-lookup"><span data-stu-id="d176c-138">Thread Properties</span></span>  
 <span data-ttu-id="d176c-139">スレッドには、次の表に示すようにいくつかの便利なプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d176c-139">Threads also contain several useful properties, as shown in the following table:</span></span>  
  
|<span data-ttu-id="d176c-140">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d176c-140">Property</span></span>|<span data-ttu-id="d176c-141">値</span><span class="sxs-lookup"><span data-stu-id="d176c-141">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="d176c-142"><xref:System.Threading.Thread.IsAlive%2A></xref:System.Threading.Thread.IsAlive%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-142"><xref:System.Threading.Thread.IsAlive%2A></span></span>|<span data-ttu-id="d176c-143">値を含む`True`スレッドがアクティブな場合です。</span><span class="sxs-lookup"><span data-stu-id="d176c-143">Contains the value `True` if a thread is active.</span></span>|  
|<span data-ttu-id="d176c-144"><xref:System.Threading.Thread.IsBackground%2A></xref:System.Threading.Thread.IsBackground%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-144"><xref:System.Threading.Thread.IsBackground%2A></span></span>|<span data-ttu-id="d176c-145">取得またはスレッドをバック グラウンド スレッドをする必要がありますかを示すブール値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d176c-145">Gets or sets a Boolean that indicates if a thread is or should be a background thread.</span></span> <span data-ttu-id="d176c-146">バック グラウンド スレッド フォア グラウンド スレッドと似ていますが、バック グラウンド スレッドが停止するプロセスを妨げられません。</span><span class="sxs-lookup"><span data-stu-id="d176c-146">Background threads are like foreground threads, but a background thread does not prevent a process from stopping.</span></span> <span data-ttu-id="d176c-147">共通言語ランタイムが呼び出すことによって、プロセスを終了するプロセスに属するすべてのフォア グラウンド スレッドが停止されると、<xref:System.Threading.Thread.Abort%2A>生きているバック グラウンド スレッド上のメソッドです</xref:System.Threading.Thread.Abort%2A>。</span><span class="sxs-lookup"><span data-stu-id="d176c-147">Once all foreground threads that belong to a process have stopped, the common language runtime ends the process by calling the <xref:System.Threading.Thread.Abort%2A> method on background threads that are still alive.</span></span>|  
|<span data-ttu-id="d176c-148"><xref:System.Threading.Thread.Name%2A></xref:System.Threading.Thread.Name%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-148"><xref:System.Threading.Thread.Name%2A></span></span>|<span data-ttu-id="d176c-149">取得またはスレッドの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="d176c-149">Gets or sets the name of a thread.</span></span> <span data-ttu-id="d176c-150">最も頻繁をデバッグするときに、個別のスレッドを検出するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d176c-150">Most frequently used to discover individual threads when you debug.</span></span>|  
|<span data-ttu-id="d176c-151"><xref:System.Threading.Thread.Priority%2A></xref:System.Threading.Thread.Priority%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-151"><xref:System.Threading.Thread.Priority%2A></span></span>|<span data-ttu-id="d176c-152">取得またはスレッドのスケジューリング優先順位を付けるオペレーティング システムによって使用される値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d176c-152">Gets or sets a value that is used by the operating system to prioritize thread scheduling.</span></span>|  
|<span data-ttu-id="d176c-153"><xref:System.Threading.Thread.ThreadState%2A></xref:System.Threading.Thread.ThreadState%2A></span><span class="sxs-lookup"><span data-stu-id="d176c-153"><xref:System.Threading.Thread.ThreadState%2A></span></span>|<span data-ttu-id="d176c-154">スレッドの状態または状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d176c-154">Contains a value that describes a thread's state or states.</span></span>|  
  
## <a name="thread-priorities"></a><span data-ttu-id="d176c-155">スレッドの優先順位</span><span class="sxs-lookup"><span data-stu-id="d176c-155">Thread Priorities</span></span>  
 <span data-ttu-id="d176c-156">すべてのスレッドでは、実行する必要があるプロセッサ時間のスライスのサイズを決定する優先度プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d176c-156">Every thread has a priority property that determines how big or small a slice of processor time it has to execute.</span></span> <span data-ttu-id="d176c-157">オペレーティング システムでは、優先度の高いスレッドに長いタイム スライスと優先度の低いスレッドに短いタイム スライスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d176c-157">The operating system allocates longer time slices to high-priority threads and shorter time slices to low-priority threads.</span></span> <span data-ttu-id="d176c-158">新しいスレッドが作成され、値の`Normal`、変更することが、<xref:System.Threading.Thread.Priority%2A>プロパティの任意の値を<xref:System.Threading.ThreadPriority>列挙体</xref:System.Threading.ThreadPriority></xref:System.Threading.Thread.Priority%2A>。</span><span class="sxs-lookup"><span data-stu-id="d176c-158">New threads are created with the value of `Normal`, but you can change the <xref:System.Threading.Thread.Priority%2A> property to any value in the <xref:System.Threading.ThreadPriority> enumeration.</span></span>  
  
 <span data-ttu-id="d176c-159">参照してください<xref:System.Threading.ThreadPriority>さまざまなスレッドの優先順位の詳細について</xref:System.Threading.ThreadPriority>。</span><span class="sxs-lookup"><span data-stu-id="d176c-159">See <xref:System.Threading.ThreadPriority> for a detailed description of the various thread priorities.</span></span>  
  
## <a name="foreground-and-background-threads"></a><span data-ttu-id="d176c-160">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="d176c-160">Foreground and Background Threads</span></span>  
 <span data-ttu-id="d176c-161">A*フォア グラウンド スレッド*一方、無期限に実行される、*スレッドが、*最後のフォア グラウンド スレッドが停止するとすぐに停止します。</span><span class="sxs-lookup"><span data-stu-id="d176c-161">A *foreground thread* runs indefinitely, whereas a *background thread* stops as soon as the last foreground thread has stopped.</span></span> <span data-ttu-id="d176c-162">使用することができます、<xref:System.Threading.Thread.IsBackground%2A>確認またはスレッドのバック グラウンドの状態を変更するプロパティ</xref:System.Threading.Thread.IsBackground%2A>。</span><span class="sxs-lookup"><span data-stu-id="d176c-162">You can use the <xref:System.Threading.Thread.IsBackground%2A> property to determine or change the background status of a thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d176c-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="d176c-163">See Also</span></span>  
 <span data-ttu-id="d176c-164"><xref:System.Threading.Thread></xref:System.Threading.Thread></span><span class="sxs-lookup"><span data-stu-id="d176c-164"><xref:System.Threading.Thread></span></span>   
<span data-ttu-id="d176c-165"> [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="d176c-165"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
<span data-ttu-id="d176c-166"> [パラメーターと戻り値のマルチ スレッド プロシージャ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d176c-166"> [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) </span></span>  
<span data-ttu-id="d176c-167"> [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)</span><span class="sxs-lookup"><span data-stu-id="d176c-167"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)</span></span>

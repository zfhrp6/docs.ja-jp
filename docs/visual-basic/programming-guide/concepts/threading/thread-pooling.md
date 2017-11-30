---
title: "スレッド プール (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="eadc4-102">スレッド プール (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eadc4-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="eadc4-103">"*スレッド プール*" とは、複数のタスクをバックグラウンドで実行するときに使用できるスレッドのコレクションです </span><span class="sxs-lookup"><span data-stu-id="eadc4-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="eadc4-104">(を参照してください[スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)背景情報についてはします)。これにより、プライマリ スレッドは他のタスクを非同期的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="eadc4-105">スレッド プールは、サーバー アプリケーションでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="eadc4-106">受信した要求がそれぞれスレッド プールのスレッドに割り当てられるため、プライマリ スレッドを占有したり、後続の要求の処理を遅延させたりすることなく、非同期的に処理できます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="eadc4-107">タスクを完了したプール内のスレッドは待機スレッドのキューに戻り、再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eadc4-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="eadc4-108">これにより、タスクごとに新しいスレッドを作成するという負荷がアプリケーションにかからなくなります。</span><span class="sxs-lookup"><span data-stu-id="eadc4-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="eadc4-109">スレッド プールには、通常、最大数のスレッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eadc4-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="eadc4-110">すべてのスレッドがビジーの場合、追加のタスクは、スレッドが使用可能になってタスクを処理できるようになるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="eadc4-111">独自のスレッド プールを実装することもできますが、.NET Framework が <xref:System.Threading.ThreadPool> クラスを通じて提供するスレッド プールを使用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="eadc4-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="eadc4-112">スレッド プールでを呼び出す、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>を実行する手順については、デリゲートにメソッドおよび Visual Basic、スレッドを作成して、プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="eadc4-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="eadc4-113">スレッド プールの例</span><span class="sxs-lookup"><span data-stu-id="eadc4-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="eadc4-114">次の例は、スレッド プールを使用して、タスクをいくつか開始する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="eadc4-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 <span data-ttu-id="eadc4-115">スレッド プールのメリットの 1 つとして、引数を状態オブジェクトでタスク プロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="eadc4-116">呼び出し先のプロシージャが複数の引数を必要とする場合は、構造体またはクラスのインスタンスを `Object` データ型にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="eadc4-117">スレッド プールのパラメーターと戻り値</span><span class="sxs-lookup"><span data-stu-id="eadc4-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="eadc4-118">スレッド プールのスレッドから値が返る際は、直接返されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="eadc4-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="eadc4-119">スレッド プールのキューに追加できるプロシージャは `Sub` プロシージャだけのため、関数呼び出しから値を返すという標準的な方法が使用できません。</span><span class="sxs-lookup"><span data-stu-id="eadc4-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="eadc4-120">一方向のパラメーターを指定してパラメーター、戻り値の値をラップすることによって値があり、メソッドのラッパー内で説明されているクラスを返す[パラメーターとマルチ スレッド プロシージャ (Visual Basic) の値を返す](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="eadc4-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="eadc4-121">より簡単にパラメーターと戻り値を提供する方法として、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="eadc4-122">この変数を使用して、クラスのインスタンスへの参照を渡すと、スレッド プールのスレッドでインスタンスのメンバーを変更し、これを戻り値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="eadc4-123">値によって渡される変数の参照先オブジェクトを変更できるということがわかりにくいかもしれません。</span><span class="sxs-lookup"><span data-stu-id="eadc4-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="eadc4-124">これが可能なのは、値によって渡されるのがオブジェクト参照のみであるためです。</span><span class="sxs-lookup"><span data-stu-id="eadc4-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="eadc4-125">オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、その変更が実際のクラス インスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="eadc4-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="eadc4-126">構造体を使用して、状態オブジェクト内の値を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="eadc4-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="eadc4-127">構造体は値型であるため、非同期プロセスで行われた変更によって元の構造体のメンバーが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="eadc4-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="eadc4-128">構造体は、戻り値を必要としないときにパラメーターを提供するために使用します。</span><span class="sxs-lookup"><span data-stu-id="eadc4-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadc4-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="eadc4-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="eadc4-130">方法: スレッド プールを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eadc4-130">How to: Use a Thread Pool (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="eadc4-131">スレッド処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eadc4-131">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="eadc4-132">マルチスレッド アプリケーション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eadc4-132">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="eadc4-133">スレッドの同期 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eadc4-133">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)

---
title: スレッド プール (C#)
ms.date: 07/20/2015
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
ms.openlocfilehash: 42e1dcedc1897dc82bbd13f12882cbef6a5da4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="thread-pooling-c"></a><span data-ttu-id="99c32-102">スレッド プール (C#)</span><span class="sxs-lookup"><span data-stu-id="99c32-102">Thread Pooling (C#)</span></span>
<span data-ttu-id="99c32-103">"*スレッド プール*" とは、複数のタスクをバックグラウンドで実行するときに使用できるスレッドのコレクションです </span><span class="sxs-lookup"><span data-stu-id="99c32-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="99c32-104">(詳細については、「[スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)」を参照してください)。これにより、プライマリ スレッドは他のタスクを非同期的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="99c32-104">(See [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="99c32-105">スレッド プールは、サーバー アプリケーションでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="99c32-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="99c32-106">受信した要求がそれぞれスレッド プールのスレッドに割り当てられるため、プライマリ スレッドを占有したり、後続の要求の処理を遅延させたりすることなく、非同期的に処理できます。</span><span class="sxs-lookup"><span data-stu-id="99c32-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="99c32-107">タスクを完了したプール内のスレッドは待機スレッドのキューに戻り、再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="99c32-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="99c32-108">これにより、タスクごとに新しいスレッドを作成するという負荷がアプリケーションにかからなくなります。</span><span class="sxs-lookup"><span data-stu-id="99c32-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="99c32-109">スレッド プールには、通常、最大数のスレッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="99c32-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="99c32-110">すべてのスレッドがビジーの場合、追加のタスクは、スレッドが使用可能になってタスクを処理できるようになるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="99c32-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="99c32-111">独自のスレッド プールを実装することもできますが、.NET Framework が <xref:System.Threading.ThreadPool> クラスを通じて提供するスレッド プールを使用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="99c32-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="99c32-112">スレッド プールを使用する場合、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> メソッドを呼び出すときに実行対象のプロシージャのデリゲートを指定すると、C# によってスレッドが作成され、プロシージャが実行されます。</span><span class="sxs-lookup"><span data-stu-id="99c32-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and C# creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="99c32-113">スレッド プールの例</span><span class="sxs-lookup"><span data-stu-id="99c32-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="99c32-114">次の例は、スレッド プールを使用して、タスクをいくつか開始する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="99c32-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 <span data-ttu-id="99c32-115">スレッド プールのメリットの 1 つとして、引数を状態オブジェクトでタスク プロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="99c32-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="99c32-116">呼び出し先のプロシージャが複数の引数を必要とする場合は、構造体またはクラスのインスタンスを `Object` データ型にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="99c32-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="99c32-117">スレッド プールのパラメーターと戻り値</span><span class="sxs-lookup"><span data-stu-id="99c32-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="99c32-118">スレッド プールのスレッドから値が返る際は、直接返されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="99c32-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="99c32-119">スレッド プールのキューに追加できるプロシージャは `Sub` プロシージャだけのため、関数呼び出しから値を返すという標準的な方法が使用できません。</span><span class="sxs-lookup"><span data-stu-id="99c32-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="99c32-120">パラメーターと戻り値を提供する方法の 1 つとして、パラメーター、戻り値、メソッドをラッパー クラスにラップする方法があります。これについては、「[マルチスレッド プロシージャのパラメーターと戻り値 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99c32-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="99c32-121">より簡単にパラメーターと戻り値を提供する方法として、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="99c32-121">An easier way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="99c32-122">この変数を使用して、クラスのインスタンスへの参照を渡すと、スレッド プールのスレッドでインスタンスのメンバーを変更し、これを戻り値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="99c32-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="99c32-123">値によって渡される変数の参照先オブジェクトを変更できるということがわかりにくいかもしれません。</span><span class="sxs-lookup"><span data-stu-id="99c32-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="99c32-124">これが可能なのは、値によって渡されるのがオブジェクト参照のみであるためです。</span><span class="sxs-lookup"><span data-stu-id="99c32-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="99c32-125">オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、その変更が実際のクラス インスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="99c32-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="99c32-126">構造体を使用して、状態オブジェクト内の値を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="99c32-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="99c32-127">構造体は値型であるため、非同期プロセスで行われた変更によって元の構造体のメンバーが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="99c32-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="99c32-128">構造体は、戻り値を必要としないときにパラメーターを提供するために使用します。</span><span class="sxs-lookup"><span data-stu-id="99c32-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c32-129">参照</span><span class="sxs-lookup"><span data-stu-id="99c32-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="99c32-130">方法: スレッド プールを使用する (C#)</span><span class="sxs-lookup"><span data-stu-id="99c32-130">How to: Use a Thread Pool (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="99c32-131">スレッド処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="99c32-131">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="99c32-132">マルチスレッド アプリケーション (C#)</span><span class="sxs-lookup"><span data-stu-id="99c32-132">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="99c32-133">スレッドの同期 (C#)</span><span class="sxs-lookup"><span data-stu-id="99c32-133">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)

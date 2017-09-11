---
title: "スレッド プール (C#)"
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
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2f8e5a2d7a83dc6fef72ef87b4003ae49656d8f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="thread-pooling-c"></a><span data-ttu-id="05917-102">スレッド プール (C#)</span><span class="sxs-lookup"><span data-stu-id="05917-102">Thread Pooling (C#)</span></span>
<span data-ttu-id="05917-103">"*スレッド プール*" とは、複数のタスクをバックグラウンドで実行するときに使用できるスレッドのコレクションです </span><span class="sxs-lookup"><span data-stu-id="05917-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="05917-104">(詳細については、「[スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)」を参照してください)。これにより、プライマリ スレッドは他のタスクを非同期的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="05917-104">(See [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="05917-105">スレッド プールは、サーバー アプリケーションでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="05917-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="05917-106">受信した要求がそれぞれスレッド プールのスレッドに割り当てられるため、プライマリ スレッドを占有したり、後続の要求の処理を遅延させたりすることなく、非同期的に処理できます。</span><span class="sxs-lookup"><span data-stu-id="05917-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="05917-107">タスクを完了したプール内のスレッドは待機スレッドのキューに戻り、再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="05917-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="05917-108">これにより、タスクごとに新しいスレッドを作成するという負荷がアプリケーションにかからなくなります。</span><span class="sxs-lookup"><span data-stu-id="05917-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="05917-109">スレッド プールには、通常、最大数のスレッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05917-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="05917-110">すべてのスレッドがビジーの場合、追加のタスクは、スレッドが使用可能になってタスクを処理できるようになるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="05917-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="05917-111">独自のスレッド プールを実装することもできますが、.NET Framework が <xref:System.Threading.ThreadPool> クラスを通じて提供するスレッド プールを使用する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="05917-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="05917-112">スレッド プールを使用する場合、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> メソッドを呼び出すときに実行対象のプロシージャのデリゲートを指定すると、C# によってスレッドが作成され、プロシージャが実行されます。</span><span class="sxs-lookup"><span data-stu-id="05917-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> method with a delegate for the procedure you want to run, and C# creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="05917-113">スレッド プールの例</span><span class="sxs-lookup"><span data-stu-id="05917-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="05917-114">次の例は、スレッド プールを使用して、タスクをいくつか開始する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="05917-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="05917-115">スレッド プールのメリットの 1 つとして、引数を状態オブジェクトでタスク プロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="05917-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="05917-116">呼び出し先のプロシージャが複数の引数を必要とする場合は、構造体またはクラスのインスタンスを `Object` データ型にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="05917-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="05917-117">スレッド プールのパラメーターと戻り値</span><span class="sxs-lookup"><span data-stu-id="05917-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="05917-118">スレッド プールのスレッドから値が返る際は、直接返されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="05917-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="05917-119">スレッド プールのキューに追加できるプロシージャは `Sub` プロシージャだけのため、関数呼び出しから値を返すという標準的な方法が使用できません。</span><span class="sxs-lookup"><span data-stu-id="05917-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="05917-120">パラメーターと戻り値を提供する方法の 1 つとして、パラメーター、戻り値、メソッドをラッパー クラスにラップする方法があります。これについては、「[マルチスレッド プロシージャのパラメーターと戻り値 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05917-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="05917-121">より簡単にパラメーターと戻り値を提供する方法として、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="05917-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="05917-122">この変数を使用して、クラスのインスタンスへの参照を渡すと、スレッド プールのスレッドでインスタンスのメンバーを変更し、これを戻り値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="05917-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="05917-123">値によって渡される変数の参照先オブジェクトを変更できるということがわかりにくいかもしれません。</span><span class="sxs-lookup"><span data-stu-id="05917-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="05917-124">これが可能なのは、値によって渡されるのがオブジェクト参照のみであるためです。</span><span class="sxs-lookup"><span data-stu-id="05917-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="05917-125">オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、その変更が実際のクラス インスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="05917-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="05917-126">構造体を使用して、状態オブジェクト内の値を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="05917-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="05917-127">構造体は値型であるため、非同期プロセスで行われた変更によって元の構造体のメンバーが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="05917-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="05917-128">構造体は、戻り値を必要としないときにパラメーターを提供するために使用します。</span><span class="sxs-lookup"><span data-stu-id="05917-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05917-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="05917-129">See Also</span></span>  
 <span data-ttu-id="05917-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="05917-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="05917-131"><xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="05917-131"><xref:System.Threading></span></span>   
 <span data-ttu-id="05917-132"><xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="05917-132"><xref:System.Threading.ThreadPool></span></span>   
 <span data-ttu-id="05917-133">[方法: スレッド プールを使用する (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span><span class="sxs-lookup"><span data-stu-id="05917-133">[How to: Use a Thread Pool (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span></span>  
 <span data-ttu-id="05917-134">[スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="05917-134">[Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) </span></span>  
 <span data-ttu-id="05917-135">[マルチスレッド アプリケーション (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="05917-135">[Multithreaded Applications (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
 [<span data-ttu-id="05917-136">スレッドの同期 (C#)</span><span class="sxs-lookup"><span data-stu-id="05917-136">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)


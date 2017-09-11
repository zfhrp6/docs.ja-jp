---
title: "スレッド プール (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eea7c94dffe525bb36c677bf3414f25ed0210074
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="1bb0d-102">スレッド プール (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bb0d-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="1bb0d-103">A*スレッド プール*をバック グラウンドでいくつかのタスクを実行するために使用できるスレッドのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="1bb0d-104">(を参照してください[スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)背景情報です)。これにより、プライマリ スレッドを自由に他のタスクを非同期的に実行します。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="1bb0d-105">スレッド プールは、サーバー アプリケーションで多く採用されています。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="1bb0d-106">受信された各要求は、プライマリ スレッドを停止したり、後続の要求の処理を遅らせることがなく、要求が、非同期的に処理できるように、スレッド プールからスレッドに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="1bb0d-107">プール内のスレッドには、そのタスクが完了すると、待機中のスレッドのキューに返される、使用できます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="1bb0d-108">この再利用により、タスクごとに新しいスレッドを作成するコストを回避できます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="1bb0d-109">スレッド プールには、通常、スレッドの最大数があります。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="1bb0d-110">すべてのスレッドがビジーである場合、その他のタスクは、スレッドが公開されたらすぐに処理できるようになるまでキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="1bb0d-111">独自のスレッド プールを実装することができますが、<xref:System.Threading.ThreadPool>クラス</xref:System.Threading.ThreadPool>を .NET Framework で提供されるスレッド プールを使用する方が簡単</span><span class="sxs-lookup"><span data-stu-id="1bb0d-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="1bb0d-112">呼び出すスレッドがプールを使用した、 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>、実行する手順については、デリゲートを使用してメソッド、および Visual Basic、スレッドを作成して、プロシージャを実行します</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="1bb0d-113">スレッド プールの例</span><span class="sxs-lookup"><span data-stu-id="1bb0d-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="1bb0d-114">次の例では、いくつかのタスクを開始するプールのスレッドを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
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
  
 <span data-ttu-id="1bb0d-115">スレッド プールの利点の&1; つは、引数、タスクの手順に状態のオブジェクトに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="1bb0d-116">呼び出しているプロシージャは、1 つ以上の引数を必要とする場合は、構造体またはにクラスのインスタンスをキャストすることができます、`Object`データ型。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="1bb0d-117">スレッド プールのパラメーターと戻り値</span><span class="sxs-lookup"><span data-stu-id="1bb0d-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="1bb0d-118">スレッド プールのスレッドからの戻り値は、簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="1bb0d-119">関数呼び出しからの戻り値の標準的な方法は許可されません`Sub`プロシージャは、スレッド プールにキューに配置するプロシージャの唯一の種類。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="1bb0d-120">一方向のパラメーターを指定し、切断したパラメーター、戻り値をラップすることによって値があり、メソッドのラッパー内クラス」の説明に従って[パラメーターとマルチ スレッド プロシージャ (Visual Basic) の値を返す](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="1bb0d-121">容易パラメーターを指定して、戻り値は省略可能なを使用して`ByVal`の状態のオブジェクト変数、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>メソッド</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="1bb0d-122">クラスのインスタンスへの参照を渡すためにこの変数を使用する場合は、インスタンスのメンバーをスレッド プールのスレッドによって変更され、戻り値として使用します。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="1bb0d-123">最初に、わかりにくいかもしれません値によって渡される変数が参照するオブジェクトを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="1bb0d-124">オブジェクトの参照だけが値によって渡されるために、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="1bb0d-125">オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、変更は、実際のクラスのインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="1bb0d-126">構造体は、状態オブジェクトの中の値を返すには使用できません。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="1bb0d-127">構造体は値型であるために、非同期プロセスによって加えられる変更は元の構造体のメンバーも変わりません。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="1bb0d-128">構造体を使用すると、戻り値が不要なときに、パラメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="1bb0d-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb0d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bb0d-129">See Also</span></span>  
 <span data-ttu-id="1bb0d-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="1bb0d-130"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="1bb0d-131"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="1bb0d-131"><xref:System.Threading></span></span>   
 <span data-ttu-id="1bb0d-132"><xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="1bb0d-132"><xref:System.Threading.ThreadPool></span></span>   
<span data-ttu-id="1bb0d-133"> [方法: スレッド プール (Visual Basic) を使用します。](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span><span class="sxs-lookup"><span data-stu-id="1bb0d-133"> [How to: Use a Thread Pool (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md) </span></span>  
<span data-ttu-id="1bb0d-134"> [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="1bb0d-134"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="1bb0d-135"> [マルチ スレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="1bb0d-135"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="1bb0d-136"> [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span><span class="sxs-lookup"><span data-stu-id="1bb0d-136"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)</span></span>

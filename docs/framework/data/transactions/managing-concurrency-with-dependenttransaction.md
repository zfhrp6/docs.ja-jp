---
title: "DependentTransaction による同時実行の管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cb0fa7f328b158613836e6ab20bd33545dc3a5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="50feb-102">DependentTransaction による同時実行の管理</span><span class="sxs-lookup"><span data-stu-id="50feb-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="50feb-103"><xref:System.Transactions.Transaction> オブジェクトは、<xref:System.Transactions.Transaction.DependentClone%2A> メソッドを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="50feb-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="50feb-104">このオブジェクトの唯一の目的は、他のコード (ワーカー スレッドなど) でトランザクションの処理を実行している間、トランザクションをコミットできないように保証することです。</span><span class="sxs-lookup"><span data-stu-id="50feb-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="50feb-105">複製されたトランザクション内の処理が完了してコミットの準備が整うと、<xref:System.Transactions.DependentTransaction.Complete%2A> メソッドを使用して、そのトランザクションの作成者に通知できます。</span><span class="sxs-lookup"><span data-stu-id="50feb-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="50feb-106">これにより、データの一貫性と正確性を保持できます。</span><span class="sxs-lookup"><span data-stu-id="50feb-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="50feb-107"><xref:System.Transactions.DependentTransaction> クラスは、非同期タスク間の同時実行の管理にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="50feb-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="50feb-108">この場合は、トランザクションに依存している複製が独自のタスクの処理を行う間、親が任意のコードの実行を継続できます。</span><span class="sxs-lookup"><span data-stu-id="50feb-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="50feb-109">つまり、依存している複製が完了するまで親の実行がブロックされることはありません。</span><span class="sxs-lookup"><span data-stu-id="50feb-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="50feb-110">トランザクションに依存している複製の作成</span><span class="sxs-lookup"><span data-stu-id="50feb-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="50feb-111">依存トランザクションを作成するには、<xref:System.Transactions.Transaction.DependentClone%2A> メソッドを呼び出し、パラメーターとして <xref:System.Transactions.DependentCloneOption> 列挙体を渡します。</span><span class="sxs-lookup"><span data-stu-id="50feb-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="50feb-112">このパラメーターは、トランザクションに依存している複製が `Commit` メソッドを呼び出してトランザクションのコミットの準備が整ったことを示す前に、親トランザクションで <xref:System.Transactions.DependentTransaction.Complete%2A> が呼び出された場合のトランザクションの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="50feb-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="50feb-113">このパラメーターで有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="50feb-113">The following values are valid for this parameter:</span></span>  
  
-   <span data-ttu-id="50feb-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> は、親トランザクションがタイムアウトするまで、またはすべての依存トランザクションで完了を示す <xref:System.Transactions.DependentTransaction.Complete%2A> が呼び出されるまで、親トランザクションのコミット プロセスをブロックする依存トランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="50feb-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="50feb-115">これは、依存トランザクションが完了するまで、クライアントが親トランザクションのコミットを望まない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="50feb-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="50feb-116">親トランザクションが依存トランザクションより前に処理を完了して <xref:System.Transactions.CommittableTransaction.Commit%2A> を呼び出した場合、すべての依存トランザクションが <xref:System.Transactions.DependentTransaction.Complete%2A> を呼び出すまで、コミット プロセスはブロックされ、そのトランザクションで追加処理を実行し、新しい参加リストを作成できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="50feb-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="50feb-117">すべての依存トランザクションの処理が完了し、<xref:System.Transactions.DependentTransaction.Complete%2A> を呼び出すとすぐに、トランザクションのコミット プロセスが開始します。</span><span class="sxs-lookup"><span data-stu-id="50feb-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
-   <span data-ttu-id="50feb-118">一方、<xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> では、<xref:System.Transactions.CommittableTransaction.Commit%2A> が呼び出される前に親トランザクションで <xref:System.Transactions.DependentTransaction.Complete%2A> が呼び出された場合、自動的に中止する依存トランザクションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="50feb-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="50feb-119">この場合、依存トランザクションで行われたすべての処理は、1 つのトランザクションの有効期間内はそのまま変更されず、その一部でもコミットすることはできません。</span><span class="sxs-lookup"><span data-stu-id="50feb-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="50feb-120">アプリケーションが依存トランザクションでその処理を完了した場合、<xref:System.Transactions.DependentTransaction.Complete%2A> メソッドを 1 回だけ呼び出す必要があります。それ以外の場合は、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="50feb-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="50feb-121">この呼び出しを行った後は、トランザクションで追加作業を行わないでください。例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="50feb-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="50feb-122">次のコード例では、依存トランザクションの複製を作成してワーカー スレッドに渡すことにより、2 つの同時実行タスクを管理する依存トランザクションを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="50feb-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);   
    }  
  
    public void ThreadMethod(object transaction)   
    {   
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);   
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */   
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();   
             dependentTransaction.Dispose();   
        }  
    }  
  
//Client code   
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;      
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="50feb-123">このクライアント コードは、アンビエント トランザクションの設定も行うトランザクション スコープを作成します。</span><span class="sxs-lookup"><span data-stu-id="50feb-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="50feb-124">アンビエント トランザクションをワーカー スレッドに渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="50feb-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="50feb-125">その代わりに、現在のトランザクションで <xref:System.Transactions.Transaction.DependentClone%2A> メソッドを呼び出すことにより、現在の (アンビエント) トランザクションを複製し、依存トランザクションをワーカー スレッドに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="50feb-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="50feb-126">`ThreadMethod` メソッドは、新しいスレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="50feb-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="50feb-127">クライアントは新しいスレッドを開始し、`ThreadMethod` パラメーターとして依存トランザクションを渡します。</span><span class="sxs-lookup"><span data-stu-id="50feb-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="50feb-128">依存トランザクションは <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> により作成されるため、2 番目のスレッド上ですべてのトランザクションの処理が完了し、依存トランザクションで <xref:System.Transactions.DependentTransaction.Complete%2A> が呼び出されるまで、トランザクションがコミットされないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="50feb-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="50feb-129">つまり、クライアントのスコープが終了した場合 (、最後のトランザクション オブジェクトを破棄しようとすると、**を使用して**ステートメント) スレッドの新しい呼び出しの前に<xref:System.Transactions.DependentTransaction.Complete%2A>まで依存のトランザクションで、クライアントコードをブロック<xref:System.Transactions.DependentTransaction.Complete%2A>依存ファイルで呼び出されるとします。</span><span class="sxs-lookup"><span data-stu-id="50feb-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the **using** statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="50feb-130">その後、トランザクションはコミットまたは中止の処理を完了できます。</span><span class="sxs-lookup"><span data-stu-id="50feb-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="50feb-131">同時実行に関する問題</span><span class="sxs-lookup"><span data-stu-id="50feb-131">Concurrency Issues</span></span>  
 <span data-ttu-id="50feb-132">同時実行に関して、<xref:System.Transactions.DependentTransaction> クラスを使用する場合に注意が必要な問題がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="50feb-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
-   <span data-ttu-id="50feb-133">ワーカー スレッドがトランザクションをロールバックし、親がトランザクションのコミットを試みた場合、<xref:System.Transactions.TransactionAbortedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="50feb-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
-   <span data-ttu-id="50feb-134">トランザクション内の各ワーカー スレッドについて、トランザクションに依存している複製を新しく作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50feb-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="50feb-135">同一の依存している複製を複数のスレッドに渡さないでください。その複製に対して <xref:System.Transactions.DependentTransaction.Complete%2A> を呼び出すことができるのは、1 つのスレッドのみであるためです。</span><span class="sxs-lookup"><span data-stu-id="50feb-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
-   <span data-ttu-id="50feb-136">ワーカー スレッドが新しいワーカー スレッドを生成する場合、依存している複製から依存している複製を作成し、それを新しいスレッドに渡してください。</span><span class="sxs-lookup"><span data-stu-id="50feb-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50feb-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="50feb-137">See Also</span></span>  
 <xref:System.Transactions.DependentTransaction>

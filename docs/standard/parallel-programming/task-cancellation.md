---
title: "タスクのキャンセル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 46e202d4f5cafdef44f908d44f9362127bc6eb1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="task-cancellation"></a><span data-ttu-id="b53c0-102">タスクのキャンセル</span><span class="sxs-lookup"><span data-stu-id="b53c0-102">Task Cancellation</span></span>
<span data-ttu-id="b53c0-103"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラスおよび <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> クラスは、.NET Framework のキャンセル トークンを使用したキャンセルをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b53c0-103">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> classes support cancellation through the use of cancellation tokens in the .NET Framework.</span></span> <span data-ttu-id="b53c0-104">詳細については、「[マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b53c0-104">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="b53c0-105">Task クラスのキャンセル処理では、キャンセル可能な操作を表すユーザー デリゲートと、キャンセルを要求したコードが連携します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-105">In the Task classes, cancellation involves cooperation between the user delegate, which represents a cancelable operation and the code that requested the cancellation.</span></span>  <span data-ttu-id="b53c0-106">キャンセル処理が正常に実行されるためには、要求コードが <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> メソッドを呼び出し、ユーザー デリゲートが操作を適時に終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b53c0-106">A successful cancellation involves the requesting code calling the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method, and the user delegate terminating the operation in a timely manner.</span></span> <span data-ttu-id="b53c0-107">次のオプションのいずれかを使用して操作を終了できます。</span><span class="sxs-lookup"><span data-stu-id="b53c0-107">You can terminate the operation by using one of these options:</span></span>  
  
-   <span data-ttu-id="b53c0-108">デリゲートから戻ります。</span><span class="sxs-lookup"><span data-stu-id="b53c0-108">By simply returning from the delegate.</span></span> <span data-ttu-id="b53c0-109">多くの場合、この処理で十分ですが、この方法で取り消されたタスク インスタンスは、<xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> 状態ではなく、<xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> 状態に遷移します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-109">In many scenarios this is sufficient; however, a task instance that is canceled in this way transitions to the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> state, not to the <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> state.</span></span>  
  
-   <span data-ttu-id="b53c0-110"><xref:System.OperationCanceledException> をスローし、これをキャンセルが要求されたトークンに渡します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-110">By throwing a <xref:System.OperationCanceledException> and passing it the token on which cancellation was requested.</span></span> <span data-ttu-id="b53c0-111">これを行うには、 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> メソッドを使用する方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b53c0-111">The preferred way to do this is to use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="b53c0-112">この方法で取り消されたタスクは Canceled 状態に遷移し、タスクがキャンセル要求に応答したことを確認するために呼び出し元のコードによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="b53c0-112">A task that is canceled in this way transitions to the Canceled state, which the calling code can use to verify that the task responded to its cancellation request.</span></span>  
  
 <span data-ttu-id="b53c0-113">次の例は、例外をスローするタスクのキャンセルの基本的なパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="b53c0-113">The following example shows the basic pattern for task cancellation that throws the exception.</span></span> <span data-ttu-id="b53c0-114">ユーザー デリゲートとタスク インスタンス自体にトークンが渡されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b53c0-114">Note that the token is passed to the user delegate and to the task instance itself.</span></span>  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 <span data-ttu-id="b53c0-115">より詳細な例については、「[方法: タスクとその子を取り消す](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b53c0-115">For a more complete example, see [How to: Cancel a Task and Its Children](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).</span></span>  
  
 <span data-ttu-id="b53c0-116">タスク インスタンスがユーザー コードによってスローされた <xref:System.OperationCanceledException> を確認した場合は、例外のトークンと関連付けられたトークン (タスクを作成した API に渡されたトークン) とを比較します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-116">When a task instance observes an <xref:System.OperationCanceledException> thrown by user code, it compares the exception's token to its associated token (the one that was passed to the API that created the Task).</span></span> <span data-ttu-id="b53c0-117">これらのトークンが同一であり、トークンの <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティから true が返されると、タスクはこれをキャンセルの受信確認と解釈し、Canceled 状態に遷移します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-117">If they are the same and the token's <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property returns true, the task interprets this as acknowledging cancellation and transitions to the Canceled state.</span></span> <span data-ttu-id="b53c0-118"><xref:System.Threading.Tasks.Task.Wait%2A> メソッドまたは <xref:System.Threading.Tasks.Task.WaitAll%2A> メソッドを使用してタスクを待機しない場合、タスクの状態は <xref:System.Threading.Tasks.TaskStatus.Canceled>に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b53c0-118">If you do not use a <xref:System.Threading.Tasks.Task.Wait%2A> or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the task, then the task just sets its status to <xref:System.Threading.Tasks.TaskStatus.Canceled>.</span></span>  
  
 <span data-ttu-id="b53c0-119">タスクが Canceled 状態に遷移するのを待っていると、<xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> 例外 (<xref:System.AggregateException> 例外にラップされている) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b53c0-119">If you are waiting on a Task that transitions to the Canceled state, a <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> exception (wrapped in an <xref:System.AggregateException> exception) is thrown.</span></span> <span data-ttu-id="b53c0-120">この例外は、障害のある状況ではなく、正常なキャンセル処理を示すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b53c0-120">Note that this exception indicates successful cancellation instead of a faulty situation.</span></span> <span data-ttu-id="b53c0-121">このため、タスクの <xref:System.Threading.Tasks.Task.Exception%2A> プロパティは `null`を返します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-121">Therefore, the task's <xref:System.Threading.Tasks.Task.Exception%2A> property returns `null`.</span></span>  
  
 <span data-ttu-id="b53c0-122">トークンの <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティが false を返した場合、または例外のトークンがタスクのトークンと一致しない場合、 <xref:System.OperationCanceledException> は標準の例外のように扱われるため、タスクは Faulted 状態に遷移します。</span><span class="sxs-lookup"><span data-stu-id="b53c0-122">If the token's <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property returns false or if the exception's token does not match the Task's token, the <xref:System.OperationCanceledException> is treated like a normal exception, causing the Task to transition to the Faulted state.</span></span> <span data-ttu-id="b53c0-123">他の例外が存在する場合も、タスクが Faulted 状態に遷移することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b53c0-123">Also note that the presence of other exceptions will also cause the Task to transition to the Faulted state.</span></span> <span data-ttu-id="b53c0-124">完了したタスクの状態は <xref:System.Threading.Tasks.Task.Status%2A> プロパティで取得できます。</span><span class="sxs-lookup"><span data-stu-id="b53c0-124">You can get the status of the completed task in the <xref:System.Threading.Tasks.Task.Status%2A> property.</span></span>  
  
 <span data-ttu-id="b53c0-125">キャンセルが要求された後も、タスクが一部の項目の処理を継続する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b53c0-125">It is possible that a task may continue to process some items after cancellation is requested.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53c0-126">参照</span><span class="sxs-lookup"><span data-stu-id="b53c0-126">See Also</span></span>  
 [<span data-ttu-id="b53c0-127">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="b53c0-127">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 [<span data-ttu-id="b53c0-128">方法: タスクとその子を取り消す</span><span class="sxs-lookup"><span data-stu-id="b53c0-128">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)

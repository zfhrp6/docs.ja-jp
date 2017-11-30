---
title: "バリア (.NET Framework)"
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
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8111cc9f2798ff96be8b128f22a75d21b441178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="barrier-net-framework"></a><span data-ttu-id="9d258-102">バリア (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="9d258-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="9d258-103">A*バリア*ユーザー定義の同期プリミティブを複数のスレッドを有効にする (と呼ばれる*参加者*) フェーズで、アルゴリズムに同時に動作します。</span><span class="sxs-lookup"><span data-stu-id="9d258-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="9d258-104">各参加要素は、コードのバリア ポイントに到達するまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9d258-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="9d258-105">バリアは、作業の 1 つのフェーズの終了を表します。</span><span class="sxs-lookup"><span data-stu-id="9d258-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="9d258-106">参加要素は、バリアに到達すると、すべての参加要素が同じバリアに到達するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="9d258-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="9d258-107">すべての参加要素がバリアに到達した後、必要に応じて、フェーズ後の処理を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="9d258-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="9d258-108">フェーズ後の処理を使用すると、他のすべてのスレッドがブロックされた状態のまま 1 つのスレッドでアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d258-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="9d258-109">アクションが実行された後、参加要素のブロックはすべて解除されます。</span><span class="sxs-lookup"><span data-stu-id="9d258-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="9d258-110">基本的なバリア パターンを次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="9d258-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="9d258-111">完全な例では、次を参照してください。[する方法: バリアの同時実行の操作を同期](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d258-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="9d258-112">参加要素の追加と削除</span><span class="sxs-lookup"><span data-stu-id="9d258-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="9d258-113"><xref:System.Threading.Barrier> を作成するときは、参加要素の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d258-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="9d258-114">また、参加要素は、いつでも動的に追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="9d258-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="9d258-115">たとえば、1 人の参加者は、その一部の問題を解決する場合は、結果、実行を停止し、そのスレッドを呼び出すを格納できます<xref:System.Threading.Barrier.RemoveParticipant%2A>バリアの参加要素の数をデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="9d258-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="9d258-116"><xref:System.Threading.Barrier.AddParticipant%2A> を呼び出して参加要素を追加すると、戻り値によって現在のフェーズ数が示されます。この値は、追加した新しい参加要素の作業を初期化するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="9d258-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="9d258-117">破損したバリア</span><span class="sxs-lookup"><span data-stu-id="9d258-117">Broken Barriers</span></span>  
 <span data-ttu-id="9d258-118">いずれかの参加要素がバリアに到達できない場合、デッドロックが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9d258-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="9d258-119">このようなデッドロックを避けるには、<xref:System.Threading.Barrier.SignalAndWait%2A> メソッドのオーバーロードを使用して、タイムアウト期間とキャンセル トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="9d258-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="9d258-120">すべての参加要素は、次のフェーズに進む前に、これらのオーバーロードから返されるブール値をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="9d258-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="9d258-121">フェーズ後の例外</span><span class="sxs-lookup"><span data-stu-id="9d258-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="9d258-122">フェーズ後のデリゲートから例外がスローされる場合、その例外は <xref:System.Threading.BarrierPostPhaseException> オブジェクトでラップされ、このオブジェクトがすべての参加要素に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="9d258-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="9d258-123">バリアと ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="9d258-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="9d258-124">バリアは、スレッドで複数のフェーズをループ処理する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="9d258-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="9d258-125">コードで作業のフェーズが 1 つか 2 つしか必要ない場合は、次のような何らかの暗黙的な結合と共に <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9d258-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="9d258-126">詳細については、「[継続タスクを使用したタスクの連結](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d258-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d258-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d258-127">See Also</span></span>  
 [<span data-ttu-id="9d258-128">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="9d258-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="9d258-129">方法: バリアを使用して同時実行操作を同期する</span><span class="sxs-lookup"><span data-stu-id="9d258-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)

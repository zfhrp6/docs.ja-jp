---
title: "方法: バリアを使用して同時実行操作を同期する"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="d2ff5-102">方法: バリアを使用して同時実行操作を同期する</span><span class="sxs-lookup"><span data-stu-id="d2ff5-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="d2ff5-103">次の例を使用して同時実行タスクを同期する方法を示しています、<xref:System.Threading.Barrier>です。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2ff5-104">例</span><span class="sxs-lookup"><span data-stu-id="d2ff5-104">Example</span></span>  
 <span data-ttu-id="d2ff5-105">次のプログラムの目的がイテレーション (または段階) の数をカウントするで必要と各検索 を 2 つのスレッドのソリューションの半分同じ段階でランダム化アルゴリズムを使用して、単語をシャッフルします。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="d2ff5-106">各スレッドには、単語がシャッフル後、barrier のフェーズ後の操作は完全な文が正しい単語の順序で表示されたかどうかに表示する 2 つの結果を比較します。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="d2ff5-107">A<xref:System.Threading.Barrier>オブジェクトにより、すべてのタスクがバリアに到達するまで続行できなく並列操作の個々 のタスクです。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="d2ff5-108">並列操作が、段階的で出現し、各フェーズのタスク間の同期が必要と便利です。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="d2ff5-109">この例では、操作を 2 つのフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="d2ff5-110">最初のフェーズでは、各タスクは、データを含むバッファーの場合は、そのセクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="d2ff5-111">各タスクでは、そのセクションの入力が完了したら、タスクは、操作を続行する準備ができたバリアし、待機を通知します。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="d2ff5-112">すべてのタスクは、バリアに通知が、ブロックが解除され、2 番目のフェーズが開始されます。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="d2ff5-113">バリアは、2 番目のフェーズでは、各タスクは、このポイントに生成されたすべてのデータへのアクセスである必要があるために必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="d2ff5-114">バリア、せず、最初のタスクを完了するが入力されていないまだ他のタスクでバッファーからの読み込みしようとする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="d2ff5-115">この方法で各フェーズの任意の数を同期することができます。</span><span class="sxs-lookup"><span data-stu-id="d2ff5-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ff5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2ff5-116">See Also</span></span>  
 [<span data-ttu-id="d2ff5-117">並列プログラミングのデータ構造</span><span class="sxs-lookup"><span data-stu-id="d2ff5-117">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)

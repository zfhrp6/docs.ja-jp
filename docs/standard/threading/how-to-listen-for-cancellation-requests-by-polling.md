---
title: "方法: ポーリングによりキャンセル要求を待機する"
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
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56a927e10cb026814302728a72acb2f32223b29b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="b8156-102">方法: ポーリングによりキャンセル要求を待機する</span><span class="sxs-lookup"><span data-stu-id="b8156-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="b8156-103">次の例は、ユーザー コードで取り消しトークンを定期的にポーリングし、呼び出し元のスレッドから取り消しが要求されているかどうかを確認する 1 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b8156-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="b8156-104">この例では <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 型を使用しますが、<xref:System.Threading.ThreadPool?displayProperty=nameWithType> 型または <xref:System.Threading.Thread?displayProperty=nameWithType> 型で直接作成される非同期操作にも同じパターンが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b8156-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8156-105">例</span><span class="sxs-lookup"><span data-stu-id="b8156-105">Example</span></span>  
 <span data-ttu-id="b8156-106">ポーリングには、ブール <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティの値を定期的に読み取ることができる、ある種のループまたは再帰的なコードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="b8156-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="b8156-107"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 型を使用し、タスクが呼び出し元スレッドで完了するまで待機する場合は、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> スレッドを使用してプロパティを確認し、例外をスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8156-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="b8156-108">このメソッドを使用することで、要求に応じて、正しい例外がスローされるようになります。</span><span class="sxs-lookup"><span data-stu-id="b8156-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="b8156-109"><xref:System.Threading.Tasks.Task> を使用する場合は、<xref:System.OperationCanceledException> を手動でスローするよりもこのスレッドを呼び出す方が効果的です。</span><span class="sxs-lookup"><span data-stu-id="b8156-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="b8156-110">例外をスローする必要がない場合は、単にプロパティを確認し、プロパティが `true` である場合はメソッドから制御を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="b8156-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="b8156-111"><xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> の呼び出しは非常に高速で、ループで大きなオーバーヘッドが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="b8156-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="b8156-112"><xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> を呼び出す場合に、例外をスローするだけではなく、取り消しに応じて他の作業を行う場合は <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティを明示的に確認するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="b8156-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="b8156-113">この例では、コードで実際にプロパティに 2 回アクセスするのがわかります。つまり、明示的なアクセスで 1 回、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> メソッドでもう 1 回です。</span><span class="sxs-lookup"><span data-stu-id="b8156-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="b8156-114">ただし、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティの読み取り操作ではアクセスごとに 1 つの volatile 読み取りのみが含まれるため、パフォーマンスの観点からは二重アクセスは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="b8156-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="b8156-115">それでも、<xref:System.OperationCanceledException> を手動でスローするよりメソッドを呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8156-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8156-116">参照</span><span class="sxs-lookup"><span data-stu-id="b8156-116">See Also</span></span>  
 [<span data-ttu-id="b8156-117">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="b8156-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)

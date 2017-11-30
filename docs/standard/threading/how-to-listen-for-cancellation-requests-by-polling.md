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
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="496dd-102">方法: ポーリングによりキャンセル要求を待機する</span><span class="sxs-lookup"><span data-stu-id="496dd-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="496dd-103">次の例では、ユーザー コードは、呼び出し元のスレッドから取り消しが要求されているかどうかを定期的にキャンセル トークンをポーリングすることを 1 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="496dd-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="496dd-104">この例では、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>によって直接作成された非同期の操作に適用されますが、同様のパターン、<xref:System.Threading.ThreadPool?displayProperty=nameWithType>型または<xref:System.Threading.Thread?displayProperty=nameWithType>型です。</span><span class="sxs-lookup"><span data-stu-id="496dd-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="496dd-105">例</span><span class="sxs-lookup"><span data-stu-id="496dd-105">Example</span></span>  
 <span data-ttu-id="496dd-106">ポーリングが必要、ブール型の値を読み取ることができる定期的にコードをループまたは再帰的な<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="496dd-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="496dd-107">使用している場合、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>の呼び出し元のスレッドが完了するタスクを待機している型にして、使用することができます、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>プロパティを調べて、例外をスローするメソッド。</span><span class="sxs-lookup"><span data-stu-id="496dd-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="496dd-108">このメソッドを使用するは、要求への応答に正しい例外がスローされたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="496dd-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="496dd-109">使用している場合、 <xref:System.Threading.Tasks.Task>、手動でスローよりはこのメソッドを呼び出す、<xref:System.OperationCanceledException>です。</span><span class="sxs-lookup"><span data-stu-id="496dd-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="496dd-110">例外をスローする必要はありませんし、先ほどプロパティをチェックし、プロパティは、メソッドから戻ることができるかどうか`true`です。</span><span class="sxs-lookup"><span data-stu-id="496dd-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="496dd-111">呼び出す<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>は非常に高速とループにかなりのオーバーヘッドを導入していません。</span><span class="sxs-lookup"><span data-stu-id="496dd-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="496dd-112">呼び出す場合<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>、のみを明示的にチェックする必要がある、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティ例外をスローしてだけでなく、取り消しに応答を行うには、その他の作業がある場合。</span><span class="sxs-lookup"><span data-stu-id="496dd-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="496dd-113">この例では、コードは、実際にはプロパティにアクセスします 2 回を確認できます: 明示的なアクセス権とで再度、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="496dd-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="496dd-114">読み取りの act、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティは、1 つだけの揮発性アクセスごとの命令を読み取り、二重のアクセスは、パフォーマンスの観点から重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="496dd-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="496dd-115">手動でをスローするのではなく、メソッドを呼び出して引き続き方が、<xref:System.OperationCanceledException>です。</span><span class="sxs-lookup"><span data-stu-id="496dd-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496dd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="496dd-116">See Also</span></span>  
 [<span data-ttu-id="496dd-117">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="496dd-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)

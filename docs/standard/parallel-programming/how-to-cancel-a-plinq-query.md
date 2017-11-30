---
title: "方法: PLINQ クエリを取り消す"
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
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a><span data-ttu-id="9b329-102">方法: PLINQ クエリを取り消す</span><span class="sxs-lookup"><span data-stu-id="9b329-102">How to: Cancel a PLINQ Query</span></span>
<span data-ttu-id="9b329-103">次の例では、PLINQ クエリを取り消すための 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b329-103">The following examples show two ways to cancel a PLINQ query.</span></span> <span data-ttu-id="9b329-104">最初の例では、データ移動のほとんどの場合で構成されているクエリをキャンセルする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b329-104">The first example shows how to cancel a query that consists mostly of data traversal.</span></span> <span data-ttu-id="9b329-105">2 番目の例では、ユーザー関数は計算コストが高いを含むクエリをキャンセルする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b329-105">The second example shows how to cancel a query that contains a user function that is computationally expensive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b329-106">「マイ コードのみ」を有効にすると、Visual Studio は例外をスローする行で中断し、「で処理されない例外ユーザー コードです」というエラー メッセージを表示</span><span class="sxs-lookup"><span data-stu-id="9b329-106">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="9b329-107">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="9b329-107">This error is benign.</span></span> <span data-ttu-id="9b329-108">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9b329-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="9b329-109">Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。</span><span class="sxs-lookup"><span data-stu-id="9b329-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
>   
>  <span data-ttu-id="9b329-110">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b329-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="9b329-111">高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b329-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b329-112">例</span><span class="sxs-lookup"><span data-stu-id="9b329-112">Example</span></span>  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 <span data-ttu-id="9b329-113">PLINQ フレームワークは、1 つをロールバックできません<xref:System.OperationCanceledException>に、 <xref:System.AggregateException?displayProperty=nameWithType>;<xref:System.OperationCanceledException>個別の catch ブロックで処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b329-113">The PLINQ framework does not roll a single <xref:System.OperationCanceledException> into an <xref:System.AggregateException?displayProperty=nameWithType>; the <xref:System.OperationCanceledException> must be handled in a separate catch block.</span></span> <span data-ttu-id="9b329-114">1 つまたは複数のユーザー デリゲート、OperationCanceledException(externalCT) をスローした場合 (外部を使用して、 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) として定義されていないその他の例外、およびクエリ`AsParallel().WithCancellation(externalCT)`、PLINQ は、1 つを発行し、 <xref:System.OperationCanceledException> (externalCT) ではなく、<xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9b329-114">If one or more user delegates throws an OperationCanceledException(externalCT) (by using an external <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) but no other exception, and the query was defined as `AsParallel().WithCancellation(externalCT)`, then PLINQ will issue a single <xref:System.OperationCanceledException> (externalCT) rather than an <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9b329-115">ただし、1 人のユーザーの委任をスロー、 <xref:System.OperationCanceledException>、別のデリゲートを別の種類の例外をスローし、両方の例外にロールバックされます、<xref:System.AggregateException>です。</span><span class="sxs-lookup"><span data-stu-id="9b329-115">However, if one user delegate throws an <xref:System.OperationCanceledException>, and another delegate throws another exception type, then both exceptions will be rolled into an <xref:System.AggregateException>.</span></span>  
  
 <span data-ttu-id="9b329-116">取り消しの一般的なガイダンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9b329-116">The general guidance on cancellation is as follows:</span></span>  
  
1.  <span data-ttu-id="9b329-117">ユーザー デリゲートの取り消し処理を実行する場合は、外部について PLINQ を通知する必要があります<xref:System.Threading.CancellationToken>をスローし、 <xref:System.OperationCanceledException>(externalCT)。</span><span class="sxs-lookup"><span data-stu-id="9b329-117">If you perform user-delegate cancellation you should inform PLINQ about the external <xref:System.Threading.CancellationToken> and throw an <xref:System.OperationCanceledException>(externalCT).</span></span>  
  
2.  <span data-ttu-id="9b329-118">取り消しが発生したその他の例外がスローされなかった場合は、し、処理、<xref:System.OperationCanceledException>ではなく、<xref:System.AggregateException>です。</span><span class="sxs-lookup"><span data-stu-id="9b329-118">If cancellation occurs and no other exceptions are thrown, then you should handle an <xref:System.OperationCanceledException> rather than an <xref:System.AggregateException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b329-119">例</span><span class="sxs-lookup"><span data-stu-id="9b329-119">Example</span></span>  
 <span data-ttu-id="9b329-120">次の例では、ユーザー コードで計算コストが高い関数があるときに取り消しを処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9b329-120">The following example shows how to handle cancellation when you have a computationally expensive function in user code.</span></span>  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 <span data-ttu-id="9b329-121">ユーザー コードでキャンセルを処理する場合を使用する必要はありません<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>クエリ定義にします。</span><span class="sxs-lookup"><span data-stu-id="9b329-121">When you handle the cancellation in user code, you do not have to use <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> in the query definition.</span></span> <span data-ttu-id="9b329-122">ただし、お勧めするこれを行うため<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>クエリのパフォーマンスに影響を与えませんし、クエリ演算子と、ユーザー コードで処理するキャンセル可能になります。</span><span class="sxs-lookup"><span data-stu-id="9b329-122">However, we recommended that you do this because <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> has no effect on query performance and it enables the cancellation to be handled by query operators and your user code.</span></span>  
  
 <span data-ttu-id="9b329-123">システムの応答性を確保できるように、ことをお勧めミリ秒ごとに 1 回の周囲のキャンセルをチェックします。ただし、10 ミリ秒までの任意の期間の許容と見なされます。</span><span class="sxs-lookup"><span data-stu-id="9b329-123">In order to ensure system responsiveness, we recommend that you check for cancellation around once per millisecond; however, any period up to 10 milliseconds is considered acceptable.</span></span> <span data-ttu-id="9b329-124">この頻度では、コードのパフォーマンスに悪影響を与えるを必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9b329-124">This frequency should not have a negative impact on your code's performance.</span></span>  
  
 <span data-ttu-id="9b329-125">列挙子が破棄されると、コードがクエリ結果を反復処理する foreach (Visual Basic では各) For ループ外分割される場合など、クエリがキャンセルされるが例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="9b329-125">When an enumerator is disposed, for example when code breaks out of a foreach (For Each in Visual Basic) loop that is iterating over query results, then the query is cancelled, but no exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b329-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b329-126">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="9b329-127">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9b329-127">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="9b329-128">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="9b329-128">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)

---
title: "方法: ForEach を使用して BlockingCollection 内の項目を削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b0f0ed30ae5192ed8a8f069d591855857bd2fa49
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="e5a1f-102">方法: ForEach を使用して BlockingCollection 内の項目を削除する</span><span class="sxs-lookup"><span data-stu-id="e5a1f-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="e5a1f-103"><xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> と <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> メソッドを使用して <xref:System.Collections.Concurrent.BlockingCollection%601> から項目を取得するだけでなく、[foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) (Visual Basic では [For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md)) を使用して、追加が完了してコレクションが空になるまで項目を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="e5a1f-104">これは、通常の `foreach` (`For Each`) ループとは異なり、この列挙子が項目を削除することでソース コレクションを変更するので、*変更列挙*または*消費列挙*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a1f-105">例</span><span class="sxs-lookup"><span data-stu-id="e5a1f-105">Example</span></span>  
 <span data-ttu-id="e5a1f-106">次の例は、`foreach` (`For Each`) ループを使用して、<xref:System.Collections.Concurrent.BlockingCollection%601> 内のすべての項目を削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 <span data-ttu-id="e5a1f-107">[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)] [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]</span><span class="sxs-lookup"><span data-stu-id="e5a1f-107">[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)] [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]</span></span>  
  
 <span data-ttu-id="e5a1f-108">この例では、消費スレッドの <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> メソッドで `foreach` ループを使用します。各項目は列挙されるとコレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-108">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="e5a1f-109"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> はコレクション内の項目の最大数を制限します。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-109"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="e5a1f-110">この方法でコレクションを列挙すると、使用できる項目がない場合、またはコレクションが空の場合は、コンシューマー スレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-110">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="e5a1f-111">この例では、プロデューサー スレッドによる項目の追加の方が項目の消費より高速なので、ブロックは問題になりません。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-111">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="e5a1f-112">プロデューサー スレッドによって追加されたのと同じ順序で、項目が列挙されるという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-112">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="e5a1f-113">コレクションを変更せずに列挙するには、<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> メソッドを使用せずに `foreach` (`For Each`) のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-113">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="e5a1f-114">ただし、この種の列挙は特定時点のコレクションのスナップショットを表すことを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-114">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="e5a1f-115">ループの実行中に同時に他のスレッドが項目を追加または削除する場合、ループはコレクションの実際の状態を表さない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5a1f-115">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a1f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5a1f-116">See Also</span></span>  
 <span data-ttu-id="e5a1f-117"><xref:System.Collections.Concurrent?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e5a1f-117"><xref:System.Collections.Concurrent?displayProperty=fullName></span></span>   
 [<span data-ttu-id="e5a1f-118">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="e5a1f-118">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)


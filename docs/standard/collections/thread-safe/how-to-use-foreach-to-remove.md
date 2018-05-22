---
title: '方法: ForEach を使用して BlockingCollection 内の項目を削除する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3337b3e6b181fd39e305e45f96b792d8051a81a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="516df-102">方法: ForEach を使用して BlockingCollection 内の項目を削除する</span><span class="sxs-lookup"><span data-stu-id="516df-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="516df-103"><xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> と <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> メソッドを使用して <xref:System.Collections.Concurrent.BlockingCollection%601> から項目を取得するだけでなく、[foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) (Visual Basic では [For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md)) を使用して、追加が完了してコレクションが空になるまで項目を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="516df-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="516df-104">これは、通常の `foreach` (`For Each`) ループとは異なり、この列挙子が項目を削除することでソース コレクションを変更するので、*変更列挙*または*消費列挙*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="516df-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="516df-105">例</span><span class="sxs-lookup"><span data-stu-id="516df-105">Example</span></span>  
 <span data-ttu-id="516df-106">次の例は、`foreach` (`For Each`) ループを使用して、<xref:System.Collections.Concurrent.BlockingCollection%601> 内のすべての項目を削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="516df-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="516df-107">この例では、消費スレッドの <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> メソッドで `foreach` ループを使用します。各項目は列挙されるとコレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="516df-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="516df-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> はコレクション内の項目の最大数を制限します。</span><span class="sxs-lookup"><span data-stu-id="516df-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="516df-109">この方法でコレクションを列挙すると、使用できる項目がない場合、またはコレクションが空の場合は、コンシューマー スレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="516df-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="516df-110">この例では、プロデューサー スレッドによる項目の追加の方が項目の消費より高速なので、ブロックは問題になりません。</span><span class="sxs-lookup"><span data-stu-id="516df-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="516df-111">プロデューサー スレッドによって追加されたのと同じ順序で、項目が列挙されるという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="516df-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="516df-112">コレクションを変更せずに列挙するには、<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> メソッドを使用せずに `foreach` (`For Each`) のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="516df-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="516df-113">ただし、この種の列挙は特定時点のコレクションのスナップショットを表すことを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="516df-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="516df-114">ループの実行中に同時に他のスレッドが項目を追加または削除する場合、ループはコレクションの実際の状態を表さない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="516df-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="516df-115">参照</span><span class="sxs-lookup"><span data-stu-id="516df-115">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="516df-116">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="516df-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)

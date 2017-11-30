---
title: "方法: PLINQ クエリの順序を制御する"
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="67409-102">方法: PLINQ クエリの順序を制御する</span><span class="sxs-lookup"><span data-stu-id="67409-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="67409-103">これらの例を使用して PLINQ クエリの順序を制御する方法を示して、<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="67409-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="67409-104">これらの例は、使用法を説明するものでは、主に可能性がありますや、可能性がありますいないほど高速で、同等の連続した LINQ to Objects クエリ。</span><span class="sxs-lookup"><span data-stu-id="67409-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67409-105">例</span><span class="sxs-lookup"><span data-stu-id="67409-105">Example</span></span>  
 <span data-ttu-id="67409-106">次の例では、ソース シーケンスの順序を維持します。</span><span class="sxs-lookup"><span data-stu-id="67409-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="67409-107">これは、操作は必要です。など一部のクエリ演算子では、正しい結果を生成するために、順序付けられたソース シーケンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="67409-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="67409-108">例</span><span class="sxs-lookup"><span data-stu-id="67409-108">Example</span></span>  
 <span data-ttu-id="67409-109">クエリ演算子を順序付けるがソース シーケンスが求められるを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="67409-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="67409-110">これらの演算子は、順序なしのシーケンスで機能しますが、予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="67409-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="67409-111">このメソッドを実行する、PLINQDataSample クラス内に貼り付け、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)プロジェクトし、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="67409-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67409-112">例</span><span class="sxs-lookup"><span data-stu-id="67409-112">Example</span></span>  
 <span data-ttu-id="67409-113">次の例では、クエリの最初の部分の順序を維持し、join 句のパフォーマンスを向上する順序を削除し、最終的な結果のシーケンスに順序を適用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="67409-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="67409-114">このメソッドを実行する、PLINQDataSample クラス内に貼り付け、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)プロジェクトし、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="67409-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67409-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="67409-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="67409-116">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="67409-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

---
title: "方法: 並列および順次の LINQ クエリを連結する"
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="ea48e-102">方法: 並列および順次の LINQ クエリを連結する</span><span class="sxs-lookup"><span data-stu-id="ea48e-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="ea48e-103">この例を使用する方法を示しています、 <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLINQ クエリのすべての後続演算子を順番に処理するように指示します。</span><span class="sxs-lookup"><span data-stu-id="ea48e-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="ea48e-104">順次処理は通常、並列処理よりも遅くなりますが、場合によっては必要正しい結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="ea48e-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ea48e-105">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea48e-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ea48e-106">高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。</span><span class="sxs-lookup"><span data-stu-id="ea48e-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea48e-107">例</span><span class="sxs-lookup"><span data-stu-id="ea48e-107">Example</span></span>  
 <span data-ttu-id="ea48e-108">次の例では、1 つのシナリオを示しますを<xref:System.Linq.ParallelEnumerable.AsSequential%2A>つまりする、必要なクエリの前の句で確立された順序を保持します。</span><span class="sxs-lookup"><span data-stu-id="ea48e-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea48e-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ea48e-109">Compiling the Code</span></span>  
 <span data-ttu-id="ea48e-110">コンパイルして、このコードを実行、貼り付けます、 [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md)プロジェクトで、行を追加してからメソッドを呼び出す`Main`、f5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ea48e-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea48e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea48e-111">See Also</span></span>  
 [<span data-ttu-id="ea48e-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ea48e-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

---
title: "方法: カスタムの PLINQ 集約関数を記述する"
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
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="41ed0-102">方法: カスタムの PLINQ 集約関数を記述する</span><span class="sxs-lookup"><span data-stu-id="41ed0-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="41ed0-103">この例を使用する方法を示しています、<xref:System.Linq.ParallelEnumerable.Aggregate%2A>ソース シーケンスに、カスタム集計関数を適用する方法です。</span><span class="sxs-lookup"><span data-stu-id="41ed0-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="41ed0-104">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41ed0-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="41ed0-105">高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。</span><span class="sxs-lookup"><span data-stu-id="41ed0-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41ed0-106">例</span><span class="sxs-lookup"><span data-stu-id="41ed0-106">Example</span></span>  
 <span data-ttu-id="41ed0-107">次の例では、整数のシーケンスの標準偏差を計算します。</span><span class="sxs-lookup"><span data-stu-id="41ed0-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="41ed0-108">この例では、PLINQ 固有の集計の標準クエリ演算子のオーバー ロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="41ed0-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="41ed0-109">このオーバー ロードは余分な<xref:System.Func%603?displayProperty=nameWithType>3 番目の入力パラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="41ed0-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="41ed0-110">このデリゲートは、集計の結果の最終的な計算が実行する前に、すべてのスレッドからの結果を結合します。</span><span class="sxs-lookup"><span data-stu-id="41ed0-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="41ed0-111">この例では合計が追加のすべてのスレッドからです。</span><span class="sxs-lookup"><span data-stu-id="41ed0-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="41ed0-112">ラムダ式の本体は、単一の式の戻り値の場合、<xref:System.Func%602?displayProperty=nameWithType>デリゲートは、式の値。</span><span class="sxs-lookup"><span data-stu-id="41ed0-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ed0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="41ed0-113">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="41ed0-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="41ed0-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)

---
title: "数値のシーケンスの合計の計算"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1735fcd28156b9060c6001eeda6743dfc160d8bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="66234-102">数値のシーケンスの合計の計算</span><span class="sxs-lookup"><span data-stu-id="66234-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="66234-103"><xref:System.Linq.Enumerable.Sum%2A> 演算子を使用すると、シーケンス内の数値の合計を計算できます。</span><span class="sxs-lookup"><span data-stu-id="66234-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="66234-104">`Sum` の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 演算子には、次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="66234-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
-   <span data-ttu-id="66234-105">標準クエリ演算子の集計演算子 `Sum` では、空のシーケンスや null のみを含むシーケンスはゼロに評価されます。</span><span class="sxs-lookup"><span data-stu-id="66234-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="66234-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、SQL のセマンティクスは維持されます。</span><span class="sxs-lookup"><span data-stu-id="66234-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="66234-107">したがって、空のシーケンスまたは null のみを含むシーケンスについては、`Sum` 演算子は 0 ではなく null に評価します。</span><span class="sxs-lookup"><span data-stu-id="66234-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
-   <span data-ttu-id="66234-108">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での集計には、中間結果に対する SQL の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="66234-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="66234-109">32 ビット整数の合計値は 64 ビットの結果を使用して計算されていないと、オーバーフローが発生する、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の翻訳`Sum`です。</span><span class="sxs-lookup"><span data-stu-id="66234-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="66234-110">これは、標準クエリ演算子の実装で、対応するメモリ内シーケンスでオーバーフローが発生しない場合でも起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="66234-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66234-111">例</span><span class="sxs-lookup"><span data-stu-id="66234-111">Example</span></span>  
 <span data-ttu-id="66234-112">`Order` テーブルに含まれるすべての注文の運賃の合計を求める例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66234-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="66234-113">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`64942.6900` です。</span><span class="sxs-lookup"><span data-stu-id="66234-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="66234-114">例</span><span class="sxs-lookup"><span data-stu-id="66234-114">Example</span></span>  
 <span data-ttu-id="66234-115">すべての製品の受注単位の合計を求める例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66234-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="66234-116">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`780` です。</span><span class="sxs-lookup"><span data-stu-id="66234-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="66234-117">`short` には `UnitsOnOrder` 型のオーバーロードがないため、short 型 (`Sum` など) をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="66234-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="66234-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="66234-118">See Also</span></span>  
 [<span data-ttu-id="66234-119">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="66234-119">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="66234-120">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="66234-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

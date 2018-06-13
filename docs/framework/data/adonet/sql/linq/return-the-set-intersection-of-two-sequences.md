---
title: 2 つのシーケンスの積集合の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 9fd2a5dc435829d08594ea3c2f1c129328386250
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358785"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="b3601-102">2 つのシーケンスの積集合の取得</span><span class="sxs-lookup"><span data-stu-id="b3601-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="b3601-103">2 つのシーケンスの積集合を返すには、<xref:System.Linq.Queryable.Intersect%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="b3601-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3601-104">例</span><span class="sxs-lookup"><span data-stu-id="b3601-104">Example</span></span>  
 <span data-ttu-id="b3601-105">この例では、<xref:System.Linq.Queryable.Intersect%2A> を使用して、`Customers` と `Employees` の両方が居住しているすべての国のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="b3601-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="b3601-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Linq.Queryable.Intersect%2A> 演算は集合でのみ適切に定義されます。</span><span class="sxs-lookup"><span data-stu-id="b3601-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="b3601-107">マルチセットのセマンティクスは未定義です。</span><span class="sxs-lookup"><span data-stu-id="b3601-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3601-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3601-108">See Also</span></span>  
 [<span data-ttu-id="b3601-109">クエリの例</span><span class="sxs-lookup"><span data-stu-id="b3601-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="b3601-110">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="b3601-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

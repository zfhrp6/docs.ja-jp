---
title: 'クエリ式の構文例: 並べ替え'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: c4cc8bf1c43c2153cf8031427bb11c4fa45b8f4c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="31401-102">クエリ式の構文例: 並べ替え</span><span class="sxs-lookup"><span data-stu-id="31401-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="31401-103">このトピックの例を使用する方法を示します、`OrderBy`と`OrderByDescending`を照会する方法、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)クエリ式の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="31401-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="31401-104">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="31401-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="31401-105">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="31401-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="31401-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="31401-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="31401-107">例</span><span class="sxs-lookup"><span data-stu-id="31401-107">Example</span></span>  
 <span data-ttu-id="31401-108">次の例では、<xref:System.Linq.Enumerable.OrderBy%2A> を使用して、姓の順に並べ替えられた連絡先の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="31401-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="31401-109">例</span><span class="sxs-lookup"><span data-stu-id="31401-109">Example</span></span>  
 <span data-ttu-id="31401-110">次の例では、<xref:System.Linq.Enumerable.OrderBy%2A> を使用して、連絡先の一覧を姓の長さの順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="31401-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="31401-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="31401-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="31401-112">例</span><span class="sxs-lookup"><span data-stu-id="31401-112">Example</span></span>  
 <span data-ttu-id="31401-113">次の例では、`orderby… descending` メソッドと同等の `Order By … Descending` (Visual Basic の場合は <xref:System.Linq.Enumerable.OrderByDescending%2A>) を使用して、価格の一覧を高いものから低い順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="31401-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="31401-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="31401-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="31401-115">例</span><span class="sxs-lookup"><span data-stu-id="31401-115">Example</span></span>  
 <span data-ttu-id="31401-116">次の例では、<xref:System.Linq.Queryable.OrderBy%2A> と <xref:System.Linq.Queryable.ThenBy%2A> を使用して、姓の順、次に名の順に並べ替えられた連絡先の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="31401-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="31401-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="31401-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="31401-118">例</span><span class="sxs-lookup"><span data-stu-id="31401-118">Example</span></span>  
 <span data-ttu-id="31401-119">次の例では、`OrderBy… Descending` メソッドと同等の <xref:System.Linq.Enumerable.ThenByDescending%2A> を使用して、製品の一覧を、名前順に、次に表示価格の高いものから低い順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="31401-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="31401-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="31401-120">See Also</span></span>  
 [<span data-ttu-id="31401-121">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="31401-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

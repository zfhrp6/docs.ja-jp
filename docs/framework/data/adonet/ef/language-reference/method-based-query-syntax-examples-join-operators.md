---
title: 'メソッド ベースのクエリ構文例: 結合演算子'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: a77a58d28c667e5dabf0dda4c8d2f4782ea83572
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761741"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="0fe3f-102">メソッド ベースのクエリ構文例: 結合演算子</span><span class="sxs-lookup"><span data-stu-id="0fe3f-102">Method-Based Query Syntax Examples: Join Operators</span></span>
<span data-ttu-id="0fe3f-103">このトピックの例を使用する方法を示します、<xref:System.Linq.Enumerable.Join%2A>と<xref:System.Linq.Enumerable.GroupJoin%2A>を照会する方法、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)メソッド ベースのクエリ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="0fe3f-104">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0fe3f-105">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="0fe3f-106">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="0fe3f-106">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="0fe3f-107">例</span><span class="sxs-lookup"><span data-stu-id="0fe3f-107">Example</span></span>  
 <span data-ttu-id="0fe3f-108">次の例では、SalesOrderHeader テーブルおよび SalesOrderDetail テーブルに対して <xref:System.Linq.Enumerable.GroupJoin%2A> を実行することによって、顧客ごとの注文数を調べます。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-108">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="0fe3f-109">GroupJoin は、左外部結合に相当します。つまり、1 つ目 (左側) のデータ ソースに存在するすべての要素は、関連する要素がもう一方のデータ ソースに存在するかどうかに関係なく返されます。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-109">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="0fe3f-110">例</span><span class="sxs-lookup"><span data-stu-id="0fe3f-110">Example</span></span>  
 <span data-ttu-id="0fe3f-111">次の例では、Contact テーブルおよび SalesOrderHeader テーブルに対して <xref:System.Linq.Enumerable.GroupJoin%2A> を実行して、連絡先ごとの注文数を調べます。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="0fe3f-112">各連絡先の注文数と ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-112">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="0fe3f-113">Join</span><span class="sxs-lookup"><span data-stu-id="0fe3f-113">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="0fe3f-114">例</span><span class="sxs-lookup"><span data-stu-id="0fe3f-114">Example</span></span>  
 <span data-ttu-id="0fe3f-115">次の例では、Contact テーブルと SalesOrderHeader テーブルの結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-115">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="0fe3f-116">例</span><span class="sxs-lookup"><span data-stu-id="0fe3f-116">Example</span></span>  
 <span data-ttu-id="0fe3f-117">次の例では、Contact テーブルと SalesOrderHeader テーブルを結合し、結果を連絡先 ID でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-117">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0fe3f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fe3f-118">See Also</span></span>  
 [<span data-ttu-id="0fe3f-119">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="0fe3f-119">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

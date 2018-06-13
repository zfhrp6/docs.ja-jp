---
title: 'クエリ式の構文例: 集計演算子'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 56eaf4c3fce6f5b64563bc2e4a7a5b6415f545c0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763067"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="51b9e-102">クエリ式の構文例: 集計演算子</span><span class="sxs-lookup"><span data-stu-id="51b9e-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="51b9e-103">このトピックの例を使用する方法を示します、 <xref:System.Linq.Enumerable.Average%2A>、 <xref:System.Linq.Enumerable.Count%2A>、 <xref:System.Linq.Enumerable.Max%2A>、 <xref:System.Linq.Enumerable.Min%2A>、および<xref:System.Linq.Enumerable.Sum%2A>を照会する方法、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)クエリ式の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="51b9e-104">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="51b9e-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="51b9e-105">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="51b9e-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="51b9e-106">平均</span><span class="sxs-lookup"><span data-stu-id="51b9e-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="51b9e-107">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-107">Example</span></span>  
 <span data-ttu-id="51b9e-108">次の例では、<xref:System.Linq.Enumerable.Average%2A> メソッドを使用して、各スタイルの製品の平均表示価格を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="51b9e-109">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-109">Example</span></span>  
 <span data-ttu-id="51b9e-110">次の例では、<xref:System.Linq.Enumerable.Average%2A> を使用して、それぞれの連絡先 ID について平均合計支払額を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="51b9e-111">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-111">Example</span></span>  
 <span data-ttu-id="51b9e-112">次の例では、<xref:System.Linq.Enumerable.Average%2A> を使用して、それぞれの連絡先について合計支払額が平均値の注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="51b9e-113">Count</span><span class="sxs-lookup"><span data-stu-id="51b9e-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="51b9e-114">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-114">Example</span></span>  
 <span data-ttu-id="51b9e-115">次の例では、<xref:System.Linq.Enumerable.Count%2A> を使用して、連絡先 ID の一覧と、それぞれの注文数を返します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="51b9e-116">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-116">Example</span></span>  
 <span data-ttu-id="51b9e-117">次の例では、製品を色でグループ分けし、<xref:System.Linq.Enumerable.Count%2A> を使用してそれぞれの色グループに含まれる製品の数を返します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="51b9e-118">最大</span><span class="sxs-lookup"><span data-stu-id="51b9e-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="51b9e-119">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-119">Example</span></span>  
 <span data-ttu-id="51b9e-120">次の例では、<xref:System.Linq.Enumerable.Max%2A> メソッドを使用して、それぞれの連絡先 ID について最大合計支払額を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="51b9e-121">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-121">Example</span></span>  
 <span data-ttu-id="51b9e-122">次の例では、<xref:System.Linq.Enumerable.Max%2A> メソッドを使用して、それぞれの連絡先 ID について合計支払額が最大の注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="51b9e-123">最小</span><span class="sxs-lookup"><span data-stu-id="51b9e-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="51b9e-124">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-124">Example</span></span>  
 <span data-ttu-id="51b9e-125">次の例では、<xref:System.Linq.Enumerable.Min%2A> メソッドを使用して、それぞれの連絡先 ID について最小合計支払額を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="51b9e-126">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-126">Example</span></span>  
 <span data-ttu-id="51b9e-127">次の例では、<xref:System.Linq.Enumerable.Min%2A> メソッドを使用して、それぞれの連絡先について合計支払額が最小の注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="51b9e-128">Sum</span><span class="sxs-lookup"><span data-stu-id="51b9e-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="51b9e-129">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-129">Example</span></span>  
 <span data-ttu-id="51b9e-130">次の例では、<xref:System.Linq.Enumerable.Sum%2A> メソッドを使用して、それぞれの連絡先 ID について合計支払額を取得します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="51b9e-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="51b9e-131">See Also</span></span>  
 [<span data-ttu-id="51b9e-132">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="51b9e-132">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

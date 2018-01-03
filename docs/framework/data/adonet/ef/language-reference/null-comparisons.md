---
title: "NULL 比較"
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
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b29caeed4bf60a5a7ad723ffd46520a89a5bd87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="null-comparisons"></a><span data-ttu-id="06e2e-102">NULL 比較</span><span class="sxs-lookup"><span data-stu-id="06e2e-102">Null Comparisons</span></span>
<span data-ttu-id="06e2e-103">データ ソースの `null` 値は不明な値を表します。</span><span class="sxs-lookup"><span data-stu-id="06e2e-103">A `null` value in the data source indicates that the value is unknown.</span></span> <span data-ttu-id="06e2e-104">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリでは、NULL 値をチェックして、必ず NULL でない有効なデータを持つ行に特定の計算または比較を行うようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-104">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, you can check for null values so that certain calculations or comparisons are only performed on rows that have valid, or non-null, data.</span></span> <span data-ttu-id="06e2e-105">ただし、CLR の NULL セマンティクスは、データ ソースの NULL セマンティクスとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="06e2e-105">CLR null semantics, however, may differ from the null semantics of the data source.</span></span> <span data-ttu-id="06e2e-106">ほとんどのデータベースでは、3 値論理を使用して NULL 比較を処理します。</span><span class="sxs-lookup"><span data-stu-id="06e2e-106">Most databases use a version of three-valued logic to handle null comparisons.</span></span> <span data-ttu-id="06e2e-107">つまり、null 値に対する比較には評価されません`true`または`false`、評価結果が`unknown`です。</span><span class="sxs-lookup"><span data-stu-id="06e2e-107">That is, a comparison against a null value does not evaluate to `true` or `false`, it evaluates to `unknown`.</span></span> <span data-ttu-id="06e2e-108">これは、多くの場合は ANSI NULL の実装ですが、そうでない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="06e2e-108">Often this is an implementation of ANSI nulls, but this is not always the case.</span></span>  
  
 <span data-ttu-id="06e2e-109">SQL Server の既定では、NULL = NULL の比較は NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="06e2e-109">By default in SQL Server, the null-equals-null comparison returns a null value.</span></span> <span data-ttu-id="06e2e-110">次の例では、`ShipDate` が NULL である行が結果セットから除外され、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ステートメントは 0 行を返します。</span><span class="sxs-lookup"><span data-stu-id="06e2e-110">In the following example, the rows where `ShipDate` is null are excluded from the result set, and the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] statement would return 0 rows.</span></span>  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 <span data-ttu-id="06e2e-111">これは、NULL = NULL の比較が true を返す CLR の NULL セマンティクスとは大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="06e2e-111">This is very different from the CLR null semantics, where the null-equals-null comparison returns true.</span></span>  
  
 <span data-ttu-id="06e2e-112">次の LINQ クエリは CLR で表されますが、データ ソースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-112">The following LINQ query is expressed in the CLR, but it is executed in the data source.</span></span> <span data-ttu-id="06e2e-113">CLR セマンティクスがデータ ソースで使用される保証はないため、動作は予測できません。</span><span class="sxs-lookup"><span data-stu-id="06e2e-113">Because there is no guarantee that CLR semantics will be honored at the data source, the expected behavior is indeterminate.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a><span data-ttu-id="06e2e-114">キー セレクター</span><span class="sxs-lookup"><span data-stu-id="06e2e-114">Key Selectors</span></span>  
 <span data-ttu-id="06e2e-115">A*キー セレクター*要素からキーを抽出する、標準クエリ演算子で使用される関数。</span><span class="sxs-lookup"><span data-stu-id="06e2e-115">A *key selector* is a function used in the standard query operators to extract a key from an element.</span></span> <span data-ttu-id="06e2e-116">キー セレクター関数では、式を定数と比較できます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-116">In the key selector function, an expression can be compared with a constant.</span></span> <span data-ttu-id="06e2e-117">式が NULL 定数と比較される場合、または 2 つの NULL 定数が比較される場合、CLR の NULL セマンティクスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-117">CLR null semantics are exhibited if an expression is compared to a null constant or if two null constants are compared.</span></span> <span data-ttu-id="06e2e-118">データ ソースの NULL 値を持つ 2 つの列が比較される場合は、ストア NULL セマンティクスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-118">Store null semantics are exhibited if two columns with null values in the data source are compared.</span></span> <span data-ttu-id="06e2e-119">キー セレクターは、<xref:System.Linq.Queryable.GroupBy%2A> など、グループ化や並べ替えの標準クエリ演算子で使用される場合が多く、クエリ結果の並べ替えやグループ化に使用するキーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-119">Key selectors are found in many of the grouping and ordering standard query operators, such as <xref:System.Linq.Queryable.GroupBy%2A>, and are used to select keys by which to order or group the query results.</span></span>  
  
## <a name="null-property-on-a-null-object"></a><span data-ttu-id="06e2e-120">NULL オブジェクトの NULL プロパティ</span><span class="sxs-lookup"><span data-stu-id="06e2e-120">Null Property on a Null Object</span></span>  
 <span data-ttu-id="06e2e-121">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] では、NULL オブジェクトのプロパティは NULL です。</span><span class="sxs-lookup"><span data-stu-id="06e2e-121">In the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], the properties of a null object are null.</span></span> <span data-ttu-id="06e2e-122">CLR で NULL オブジェクトのプロパティを参照しようとすると、<xref:System.NullReferenceException> が返されます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-122">When you attempt to reference a property of a null object in the CLR, you will receive a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="06e2e-123">LINQ クエリに NULL オブジェクトのプロパティが含まれている場合、動作の一貫性が失われることがあります。</span><span class="sxs-lookup"><span data-stu-id="06e2e-123">When a LINQ query involves a property of a null object, this can result in inconsistent behavior.</span></span>  
  
 <span data-ttu-id="06e2e-124">たとえば、次のクエリでは、`NewProduct` へのキャストはコマンド ツリー レイヤーで行われ、`Introduced` プロパティが NULL になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06e2e-124">For example, in the following query, the cast to `NewProduct` is done in the command tree layer, which might result in the `Introduced` property being null.</span></span> <span data-ttu-id="06e2e-125"><xref:System.DateTime> の比較が true に評価されるように NULL 比較がデータベースで定義されている場合に、その行が含められます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-125">If the database defined null comparisons such that the <xref:System.DateTime> comparison evaluates to true, the row will be included.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a><span data-ttu-id="06e2e-126">集計関数に NULL コレクションを渡す</span><span class="sxs-lookup"><span data-stu-id="06e2e-126">Passing Null Collections to Aggregate Functions</span></span>  
 <span data-ttu-id="06e2e-127">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]をサポートするコレクションを渡すと、`IQueryable`で集計関数では、データベースで集計演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-127">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], when you pass a collection that supports `IQueryable` to an aggregate function, aggregate operations are performed at the database.</span></span> <span data-ttu-id="06e2e-128">メモリ内で実行されたクエリとデータベースで実行されたクエリの結果の違いがある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06e2e-128">There might be differences in the results of a query that was performed in-memory and a query that was performed at the database.</span></span> <span data-ttu-id="06e2e-129">メモリ内のクエリを使用して、一致がない場合、クエリは 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="06e2e-129">With an in-memory query, if there are no matches, the query returns zero.</span></span> <span data-ttu-id="06e2e-130">データベースでは、これと同じクエリから `null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-130">At the database, the same query returns `null`.</span></span> <span data-ttu-id="06e2e-131">場合、`null`値が LINQ 集計関数に渡される、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="06e2e-131">If a `null` value is passed to a LINQ aggregate function, an exception will be thrown.</span></span> <span data-ttu-id="06e2e-132">受け入れるに`null`値、キャスト、型と null 許容型にクエリ結果を受信した種類のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="06e2e-132">To accept possible `null` values, cast the types and the properties of the types that receive query results to nullable types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e2e-133">参照</span><span class="sxs-lookup"><span data-stu-id="06e2e-133">See Also</span></span>  
 [<span data-ttu-id="06e2e-134">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="06e2e-134">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

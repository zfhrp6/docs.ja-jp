---
title: "比較式"
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
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: def78e45fa59fafbc6b8e5ffec7273f755e49d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="comparison-expressions"></a><span data-ttu-id="178d6-102">比較式</span><span class="sxs-lookup"><span data-stu-id="178d6-102">Comparison Expressions</span></span>
<span data-ttu-id="178d6-103">比較式は、定数値、プロパティ値、またはメソッドの結果と別の値を比較して、両者が等しいかどうか、または一方の値がもう一方の値より大きい (小さい) かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="178d6-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="178d6-104">特定の比較が [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] に対して無効な場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="178d6-104">If a particular comparison is not valid for [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], an exception will be thrown.</span></span> <span data-ttu-id="178d6-105">暗黙的および明示的な比較を行う場合は、データ ソース内のすべてのコンポーネントが比較可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="178d6-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="178d6-106">比較式は、クエリ結果を絞り込むために `Where` 句で頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="178d6-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="178d6-107">次のクエリ式の構文の例は、販売注文番号が "SO43663" である結果を返すクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="178d6-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="178d6-108">次のメソッド ベースのクエリ構文の例は、販売注文番号が "SO43663" である結果を返すクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="178d6-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="178d6-109">次のクエリ式の構文の例は、出荷日が 2001 年 7 月 8 日である販売注文情報を返すクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="178d6-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="178d6-110">次のメソッド ベースのクエリ構文の例は、出荷日が 2001 年 7 月 8 日である販売注文情報を返すクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="178d6-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="178d6-111">定数を返す式はサーバーで変換されます。そのため、ローカルで評価されることはありません。</span><span class="sxs-lookup"><span data-stu-id="178d6-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="178d6-112">次の例では、定数を返す式を `Where` 句で使用しています。</span><span class="sxs-lookup"><span data-stu-id="178d6-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="178d6-113"> では、ユーザー クラスを定数として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="178d6-113"> does not support using a user class as a constant.</span></span> <span data-ttu-id="178d6-114">ただし、ユーザー クラスのプロパティ参照は定数と見なされます。そのため、コマンド ツリーの定数式に変換され、データ ソースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="178d6-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="178d6-115">定数式を返すメソッドはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="178d6-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="178d6-116">次の例の `Where` 句には、定数を返すメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="178d6-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="178d6-117">この例を実行すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="178d6-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="178d6-118">参照</span><span class="sxs-lookup"><span data-stu-id="178d6-118">See Also</span></span>  
 [<span data-ttu-id="178d6-119">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="178d6-119">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

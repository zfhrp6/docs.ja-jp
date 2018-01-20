---
title: "メソッド ベースのクエリ構文例: 並べ替え"
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
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0ba6dc4127a3240adb686fe8c0753a1c93afef12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="70279-102">メソッド ベースのクエリ構文例: 並べ替え</span><span class="sxs-lookup"><span data-stu-id="70279-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="70279-103">このトピックの例を使用する方法を示します、<xref:System.Linq.Enumerable.ThenBy%2A>メソッド クエリを[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)メソッド ベースのクエリ構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="70279-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="70279-104">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="70279-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="70279-105">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="70279-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="70279-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="70279-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="70279-107">例</span><span class="sxs-lookup"><span data-stu-id="70279-107">Example</span></span>  
 <span data-ttu-id="70279-108">次の例では、メソッド ベースのクエリ構文で <xref:System.Linq.Queryable.OrderBy%2A> と <xref:System.Linq.Queryable.ThenBy%2A> を使用し、姓の順、次に名の順に並べ替えられた連絡先の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="70279-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="70279-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="70279-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="70279-110">例</span><span class="sxs-lookup"><span data-stu-id="70279-110">Example</span></span>  
 <span data-ttu-id="70279-111">次の例では、<xref:System.Linq.Queryable.OrderBy%2A> メソッドおよび <xref:System.Linq.Queryable.ThenByDescending%2A> メソッドを使用し、最初に表示価格で並べ替えた後、製品名の降順で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="70279-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="70279-112">参照</span><span class="sxs-lookup"><span data-stu-id="70279-112">See Also</span></span>  
 [<span data-ttu-id="70279-113">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="70279-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

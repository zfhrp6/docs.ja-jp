---
title: "シーケンスの最初の要素の取得"
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
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 476b8863d05f0c2d77b1b90c8795b85449ed3160
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="2b773-102">シーケンスの最初の要素の取得</span><span class="sxs-lookup"><span data-stu-id="2b773-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="2b773-103"><xref:System.Linq.Enumerable.First%2A> 演算子を使用すると、シーケンスの内最初の要素を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2b773-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="2b773-104"><xref:System.Linq.Enumerable.First%2A> を使用するクエリは直ちに実行されます。</span><span class="sxs-lookup"><span data-stu-id="2b773-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2b773-105"> は <xref:System.Linq.Enumerable.Last%2A> 演算子をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="2b773-105"> does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b773-106">例</span><span class="sxs-lookup"><span data-stu-id="2b773-106">Example</span></span>  
 <span data-ttu-id="2b773-107">次のコードは、テーブル内の最初の `Shipper` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="2b773-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="2b773-108">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2b773-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="2b773-109">`ID = 1, Company = Speedy Express`。</span><span class="sxs-lookup"><span data-stu-id="2b773-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="2b773-110">例</span><span class="sxs-lookup"><span data-stu-id="2b773-110">Example</span></span>  
 <span data-ttu-id="2b773-111">次のコードは、`Customer` が BONAP の単一の `CustomerID` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="2b773-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="2b773-112">Northwind サンプル データベースに対してこのクエリを実行すると、結果は `ID = BONAP, Contact = Laurence Lebihan` になります。</span><span class="sxs-lookup"><span data-stu-id="2b773-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="2b773-113">参照</span><span class="sxs-lookup"><span data-stu-id="2b773-113">See Also</span></span>  
 [<span data-ttu-id="2b773-114">クエリの例</span><span class="sxs-lookup"><span data-stu-id="2b773-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="2b773-115">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="2b773-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

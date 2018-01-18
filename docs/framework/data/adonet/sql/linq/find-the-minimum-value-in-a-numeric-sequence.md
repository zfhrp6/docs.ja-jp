---
title: "一連の数値の中の最小値の検出"
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
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9cc16b09912cb9cc695fc350d9fd4530ea99e794
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="e68e1-102">一連の数値の中の最小値の検出</span><span class="sxs-lookup"><span data-stu-id="e68e1-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="e68e1-103">一連の数値の中から最小値を返すには、<xref:System.Linq.Enumerable.Min%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="e68e1-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e68e1-104">例</span><span class="sxs-lookup"><span data-stu-id="e68e1-104">Example</span></span>  
 <span data-ttu-id="e68e1-105">次の例では、製品の最低単価を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e68e1-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="e68e1-106">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`2.5000` です。</span><span class="sxs-lookup"><span data-stu-id="e68e1-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="e68e1-107">例</span><span class="sxs-lookup"><span data-stu-id="e68e1-107">Example</span></span>  
 <span data-ttu-id="e68e1-108">次の例では、注文の最低配送料を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e68e1-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="e68e1-109">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`0.0200` です。</span><span class="sxs-lookup"><span data-stu-id="e68e1-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="e68e1-110">例</span><span class="sxs-lookup"><span data-stu-id="e68e1-110">Example</span></span>  
 <span data-ttu-id="e68e1-111">次の例では、Min を使用して、各カテゴリ内で単価が最も安い `Products` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e68e1-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="e68e1-112">出力はカテゴリごとに行われます。</span><span class="sxs-lookup"><span data-stu-id="e68e1-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="e68e1-113">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e68e1-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="e68e1-114">参照</span><span class="sxs-lookup"><span data-stu-id="e68e1-114">See Also</span></span>  
 [<span data-ttu-id="e68e1-115">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="e68e1-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="e68e1-116">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="e68e1-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

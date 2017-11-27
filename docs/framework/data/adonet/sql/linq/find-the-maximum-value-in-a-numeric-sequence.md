---
title: "一連の数値の中の最大値の検出"
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
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 06c8d2b2eedc2d3684ef44f028cd73e80a8da5cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="8f3e9-102">一連の数値の中の最大値の検出</span><span class="sxs-lookup"><span data-stu-id="8f3e9-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="8f3e9-103">一連の数値の中の最大値を見つけるには、<xref:System.Linq.Enumerable.Max%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f3e9-104">例</span><span class="sxs-lookup"><span data-stu-id="8f3e9-104">Example</span></span>  
 <span data-ttu-id="8f3e9-105">次の例では、従業員の最新の入社日を見つけます。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="8f3e9-106">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`11/15/1994 12:00:00 AM` です。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="8f3e9-107">例</span><span class="sxs-lookup"><span data-stu-id="8f3e9-107">Example</span></span>  
 <span data-ttu-id="8f3e9-108">次の例では、製品の最大在庫数を見つけます。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="8f3e9-109">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`125` です。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="8f3e9-110">例</span><span class="sxs-lookup"><span data-stu-id="8f3e9-110">Example</span></span>  
 <span data-ttu-id="8f3e9-111">次の例では、Max を使用して、各カテゴリ内で単価が最も高い `Products` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="8f3e9-112">出力では、カテゴリごとに結果の一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="8f3e9-113">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8f3e9-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="8f3e9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f3e9-114">See Also</span></span>  
 [<span data-ttu-id="8f3e9-115">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="8f3e9-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="8f3e9-116">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="8f3e9-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

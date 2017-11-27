---
title: "シーケンスの要素のグループ化"
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
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a398bb7b951fcf2dd2449b6468a19d39a134a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="520f8-102">シーケンスの要素のグループ化</span><span class="sxs-lookup"><span data-stu-id="520f8-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="520f8-103"><xref:System.Linq.Enumerable.GroupBy%2A> 演算子はシーケンスの要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="520f8-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="520f8-104">Northwind データベースを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="520f8-105">null 列値が <xref:System.Linq.Enumerable.GroupBy%2A> クエリに含まれると、<xref:System.InvalidOperationException> がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="520f8-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="520f8-106">詳細についてを参照してください"GroupBy InvalidOperationException"の[トラブルシューティング](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)です。</span><span class="sxs-lookup"><span data-stu-id="520f8-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="520f8-107">例</span><span class="sxs-lookup"><span data-stu-id="520f8-107">Example</span></span>  
 <span data-ttu-id="520f8-108">次の例では、`Products` を基準として `CategoryID` をグループ化しています。</span><span class="sxs-lookup"><span data-stu-id="520f8-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="520f8-109">例</span><span class="sxs-lookup"><span data-stu-id="520f8-109">Example</span></span>  
 <span data-ttu-id="520f8-110"><xref:System.Linq.Enumerable.Max%2A> を使用して各 `CategoryID` の最も高い単価を調べる例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="520f8-111">例</span><span class="sxs-lookup"><span data-stu-id="520f8-111">Example</span></span>  
 <span data-ttu-id="520f8-112">Average を使用して各 `UnitPrice` の `CategoryID` の平均値を求める例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="520f8-113">例</span><span class="sxs-lookup"><span data-stu-id="520f8-113">Example</span></span>  
 <span data-ttu-id="520f8-114"><xref:System.Linq.Queryable.Sum%2A> を使用して各 `UnitPrice` の `CategoryID` の合計値を求める例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="520f8-115">例</span><span class="sxs-lookup"><span data-stu-id="520f8-115">Example</span></span>  
 <span data-ttu-id="520f8-116"><xref:System.Linq.Queryable.Count%2A> を使用して各 `Products` に含まれる生産中止の `CategoryID` の数を調べる例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="520f8-117">例</span><span class="sxs-lookup"><span data-stu-id="520f8-117">Example</span></span>  
 <span data-ttu-id="520f8-118">`where` 句を使用して最低 10 種類の製品が含まれるすべてのカテゴリを調べる方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="520f8-119">例</span><span class="sxs-lookup"><span data-stu-id="520f8-119">Example</span></span>  
 <span data-ttu-id="520f8-120">`CategoryID` と `SupplierID` を使用して製品をグループ化する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="520f8-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="520f8-121">例</span><span class="sxs-lookup"><span data-stu-id="520f8-121">Example</span></span>  
 <span data-ttu-id="520f8-122">次の例は、製品の 2 つのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="520f8-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="520f8-123">最初のシーケンスには、単価が 10 以下の製品が含まれます。</span><span class="sxs-lookup"><span data-stu-id="520f8-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="520f8-124">2 番目のシーケンスには、単価が 10 よりも大きい製品が含まれます。</span><span class="sxs-lookup"><span data-stu-id="520f8-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="520f8-125">例</span><span class="sxs-lookup"><span data-stu-id="520f8-125">Example</span></span>  
 <span data-ttu-id="520f8-126"><xref:System.Linq.Queryable.GroupBy%2A> 演算子は、単一キーの引数のみを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="520f8-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="520f8-127">複数のキーを使用してグループ化する場合は、次の例に示すように、匿名型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="520f8-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="520f8-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="520f8-128">See Also</span></span>  
 [<span data-ttu-id="520f8-129">クエリの例</span><span class="sxs-lookup"><span data-stu-id="520f8-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="520f8-130">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="520f8-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

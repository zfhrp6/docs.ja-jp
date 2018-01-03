---
title: "メソッド ベースのクエリ構文例: パーティション分割 (LINQ"
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
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2c6d171e289195dbff69dcc77ae9823b62681695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="aafe9-102">メソッド ベースのクエリ構文例: パーティション分割 (LINQ</span><span class="sxs-lookup"><span data-stu-id="aafe9-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="aafe9-103">このトピックでは、<xref:System.Linq.Enumerable.Skip%2A>、<xref:System.Linq.Enumerable.SkipWhile%2A>、<xref:System.Linq.Enumerable.Take%2A>、<xref:System.Linq.Enumerable.TakeWhile%2A> の各メソッドで、クエリ式の構文を使って <xref:System.Data.DataSet> に対するクエリを実行する例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="aafe9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="aafe9-104">`FillDataSet`でこれらの例で使用されるメソッドが指定された[、データセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="aafe9-105">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="aafe9-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aafe9-106">このトピックの例では、次を使用して`using` / `Imports`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="aafe9-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="aafe9-107">詳細については、次を参照してください。[する方法: Visual Studio でデータセット プロジェクトに LINQ 作成](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)です。</span><span class="sxs-lookup"><span data-stu-id="aafe9-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="aafe9-108">Skip</span><span class="sxs-lookup"><span data-stu-id="aafe9-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="aafe9-109">例</span><span class="sxs-lookup"><span data-stu-id="aafe9-109">Example</span></span>  
 <span data-ttu-id="aafe9-110">この例では、<xref:System.Linq.Enumerable.Skip%2A> テーブルから最初の 5 つを除くすべての連絡先を、`Contact` メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="aafe9-111">例</span><span class="sxs-lookup"><span data-stu-id="aafe9-111">Example</span></span>  
 <span data-ttu-id="aafe9-112">この例では、Seattle から最初の 2 つを除くすべての住所を、<xref:System.Linq.Enumerable.Skip%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="aafe9-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="aafe9-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="aafe9-114">例</span><span class="sxs-lookup"><span data-stu-id="aafe9-114">Example</span></span>  
 <span data-ttu-id="aafe9-115">この例では、<xref:System.Linq.Enumerable.OrderBy%2A> メソッドおよび <xref:System.Linq.Enumerable.SkipWhile%2A> メソッドを使用し、表示価格が 300.00 を超える製品を `Product` テーブルから取得します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="aafe9-116">Take</span><span class="sxs-lookup"><span data-stu-id="aafe9-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="aafe9-117">例</span><span class="sxs-lookup"><span data-stu-id="aafe9-117">Example</span></span>  
 <span data-ttu-id="aafe9-118">この例では、<xref:System.Linq.Enumerable.Take%2A> テーブルから最初の 5 つの連絡先だけを、`Contact` メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="aafe9-119">例</span><span class="sxs-lookup"><span data-stu-id="aafe9-119">Example</span></span>  
 <span data-ttu-id="aafe9-120">この例では、Seattle から最初の 3 つの住所を、<xref:System.Linq.Enumerable.Take%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="aafe9-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="aafe9-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="aafe9-122">例</span><span class="sxs-lookup"><span data-stu-id="aafe9-122">Example</span></span>  
 <span data-ttu-id="aafe9-123">この例では、<xref:System.Linq.Enumerable.OrderBy%2A> メソッドおよび <xref:System.Linq.Enumerable.TakeWhile%2A> メソッドを使用し、表示価格が 300.00 未満の製品を `Product` テーブルから取得します。</span><span class="sxs-lookup"><span data-stu-id="aafe9-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="aafe9-124">参照</span><span class="sxs-lookup"><span data-stu-id="aafe9-124">See Also</span></span>  
 [<span data-ttu-id="aafe9-125">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="aafe9-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="aafe9-126">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="aafe9-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="aafe9-127">標準クエリ演算子の概要</span><span class="sxs-lookup"><span data-stu-id="aafe9-127">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

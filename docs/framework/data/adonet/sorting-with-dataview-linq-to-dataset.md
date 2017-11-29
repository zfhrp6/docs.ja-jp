---
title: "DataView による並べ替え (LINQ to DataSet)"
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
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5ce75aba79af617b7c3b342a25f2ac8f8ab0f672
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="75b64-102">DataView による並べ替え (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="75b64-102">Sorting with DataView (LINQ to DataSet)</span></span>
<span data-ttu-id="75b64-103">特定の条件に基づいてデータを並べ替え、UI コントロールを介してそのデータをクライアントに提供する機能は、データ バインディングの重要な特徴です。</span><span class="sxs-lookup"><span data-stu-id="75b64-103">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="75b64-104"><xref:System.Data.DataView> には、データを並べ替え、特定の並べ替え条件に従って並べ替えられたデータ行を返す方法がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="75b64-104"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="75b64-105">だけでなく、文字列ベースの並べ替え機能、<xref:System.Data.DataView>を使用することもできます[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]並べ替えの基準の式。</span><span class="sxs-lookup"><span data-stu-id="75b64-105">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] expressions for the sorting criteria.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="75b64-106">式は、文字列ベースの並べ替えよりもはるかに複雑で強力なの並べ替え操作を許可します。</span><span class="sxs-lookup"><span data-stu-id="75b64-106"> expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="75b64-107">このトピックでは、<xref:System.Data.DataView> を使用して並べ替えを行うこの 2 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="75b64-107">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="75b64-108">並べ替え情報を含むクエリによる DataView の作成</span><span class="sxs-lookup"><span data-stu-id="75b64-108">Creating DataView from a Query with Sorting Information</span></span>  
 <span data-ttu-id="75b64-109"><xref:System.Data.DataView> オブジェクトは [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから作成できます。</span><span class="sxs-lookup"><span data-stu-id="75b64-109">A <xref:System.Data.DataView> object can be created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query.</span></span> <span data-ttu-id="75b64-110">そのクエリが含まれている場合、 <xref:System.Linq.Enumerable.OrderBy%2A>、 <xref:System.Linq.Enumerable.OrderByDescending%2A>、 <xref:System.Linq.Enumerable.ThenBy%2A>、または<xref:System.Linq.Enumerable.ThenByDescending%2A>これらの句内の式がデータの並べ替えの基準として使用される句、<xref:System.Data.DataView>です。</span><span class="sxs-lookup"><span data-stu-id="75b64-110">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="75b64-111">たとえば、クエリに含まれる場合、`Order By…`と`Then By…`句、その結果<xref:System.Data.DataView>指定された両方の列によってデータの順序付けはします。</span><span class="sxs-lookup"><span data-stu-id="75b64-111">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="75b64-112">式ベースの並べ替えは、文字列ベースの並べ替えよりもはるかに強力で複雑な並べ替え機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="75b64-112">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="75b64-113">文字列ベースの並べ替え機能と式ベースの並べ替え機能は、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="75b64-113">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="75b64-114"><xref:System.Data.DataView.Sort%2A> をクエリから作成した後に文字列ベースの <xref:System.Data.DataView> を設定した場合、クエリから推論される式ベースの並べ替えはクリアされます (再設定できません)。</span><span class="sxs-lookup"><span data-stu-id="75b64-114">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="75b64-115"><xref:System.Data.DataView> のインデックスは、<xref:System.Data.DataView> の作成時に構築されるほか、並べ替えまたはフィルター処理の情報が変更されたときにも構築されます。</span><span class="sxs-lookup"><span data-stu-id="75b64-115">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="75b64-116">最高のパフォーマンスを得るには、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を作成する <xref:System.Data.DataView> クエリに並べ替え条件を指定し、後で並べ替え情報を変更しないようにします。</span><span class="sxs-lookup"><span data-stu-id="75b64-116">You get the best performance by supplying sorting criteria in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="75b64-117">詳細については、次を参照してください。 [DataView のパフォーマンス](../../../../docs/framework/data/adonet/dataview-performance.md)です。</span><span class="sxs-lookup"><span data-stu-id="75b64-117">For more information, see [DataView Performance](../../../../docs/framework/data/adonet/dataview-performance.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75b64-118">ほとんどの場合、並べ替えに使用する式は、副作用のない確定的な式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="75b64-118">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="75b64-119">また、並べ替え処理は任意の回数実行されるため、特定の実行回数に依存するロジックが式に含まれないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="75b64-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="75b64-120">例</span><span class="sxs-lookup"><span data-stu-id="75b64-120">Example</span></span>  
 <span data-ttu-id="75b64-121">次の例では、SalesOrderHeader テーブルに対してクエリを実行し、返された行を発注日順に並べ替えます。次にこのクエリから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="75b64-121">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="75b64-122">例</span><span class="sxs-lookup"><span data-stu-id="75b64-122">Example</span></span>  
 <span data-ttu-id="75b64-123">次の例では、SalesOrderHeader テーブルに対してクエリを実行し、返された行を合計支払額順に並べ替えます。次にこのクエリから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="75b64-123">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="75b64-124">例</span><span class="sxs-lookup"><span data-stu-id="75b64-124">Example</span></span>  
 <span data-ttu-id="75b64-125">次の例では、SalesOrderDetail テーブルに対してクエリを実行し、返された行を注文数量順および販売注文 ID 順に並べ替えます。次にこのクエリから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="75b64-125">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="75b64-126">文字列ベースの Sort プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="75b64-126">Using the String-Based Sort Property</span></span>  
 <span data-ttu-id="75b64-127"><xref:System.Data.DataView> の文字列ベースの並べ替え機能は [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] で動作します。</span><span class="sxs-lookup"><span data-stu-id="75b64-127">The string-based sorting functionality of <xref:System.Data.DataView> still works with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="75b64-128"><xref:System.Data.DataView> を [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから作成した後、<xref:System.Data.DataView.Sort%2A> プロパティを使用して、<xref:System.Data.DataView> の並べ替えを設定できます。</span><span class="sxs-lookup"><span data-stu-id="75b64-128">After a <xref:System.Data.DataView> has been created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="75b64-129">文字列ベースの並べ替え機能と式ベースの並べ替え機能は、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="75b64-129">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="75b64-130"><xref:System.Data.DataView.Sort%2A> プロパティを設定すると、<xref:System.Data.DataView> の作成元のクエリから推論される式ベースの並べ替えはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="75b64-130">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="75b64-131">文字列ベースの詳細については<xref:System.Data.DataView.Sort%2A>フィルター処理を参照してください[並べ替え/フィルター データ](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="75b64-131">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="75b64-132">例</span><span class="sxs-lookup"><span data-stu-id="75b64-132">Example</span></span>  
 <span data-ttu-id="75b64-133">次の例では、<xref:System.Data.DataView> を Contact テーブルから作成した後、姓を降順に並べ替え、名を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="75b64-133">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="75b64-134">例</span><span class="sxs-lookup"><span data-stu-id="75b64-134">Example</span></span>  
 <span data-ttu-id="75b64-135">次の例では、姓が "S" で始まる連絡先を取得するクエリを Contact テーブルに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="75b64-135">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="75b64-136">このクエリから <xref:System.Data.DataView> が作成され、<xref:System.Windows.Forms.BindingSource> オブジェクトにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="75b64-136">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="75b64-137">並べ替えのクリア</span><span class="sxs-lookup"><span data-stu-id="75b64-137">Clearing the Sort</span></span>  
 <span data-ttu-id="75b64-138"><xref:System.Data.DataView> の並べ替え情報は、<xref:System.Data.DataView.Sort%2A> プロパティを使用すると、並べ替えが設定された後にクリアできます。</span><span class="sxs-lookup"><span data-stu-id="75b64-138">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="75b64-139"><xref:System.Data.DataView> の並べ替え情報は、2 つの方法でクリアできます。</span><span class="sxs-lookup"><span data-stu-id="75b64-139">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
-   <span data-ttu-id="75b64-140"><xref:System.Data.DataView.Sort%2A> プロパティを `null` に設定します。</span><span class="sxs-lookup"><span data-stu-id="75b64-140">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
-   <span data-ttu-id="75b64-141"><xref:System.Data.DataView.Sort%2A> プロパティを空の文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="75b64-141">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="75b64-142">例</span><span class="sxs-lookup"><span data-stu-id="75b64-142">Example</span></span>  
 <span data-ttu-id="75b64-143">次の例では、クエリから <xref:System.Data.DataView> を作成した後、<xref:System.Data.DataView.Sort%2A> プロパティを空の文字列に設定して並べ替えをクリアします。</span><span class="sxs-lookup"><span data-stu-id="75b64-143">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="75b64-144">例</span><span class="sxs-lookup"><span data-stu-id="75b64-144">Example</span></span>  
 <span data-ttu-id="75b64-145">次の例では、Contact テーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.Sort%2A> プロパティを設定して、連絡先の姓を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="75b64-145">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="75b64-146">次に、<xref:System.Data.DataView.Sort%2A> プロパティを `null` に設定して並べ替え情報をクリアします。</span><span class="sxs-lookup"><span data-stu-id="75b64-146">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="75b64-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="75b64-147">See Also</span></span>  
 [<span data-ttu-id="75b64-148">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="75b64-148">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [<span data-ttu-id="75b64-149">DataView によるフィルター処理</span><span class="sxs-lookup"><span data-stu-id="75b64-149">Filtering with DataView</span></span>](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [<span data-ttu-id="75b64-150">データの並べ替え</span><span class="sxs-lookup"><span data-stu-id="75b64-150">Sorting Data</span></span>](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)

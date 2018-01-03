---
title: "DataView オブジェクトの作成 (LINQ to DataSet)"
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
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b8a4a1f0dc004957b64e3adb5d106c2cd4f413a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a><span data-ttu-id="010a7-102">DataView オブジェクトの作成 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="010a7-102">Creating a DataView Object (LINQ to DataSet)</span></span>
<span data-ttu-id="010a7-103"><xref:System.Data.DataView> のコンテキストで [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を作成するには 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="010a7-103">There are two ways to create a <xref:System.Data.DataView> in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] context.</span></span> <span data-ttu-id="010a7-104"><xref:System.Data.DataView> は、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] に対する <xref:System.Data.DataTable> クエリから作成したり、型指定されているまたは型指定されていない <xref:System.Data.DataTable> から作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="010a7-104">You can create a <xref:System.Data.DataView> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query over a <xref:System.Data.DataTable>, or you can create it from a typed or un-typed <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="010a7-105">どちらの場合も、作成、<xref:System.Data.DataView>のいずれかを使用して、<xref:System.Data.DataTableExtensions.AsDataView%2A>拡張メソッドです。<xref:System.Data.DataView>に直接構築することはできません、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="010a7-105">In both cases, you create the <xref:System.Data.DataView> by using one of the <xref:System.Data.DataTableExtensions.AsDataView%2A> extension methods; <xref:System.Data.DataView> is not directly constructible in the [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] context.</span></span>  
  
 <span data-ttu-id="010a7-106"><xref:System.Data.DataView> を作成した後に、Windows フォーム アプリケーションまたは ASP.NET アプリケーションの UI コントロールにバインドしたり、フィルターおよび並べ替えの設定を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="010a7-106">After the <xref:System.Data.DataView> has been created, you can bind it to a UI control in a Windows forms application or an ASP.NET application, or change the filtering and sorting settings.</span></span>  
  
 <span data-ttu-id="010a7-107"><xref:System.Data.DataView> は、インデックスを構築します。これにより、フィルター処理や並べ替えなど、インデックスを使用できる操作のパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="010a7-107"><xref:System.Data.DataView> constructs an index, which significantly increases the performance of operations that can use the index, such as filtering and sorting.</span></span> <span data-ttu-id="010a7-108"><xref:System.Data.DataView> のインデックスは、<xref:System.Data.DataView> の作成時に構築されるほか、並べ替えまたはフィルター処理の情報が変更されたときにも構築されます。</span><span class="sxs-lookup"><span data-stu-id="010a7-108">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="010a7-109"><xref:System.Data.DataView> を作成した後で、並べ替えまたはフィルター処理の情報を設定した場合、インデックスが最低でも 2 回 (<xref:System.Data.DataView> の作成時と、並べ替えまたはフィルターのプロパティの変更時) 構築されることになります。</span><span class="sxs-lookup"><span data-stu-id="010a7-109">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="010a7-110">フィルター処理と並べ替えの詳細については<xref:System.Data.DataView>を参照してください[DataView によるフィルター処理](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)と[DataView による並べ替え](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)です。</span><span class="sxs-lookup"><span data-stu-id="010a7-110">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a><span data-ttu-id="010a7-111">LINQ to DataSet クエリの結果からの DataView の作成</span><span class="sxs-lookup"><span data-stu-id="010a7-111">Creating DataView from a LINQ to DataSet Query</span></span>  
 <span data-ttu-id="010a7-112"><xref:System.Data.DataView> オブジェクトは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] オブジェクトの射影である <xref:System.Data.DataRow> クエリの結果から作成できます。</span><span class="sxs-lookup"><span data-stu-id="010a7-112">A <xref:System.Data.DataView> object can be created from the results of a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query, where the results are a projection of <xref:System.Data.DataRow> objects.</span></span> <span data-ttu-id="010a7-113">新しく作成される <xref:System.Data.DataView> は、その基となるクエリからのフィルター処理および並べ替え情報を継承します。</span><span class="sxs-lookup"><span data-stu-id="010a7-113">The newly created <xref:System.Data.DataView> inherits the filtering and sorting information from the query it is created from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="010a7-114">ほとんどの場合、フィルターに使用する式は、副作用のない確定的な式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="010a7-114">In most cases, the expressions used for filtering and sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="010a7-115">また、並べ替えおよびフィルター処理は任意の回数実行されるため、特定の実行回数に依存するロジックが式に含まれないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="010a7-115">Also, the expressions should not contain any logic that depend on a set number of executions, as the sorting and filtering operations may be executed any number of times.</span></span>  
  
 <span data-ttu-id="010a7-116">匿名型を返すクエリまたは結合操作を実行するクエリからの <xref:System.Data.DataView> の作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="010a7-116">Creating a <xref:System.Data.DataView> from a query that returns anonymous types or queries that perform join operations is not supported.</span></span>  
  
 <span data-ttu-id="010a7-117"><xref:System.Data.DataView> の作成に使用されるクエリでは、次のクエリ演算子のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="010a7-117">Only the following query operators are supported in a query used to create <xref:System.Data.DataView>:</span></span>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 <span data-ttu-id="010a7-118">場合、<xref:System.Data.DataView>から作成された、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ、<xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>メソッドは、クエリで呼び出された最終的なメソッドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="010a7-118">Note that when a <xref:System.Data.DataView> is created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query the <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> method must be the final method called in the query.</span></span> <span data-ttu-id="010a7-119">これは、次の例に示すを作成する、<xref:System.Data.DataView>合計支払額順に並べ替えてのオンライン注文の。</span><span class="sxs-lookup"><span data-stu-id="010a7-119">This is shown in the following example, which creates a <xref:System.Data.DataView> of online orders sorted by total due:</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 <span data-ttu-id="010a7-120">文字列ベースを使用することも<xref:System.Data.DataView.RowFilter%2A>と<xref:System.Data.DataView.Sort%2A>フィルターおよび並べ替えプロパティを<xref:System.Data.DataView>がクエリから作成された後です。</span><span class="sxs-lookup"><span data-stu-id="010a7-120">You can also use the string-based <xref:System.Data.DataView.RowFilter%2A> and <xref:System.Data.DataView.Sort%2A> properties to filter and sort a <xref:System.Data.DataView> after it has been created from a query.</span></span> <span data-ttu-id="010a7-121">この操作を行うと、クエリから継承された並べ替えおよびフィルター情報がクリアされます。</span><span class="sxs-lookup"><span data-stu-id="010a7-121">Note that this will clear the sorting and filtering information inherited from the query.</span></span> <span data-ttu-id="010a7-122">次の例では、姓が "S" で始まる連絡先をフィルター処理する <xref:System.Data.DataView> クエリから [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を作成します。</span><span class="sxs-lookup"><span data-stu-id="010a7-122">The following example creates a <xref:System.Data.DataView> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query that filters by last names that start with 'S'.</span></span> <span data-ttu-id="010a7-123">文字列ベースの <xref:System.Data.DataView.Sort%2A> プロパティは、姓を昇順に並べ替え、名を降順に並べ替えるように設定されています。</span><span class="sxs-lookup"><span data-stu-id="010a7-123">The string-based <xref:System.Data.DataView.Sort%2A> property is set to sort on last names in ascending order and then first names in descending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a><span data-ttu-id="010a7-124">DataTable からの DataView の作成</span><span class="sxs-lookup"><span data-stu-id="010a7-124">Creating a DataView from a DataTable</span></span>  
 <span data-ttu-id="010a7-125">作成されるだけでなく、 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 、クエリ、<xref:System.Data.DataView>からオブジェクトを作成することができます、<xref:System.Data.DataTable>を使用して、<xref:System.Data.DataTableExtensions.AsDataView%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="010a7-125">In addition to being created from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query, a <xref:System.Data.DataView> object can be created from a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTableExtensions.AsDataView%2A> method.</span></span>  
  
 <span data-ttu-id="010a7-126">次の例では、<xref:System.Data.DataView> を SalesOrderDetail テーブルから作成した後、<xref:System.Windows.Forms.BindingSource> オブジェクトのデータ ソースとして設定します。</span><span class="sxs-lookup"><span data-stu-id="010a7-126">The following example creates a <xref:System.Data.DataView> from the SalesOrderDetail table and sets it as the data source of a <xref:System.Windows.Forms.BindingSource> object.</span></span> <span data-ttu-id="010a7-127">このオブジェクトは、<xref:System.Windows.Forms.DataGridView> コントロールのプロキシとして動作します。</span><span class="sxs-lookup"><span data-stu-id="010a7-127">This object acts as a proxy for a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 <span data-ttu-id="010a7-128"><xref:System.Data.DataView> から <xref:System.Data.DataTable> を作成した後、フィルターおよび並べ替えを設定できます。</span><span class="sxs-lookup"><span data-stu-id="010a7-128">Filtering and sorting can be set on the <xref:System.Data.DataView> after it has been created from a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="010a7-129">次の例では、<xref:System.Data.DataView> を Contact テーブルから作成した後、姓を昇順に並べ替え、名を降順に並べ替えるための <xref:System.Data.DataView.Sort%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="010a7-129">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort on last names in ascending order and then first names in descending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 <span data-ttu-id="010a7-130">ただし、<xref:System.Data.DataView.RowFilter%2A> をクエリから作成した後に <xref:System.Data.DataView.Sort%2A> プロパティまたは <xref:System.Data.DataView> プロパティを設定する操作を行うと、パフォーマンスが低下します。なぜなら、<xref:System.Data.DataView> により、フィルター処理および並べ替え処理をサポートするためのインデックスが構築されるからです。</span><span class="sxs-lookup"><span data-stu-id="010a7-130">However, there is a performance loss that comes with setting the <xref:System.Data.DataView.RowFilter%2A> or <xref:System.Data.DataView.Sort%2A> property after the <xref:System.Data.DataView> has been created from a query, because <xref:System.Data.DataView> constructs an index to support filtering and sorting operations.</span></span> <span data-ttu-id="010a7-131"><xref:System.Data.DataView.RowFilter%2A> プロパティまたは <xref:System.Data.DataView.Sort%2A> プロパティを設定すると、データのインデックスが再構築され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。</span><span class="sxs-lookup"><span data-stu-id="010a7-131">Setting the <xref:System.Data.DataView.RowFilter%2A> or <xref:System.Data.DataView.Sort%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="010a7-132">可能な場合は、<xref:System.Data.DataView> を最初に作成するときにフィルター処理および並べ替え情報を指定して、後で情報を変更するのを避けてください。</span><span class="sxs-lookup"><span data-stu-id="010a7-132">When possible, it is better to specify the filtering and sorting information when you first create the <xref:System.Data.DataView> and avoid modifying it afterwards.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="010a7-133">参照</span><span class="sxs-lookup"><span data-stu-id="010a7-133">See Also</span></span>  
 [<span data-ttu-id="010a7-134">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="010a7-134">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [<span data-ttu-id="010a7-135">DataView によるフィルター処理</span><span class="sxs-lookup"><span data-stu-id="010a7-135">Filtering with DataView</span></span>](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [<span data-ttu-id="010a7-136">DataView による並べ替え</span><span class="sxs-lookup"><span data-stu-id="010a7-136">Sorting with DataView</span></span>](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)

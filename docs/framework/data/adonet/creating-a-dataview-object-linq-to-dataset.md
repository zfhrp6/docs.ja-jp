---
title: "Creating a DataView Object (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Creating a DataView Object (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のコンテキストで <xref:System.Data.DataView> を作成するには 2 つの方法があります。  <xref:System.Data.DataView> は、<xref:System.Data.DataTable> に対する [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから作成したり、型指定されているまたは型指定されていない <xref:System.Data.DataTable> から作成したりできます。  どちらの場合でも、<xref:System.Data.DataView> を作成するのにいずれかの <xref:System.Data.DataTableExtensions.AsDataView%2A> 拡張メソッドを使用します。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のコンテキストで <xref:System.Data.DataView> を直接作成することはできません。  
  
 <xref:System.Data.DataView> を作成した後に、Windows フォーム アプリケーションまたは ASP.NET アプリケーションの UI コントロールにバインドしたり、フィルターおよび並べ替えの設定を変更したりできます。  
  
 <xref:System.Data.DataView> は、インデックスを構築します。これにより、フィルター処理や並べ替えなど、インデックスを使用できる操作のパフォーマンスが大幅に向上します。  <xref:System.Data.DataView> のインデックスは、<xref:System.Data.DataView> の作成時に構築されるほか、並べ替えまたはフィルター処理の情報が変更されたときにも構築されます。  <xref:System.Data.DataView> を作成した後で、並べ替えまたはフィルター処理の情報を設定した場合、インデックスが最低でも 2 回 \(<xref:System.Data.DataView> の作成時と、並べ替えまたはフィルターのプロパティの変更時\) 構築されることになります。  
  
 <xref:System.Data.DataView> でのフィルターおよび並べ替えの詳細については、「[Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)」および「[Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)」を参照してください。  
  
## LINQ to DataSet クエリの結果からの DataView の作成  
 <xref:System.Data.DataView> オブジェクトは、<xref:System.Data.DataRow> オブジェクトの射影である [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリの結果から作成できます。  新しく作成される <xref:System.Data.DataView> は、その基となるクエリからのフィルター処理および並べ替え情報を継承します。  
  
> [!NOTE]
>  ほとんどの場合、フィルターに使用する式は、副作用のない確定的な式である必要があります。  また、並べ替えおよびフィルター処理は任意の回数実行されるため、特定の実行回数に依存するロジックが式に含まれないようにしてください。  
  
 匿名型を返すクエリまたは結合操作を実行するクエリからの <xref:System.Data.DataView> の作成はサポートされていません。  
  
 <xref:System.Data.DataView> の作成に使用されるクエリでは、次のクエリ演算子のみがサポートされます。  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから <xref:System.Data.DataView> を作成する場合は、<xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> メソッドをクエリで呼び出す最後のメソッドとする必要があります。次の例では、合計支払額別に並べ替えられたオンライン注文の <xref:System.Data.DataView> を作成します。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 また、文字列ベースの <xref:System.Data.DataView.RowFilter%2A> プロパティおよび <xref:System.Data.DataView.Sort%2A> プロパティを使用して、<xref:System.Data.DataView> をクエリから作成した後でフィルターを適用し、並べ替えることができます。  この操作を行うと、クエリから継承された並べ替えおよびフィルター情報がクリアされます。  次の例では、姓が "S" で始まる連絡先をフィルター処理する [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから <xref:System.Data.DataView> を作成します。  文字列ベースの <xref:System.Data.DataView.Sort%2A> プロパティは、姓を昇順に並べ替え、名を降順に並べ替えるように設定されています。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## DataTable からの DataView の作成  
 <xref:System.Data.DataView> オブジェクトは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから作成できるほか、<xref:System.Data.DataTableExtensions.AsDataView%2A> メソッドを使用して <xref:System.Data.DataTable> から作成することもできます。  
  
 次の例では、<xref:System.Data.DataView> を SalesOrderDetail テーブルから作成した後、<xref:System.Windows.Forms.BindingSource> オブジェクトのデータ ソースとして設定します。  このオブジェクトは、<xref:System.Windows.Forms.DataGridView> コントロールのプロキシとして動作します。  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 <xref:System.Data.DataTable> から <xref:System.Data.DataView> を作成した後、フィルターおよび並べ替えを設定できます。  次の例では、<xref:System.Data.DataView> を Contact テーブルから作成した後、姓を昇順に並べ替え、名を降順に並べ替えるための <xref:System.Data.DataView.Sort%2A> プロパティを設定します。  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 ただし、<xref:System.Data.DataView> をクエリから作成した後に <xref:System.Data.DataView.RowFilter%2A> プロパティまたは <xref:System.Data.DataView.Sort%2A> プロパティを設定する操作を行うと、パフォーマンスが低下します。なぜなら、<xref:System.Data.DataView> により、フィルター処理および並べ替え処理をサポートするためのインデックスが構築されるからです。  <xref:System.Data.DataView.RowFilter%2A> プロパティまたは <xref:System.Data.DataView.Sort%2A> プロパティを設定すると、データのインデックスが再構築され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。  可能な場合は、<xref:System.Data.DataView> を最初に作成するときにフィルター処理および並べ替え情報を指定して、後で情報を変更するのを避けてください。  
  
## 参照  
 [Data Binding and LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)   
 [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)   
 [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
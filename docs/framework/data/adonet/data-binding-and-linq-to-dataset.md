---
title: "Data Binding and LINQ to DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Data Binding and LINQ to DataSet
*データ バインド*とは、アプリケーションの UI とビジネス ロジックの間の接続を確立する処理です。  バインドが適切に設定され、データから適切な通知が提供される場合、データの値が変更されると、そのデータにバインドされている要素に変更が自動的に反映されます。  <xref:System.Data.DataSet> はメモリ内データ表現であり、含まれているデータ ソースとは関係なく、一貫性のあるリレーショナル プログラミング モデルを提供します。  ADO.NET 2.0 の <xref:System.Data.DataView> では、<xref:System.Data.DataTable> に格納されているデータの並べ替えとフィルター処理を行うことができます。  この機能は、データ バインド アプリケーションで一般に使用されます。  <xref:System.Data.DataView> を使用すると、さまざまな並べ替え順序を使用してテーブルのデータを公開したり、行の状態やフィルター式に基づいてデータをフィルター処理したりできます。  <xref:System.Data.DataView> オブジェクトの詳細については、「[DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)」を参照してください。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、開発者は、[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] を使用して、<xref:System.Data.DataSet> に対する複雑で強力なクエリを作成できます。  ただし、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリは、バインド シナリオで簡単に使用できない <xref:System.Data.DataRow> オブジェクトの列挙を返します。バインドを容易にするには、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリから <xref:System.Data.DataView> を作成します。  この <xref:System.Data.DataView> は、クエリに指定されているフィルター処理および並べ替え処理を使用しますが、よりデータ バインドに適しています。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] は、文字列ベースのフィルター処理および並べ替え処理よりもはるかに複雑で強力な [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 式ベースのフィルター処理および並べ替え処理を提供することで、<xref:System.Data.DataView> の機能を拡張します。  
  
 <xref:System.Data.DataView> はクエリ自体を表すもので、クエリに基づくビューではありません。  単純なデータ バインド モデルを提供する場合、<xref:System.Data.DataView> は、<xref:System.Windows.Forms.DataGrid> や <xref:System.Windows.Forms.DataGridView> などの UI コントロールにバインドされます。  当該テーブルの既定のビューを提供する場合、<xref:System.Data.DataView> は、<xref:System.Data.DataTable> から作成することもできます。  
  
## このセクションの内容  
 [Creating a DataView Object](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 <xref:System.Data.DataView> の作成に関する情報を提供します。  
  
 [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView> を使用してフィルター処理する方法について説明します。  
  
 [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 <xref:System.Data.DataView> を使用して並べ替えを行う方法について説明します。  
  
 [Querying the DataRowView Collection in a DataView](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 <xref:System.Data.DataView> が公開する <xref:System.Data.DataRowView> コレクションを照会する方法について説明します。  
  
 [DataView Performance](../../../../docs/framework/data/adonet/dataview-performance.md)  
 <xref:System.Data.DataView> およびパフォーマンスに関する情報を提供します。  
  
 [How to: Bind a DataView Object to a Windows Forms DataGridView Control](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 <xref:System.Data.DataView> オブジェクトを <xref:System.Windows.Forms.DataGridView> にバインドする方法について説明します。  
  
## 参照  
 [Programming Guide](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
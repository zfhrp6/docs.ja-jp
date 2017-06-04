---
title: "Loading Data Into a DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Loading Data Into a DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] で <xref:System.Data.DataSet> オブジェクトに対するクエリを実行するには、まずデータセットにデータを読み込んでおく必要があります。  <xref:System.Data.DataSet> には、複数の方法でデータを読み込むことができます。  たとえば、[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] を使用してデータベースに対するクエリを実行し、その結果を <xref:System.Data.DataSet> に読み込む方法です。  詳細については、「[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
 データを <xref:System.Data.DataSet> に読み込む一般的な方法としては、他にも <xref:System.Data.Common.DataAdapter> クラスを使用してデータベースからデータを取得する方法もあります。  この例を次に示します。  
  
## 例  
 この例では、<xref:System.Data.Common.DataAdapter> を使用して、2002 年度の売上情報を照会するクエリを AdventureWorks データベースに対して実行し、その結果を <xref:System.Data.DataSet> に読み込んでいます。  <xref:System.Data.DataSet> への読み込みが完了した後、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用して、そのデータセットに対するクエリを作成できます。  この例の `FillDataSet` メソッドは、「[LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)」のクエリ例で使用されています。  詳細については、「[Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)」を参照してください。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## 参照  
 [LINQ to DataSet Overview](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)   
 [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
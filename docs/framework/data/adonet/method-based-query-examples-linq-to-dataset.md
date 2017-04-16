---
title: "Method-Based Query Examples (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Method-Based Query Examples (LINQ to DataSet)
このセクションでは、標準クエリ演算子を使った [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] プログラミングの例をメソッド ベースのクエリ構文を中心に紹介しています。  これらの例に使用されている <xref:System.Data.DataSet> のデータは、`FillDataSet` メソッド \(「[Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)」を参照\) を使って読み込みます。  詳細については、「[Standard Query Operators Overview](../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  
  
## このセクションの内容  
 [Projection](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Select%2A> メソッドおよび <xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
 [Partitioning](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Skip%2A> メソッドおよび <xref:System.Linq.Enumerable.Take%2A> メソッドを使って <xref:System.Data.DataSet> を照会し、結果をパーティション分割する例を取り上げます。  
  
 [Ordering](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A>、<xref:System.Linq.Enumerable.ThenByDescending%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、結果を並べ替える例を取り上げます。  
  
 [Set Operators](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A>、<xref:System.Linq.Enumerable.Union%2A> の各演算子を使って、データ行の集合に対する値ベースの比較操作を実行する例を取り上げます。  
  
 [Conversion Operators](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A>、<xref:System.Linq.Enumerable.ToList%2A> の各メソッドを使ってクエリ式を即時実行する例を示しています。  
  
 [Element Operators](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.First%2A> メソッドおよび <xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用して <xref:System.Data.DataSet> から <xref:System.Data.DataRow> 要素を取得する例を取り上げます。  
  
 [Aggregate Operators](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Sum%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、データを集計する例を取り上げます。  
  
 [Join](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドおよび <xref:System.Linq.Enumerable.Join%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
## 参照  
 [Query Expression Examples](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)   
 [DataSet\-Specific Operator Examples](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)   
 [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
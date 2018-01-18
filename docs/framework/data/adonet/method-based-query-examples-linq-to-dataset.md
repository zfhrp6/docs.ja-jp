---
title: "メソッド ベースのクエリ例 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1c34420d567e030eb681dbe90a4154e7b709daf7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-examples-linq-to-dataset"></a>メソッド ベースのクエリ例 (LINQ to DataSet)
このセクションでは、標準クエリ演算子を使った [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] プログラミングの例をメソッド ベースのクエリ構文を中心に紹介しています。 <xref:System.Data.DataSet>これらの例で使用されるを使用して設定されます、`FillDataSet`で指定されているメソッド[、データセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)します。 詳細については、次を参照してください。[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [射影](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Select%2A> メソッドおよび <xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
 [パーティション分割](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Skip%2A> メソッドおよび <xref:System.Linq.Enumerable.Take%2A> メソッドを使って <xref:System.Data.DataSet> を照会し、結果をパーティション分割する例を取り上げます。  
  
 [順序付け](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A>、<xref:System.Linq.Enumerable.ThenByDescending%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、結果を並べ替える例を取り上げます。  
  
 [集合演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A>、<xref:System.Linq.Enumerable.Union%2A> の各演算子を使って、データ行の集合に対する値ベースの比較操作を実行する例を取り上げます。  
  
 [変換演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A>、<xref:System.Linq.Enumerable.ToList%2A> の各メソッドを使ってクエリ式を即時実行する例を示しています。  
  
 [要素演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.First%2A> メソッドおよび <xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用して <xref:System.Data.DataRow> から <xref:System.Data.DataSet> 要素を取得する例を取り上げます。  
  
 [集計演算子](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Sum%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、データを集計する例を取り上げます。  
  
 [Join](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドおよび <xref:System.Linq.Enumerable.Join%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
## <a name="see-also"></a>参照  
 [クエリ式の例](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 [DataSet 固有の演算子の例](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

---
title: "クエリ式の例 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1967575aa7a287064d6da54d929ce095e89ee24f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-examples-linq-to-dataset"></a>クエリ式の例 (LINQ to DataSet)
このセクションでは、標準クエリ演算子を使った [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] プログラミングの例を、クエリ式の構文を中心に説明します。 <xref:System.Data.DataSet>これらの例で使用されるを使用して設定されます、`FillDataSet`で指定されているメソッド[、データセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)します。 詳細については、次を参照してください。[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクション](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Select%2A> メソッドおよび <xref:System.Linq.Enumerable.SelectMany%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
 [制限](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Where%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
 [パーティション分割](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Skip%2A> メソッドおよび <xref:System.Linq.Enumerable.Take%2A> メソッドを使って <xref:System.Data.DataSet> を照会し、結果をパーティション分割する例を取り上げます。  
  
 [順序付け](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 このトピックでは、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A>、<xref:System.Linq.Enumerable.ThenByDescending%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、結果を並べ替える例を取り上げます。  
  
 [要素演算子](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.First%2A> メソッドおよび <xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用して <xref:System.Data.DataRow> から <xref:System.Data.DataSet> 要素を取得する例を取り上げます。  
  
 [集計演算子](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Sum%2A> の各メソッドを使って <xref:System.Data.DataSet> を照会し、データを集計する例を取り上げます。  
  
 [結合演算子](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 このトピックでは、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドおよび <xref:System.Linq.Enumerable.Join%2A> メソッドを使って <xref:System.Data.DataSet> を照会する例を取り上げます。  
  
## <a name="see-also"></a>関連項目  
 [メソッド ベースのクエリ例](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 [データセット固有の演算子の例](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

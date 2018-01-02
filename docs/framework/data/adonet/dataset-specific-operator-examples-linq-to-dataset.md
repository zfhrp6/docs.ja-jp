---
title: "DataSet 固有の演算子の例 (LINQ to DataSet)"
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
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 74b6af309bf595e0caaf4e81ab0192bcda7dde35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a>DataSet 固有の演算子の例 (LINQ to DataSet)
このトピックでは、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドおよび <xref:System.Data.DataRowComparer> クラスの使用例を紹介しています。  
  
 `FillDataSet`でこれらの例で使用されるメソッドが指定された[、データセットにデータを読み込む](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)します。  
  
 このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。  
  
 このトピックの例では、次を使用して`using` / `Imports`ステートメント。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 詳細については、次を参照してください。[する方法: Visual Studio でデータセット プロジェクトに LINQ 作成](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md)です。  
  
## <a name="copytodatatable"></a>CopyToDataTable  
  
### <a name="example"></a>例  
 この例では、<xref:System.Data.DataTable> メソッドを使用して、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> にクエリ結果を読み込みます。  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a>DataRowComparer  
  
### <a name="example"></a>例  
 この例では 2 つの異なるデータ行を <xref:System.Data.DataRowComparer> を使用して比較します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a>参照  
 [DataSet へのデータの読み込み](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)

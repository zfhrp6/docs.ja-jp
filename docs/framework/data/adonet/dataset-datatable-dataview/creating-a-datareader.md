---
title: "DataReader の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DataReader の作成
<xref:System.Data.DataTable> クラスおよび <xref:System.Data.DataSet> クラスには、<xref:System.Data.DataTable> の内容または <xref:System.Data.DataSet> オブジェクトの <xref:System.Data.DataSet.Tables%2A> コレクションの内容を、読み取り専用で前方参照専用の 1 つ以上の結果セットとして返す <xref:System.Data.DataTable.CreateDataReader%2A> メソッドがあります。  
  
## 例  
 <xref:System.Data.DataTable> インスタンスを作成するコンソール アプリケーションの例を次に示します。  このアプリケーションは、データが格納された <xref:System.Data.DataTable> `` を、<xref:System.Data.DataTable.CreateDataReader%2A> メソッドを呼び出すプロシージャに渡します。このメソッドは、<xref:System.Data.DataTableReader> 内に格納された結果の反復処理を行います。  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 この例では、次の出力がコンソール ウィンドウに表示されます。  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## 参照  
 <xref:System.Data.DataTable.CreateDataReader%2A>   
 <xref:System.Data.DataSet.CreateDataReader%2A>   
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
---
title: "DataTableReaders | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTableReaders
<xref:System.Data.DataTableReader> は、<xref:System.Data.DataTable> または <xref:System.Data.DataSet> の内容を、読み取り専用かつ前方参照専用の 1 つ以上の結果セットとして表します。  
  
 **DataTable** から **DataTableReader** を作成すると、**DataTableReader** オブジェクトには、その作成元である **DataTable** と同一データ \(ただし、Deleted とマークされた行は除く\) を持つ結果セットが 1 つ設定されます。  各列は、元の **DataTable** と同じ順序で格納されます。  
  
 <xref:System.Data.DataSet.CreateDataReader%2A> の呼び出しにより **DataTableReader** を作成した場合、**DataTableReader** に複数の結果セットが含まれる場合があります。  結果は、**DataSet** オブジェクトの <xref:System.Data.DataSet.Tables%2A> コレクション内の **DataTables** と同じ順序になります。  
  
## このセクションの内容  
 [DataReader の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 **DataTableReader** オブジェクトの作成方法について説明します。  
  
 [DataTable の移動](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 **Read** メソッドを使用して、**DataTableReader** の内容を取得する方法について説明します。  
  
## 参照  
 [ADO.NET でのデータの取得および変更](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
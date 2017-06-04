---
title: "AutoIncrement 列の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# AutoIncrement 列の作成
列値を一意にするために、新しい行がテーブルに追加されたときに列値が自動的にインクリメントされるように設定できます。  自動インクリメント <xref:System.Data.DataColumn> を作成するには、列の <xref:System.Data.DataColumn.AutoIncrement%2A> プロパティを **true** に設定します。  <xref:System.Data.DataColumn> の値は <xref:System.Data.DataColumn.AutoIncrementSeed%2A> プロパティで定義された値から開始され、行が追加されるたびに、**AutoIncrement** 列の値には、列の <xref:System.Data.DataColumn.AutoIncrementStep%2A> プロパティで定義された値が加算されます。  
  
 **AutoIncrement** 列では、**DataColumn** の <xref:System.Data.DataColumn.ReadOnly%2A> プロパティを **true** に設定することをお勧めします。  
  
 値 200 から開始して 3 ずつインクリメントする列を作成する方法を次の例に示します。  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## 参照  
 <xref:System.Data.DataColumn>   
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
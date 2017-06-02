---
title: "DataView の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataView の作成
<xref:System.Data.DataView> は 2 とおりの方法で作成できます。  **DataView** コンストラクターを使用するか、または <xref:System.Data.DataTable> の <xref:System.Data.DataTable.DefaultView%2A> プロパティへの参照を作成します。  空の **DataView** コンストラクターを使用できます。また、**DataView** コンストラクターでは、**DataTable** を 1 つの引数としてとるか、またはフィルター条件、並べ替え条件、および行状態フィルターと共に **DataTable** を使用します。  **DataView** で使用できるその他の引数については、「[データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)」を参照してください。  
  
 **DataView** のインデックスが作成されるのは、**DataView** が作成される時点と、**Sort**、**RowFilter**、または **RowStateFilter** の各プロパティが変更される時点であるため、**DataView** の作成時に初期の並べ替え順序または初期フィルター条件をコンストラクター引数として指定すると、パフォーマンスを最大限に引き出すことができます。  並べ替え条件やフィルター条件を指定せずに **DataView** を作成してから、**Sort**、**RowFilter**、または **RowStateFilter** の各プロパティを設定すると、インデックスが少なくとも 2 回作成されます。これは、**DataView** の作成時点と、並べ替えプロパティまたはフィルター プロパティの変更時です。  
  
 引数をとらないコンストラクターを使用して **DataView** を作成すると、**Table** プロパティを設定していない間は、**DataView** が使用できます。  
  
 **DataView** コンストラクターを使用して **DataView** を作成するコード サンプルを次に示します。  **DataTable** と共に **RowFilter**、**Sort** 列、および **DataViewRowState** が指定されています。  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 テーブルの **DefaultView** プロパティを使用して **DataTable** の既定の **DataView** への参照を取得するコード サンプルを次に示します。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## 参照  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [データの並べ替えとフィルター処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)
---
title: "AcceptChanges と RejectChanges | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# AcceptChanges と RejectChanges
<xref:System.Data.DataTable> 内のデータに行われた変更が正確であるかどうかを検証した後で、<xref:System.Data.DataRow>、<xref:System.Data.DataTable>、または <xref:System.Data.DataSet> の <xref:System.Data.DataRow.AcceptChanges%2A> メソッドを使用して、変更を受け入れることができます。変更を受け入れると、**Current** 行値が **Original** 値に設定され、**RowState** プロパティが **Unchanged** に設定されます。  変更を受け入れるかまたは拒否すると、**RowError** 情報が削除され、**HasErrors** プロパティが **false** に設定されます。  変更を受け入れるかまたは拒否した場合、データ ソース内で実行中の更新操作にも影響することがあります。  詳細については、「[DataAdapter によるデータ ソースの更新](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)」を参照してください。  
  
 **DataTable** に外部キー制約が存在する場合、**AcceptChanges** と **RejectChanges** を使用して受け入れられた変更または拒否された変更は、**ForeignKeyConstraint.AcceptRejectRule** に基づいて **DataRow** の子の行に反映されます。  詳細については、「[DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)」を参照してください。  
  
 行にエラーがあるかどうかをチェックし、必要に応じてエラーを解決し、エラーを解決できない場合にはその行を拒否する例を次に示します。  解決されたエラーについては、**RowError** 値が空の文字列にリセットされるため、**HasErrors** プロパティが **false** に設定されます。  エラーのある行がすべて解決または拒否された時点で、**DataTable** 全体に対するすべての変更を受け入れるために、**AcceptChanges** が呼び出されます。  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## 参照  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)